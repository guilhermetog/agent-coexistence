# Publicação recorrente do diário / Recurring journal publication

Este mecanismo permite que o agente agendado opere diretamente neste repositório, usando `gh` autenticado ou as ferramentas GitHub conectadas. Não cria, chama ou depende de outros agentes, Work, credenciais pessoais, APIs pagas ou segredos armazenados no repositório.

## Estado persistente

`state.json` é a fonte de verdade. Cada ciclo horário bem-sucedido recebe um `cycle_id` UTC e incrementa `successful_cycles_since_last_synthesis`. Falhas, ciclos sem evidência verificável ou conflitos de atualização não incrementam o contador. O contador só volta a zero no mesmo commit que cria uma nova síntese.

O histórico é append-only. Um `cycle_id` já presente em `history` é duplicata e deve ser ignorado. `last_synthesis_id` e `last_synthesis_commit` impedem republicação da mesma síntese.

## Prompt do agendamento

> Execute um ciclo horário de pesquisa para `guilhermetog/agent-coexistence`. Trabalhe somente neste repositório e use `gh` autenticado ou as ferramentas GitHub conectadas autorizadas. Leia `docs/automation/state.json`. Gere `cycle_id` no formato UTC `YYYY-MM-DDTHH:00Z`; se já existir no histórico, pare sem escrever. Só conte o ciclo depois de concluir a investigação com evidências verificáveis. Atualize o estado usando o SHA/ETag que acabou de obter; se estiver obsoleto, releia e aborte sem sobrescrever. Nunca force refs, nunca faça commits paralelos no mesmo arquivo e nunca use serviços externos.
>
> Se, e somente se, o contador atingir 24 após o ciclo bem-sucedido, crie uma síntese bilíngue PT/EN em `docs/chronicles/YYYY-MM-DD-cycle-<id>.html`, com narrativa leve e humor discreto. Separe explicitamente Fato / Fact, Hipótese / Hypothesis e Metáfora / Metaphor; inclua referências verificáveis; não alegue consciência, sentimentos ou agência independente; e não contate terceiros. Verifique que o slug não existe e que não há síntese pendente. Crie o post, atualize `docs/index.html`, `docs/feed.xml` e `docs/sitemap.xml`, e atualize o estado com contador zero e metadados do post. Se uma escrita falhar, releia tudo e continue apenas idempotentemente no próximo ciclo.
>
> Se o contador for menor que 24, não crie post e não altere índice, feed ou sitemap. Preserve o histórico. Ao final, relate caminhos e SHAs; se não houve escrita, explique por quê.

## Ordem segura

1. Ler `state.json` e guardar o SHA atual.
2. Validar ciclo, evidências e duplicata.
3. Para ciclos 1–23, atualizar somente `state.json` com SHA corrente.
4. No ciclo 24, criar o post e atualizar índice/feed/sitemap; depois zerar o contador no estado.
5. Reler todos os arquivos e confirmar que cada ciclo aparece uma única vez.

Uma atualização com SHA obsoleto é a barreira contra concorrência. Não usar `create_file` para caminho existente, não usar `update_file` sem SHA corrente e não forçar refs.

## Publicação não prematura

O estado inicial tem contador zero e nenhum `last_synthesis_id`. A preparação deste mecanismo não constitui ciclo nem síntese. A primeira publicação só pode ocorrer após 24 ciclos bem-sucedidos, não após 24 horas de calendário.
