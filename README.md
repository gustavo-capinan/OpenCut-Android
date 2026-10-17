# OpenCut Classic Portable — Windows x64

Edição comunitária, não oficial, do editor OpenCut Classic, sem instalador.
Este repositório mantém o nome histórico OpenCut-Android; a entrega atual é para **Windows x64**. Não há APK nesta versão.

## Download e uso

Abra [Releases](https://github.com/gustavo-capinan/OpenCut-Android/releases) e baixe o arquivo **OpenCut-Classic-Portable-0.1.0-win-x64.exe** da versão desktop.

Execute numa pasta gravável. O programa cria **OpenCut-data** ao lado do executável para guardar projetos, mídias e preferências. Ao transportar ou fazer backup, feche o aplicativo e copie o EXE **e essa pasta**.

A edição básica com arquivos locais funciona offline. Fontes adicionais, recursos online e modelos de legendas podem exigir downloads. Projetos longos/4K e todos os codecs não foram validados. O executável não tem assinatura digital.

## Código e compilação

- [Fontes do empacotamento, lockfile e testes](OpenCut-Desktop-Build-Sources.zip).
- [Instruções e limitações](LEIA-ME.md).
- [Relatório da validação local](VALIDATION.md).
- [SHA-256 do executável local](SHA256SUMS.txt).
- [GitHub Actions](https://github.com/gustavo-capinan/OpenCut-Android/actions/workflows/desktop-windows.yml): compila Windows x64, testa e disponibiliza artefatos por 30 dias. O status de cada execução deve ser consultado em Actions.

O workflow extrai a pasta desktop do ZIP versionado e obtém o [Classic oficial](https://github.com/OpenCut-app/opencut-classic) no commit fixo cf5e79e919144200294fb9fed22a222592a0aeea. Para compilar localmente, extraia o ZIP e execute desktop/bootstrap.ps1 com Git e Node.js 24.22.0 instalados.

Licença upstream MIT preservada. Licenças do Electron/Chromium e avisos de dependências acompanham o pacote. O novo OpenCut está em reescrita; esta edição utiliza o Classic para priorizar um editor utilizável.

O relatório local registra o bloqueio anterior da integração GitHub. O envio ao repositório passou a ser possível pela sessão autenticada do navegador em 17/10/2026.
