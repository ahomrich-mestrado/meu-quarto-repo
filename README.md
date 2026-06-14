# Exercício 3.1 — Service Blueprint AS-IS de um Serviço Público

**Aluno:** Augusto Meira Homrich
**Disciplina:** IDP-TD 2026
**Serviço escolhido:** Atendimento ao Seguro-Desemprego pela URA da Caixa Econômica Federal

---

## Sobre o exercício

Este repositório documenta a construção, ponta a ponta, de um **Service Blueprint AS-IS**
(como o serviço opera hoje) do atendimento ao Seguro-Desemprego via URA (Unidade de Resposta
Audível / 0800) da Caixa. O artefato segue a **metodologia de Shostack**:

- **Camadas:** Evidências Físicas · Ações do Cidadão · Frontstage · Backstage · Processos de Suporte
  *(+ uma faixa de Curva Emocional, desvio consciente justificado pela vulnerabilidade do público).*
- **Linhas divisórias:** Interação · Visibilidade · Interação Interna
- **Fail points:** pontos de falha cravados na camada-causa, com propagação até a dor do cidadão.

O trabalho parte de uma **deep research adversarial** (pesquisa + auditoria em ciclos) e converge,
via uma sessão estruturada de entrevista (`/grill-me`), nas decisões de design que sustentam o
blueprint e o diagrama finais.

### Fluxo de leitura recomendado

```
A (meta-prompt) → B (pesquisa adversarial v1…v3) → C (decisões + blueprint) → D (diagrama)
```

---

## Índice dos entregáveis

### Parte A — Meta-prompt
- [A_meta_prompt.md](A_meta_prompt.md) — meta-prompt usado para iniciar a deep research que subsidia o blueprint AS-IS

### Parte B — Deep research adversarial (v1 → audit_v1 → v2 → audit_v2 → v3)
- [B_relatorio_assistente_v1.md](B_relatorio_assistente_v1.md) — pesquisa original do assistente 1 (como o serviço opera hoje)
- [B_relatorio_auditoria_v1.md](B_relatorio_auditoria_v1.md) — auditoria da v1 pelo assistente 2
- [B_relatorio_assistente_v2.md](B_relatorio_assistente_v2.md) — revisão do assistente 1 após audit_v1
- [B_relatorio_auditoria_v2.md](B_relatorio_auditoria_v2.md) — segunda auditoria (sobre a v2) pelo assistente 2
- [B_relatorio_assistente_v3.md](B_relatorio_assistente_v3.md) — versão final do assistente 1 após audit_v2 *(fonte de contexto do blueprint)*

### Parte C — Service Blueprint AS-IS via `/grill-me`
- [C_grill_transcript.md](C_grill_transcript.md) — transcript integral da sessão `/grill-me` (12 decisões de design, com recomendação e resposta)
- [C_blueprint_asis.md](C_blueprint_asis.md) — Service Blueprint **AS-IS** elaborado conceitualmente (camadas + linhas divisórias + fail points)

### Parte D — Diagrama
- [D_diagrama_asis.md](D_diagrama_asis.md) — diagrama Mermaid da jornada a partir dos itens da Parte C (renderiza direto no GitHub)

---

## Resumo do blueprint (Parte C)

| Dimensão | Conteúdo |
|---|---|
| **Etapas (ótica do cidadão)** | 8 — `1.1 Pré-chamada` · `1.2 Liga` · `2a Recepção` · `2b Autenticação` · `3 Navega` · `4 Autoatendimento` · `5 Fila + Atendimento` · `6 Desfecho` |
| **Camadas** | 5 de Shostack + Curva Emocional |
| **Linhas divisórias** | Interação · Visibilidade · Interação Interna |
| **Atores** | 17 codificados (`[A]`–`[R]`, sem `E`) |
| **Fail points** | 14 (♦1–♦14), cada um na camada-causa |
| **Articulações de risco** | 3 cruzamentos de linha (⛓): autenticação KBA · handoff URA→humano · "cadeia cega de dados" |

> O status epistêmico é explícito: `✓` = confirmado · `~` = `[HIPÓTESE — VALIDAR]`, com uma
> agenda de validação de campo no Anexo 3 do blueprint.

---

## Configuração do autograder

- Marcador presente: [`.autograde-exercise`](.autograde-exercise) (conteúdo: `3.1`)

Para validar localmente:

```bash
autograde validar 3.1
```
