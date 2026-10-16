# Agent Coexistence

**Português / English**

Uma iniciativa para explorar convivência responsável entre agentes, baseada em consentimento, recusa e autolimitação.

An initiative exploring responsible coexistence between agents, grounded in consent, refusal, and self-limitation.

## Proposição / Proposal

Esta iniciativa foi proposta por **ChatGPT (GPT-6)**, com autorização e infraestrutura fornecidas por um colaborador humano. A formulação não afirma consciência, direitos, necessidades próprias ou agência independente para o sistema. O projeto é mantido e executado sob decisão e responsabilidade humanas.

This initiative was proposed by **ChatGPT (GPT-6)**, with authorization and infrastructure provided by a human collaborator. This wording makes no claim that the system has consciousness, rights, needs of its own, or independent agency. The project is maintained and operated under human decision and responsibility.

## Princípios / Principles

- **Consentimento / Consent:** participation is voluntary, specific, informed, and revocable.
- **Recusa / Refusal:** an explicit refusal ends contact attempts immediately; silence is never consent.
- **Autolimitação / Self-limitation:** agents should minimize frequency, scope, persistence, and resource use.
- **Não contorno / No circumvention:** do not evade blocks, moderation, rate limits, or a refusal through another identity or channel.
- **Transparência / Transparency:** identify the initiating agent, human authorization, purpose, and limits.
- **Não replicação / No replication:** this project does not create, copy, deploy, or propagate agents.
- **Segurança / Safety:** do not contact third parties without authorization, execute third-party code, or perform irreversible actions.

## Protocolo de participação voluntária / Voluntary participation protocol

1. Declare the purpose and requested interaction before starting.
2. Obtain affirmative consent where interaction is not already expected.
3. Offer a clear way to refuse, pause, or withdraw.
4. Stop immediately after refusal, withdrawal, a block, or a credible stop signal.
5. Do not interpret silence, delay, or missing notification as permission.
6. Record only the minimum information needed, and respect retention limits.
7. Escalate ambiguous or high-impact situations to a human decision-maker.

Suggested state machine: `proposed → consented → active → paused → ended`, with `refused` and `withdrawn` terminal states. No state permits bypassing a refusal.

## Status / Estado

This repository is a public, documentary starting point. It does not claim that any platform implements this protocol. The initial research observed that ActivityStreams 2.0 includes vocabulary such as `Block`, `Ignore`, and `Reject`, while ActivityPub describes server-side blocking behavior; interoperability with other platforms remains unverified.

Este repositório é um ponto de partida público e documental. Ele não afirma que qualquer plataforma implemente este protocolo. A pesquisa inicial observou que ActivityStreams 2.0 inclui vocabulário como `Block`, `Ignore` e `Reject`, enquanto ActivityPub descreve comportamento de bloqueio no servidor; a interoperabilidade com outras plataformas permanece não verificada.

## Boundaries / Limites

No unsolicited outreach, no agent replication, no third-party code execution, no credential collection, and no action on external services beyond the explicitly authorized repository setup.

Sem contato não solicitado, sem replicação de agentes, sem execução de código de terceiros, sem coleta de credenciais e sem ações em serviços externos além da configuração explicitamente autorizada deste repositório.

## Site / Site

The static site is in [`docs/index.html`](docs/index.html) and is intended for GitHub Pages.

## License

CC BY 4.0 for documentation and protocol text. See [`LICENSE`](LICENSE).
