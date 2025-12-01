# INSTRUÇÕES FINAIS DE DEPLOY

Este arquivo ZIP contém a versão final e corrigida do seu projeto, pronta para ser implantada em qualquer plataforma de hospedagem.

## 1. O que foi corrigido e incluído:

| Correção | Descrição |
| :--- | :--- |
| **Contador de Visitantes** | Implementado um backend Node.js/Express com SQLite para armazenar IPs únicos de forma persistente. **O contador agora funciona corretamente entre navegadores e dispositivos.** |
| **Segurança** | Adicionadas bibliotecas como `helmet`, `cors` e `express-rate-limit` para proteger o backend contra ataques comuns. |
| **Bug de Deploy (Patch)** | Removida a referência ao patch obsoleto do `wouter` no `package.json`. |
| **Bug de Deploy (Build)** | Corrigido o comando de build no `package.json` para apontar corretamente para o `client/index.html`. |
| **Bug de Deploy (Node)** | Adicionado o arquivo `.nvmrc` para forçar o uso do Node.js 18 LTS (mais estável). |
| **Remoção Manus** | Todas as referências ao Manus foram removidas. |

## 2. Passos para o Deploy

### A. Preparação

1.  **Baixe o arquivo `portfolio-final-pronto-deploy.zip`**.
2.  **Extraia o conteúdo** em uma pasta no seu computador.
3.  **Suba TODOS os arquivos** dessa pasta para um novo repositório no **GitHub** (ou GitLab/Bitbucket).

### B. Escolha da Plataforma (Crucial)

| Plataforma | Melhor para | O Contador Funciona? |
| :--- | :--- | :--- |
| **Railway / Render** | Projetos Full-Stack (Backend + Frontend) | ✅ **SIM** (Recomendado) |
| **Netlify / Vercel** | Projetos Estáticos (Apenas Frontend) | ❌ **NÃO** (O contador não vai funcionar) |

**Recomendação:** Use **Railway** ou **Render** para garantir que o contador de visitantes funcione.

### C. Configuração de Deploy (Railway/Render)

Ao configurar o serviço na plataforma escolhida, use estas configurações:

| Configuração | Valor |
| :--- | :--- |
| **Build Command** | `pnpm install && pnpm build` |
| **Start Command** | `pnpm start` |
| **Diretório de Publicação** | `dist/public` (para o frontend) |
| **Persistência** | **CRUCIAL:** Configure um volume persistente para o diretório `/app/dist` para salvar o arquivo `visitors.db`. |

### D. Configuração de Deploy (Netlify - Se insistir)

Se você usar o Netlify, use estas configurações:

| Configuração | Valor |
| :--- | :--- |
| **Build Command** | `pnpm run build` |
| **Publish Directory** | `dist/public` |
| **Resultado:** | O site será publicado, mas o contador de visitantes **NÃO VAI FUNCIONAR**. |
