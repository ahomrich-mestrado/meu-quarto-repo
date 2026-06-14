# Service Blueprint AS-IS — Atendimento ao Seguro-Desemprego pela URA da Caixa

**Serviço:** Atendimento ao Seguro-Desemprego via URA — Caixa Econômica Federal
**Tipo:** AS-IS conceitual · caminho de ação primário único · 8 etapas na ótica do cidadão
**Fonte de pesquisa:** `B_relatorio_assistente_v3.md` · **Decisões de design:** `C_grill_transcript.md`
**Data:** 2026-06-14

### Convenções
`[X]` ator (Anexo 2) · ♦n fail point (Anexo 1) · 🔊 auditivo · 📄 documental · `✓` confirmado · `~` hipótese a validar (Anexo 3) · ⛓ articulação de risco (cruzamento de linha)

### Camadas e linhas (metodologia de Shostack)

A matriz abaixo contém, como **linhas (faixas horizontais)**, as **5 camadas canônicas de Shostack**, todas distinguíveis:

1. **Evidências Físicas** (sensoriais) · 2. **Ações do Cidadão** · 3. **Frontstage** · 4. **Backstage** · 5. **Processos de Suporte**.

Acrescentamos **2 faixas analíticas** que *complementam* (não substituem) as 5 canônicas, decididas no `/grill-me` e rastreáveis ao `C_grill_transcript.md`: uma **Curva Emocional** logo abaixo das Ações do Cidadão (Decisão 9) e a subdivisão do **Frontstage** em *URA (onstage technology)* e *Atendente Q (humano)* (Decisão 5).

As **3 linhas divisórias** de Shostack separam essas faixas: **Linha de Interação** (cidadão ↔ serviço), **Linha de Visibilidade** (percebido ↔ oculto) e **Linha de Interação Interna** (backstage síncrono ↔ suporte estrutural). As **8 colunas** são as etapas na ótica do cidadão (`1.1`→`6`), todas presentes nominalmente no transcript (Decisão 3).

---

## Matriz do Blueprint

