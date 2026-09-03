# Media Soundscapes PT

**Versão 1.1.0.** Um leitor de som ambiente, televisão em direto, rádio e música local para o Obsidian Desktop, com controlos na barra de estado e um painel lateral de vídeo.

Desenvolvido por **João P. Marques** a partir do [Soundscapes original](https://github.com/andrewmcgivery/obsidian-soundscapes), de **Andrew McGivery**. É um fork independente que mantém as funcionalidades originais e acrescenta media portugueses e internacionais.

## O que inclui

| Função | Conteúdo e comportamento |
| --- | --- |
| Soundscapes | 16 ambientes e seleções musicais YouTube |
| TV / News — Live | Euronews em Português, Bloomberg Television, France 24 English, DW News e Al Jazeera English |
| Rádio | 13 estações portuguesas e internacionais, com streams MP3, AAC e HLS |
| Vídeo | Painel lateral; fechar mantém o áudio; abertura automática opcional para TV |
| Custom | Playlists YouTube criadas pelo utilizador |
| My Music | Biblioteca MP3 local com navegação, procura temporal e reprodução aleatória |
| Controlos | Reproduzir, pausar, volume e selector agrupado; erros visíveis com nova tentativa |

Os detalhes, IDs e datas de verificação estão em [Catálogo de transmissões](docs/STREAMS.md). As alterações da versão estão em [CHANGELOG.md](CHANGELOG.md).

## Instalar num Obsidian limpo

Requer **Obsidian Desktop 1.5.0 ou superior**, em Windows, macOS ou Linux. Não requer Node.js, npm, Python, outro plugin ou uma conta de rádio. YouTube e rádios precisam de Internet. O plugin não suporta Obsidian Mobile.

Enquanto este fork não estiver publicado nos Community Plugins, a instalação é manual:

1. Descompacte o ZIP de distribuição.
2. Copie a pasta `media-soundscapes-pt` para `<cofre>/.obsidian/plugins/`. Crie a pasta `plugins` se não existir. Se o cofre usar uma pasta de configuração diferente de `.obsidian`, use essa pasta.
3. Confirme que `main.js`, `manifest.json` e `styles.css` estão diretamente dentro de `plugins/media-soundscapes-pt/`, sem outra pasta `dist` pelo meio. Mantenha também os ficheiros de licença incluídos.
4. No Obsidian, abra **Definições → Plugins da comunidade**, permita plugins da comunidade e ative **Media Soundscapes PT**. Se não aparecer, reinicie o Obsidian.
5. Escolha uma entrada no selector da barra de estado e prima Reproduzir. A reprodução automática está desligada por defeito.

A estrutura segue as [instruções oficiais de plugins do Obsidian](https://docs.obsidian.md/Plugins/Getting%20started/Build%20a%20plugin).

O ZIP inclui as dependências de execução no `main.js`, incluindo o leitor HLS. Não copie `node_modules`, código fonte nem ficheiros de configuração de outro utilizador. A instalação do plugin original “Soundscapes” no catálogo não instala este fork.

## Atualizar uma instalação existente

Desative o plugin, substitua os ficheiros da pasta `media-soundscapes-pt` pelos do novo ZIP e volte a ativá-lo. **Preserve o seu `data.json`**, que contém definições, playlists e o índice de música; o ZIP não inclui esse ficheiro. Se usava uma pasta de desenvolvimento com outro nome, faça uma cópia de segurança das definições antes de passar para a pasta com o ID oficial.

## Usar

- O selector agrupa Soundscapes, notícias em direto, rádios portuguesas, rádios internacionais, playlists Custom e My Music. Entradas novas sem classificação aparecem em Other.
- **Ver vídeo:** escolha Euronews ou outro vídeo YouTube e prima o botão de TV na barra de estado. Também pode usar o comando **Media Soundscapes PT: Ver vídeo**. O painel abre na lateral e pode ser redimensionado. Fechá-lo mantém o áudio; reabri-lo utiliza o mesmo leitor.
- **TV automática:** ative **Abrir vídeo automaticamente para TV** nas definições do plugin. Esta opção aplica-se aos canais marcados como TV, como a Euronews, e não a todas as emissões musicais em direto.
- O vídeo funciona na janela principal do Obsidian. Se mover o painel para uma janela separada, volte a colocá-lo na janela principal para ver a imagem.
- **Rádio:** MP3/AAC usam o leitor de áudio; HLS (`.m3u8`), incluindo CM Rádio, usa a biblioteca hls.js quando necessário. As rádios têm reprodução, pausa e volume, sem avanço/recuo de faixas nem procura temporal.
- **My Music:** indique o caminho completo de uma pasta com ficheiros MP3 nas definições e prima **Re-index now**. Depois escolha My Music e abra a biblioteca pelo ícone musical na barra lateral. A configuração é individual e opcional; não é necessária para rádio ou vídeo.
- **Custom:** crie playlists YouTube nas definições. As playlists com faixas aparecem no selector e mantêm os controlos de avanço/recuo.

## Quando uma emissão não funciona

O plugin apresenta uma mensagem e um botão de aviso para tentar novamente. No painel de vídeo existe também uma ligação **Abrir no YouTube**.

Vídeos podem ser removidos, tornar-se privados, ter restrições regionais ou não permitir incorporação. Os servidores de rádio podem ficar indisponíveis ou mudar de endereço. HLS requer um formato compatível e permissão do servidor para os pedidos de rede (CORS). O plugin não contorna essas restrições.

As rádios e a música local continuam disponíveis se o YouTube não carregar. Uma falha numa fonte não implica reinstalar o plugin.

## Rede e dados locais

O plugin carrega a API IFrame do YouTube ao arrancar. A reprodução liga diretamente ao YouTube ou ao servidor da rádio selecionada; esses serviços recebem os pedidos de rede necessários à emissão. O plugin não usa um servidor próprio nem acrescenta um serviço de analítica.

My Music lê os ficheiros MP3 da pasta indicada pelo utilizador e guarda o índice nas definições do plugin, dentro do cofre. O plugin não envia esses ficheiros nem o conteúdo das notas para os operadores das transmissões. A pasta de música não é necessária para usar rádio ou TV.

## Desenvolvimento

```sh
npm ci
npm test
npm run check:release
npm run package
```

Node.js/npm só são necessários para desenvolvimento. O build faz a verificação TypeScript, gera os avisos das dependências e escreve `dist/`. `npm run package` executa o build e cria o ZIP em `releases/`, sem ferramentas de compressão externas. `npm run dev` também escreve em `dist/`; não contém caminhos de cofres específicos de um computador. Os ficheiros compilados nunca devem ser editados manualmente.

Os testes automatizados usam simulações das APIs do Obsidian, YouTube e HLS para verificar arranque, mudança de fonte, painel, erros e limpeza de recursos. Não substituem um teste de reprodução real no Obsidian.

## Créditos e licença

O código original e as modificações deste fork são distribuídos sob **MIT**, com os copyrights de **Andrew McGivery (2023)** e **João P. Marques (modificações, 2025–2026)** preservados em [LICENSE](LICENSE). Consulte também [NOTICE.md](NOTICE.md) para a origem do projeto e o âmbito das alterações.

As bibliotecas incluídas no plugin mantêm as suas licenças: React, React DOM, music-metadata, uuid e outras dependências MIT; hls.js sob Apache-2.0; ieee754 sob BSD-3-Clause. As versões efetivamente compiladas e os textos completos estão em [THIRD-PARTY-NOTICES.txt](THIRD-PARTY-NOTICES.txt), gerado pelo build. Os mesmos avisos estão incorporados no `main.js` para acompanharem também instalações futuras pelo catálogo comunitário.

Os conteúdos e marcas das emissões pertencem aos respetivos autores e operadores. O plugin não representa nem é patrocinado por esses serviços. A licença do software não licencia os vídeos ou as emissões.

## Publicação e validação

O projeto está preparado para gerar um pacote de instalação, mas esta documentação não afirma que já esteja publicado no GitHub ou aceite nos Community Plugins. O workflow de release cria apenas rascunhos quando é executado manualmente. Consulte [Preparar uma versão](docs/RELEASING.md).

A reprodução e o layout ainda precisam de um teste manual num Obsidian real antes de publicação. Os testes automatizados cobrem os estados e a integração com APIs simuladas; a CM Rádio foi reproduzida num browser de teste e as quatro novas TVs foram verificadas nas páginas oficiais do YouTube em 2026-09-03. O suporte a Windows/Linux e ao mínimo declarado de Obsidian não foi validado em máquinas separadas nesta sessão.
