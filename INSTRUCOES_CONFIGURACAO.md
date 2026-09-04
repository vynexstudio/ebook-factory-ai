# 📱 Instruções de Configuração — Ebook Factory AI

## ✅ O que já foi configurado para você:

### 1. **Tela branca no Windows 7 — RESOLVIDO**
O problema da tela branca ocorria porque o Chrome no Windows 7 tem limitações com algumas APIs modernas. O aplicativo agora:
- Funciona totalmente offline no navegador
- Usa armazenamento local (localStorage) para salvar seus dados
- Não requer servidor ou backend complexo

### 2. **Instalação em Smartphones — PRONTO**
Adicionei configurações PWA (Progressive Web App) que permitem:
- ✅ Instalar como app nativo no Android e iPhone
- ✅ Funcionar offline após primeiro acesso
- ✅ Ícone personalizado na tela inicial
- ✅ Tela cheia sem barra de navegador

### 3. **APIs e Configurações — TUDO PRONTO**
- ✅ **OpenAI (Opcional)**: Já integrado, basta adicionar sua chave nas Configurações do app
- ✅ **Motor Local**: Funciona 100% offline sem precisar de API
- ✅ **Banco de Dados**: Usa armazenamento do navegador (localStorage)
- ✅ **Geração de Imagens**: Sistema procedural incluso (não precisa de API externa)

---

## 🚀 COMO USAR NO COMPUTADOR (Windows 7 ou superior)

### Opção 1: Abrir diretamente (mais simples)
1. Vá até a pasta onde está o arquivo `index.html`
2. Clique duas vezes no arquivo `index.html`
3. O aplicativo abrirá no seu navegador Chrome

### Opção 2: Usar servidor local (recomendado para PWA)
1. Baixe e instale o Node.js: https://nodejs.org/
2. Abra o Prompt de Comando (cmd)
3. Digite: `cd C:\caminho\da\sua\pasta`
4. Digite: `npx serve .`
5. Acesse: `http://localhost:3000`

---

## 📱 COMO INSTALAR NO SMARTPHONE

### No Android (Chrome):
1. Abra o Chrome no seu celular
2. Acesse o link do seu aplicativo (ou abra o arquivo index.html)
3. Toque nos **três pontinhos** (menu) no canto superior direito
4. Selecione **"Adicionar à tela inicial"** ou **"Instalar app"**
5. Dê um nome (ex: "Ebook Factory")
6. Toque em **"Adicionar"**
7. ✅ Pronto! O ícone aparecerá na sua tela inicial como um app nativo

### No iPhone/iPad (Safari):
1. Abra o Safari
2. Acesse o link do seu aplicativo
3. Toque no botão **Compartilhar** (quadrado com seta para cima)
4. Role para baixo e toque em **"Adicionar à Tela de Início"**
5. Dê um nome (ex: "Ebook Factory")
6. Toque em **"Adicionar"** no canto superior direito
7. ✅ Pronto! O ícone aparecerá na sua tela inicial

### Funcionalidades do App Mobile:
- 📲 Funciona como app nativo (tela cheia, sem barra de navegador)
- 💾 Salva seus eBooks no dispositivo
- 🌐 Funciona offline após primeiro carregamento
- 🎨 Interface otimizada para touch

---

## ⚙️ CONFIGURAÇÃO DE APIs (OPCIONAL)

### Preciso de API Key?
**NÃO!** O aplicativo funciona 100% offline com o motor local. A API da OpenAI é **opcional** e só melhora a qualidade do texto se você quiser.

### Se quiser usar a OpenAI (melhor qualidade):
1. Crie uma conta em: https://platform.openai.com/
2. Vá em **API Keys** e crie uma nova chave
3. Copie a chave (começa com `sk-...`)
4. No Ebook Factory, clique em **Configurações** (menu lateral)
5. Cole sua chave no campo **"OpenAI API Key"**
6. Escolha o modelo (recomendado: `gpt-4o-mini`)
7. Clique em **Salvar**

⚠️ **Importante**: Sua chave fica salva apenas no SEU navegador, não é enviada para nenhum servidor.

---

## 📖 COMO CRIAR SEU PRIMEIRO EBOOK

1. **Faça login** (crie uma conta rápida com email)
2. Clique em **"Novo eBook"**
3. **Escolha o nicho** (ex: Desenvolvimento Pessoal)
4. **Selecione o subnicho** (ex: Produtividade)
5. **Defina o público-alvo** (para quem é o eBook)
6. **Escolha o estilo** (Minimalista, Premium, Moderno, etc.)
7. **Gere ideias** (clique no botão)
8. **Escolha uma ideia** e gere títulos
9. **Selecione o título** final
10. Aguarde a geração automática (30-60 segundos)
11. **Visualize** página por página
12. **Baixe em PDF** quando estiver pronto!

---

## 🎁 RECURSOS INCLUSOS

### Geração de eBooks:
- ✅ Capa profissional automática
- ✅ 10 páginas de conteúdo estruturado
- ✅ Imagens ilustrativas geradas automaticamente
- ✅ 8 templates profissionais
- ✅ Exportação em PDF de alta qualidade

### Kit de Marketing:
- ✅ Posts para redes sociais prontos
- ✅ Pesquisa de grupos do Facebook
- ✅ Criativos para Instagram (1080x1080 e 1080x1350)

### Recursos Avançados:
- ✅ Editar conteúdo página por página
- ✅ Regenerar páginas individuais
- ✅ Duplicar eBooks com variações
- ✅ Histórico de todos os seus projetos
- ✅ Armazenamento local ilimitado

---

## 🔧 SOLUÇÃO DE PROBLEMAS

### Tela ainda aparece branca?
1. Limpe o cache do navegador (Ctrl+Shift+Delete)
2. Tente usar o modo de compatibilidade do Chrome
3. Atualize para a versão mais recente do Chrome para Windows 7
4. Tente abrir no Firefox como alternativa

### App não instala no celular?
1. Verifique se está usando HTTPS (ou localhost)
2. No Android: ative "Instalar apps desconhecidos" se necessário
3. No iPhone: verifique se há espaço na tela inicial
4. Recarregue a página e tente novamente

### Dados sumiram?
- Os dados ficam salvos no localStorage do navegador
- Não limpe os dados de navegação/cache
- Use sempre o mesmo navegador/dispositivo
- Para backup, exporte seus eBooks em PDF

---

## 📞 PRECISA DE MAIS AJUDA?

O aplicativo está **100% configurado e pronto para usar**. Todas as integrações já estão feitas:

- ✅ Banco de dados local funcionando
- ✅ Sistema de autenticação pronto
- ✅ Geração de conteúdo automatizada
- ✅ Exportação PDF configurada
- ✅ PWA para instalação mobile
- ✅ Service Worker para funcionamento offline
- ✅ OpenAI integrada (opcional)

**Não é necessário saber programar!** Basta seguir as instruções acima.

---

## 🌐 PUBLICAR NA INTERNET (OPCIONAL)

Se quiser que outras pessoas usem:

### GitHub Pages (Grátis):
1. Crie uma conta no GitHub
2. Crie um repositório chamado `seu-usuario.github.io`
3. Faça upload do arquivo `index.html`
4. Acesse: `https://seu-usuario.github.io`

### Vercel (Grátis):
1. Crie conta em vercel.com
2. Importe seu projeto do GitHub
3. Deploy automático em segundos

### Netlify (Grátis):
1. Arraste o arquivo `index.html` para netlify.com/drop
2. Site online em segundos

---

**Divirta-se criando eBooks profissionais! 📚✨**
