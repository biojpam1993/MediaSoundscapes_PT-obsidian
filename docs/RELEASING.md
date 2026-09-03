# Preparar uma versão

1. Atualize o catálogo e registe as fontes e verificações em `docs/STREAMS.md`.
2. Atualize `CHANGELOG.md` e `README.md`.
3. Use `npm version <versão> --no-git-tag-version` para sincronizar package, lockfile, manifestos e `versions.json`.
4. Execute `npm ci`, `npm test`, `npm run check:release` e `npm run package`.
5. Teste o ZIP num cofre Obsidian Desktop limpo: instalação, rádio MP3/AAC, CM Rádio HLS, TV, fechar/reabrir painel, música local, playlists, pausa, volume e desativação do plugin.
6. Reveja as alterações e publique apenas depois dessa validação. O workflow Release é manual e cria um **rascunho**; não publica automaticamente.

`npm run package` cria `releases/media-soundscapes-pt-<versão>.zip` com a pasta de plugin no primeiro nível. Não empacota `data.json`, `node_modules`, ficheiros pessoais ou mapas de código fonte. O build escreve todos os artefactos em `dist/`; não edite essa pasta manualmente.

O manifesto beta é mantido como espelho do manifesto atual para compatibilidade com ferramentas que consultem esse nome. Não anuncia uma beta independente. Para uma pré-versão futura, use uma versão como `1.2.0-beta.1`; o workflow identifica o sufixo e marca o rascunho como prerelease. Não existe workflow que faça commits automáticos no repositório nem integração com o projeto GitHub do autor original.

Os avisos de dependências são gerados a partir dos módulos efetivamente incluídos no bundle. Se uma dependência nova não contiver ficheiro de licença, o build falha para permitir revisão. Não substitua licenças de terceiros pela MIT do plugin. `licenses/Apache-2.0.txt` contém a cópia oficial completa da licença usada por hls.js.

Para o futuro catálogo comunitário, a release precisa de `main.js`, `manifest.json` e `styles.css`, com uma tag igual à versão do manifesto (sem prefixo `v`). Os avisos de licença também estão dentro de `main.js`, pois esses três ficheiros são os que o instalador comunitário descarrega. Consulte a [documentação oficial de submissão](https://docs.obsidian.md/plugins/releasing/submit-plugin).

O URL do repositório do fork não é inventado nos metadados. Quando existir um repositório público, acrescente os URLs reais de repository/homepage/bugs em `package.json` e as ligações de downloads e suporte no README.
