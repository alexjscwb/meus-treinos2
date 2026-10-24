# Meus Treinos — versão instalável (PWA)

Este pacote preserva o aplicativo HTML original e adiciona manifesto, ícones e service worker para instalação na tela inicial e funcionamento offline após o primeiro carregamento.

## Como publicar

O app precisa ser servido em HTTPS (ou localhost). Abrir `index.html` diretamente como arquivo (`file://`) NÃO permite instalar corretamente como PWA.

**Opção prática — GitHub Pages:** crie um repositório, envie os arquivos mantendo a estrutura, ative Settings > Pages > Deploy from a branch > main / (root) e use o endereço HTTPS fornecido pelo GitHub. O arquivo inicial deve se chamar `index.html`, como neste pacote.

**Android / Chrome:** abra o endereço HTTPS e use o menu > Instalar app / Adicionar à tela inicial, conforme as opções mostradas pelo navegador.

**iPhone / Safari:** abra no Safari > Compartilhar > Adicionar à Tela de Início > Adicionar.

## Atenção aos seus dados

O app original salva informações no `localStorage` do navegador. Esse armazenamento depende da origem do site (endereço). Dados gravados via `file://` ou outro domínio NÃO migrarão automaticamente para o novo domínio HTTPS. Antes de migrar, exporte os registros no app antigo; no novo endereço, importe os dados suportados pela função CSV. O CSV pode não abranger todas as configurações e rotinas: confira o que é preservado antes de abandonar o arquivo antigo. Não limpe os dados do site sem cópia de segurança.

Após o primeiro carregamento online, o aplicativo principal estará em cache para uso offline. Fontes externas do Google podem não estar disponíveis na primeira utilização offline; o navegador usará fontes de sistema.

## Estrutura

- `index.html`: app original com metadados e registro do service worker
- `manifest.webmanifest`: informações do aplicativo instalável
- `sw.js`: cache offline
- `icons/`: ícones da tela inicial

## Limites

Este pacote é um PWA, não um APK Android nem um aplicativo distribuído pela App Store. Os dados permanecem locais, sem sincronização em nuvem. Não foi realizada uma bateria de testes em dispositivos físicos.
