# Catálogo de transmissões

Os IDs de YouTube são de emissões específicas: podem mudar quando o operador reinicia uma transmissão. Para atualizar, confirme a emissão no canal oficial e altere `src/Soundscapes.ts`; depois compile novamente. Não use o endereço `/live` diretamente como `youtubeId`.

## TVs e notícias em direto

| Entrada | Idioma | YouTube ID | Fonte oficial | Verificação |
| --- | --- | --- | --- | --- |
| Euronews em Português | Português | `XuZAl-ZPEcA` | [Vídeo existente](https://www.youtube.com/watch?v=XuZAl-ZPEcA) | Mantido do catálogo anterior; não revalidado nesta atualização |
| Bloomberg Television | Inglês | `QB5BNdBFujE` | [Bloomberg Television](https://www.youtube.com/@markets/live) | 2026-09-03: live ativa, autor Bloomberg Television, reprodução e incorporação permitidas na resposta do YouTube |
| France 24 English | Inglês | `HvZt-nh9sGg` | [France 24 English](https://www.youtube.com/@France24_en/live) | 2026-09-03: live ativa, autor FRANCE 24 English, reprodução e incorporação permitidas na resposta do YouTube |
| DW News | Inglês | `LuKwFajn37U` | [DW News](https://www.youtube.com/@dwnews/live) | 2026-09-03: live ativa, autor DW News, reprodução e incorporação permitidas na resposta do YouTube |
| Al Jazeera English | Inglês | `gCNeDWCI0vo` | [Al Jazeera English](https://www.youtube.com/@aljazeeraenglish/live) | 2026-09-03: live ativa, autor Al Jazeera English, reprodução e incorporação permitidas na resposta do YouTube |

Estas verificações consultaram os metadados públicos `isLiveNow`, `playabilityStatus.status` e `playableInEmbed` nas páginas oficiais. Não são testes de reprodução dentro do Obsidian nem garantias de disponibilidade futura ou em todas as regiões.

Todas as entradas desta tabela têm `isTv: true` e `isLiveVideo: true`, aparecem em **News — Live** e podem abrir o painel automaticamente se essa opção estiver ativa.

A ligação `/live` da Sky News apontava para um evento pontual em 2026-09-03; esse evento não foi acrescentado como canal permanente.

## Rádio

- **Portugal — Informação:** TSF, Observador, Antena 1, CM Rádio.
- **Portugal — Música:** RFM, Rádio Comercial, Mega Hits, Cidade FM, Antena 3.
- **Portugal — Relax:** Smooth FM, Oceano Pacífico.
- **International:** BBC World Service, France Info.

Os endereços efetivos encontram-se em `src/Soundscapes.ts`. MP3/AAC usam áudio nativo. A CM Rádio usa HLS: `https://emdireto.cmradio.pt/audio2/output-stream_1.m3u8`.

A emissão HLS da CM Rádio foi reproduzida num browser de teste em 2026-09-03, com som desligado. A compatibilidade dentro do Obsidian ainda precisa de validação manual; os restantes streams não foram todos revalidados nesta atualização.

## Soundscapes e playlists

Mantêm-se 16 soundscapes predefinidos: Lofi beats, Spa, The Sims, Thunderstorm, Fireplace, Birds, Ocean, Jazz, Coffee shop, Yakuza bar, Nintendo, Sky: Children of the Light, Vampire: The Masquerade — Bloodlines, Chill synth, Peaceful piano e Synthwave.

Os IDs de Lofi beats, Nintendo e Peaceful piano foram atualizados com os valores fornecidos pelo mantenedor. Animal Crossing foi removido a pedido do mantenedor. Playlists personalizadas e My Music continuam disponíveis.
