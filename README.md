# padrao-lucas

Skill de agente que aplica e fiscaliza um guia de boas práticas de programação
pessoal, multi-linguagem — síntese editorial inspirada em *Clean Code* e
*Clean Architecture* (Robert C. Martin) e em obras de engenharia de software da
O'Reilly (bibliografia completa na seção 25 do guia embutido).

## Instalação

```bash
npx skills add luscas/padrao-lucas
```

O CLI detecta os agentes instalados (OpenCode, Claude Code, Codex, Cursor e
outros 75+) e pergunta para quais instalar. Use `-g` para instalar no escopo
global do usuário, em vez do escopo do projeto.

```bash
# listar o que o repositório oferece
npx skills add luscas/padrao-lucas --list

# usar sem instalar (gera o prompt da skill)
npx skills use luscas/padrao-lucas

# instalar direto pela URL de árvore
npx skills add https://github.com/luscas/padrao-lucas/tree/main/skills/padrao-lucas
```

## O que a skill faz

- **Gate proporcional**: violação de regra DEVE/NÃO DEVE no caminho tocado é
  bloqueadora — em código novo, corrija antes de entregar; em código legado fora
  do escopo, registre pendência com impacto. PREFIRA é recomendação, não bloqueio.
- **Dois modos por risco** (não por tamanho): inline para mudanças rotineiras e
  de risco baixo; orquestração — agente coordenador + subagentes paralelos de
  revisão, um por dimensão de risco (contratos/erros, segurança,
  concorrência/persistência, testes, arquitetura/nomes) — para mudanças amplas
  ou críticas (pagamentos, senhas, SQL, transações).
- **Entrega estruturada**: achados com severidade e evidência; resumo final com
  resultado, decisões, validação e limitações.
- **Guia embutido**: a skill carrega o guia completo
  (`references/llms-full.txt`, pin da v1.0.1) e funciona offline; se o
  repositório em uso tiver o próprio guia (`llms.txt`/`llms-full.txt`) ou um
  `AGENTS.md`/`CLAUDE.md` apontando para um, esse tem prioridade.

## Estrutura

```text
skills/padrao-lucas/SKILL.md                    # receita e contrato da skill
skills/padrao-lucas/references/llms-full.txt    # guia completo (v1.0.1)
```

## Uso em um repositório

Para que todos os agentes de um projeto sigam o padrão sem instalar nada,
committe um `AGENTS.md` na raiz apontando para o guia — exemplo mínimo:

```markdown
Antes de implementar ou revisar código, leia `llms.txt` e as seções
pertinentes de `llms-full.txt`. Regras DEVE/NÃO DEVE são bloqueadoras.
Se a skill `padrao-lucas` estiver disponível, use-a.
```

## Licença

[MIT](LICENSE) — o guia embutido é síntese editorial original; não reproduz
texto dos livros citados, que permanecem obras protegidas de seus autores.
