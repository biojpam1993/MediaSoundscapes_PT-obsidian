# Changelog

As versões referem-se ao fork Media Soundscapes PT, não à numeração do Soundscapes original.

## 1.1.0 — 2026-09-03

### Funcionalidades

- Painel lateral de vídeo YouTube, reaberto sem criar outro leitor; fechar mantém o áudio.
- Botão e comando Ver vídeo; abertura automática opcional para canais de TV.
- Novas TVs: Bloomberg Television, France 24 English, DW News e Al Jazeera English, além da Euronews em Português.
- Rádios com modo próprio, separado de My Music, e sem controlos de faixas ou procura temporal.
- Reprodução HLS com hls.js e inclusão da CM Rádio.
- Erros de YouTube, rede e áudio apresentados ao utilizador, com possibilidade de repetir a tentativa.

### Correções e manutenção

- Controlos e rádios disponíveis mesmo quando o YouTube não responde.
- Limpeza dos leitores ao trocar de fonte ou desativar o plugin.
- Preservação de playlists, My Music, `seek()` e `changeMyMusicTrack()`.
- Selector com optgroups e grupo Other para futuras entradas não classificadas.
- Atualização dos IDs de Lofi beats, Nintendo e Peaceful piano; remoção de Animal Crossing.
- Configuração da pasta MP3 sem dependência da antiga API `electron.remote`.
- Build portátil sem caminhos pessoais nem aviso de importação JSON com `assert`.
- README, manifestos, atribuição MIT e avisos das dependências atualizados.
- Avisos gerados a partir do bundle, também incorporados em `main.js`.
- ZIP de instalação reproduzível com `npm run package`; workflows adaptados ao fork e lançamentos em rascunho.

### Validação e limites

- Testes automatizados de reprodução/estado com APIs do Obsidian, YouTube e HLS simuladas.
- Painel inspecionado em browser com YouTube simulado; CM Rádio HLS reproduzida em browser.
- Novas TVs verificadas nas páginas oficiais do YouTube em 2026-09-03.
- Continua pendente o teste manual de reprodução e layout num Obsidian real; não há suporte Mobile.

## 1.0.0 — Base de desenvolvimento do fork

- Identidade Media Soundscapes PT e versão própria a partir do Soundscapes de Andrew McGivery.
- Catálogo de soundscapes YouTube, playlists personalizadas, música MP3 local e rádios portuguesas/internacionais.
- Atribuição e licença MIT originais preservadas.

Esta entrada descreve a base local do projeto; não afirma que a versão 1.0.0 tenha sido publicada no GitHub ou no catálogo comunitário.
