# OpenCut Classic Portable — Windows x64

Edição comunitária não oficial. Base: OpenCut-app/opencut-classic, commit
`cf5e79e919144200294fb9fed22a222592a0aeea`, licença MIT (incluída).
O novo OpenCut-app/OpenCut ainda está em reescrita; seu desktop é uma janela
inicial. Por isso esta edição utiliza o editor Classic.

## Uso

Coloque o `.exe` numa pasta gravável e execute. Não precisa instalar Node,
navegador ou servidor. O executável extrai o runtime para uma pasta temporária
durante a execução. `OpenCut-data`, ao lado do `.exe`, contém projetos, mídias
importadas, preferências e logs. Para transportar ou fazer backup, feche o
programa e copie o executável **e a pasta inteira OpenCut-data**.
Não apague essa pasta: os projetos não são guardados dentro do executável.

Requer Windows x64 compatível com Electron 44 (Windows 10/11).
O binário não possui assinatura digital; o Windows pode indicar editor desconhecido.
O editor usa um servidor exclusivamente em `127.0.0.1:47831`. A porta fixa
mantém o mesmo endereço para armazenamento local. Se estiver ocupada, a abertura
falha com mensagem, sem mudar silenciosamente a localização dos projetos.

## Offline e exportação

O código do editor, runtime Chromium, WASM e recursos públicos estão incluídos.
Importação de arquivos locais e edição não precisam de conta ou banco remoto.
Fontes Google adicionais, bibliotecas online de stickers e modelos de legendas
dependem de downloads. Para trabalho offline, prefira fontes do sistema e mídia
local. A biblioteca Freesound e o envio de feedback foram retirados desta edição.
Recursos inacabados no Classic continuam inacabados.

Exportação usa MediaBunny/WebCodecs: WebM (VP9/Opus) e MP4 (H.264, AAC quando
disponível; upstream pode substituir AAC por Opus). Não há FFmpeg nativo
incluído. Suporte a codecs, WebGPU e desempenho variam conforme GPU/driver.
MP4 com áudio Opus pode ter compatibilidade menor em outros players.
O resultado é montado em memória: projetos longos ou 4K podem exceder a RAM.
Consulte VALIDATION.md para distinguir testes executados de recursos não testados.

## Compilar

No checkout do commit acima, coloque esta pasta em `desktop/` e execute:

```powershell
npx --yes bun@1.2.18 install --frozen-lockfile
npm ci --prefix desktop --workspaces=false
node desktop/node_modules/electron/install.js
node desktop/build-web.cjs
npm --prefix desktop run dist
```

O preparo gera `apps/portable-web/` sem alterar `apps/web/`. Ele inclui somente
as rotas do editor/projetos e corrige seis chamadas de API deixadas incompatíveis
por uma refatoração upstream. A compilação mantém TypeScript habilitado.

O workflow `desktop-windows.yml` faz checkout dessa revisão fixa, aplica o
empacotamento, compila e disponibiliza o EXE e checksum em Actions. Não publica
uma Release automaticamente. Licença MIT e licenças do Electron acompanham o
pacote. Redistribuições devem preservar avisos e licenças das dependências.
