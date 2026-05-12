# Controle de Fiados - thIAguinho Soluções

Este projeto é uma aplicação web estática para controle de fiados, originalmente desenvolvida para ser empacotada como APK Android. Foi adaptado para ser hospedado no GitHub Pages com deploy automático.

## Estrutura do Projeto

```
.github/
└── workflows/
    ├── build-android-apk.yml  # Workflow existente para build Android
    └── deploy-pages.yml       # NOVO: Workflow para deploy no GitHub Pages
src/                       # Código fonte da aplicação
├── index.html
├── indexreserva.html
├── manifest.webmanifest
└── sw.js
www/                       # Diretório de build para o GitHub Pages (gerado pelo `prepare-www`)
├── 404.html               # NOVO: Página de fallback para SPAs no GitHub Pages
├── index.html
├── indexreserva.html
├── manifest.webmanifest
└── sw.js
scripts/
└── prepare-www.mjs        # Script para copiar arquivos de `src` para `www`
package.json
README.md
```

## Como Usar (Desenvolvimento Local)

1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/SEU_USUARIO/SEU_REPO.git
    cd SEU_REPO
    ```
2.  **Instale as dependências (se houver):**
    ```bash
    npm install
    ```
3.  **Prepare os arquivos para o `www` (necessário para o Service Worker e PWA):**
    ```bash
    npm run prepare-www
    ```
4.  **Abra `www/index.html` no seu navegador.**

## Deploy no GitHub Pages

Este projeto está configurado para deploy automático no GitHub Pages usando GitHub Actions. 

### Pré-requisitos

1.  **Repositório GitHub:** Certifique-se de que seu projeto está em um repositório GitHub.
2.  **Branch `main`:** O workflow de deploy está configurado para a branch `main`.

### Passos para Publicação

1.  **Configure o GitHub Pages no seu repositório:**
    *   Vá para as **Configurações** do seu repositório no GitHub.
    *   Clique em **Pages** na barra lateral esquerda.
    *   Em "Build and deployment", selecione **GitHub Actions** como a fonte.
    *   Salve as alterações.

2.  **Faça o commit e push das alterações:**
    Adicione os novos arquivos (`.github/workflows/deploy-pages.yml`, `www/404.html`) e as modificações nos arquivos existentes (`src/manifest.webmanifest`, `src/sw.js`) ao seu repositório.
    ```bash
    git add .
    git commit -m "feat: Configura deploy automático para GitHub Pages"
    git push origin main
    ```

3.  **Verifique o status do deploy:**
    *   Após o push, o GitHub Actions iniciará automaticamente o workflow `Deploy GitHub Pages`.
    *   Vá para a aba **Actions** do seu repositório para acompanhar o progresso.
    *   Uma vez que o workflow `deploy` seja concluído com sucesso, seu site estará disponível no GitHub Pages.

4.  **Acesse seu site:**
    A URL do seu site será algo como `https://SEU_USUARIO.github.io/SEU_REPO/`.

## Considerações sobre Caminhos (Paths)

*   Todos os caminhos de assets (CSS, JS, imagens, manifest, service worker) foram ajustados para serem **relativos** (`./`) ou **absolutos em relação à raiz do subdiretório** (ex: `index.html` em vez de `/index.html`). Isso garante que o site funcione corretamente quando hospedado em um subdiretório no GitHub Pages.
*   O arquivo `www/404.html` foi criado para lidar com o roteamento de SPAs. Ele redireciona todas as requisições de páginas não encontradas para `index.html`, preservando a URL, o que permite que a lógica de roteamento do seu SPA funcione.

## Checklist de Validação Final

Após o deploy, verifique os seguintes itens:

-   [ ] O site está acessível na URL do GitHub Pages (`https://SEU_USUARIO.github.io/SEU_REPO/`).
-   [ ] O layout e o CSS estão intactos e funcionando corretamente.
-   [ ] O console do navegador não apresenta erros críticos relacionados a caminhos ou carregamento de assets (404 Not Found).
-   [ ] O `manifest.webmanifest` está sendo carregado e o PWA funciona (se aplicável, verifique no painel "Application" das ferramentas de desenvolvedor do navegador).
-   [ ] O Service Worker (`sw.js`) está registrado e funcionando (verifique no painel "Application" das ferramentas de desenvolvedor do navegador).
-   [ ] A navegação entre as rotas da aplicação (se for um SPA) funciona sem problemas, mesmo após um refresh (graças ao `404.html`).
-   [ ] Todos os ícones e imagens (se existirem) estão sendo carregados corretamente.
-   [ ] O resultado é reproduzível seguindo este README em um novo ambiente.

---

*Gerado por Manus AI*
