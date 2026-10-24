# Plano de validação não destrutiva

- Estado inicial: contador `0`, histórico vazio, nenhum post pendente.
- Ciclo válido: incrementa uma vez e registra `cycle_id`.
- Ciclo repetido ou falho: não escreve e não incrementa.
- SHA obsoleto: não sobrescreve; relê o estado e encerra.
- Ciclo 24: só então cria post, atualiza índice/feed/sitemap e zera o contador.
- Reexecução após falha parcial: completa apenas arquivos ausentes, sem novo post.

Esta preparação não cria síntese, não conta ciclo e não republica conteúdo existente.