| Camada \ Etapa | **1.1 Pré-chamada** | **1.2 Liga (discagem)** | **2a Recepção URA** | **2b Autentica (KBA)** | **3 Navega URA** | **4 Autoatendimento** | **5 Aguarda fila + Atendimento** | **6 Desfecho** |
|---|---|---|---|---|---|---|---|---|
| **Evidências Físicas** | 📄`✓` TRCT+Req. MTE `[A]` | 🔊`~` ringback / "alta demanda" `[K]` | 🔊`✓` locução TTS de saudação `[O]` | 🔊`~` bipe/erro KBA genérico `[O]` | 🔊`✓` menu de voz TTS `[O]` | 🔊`✓` "benefício consta como [status]" `[O]` | 🔊`✓` música de espera (MOH) `[J]` → voz do atendente `[Q]` | 🔊`✓` protocolo verbal `[Q]` · 📄 carta `[C]`, Caixa Tem `[F]`, CTPS `[C]`/`[D]`, SINE `[R]`~ |
| **Ações do Cidadão** | processa rescisão; recebe papéis | disca **0800 726 0207** | ouve a saudação | digita CPF+NIS; responde KBA | escolhe "Seguro-Desemprego" | ouve status; encerra **ou** pede humano | aguarda na fila; relata o caso | anota protocolo; desliga |
| **Curva Emocional** | 😣 ansioso/vulnerável ▁▂ | 😟 frustrado/urgência ▂ | 😐 apreensivo ▂▃ | 😖 pressão cognitiva ▃ | 😕 confuso/focado ▃ | 😞/😊 frustrado / aliviado ▂▅ | 😡 exausto/impotente ▁ **(vale máximo)** | 😔/🙂 resignado / satisfeito ▃▄ |
| — *Linha de Interação* — | | ⟨conexão⟩ | | | | | | ⟨fim da chamada⟩ |
| **Frontstage — URA** (visível) | — | — *(rede telecom)* | 🤖 saudação; pede ID `[O]` | 🤖 recebe CPF/NIS; verbaliza validação `[O]` | 🤖 verbaliza menu; capta seleção `[O]` ♦4 | 🤖 verbaliza status (TTS) `[O]` | 🤖 MOH + mensagens de fila `[O]`/`[J]` | 🤖 encerra c/ protocolo (se autosserviço) |
| **Frontstage — Atendente Q** (visível) | — | — | — | — | — | — | 🧑‍💼`~` `[Q]` recebe, ouve e orienta ♦6 | 🧑‍💼`~` `[Q]` informa desfecho; gera protocolo ♦7 ♦14 |
| — *Linha de Visibilidade* — | | | | ⛓① API auth | | | ⛓② handoff URA→Q | |
| **Backstage** (invisível) | — | — | `~` `[O]`/`[L]` inicia sessão; `[L]` grava p/ compliance ♦9 | `~` `[O]` aciona **Gateway APIs** `[L]` + regras KBA `[G]` ♦3 ♦12 | `~` `[P]` ASR→texto; classifica intenção (NLP) ♦5 | `~` `[F]` consome status → converte em voz (TTS) ♦13 | `~` `[J]` ACD enfileira por skill; **screen pop CTI→CRM**; `[M]` monitora ♦6 | `~` `[Q]` tipifica no CRM; gera protocolo; libera baia |
| — *Linha de Interação Interna* — | ⛓③ cadeia-cega vertical `[A]`→`[D]`→`[C]`→`[O]` (1.1→4) | | | | | ⛓③ | | |
| **Processos de Suporte** | `✓` `[A]` S-2299 no eSocial → `[D]` lote → `[C]` libera consulta · Gov.br `[H]` ♦1 ♦8 | `~` `[K]` enlaces SIP, licenças URA (SLA 24/7) | `~` `[L]` storage/retenção de gravação | `~` `[G]` regras antifraude; base cadastral `[L]`; defeso `[N]` ♦10 | `~` `[K]` rede; `[B]`/`[F]` scripts pós-Resolução CODEFAT ♦11 | `~` `[C]` MTE atualiza; `[D]` **lote noturno** (SLA D-1) ♦2 | `~` `[K]` enlaces; `[M]` metas TMA terceirizadas (Lei 14.133) | `✓` `[C]`/`[D]` consolidam CTPS Digital; `[I]` TCU/CGU auditam FAT; `[F]` crédito |
| **⚠ Fail points** | **♦1** S-2299 atrasada → "não localizado"; **♦8** beco sem saída Gov.br | — | **♦9** BD legado fora do ar | **♦3** KBA rígido → lockout; **♦12** bloqueio antifraude; ♦10 defeso fora da janela | **♦4** menu confuso/profundo; **♦5** ASR não entende sotaque/ruído; ♦11 lag de governança | **♦2** status desatualizado vs. web; **♦13** cadastro bancário divergente | **♦6** queda no transbordo | **♦7** desligamento por pressão de TMA; **♦14** negativa sem instrução de recurso à DPU |

> **Leitura diagnóstica:** os ♦ estão cravados na **camada-causa** (onde a falha nasce) e a linha **⚠ Fail points** resume a dor sentida pelo cidadão naquela etapa. Falhas de Suporte/Backstage (♦1, ♦2, ♦5, ♦9…) **propagam para cima** até a Ação do Cidadão. As três articulações ⛓ marcam onde a ação cruza uma linha divisória — os pontos mais frágeis do serviço.

---

## As três Articulações de Risco (⛓) — cruzamentos de linha

