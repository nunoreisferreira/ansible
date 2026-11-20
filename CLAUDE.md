# CLAUDE.md

Repositório de playbooks Ansible (RedHat, RSYSLOG, CheckMK, CrowdStrike, utilizadores, loops), organizado em pastas numeradas.

## Orquestração de agentes

A sessão principal (Opus) coordena e delega para os subagentes em `.claude/agents/`:

| Agente | Modelo | Papel |
|---|---|---|
| `planner-reviewer` | Opus | Planeia tarefas com várias etapas e revê cada implementação |
| `implementer` | Sonnet | Implementa as alterações (playbooks, roles, templates, docs) |
| `quick-task` | Haiku | Tarefas simples: pesquisas, resumos, typos, renomeações, formatação |

Fluxo por defeito para qualquer alteração não trivial:

1. **Planear** — `planner-reviewer` produz o plano.
2. **Implementar** — `implementer` executa o plano; partes mecânicas vão para `quick-task`.
3. **Rever** — `planner-reviewer` revê o diff. Se houver achados, volta ao passo 2.
4. A sessão principal resume o resultado ao utilizador.

Tarefas triviais (uma pergunta, uma linha) fazem-se diretamente, sem delegar.

## Convenções

- YAML com `---` no topo e indentação de 2 espaços.
- Preferir módulos Ansible a `shell`/`command`; tasks idempotentes.
- Segredos sempre em Ansible Vault, nunca em claro.
- Verificar com `ansible-playbook --syntax-check` e `ansible-lint` quando disponíveis.
