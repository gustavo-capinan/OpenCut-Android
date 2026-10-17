# Validação local — 16 de outubro de 2026 (São Paulo)

## Base e decisão técnica

- Classic: `cf5e79e919144200294fb9fed22a222592a0aeea`, obtido do repositório oficial.
- Licença MIT preservada; avisos de dependências acompanham o binário.
- O README oficial do OpenCut recomenda Classic para uso atual; o README de
  `OpenCut/apps/desktop` descreve a nova aplicação como apenas uma janela.
- Electron 44.8.0 / Chromium incluído, Next.js 16.2.4 standalone, Windows x64.
- Nenhum serviço remoto, login, PostgreSQL, Redis ou Node instalado pelo usuário
  é necessário para abrir o editor e trabalhar com arquivos locais.
- As adaptações são feitas numa cópia gerada. O código upstream é preservado.

## Testes executados

- Compilação de produção e TypeScript: passaram, sem ignorar erros de tipos.
- Empacotamento Windows x64 portable: executado localmente.
- Aplicação empacotada com requisições externas bloqueadas: abriu e criou projeto.
- Importação PNG e WAV; adição às faixas de imagem e áudio: passaram.
- Exportação WebM: VP9, áudio decodificável, duração aproximadamente 5,02 s,
  resolução 640×360; pixels conferidos e áudio não silencioso.
- Exportação MP4: H.264, áudio decodificável, duração aproximadamente 5,016 s,
  resolução 640×360; pixels conferidos e áudio não silencioso.
- A máquina de teste informou suporte a H.264, VP9, AAC e WebGPU.
- Fechar e reabrir: mesmo projeto, mídias e duração preservados.
- Reimportação do MP4 gerado e divisão do clipe em dois pela linha do tempo: passaram.
- Nenhum erro JavaScript capturado pelo teste de uso básico.
- Executável portátil final iniciado diretamente, em caminho com espaços:
  passou. Criação de projeto, pasta adjacente `OpenCut-data` e persistência após
  reiniciar o próprio iniciador portátil foram verificadas.
- Binário final: 116.872.073 bytes; SHA-256
  `664ae024fd63905394011e926206644af06014f8103bbf7a6c2d90881f3d9c21`.
- Assinatura Authenticode consultada: `NotSigned`.
- Resultados detalhados e capturas: `test-results/smoke.json` e `packaged-editor.png`.

O webpack emitiu um aviso genérico sobre async/await no módulo WASM; o WASM
funcionou nos testes do Chromium embarcado. Não desativamos a checagem de tipos.

## Limites da evidência

Teste realizado em uma máquina Windows 10 x64; não é uma matriz de GPUs/Windows.
Não foram validados projetos longos, 4K, todos os codecs de entrada, todas as
operações/efeitos, legendas automáticas ou migrações de projetos antigos.
Exportação acumula o arquivo em memória. Bibliotecas externas e fontes adicionais
podem exigir rede; alguns recursos ainda são incompletos no Classic.
O aplicativo não tem assinatura digital nem mecanismo de atualização automática.
O modo offline do teste bloqueia tráfego externo no contexto do editor; não é
uma auditoria de rede de todo o sistema operacional.

## GitHub

A consulta ao repositório `gustavo-capinan/OpenCut-Android` funcionou, mas a
tentativa de criar README retornou HTTP 403, `Resource not accessible by integration`.
Nada foi publicado pela integração. Nenhum workflow remoto foi executado.
O workflow entregue foi preparado para repetir os comandos validados localmente;
seu funcionamento no runner hospedado só estará confirmado após execução real.