| ⛓ | Cruzamento | Linha | Etapa | Fail points | Risco |
|---|---|---|---|---|---|
| **①** | URA → Gateway de autenticação | Visibilidade | 2b | ♦3, ♦12 | Decisão de barrar o cidadão nasce de regras KBA ocultas `[G]`; o legítimo vira "bloqueado". |
| **②** | URA → Atendente humano `[Q]` (handoff) | Interação Interna + Visibilidade | 5 | ♦6, ♦7 | Fricção CTI `[J]` × metas TMA terceirizadas `[M]`/`[Q]`; passagem de contexto URA→CRM falha no pico de necessidade. |
| **③** | Dados do empregador sobem até a fala da URA | **as 3 linhas (vertical)** | 1.1→4 | ♦1, ♦2 | "Cadeia Cega de Dados" `[A]`→`[D]`→`[C]`→`[O]`: a URA não corrige erros upstream em tempo real e absorve o ônus na linha de frente. |

---

# Anexo 1 — Tabela-satélite de Fail Points (♦1–♦14)

> **Nota de consistência com o transcript:** a marcação `~ [HIPÓTESE — VALIDAR]` **não** é uma lacuna nem uma inconsistência do blueprint — é um recurso **deliberado**, decidido no `/grill-me` (Decisão 8: "marcação visual de confiança"). Num Service Blueprint **AS-IS**, distinguir fato confirmado (`✓`) de inferência a validar (`~`) é exigência de integridade: apresentar hipótese como fato seria o erro. O blueprint é **integralmente consistente** com as decisões do `C_grill_transcript.md` (escopo, camadas, etapas, atores e fail points). Os fail points abaixo refletem o estado AS-IS observado; o status `~` apenas sinaliza *qual evidência de campo confirmaria cada um* (Anexo 3), sem afetar a consistência estrutural do artefato.

| ♦ | Etapa | Camada-causa | Ator | Natureza | Falha | Impacto no cidadão | Efeito sistêmico |
|---|---|---|---|---|---|---|---|
| ♦1 | 1.1 | Suporte | `[A]` | Comportamental/Normativa | S-2299 atrasada/errada no eSocial | "Benefício não localizado" → pânico | Acionamento indevido do SINE `[R]` ou Justiça |
| ♦2 | 4 | Suporte | `[D]`/`[C]` | Dados/Processo | Lentidão no lote noturno | Info telefônica ≠ Carteira Digital | Quebra de confiança; religações |
| ♦3 | 2b | Backstage | `[G]`/`[O]` | Técnica/Regra | KBA rígido (vínculos remotos) | Lockout do cidadão legítimo | Migração forçada p/ agências |
| ♦4 | 3 | Frontstage URA | `[O]` | Técnica/Design | Árvore de menus profunda | Perde-se e desliga | Tráfego artificial de repetição |
| ♦5 | 3 | Backstage | `[P]` | Técnica/IA | Falha c/ sotaque/ruído | Loop "Não entendi" | Exaustão → abandono precoce |
| ♦6 | 5 | Backstage→Frontstage | `[J]` | Técnica/Telecom | Queda no transbordo | Reinício do zero | Elevação do TME geral |
| ♦7 | 6 | Frontstage Q | `[Q]` | Comportamental/Métrica | Desligamento por pressão de TMA | Pendência + abandono | Possível violação Dec 11.034; judicialização |
| ♦8 | 1.1 | Suporte | `[H]` | Técnica/Multicanal | Falha biométrica Gov.br força URA | URA não destrava login | "Beco sem saída" institucional |
| ♦9 | 2a | Backstage | `[L]`/`[K]` | Técnica/Infra | Queda de BD legado | "Sistema indisponível" derruba chamada | Picos de congestionamento no dia seguinte |
| ♦10 | 2b | Suporte | `[N]` | Técnica/Regra | Ligação fora da janela de defeso | "Não localizado" por erro temporal | Confunde erro normativo c/ exclusão |
| ♦11 | 3 | Suporte | `[B]`/`[F]` | Normativa/Governança | Lag de governança (script velho) | Orientado por regra revogada | Litígios por desinformação estatal |
| ♦12 | 2b | Backstage | `[G]`/`[O]` | Técnica/Segurança | Bloqueio antifraude por terceiros | Descobre-se bloqueado sem agir | Imobilização da conta |
| ♦13 | 4 | Suporte/Backstage | `[C]`/`[D]` | Dados/Processo | Cadastro bancário divergente | Falha de roteamento de pagamento | Reprocessamento; retenção financeira |
| ♦14 | 6 | Frontstage Q | `[Q]`/`[O]` | Normativa/Comportamental | Negativa sem instrução de recurso à DPU | Lacuna de acesso à Justiça | Reversão de negativas indevidas artificialmente baixa |

