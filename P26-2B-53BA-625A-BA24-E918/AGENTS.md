# Engenharia de agentes — P26-2B-53BA-625A-BA24-E918

## Harness

- **Harness principal:** Copilot SDK integrado ao VS Code.
- **Coordenação:** o agente principal definiu os contratos, integrou o esquema e a documentação; agentes delegados trabalharam em áreas de arquivos separadas e a integração final é verificada localmente.
- **Modelos:** não identificados pelo harness nesta execução; não são declarados para evitar atribuição incorreta.

## Agentes e entregas

### Agente 1 — Backend Cloudflare, D1 e OAuth2

- Implementa Pages Functions, validação de entrada, autorização de autoria e sessão assinada.
- Usa `skills/serverless-d1-discord/SKILL.md`.
- Entrega: `functions/api/` e `functions/_lib/`.

### Agente 2 — Interface Vanilla JS

- Implementa a interface responsiva, acessível, sem framework, integrada aos endpoints do mural.
- Usa `skills/vanilla-dom-ui/SKILL.md`.
- Entrega: `public/index.html`, `public/styles.css` e `public/app.js`.

### Agente 3 — Teste e validação

- Responsável pela checagem de sintaxe e integração dos endpoints e pela validação dos critérios determinísticos locais.
- Usa `skills/teste-validacao/SKILL.md`.
- Validou sintaxe de 12 arquivos JavaScript, executou a migração e verificou constraints com SQLite em memória e rodou o validador local. Os critérios estruturais 1–8 passaram; deploy público ainda não foi configurado.
- A revisão identificou uma divergência documental do método de estado, corrigida para `PATCH`, e tratamento ambíguo de sessão ausente no cliente, corrigido para preservar o status HTTP e tratar `401`/`403` como login necessário.
- O fluxo OAuth real ainda depende de credenciais externas e não foi executado.

## Contratos de dados

- A identidade autenticada é obtida da sessão HttpOnly assinada, não de campos enviados pelo cliente.
- `subscriptions` define o feed que cada estudante acompanha.
- `post_states` guarda `is_read` e `is_pinned` por par aviso/usuário.
- O D1 mantém autor e cópia pública do perfil na criação do aviso para rastreabilidade.
