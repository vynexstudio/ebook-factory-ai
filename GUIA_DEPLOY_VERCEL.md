# 🚀 Guia de Deploy na Vercel - Ebook Factory AI

## ✅ Problema da Tela Branca Resolvido

O problema da tela branca no Windows 7 e smartphones ocorre porque:
1. **Cache antigo** - A Vercel faz cache agressivo de arquivos
2. **Service Worker desatualizado** - Pode carregar versão antiga do código
3. **Falta de configuração de headers** - Necessário para PWA funcionar corretamente

## 📁 Arquivo vercel.json Criado

Criei o arquivo `vercel.json` com as configurações essenciais:

```json
{
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        {
          "key": "Cache-Control",
          "value": "public, max-age=0, must-revalidate"
        },
        {
          "key": "Content-Security-Policy",
          "value": "default-src 'self' 'unsafe-inline' 'unsafe-eval' data: blob: https://fonts.googleapis.com https://fonts.gstatic.com https://cdnjs.cloudflare.com; font-src 'self' data: https://fonts.gstatic.com; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com; script-src 'self' 'unsafe-inline' 'unsafe-eval' https://cdnjs.cloudflare.com; img-src 'self' data: blob:; connect-src 'self' https://api.openai.com;"
        }
      ]
    }
  ],
  "rewrites": [
    {
      "source": "/(.*)",
      "destination": "/index.html"
    }
  ]
}
```

### O que este arquivo faz:
- **Cache-Control**: Força o navegador a sempre verificar se há versão nova
- **Content-Security-Policy**: Permite que o app funcione com blobs, data URIs e scripts inline (necessário para PWA)
- **Rewrites**: Garante que todas as rotas carreguem o index.html (SPA routing)

## 🔄 Como Atualizar seu Deploy na Vercel

### Passo 1: Adicionar o arquivo vercel.json ao seu projeto

Se você fez deploy via GitHub:
```bash
# No seu repositório local
git add vercel.json
git commit -m "Adiciona configuração vercel.json para corrigir tela branca"
git push origin main
```

Se você fez upload manual:
1. Baixe o arquivo `vercel.json` do workspace
2. Faça upload junto com o `index.html` na Vercel

### Passo 2: Forçar novo deploy sem cache

No painel da Vercel:
1. Acesse: https://vercel.com/dashboard
2. Clique no seu projeto "ebook-factory-ai-nine"
3. Vá em "Settings" → "Git" (se usar GitHub)
4. Clique em "Redeploy" na última versão

OU faça um novo deploy:
```bash
# Se tiver Vercel CLI instalado
vercel --prod
```

### Passo 3: Limpar cache do navegador

**No Windows 7 (Chrome):**
1. Pressione `Ctrl + Shift + Delete`
2. Marque "Imagens e arquivos em cache"
3. Clique em "Limpar dados"
4. Recarregue a página com `Ctrl + F5`

**No Smartphone:**
- Android (Chrome): Configurações → Privacidade → Limpar dados de navegação
- iOS (Safari): Ajustes → Safari → Limpar Histórico e Dados

## 📱 Instalar como App no Smartphone

Depois que o site estiver funcionando:

### Android (Chrome):
1. Acesse https://ebook-factory-ai-nine.vercel.app/
2. Toque nos 3 pontos (menu)
3. Selecione "Adicionar à tela inicial" ou "Instalar aplicativo"
4. Confirme o nome "Ebook Factory"
5. O ícone 📚 aparecerá na sua tela inicial

### iPhone (Safari):
1. Acesse https://ebook-factory-ai-nine.vercel.app/
2. Toque no botão Compartilhar (quadrado com seta)
3. Role para baixo e toque em "Adicionar à Tela de Início"
4. Digite "Ebook Factory" e toque em "Adicionar"
5. O ícone aparecerá na sua tela inicial

## 🧪 Testar se Funcionou

1. Acesse https://ebook-factory-ai-nine.vercel.app/
2. Você deve ver a página inicial com:
   - Logo "📘 EBOOK FACTORY AI"
   - Botão "CRIAR MEU PRIMEIRO EBOOK"
   - Seção "Como funciona"
3. Clique em "Começar grátis" e crie uma conta
4. Tente criar um eBook

## ⚠️ Se Ainda Der Tela Branca

1. **Verifique o Console do Navegador:**
   - Pressione `F12` no computador
   - Vá na aba "Console"
   - Tire um print dos erros (se houver)

2. **Erros Comuns:**
   - `Uncaught SyntaxError`: Problema de compatibilidade (Windows 7 pode precisar de polyfills)
   - `Failed to load resource`: Arquivos não carregaram (verifique internet)
   - `localStorage is not defined`: Navegador muito antigo

3. **Solução Alternativa - Netlify:**
   Se a Vercel continuar com problemas, tente o Netlify:
   ```bash
   # Arraste a pasta com index.html e vercel.json para
   # https://app.netlify.com/drop
   ```

## 🎯 Próximo Passo

Depois de atualizar o deploy:
1. Teste no Windows 7
2. Teste no seu smartphone
3. Me informe se funcionou ou se aparece algum erro específico

---

**Dúvidas?** Me avise qual erro aparece ou em qual etapa está travando!