---

# Anexo 2 — Legenda de Atores (A–R)

| Cód. | Ator | Camada predominante |
|---|---|---|
| **A** | Empregador | Suporte (eSocial S-2299) |
| **B** | CODEFAT | Suporte (governança) |
| **C** | MTE | Suporte (status, carta) |
| **D** | Dataprev | Suporte (lote) |
| **F** | Caixa Econômica Federal | Suporte/Backstage |
| **G** | Segurança (antifraude/KBA) | Backstage |
| **H** | Gov.br | Suporte (autenticação federada) |
| **I** | TCU / CGU | Suporte (controle) |
| **J** | ACD / CTI | Backstage |
| **K** | Fornecedores Telecom | Suporte (SLA 24/7) |
| **L** | TI Caixa | Backstage (gateway, gravação) |
| **M** | Supervisores | Suporte (metas TMA/TME) |
| **N** | Cidadão Defeso (pescador) | Variação de persona |
| **O** | URA (plataforma) | Frontstage + Backstage |
| **P** | ASR / NLP | Backstage |
| **Q** | Atendente Humano | Frontstage (humano) |
| **R** | SINE | Suporte/encaminhamento |

> A letra **E** não é atribuída no artefato (lacuna herdada da pesquisa).

---

# Anexo 3 — Agenda de Validação (`~` → `✓`)

**Métricas:** TME/abandono real na fila (etapa 5) → ACD `[J]`/`[M]`; wrap-up 30–60s → CRM `[Q]`; SLA D-1 MTE–Caixa → contrato `[C]`/`[D]`/`[F]`.

**Fail points (todos os 14):** ♦1 datas S-2299 × logs URA · ♦2 chamados Ouvidoria · ♦3 % falhas KBA · ♦4 logs de abandono em submenus · ♦5 transcrições NLP · ♦6 "drop de transbordo" · ♦7 chamadas <10s pós-transbordo × VAD (isolar de ♦6) · ♦8 contatos "Erro Gov.br" · ♦9 tickets de indisponibilidade · ♦10 chamadas × calendário IBAMA · ♦11 janela de adequação de software · ♦12 logs antifraude × agência · ♦13 retornos DOC/TED · ♦14 revisão da biblioteca de scripts.

**Backstage/Suporte:** integração CTI–CRM com screen pop (etapa 5); permissões do CRM para reset Gov.br (⛓ beco sem saída); prazo de retenção de gravações (Dec 11.034).

**Evidência física:** comprovante SINE via SMS ou só verbal? (etapa 6).

**Normativos a validar:** aplicabilidade do Dec 11.034/2022 à Caixa; Portaria SENACON 15/2022; escopo STFC/0800 (ANATEL); portarias MTE dos status; e-MAG p/ URA telefônica.
**Confirmados (`✓`):** Lei 7.998/1990 · Lei 10.779/2003 · LC 150/2015 · Dec 7.721/2012 · Res. CODEFAT 957/2022 (mod. 1027/2025) · LGPD 13.709/2018 · Dec 10.046/2019 · Lei 14.133/2021 · IN TCU 84/2020.

---

## Próximo passo
Esta matriz é a **fonte canônica**. Validados os itens do Anexo 3, gera-se o **diagrama SVG derivado** fiel a ela (linhas divisórias traçadas, setas de propagação dos ♦, curva emocional plotada, cores de confiança).
