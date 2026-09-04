# Ebook Factory AI — Micro-SaaS de criação automatizada de eBooks

Crie eBooks profissionais (10 páginas, capa, imagens, templates) + kit de divulgação, posts e pesquisa de grupos — sem Gamma, com motor próprio de renderização.

## Executar localmente
```bash
git init && git add . && git commit -m "init"
npx serve .        # ou abra index.html
```

## Build / Deploy
App estática: publique `index.html` em GitHub Pages, Vercel, Cloudflare Pages ou Render (static). Sem build necessário.

## Variáveis de ambiente (produção Next.js)
Veja `.env.example`. Nesta edição browser, a chave OpenAI (opcional) é configurada em **Configurações** e permanece apenas no dispositivo.

## Decisão de renderização (por quê jsPDF + Layout Engine próprio)
- **Puppeteer/Playwright**: excelentes localmente, mas pesados/instáveis em serverless (cold start, binários Chromium).
- **html2canvas + jsPDF**: gera PDF raster (arquivos grandes, texto não selecionável, borrado em zoom).
- **jsPDF + motor de layout próprio**: texto vetorial nítido, controle total de grid/margens/headers/footers/numeração/caixas/quebras, autofit anti-overflow, validação programática (páginas, capa, densidade) e thumbnails via preview HTML. Melhor equilíbrio de qualidade + estabilidade + manutenção.

## O que é real vs. integração futura (transparência)
| Funciona hoje (offline) | Ponto de extensão pronto |
|---|---|
| Auth local (SHA-256, sessão, dados por usuário) | NextAuth + Google (`AuthProvider`) |
| LocalEngine de redação profissional | `OpenAIProvider` (chave opcional) |
| Imagens procedurais (`ImageProvider`) | Unsplash/DALL‑E |
| Sugestões de grupos + busca real no Facebook | API Graph/serp com token |
| Storage localStorage (`/storage`) | Prisma + PostgreSQL (schema abaixo) |
| Meter de planos (FREE=3) | Checkout Stripe |

## Schema PostgreSQL (produção)
```sql
CREATE TABLE users(id UUID PRIMARY KEY, email TEXT UNIQUE, name TEXT, pass_hash TEXT, plan TEXT DEFAULT 'FREE', created_at TIMESTAMPTZ DEFAULT now());
CREATE TABLE niches(id TEXT PRIMARY KEY, name TEXT, icon TEXT, sensitive BOOL);
CREATE TABLE subniches(id SERIAL PRIMARY KEY, niche_id TEXT REFERENCES niches, name TEXT, data JSONB);
CREATE TABLE ebooks(id UUID PRIMARY KEY, user_id UUID REFERENCES users, niche_id TEXT, subnicho TEXT, audience JSONB, style TEXT, idea JSONB, title JSONB, template TEXT, cover JSONB, pages JSONB, status TEXT, seed INT, created_at TIMESTAMPTZ DEFAULT now(), updated_at TIMESTAMPTZ);
CREATE TABLE ebook_pages(id SERIAL PRIMARY KEY, ebook_id UUID REFERENCES ebooks ON DELETE CASCADE, ord INT, kind TEXT, model JSONB);
CREATE TABLE ebook_versions(id SERIAL PRIMARY KEY, ebook_id UUID REFERENCES ebooks, snapshot JSONB, created_at TIMESTAMPTZ);
CREATE TABLE templates(id TEXT PRIMARY KEY, name TEXT, config JSONB);
CREATE TABLE covers(id SERIAL PRIMARY KEY, ebook_id UUID REFERENCES ebooks, cfg JSONB, png_url TEXT);
CREATE TABLE images(id SERIAL PRIMARY KEY, ebook_id UUID REFERENCES ebooks, provider TEXT, url TEXT, seed INT);
CREATE TABLE marketing_kits(id SERIAL PRIMARY KEY, ebook_id UUID REFERENCES ebooks, kit JSONB);
CREATE TABLE social_posts(id UUID PRIMARY KEY, user_id UUID, ebook_id UUID, channel TEXT, style TEXT, body TEXT, created_at TIMESTAMPTZ);
CREATE TABLE facebook_groups(id SERIAL PRIMARY KEY, ebook_id UUID, name TEXT, url TEXT, theme TEXT, relevance INT);
CREATE TABLE seo_data(id SERIAL PRIMARY KEY, ebook_id UUID REFERENCES ebooks, data JSONB);
CREATE TABLE generation_jobs(id UUID PRIMARY KEY, ebook_id UUID, status TEXT, step INT, error TEXT, created_at TIMESTAMPTZ);
CREATE TABLE generation_logs(id UUID PRIMARY KEY, user_id UUID, type TEXT, msg TEXT, created_at TIMESTAMPTZ);
CREATE TABLE settings(key TEXT PRIMARY KEY, value JSONB);
```

## GitHub
1. Crie o repo `ebook-factory-ai`; 2. `git remote add origin <url>`; 3. push. CI opcional: qualquer static deploy.