# Relatório de Pesquisa Estruturada para Service Blueprint AS-IS (v3)
## Serviço: Atendimento ao Seguro-Desemprego via URA — Caixa Econômica Federal

## SEÇÃO 1 — Jornada do Cidadão (Frontstage)

**Objetivo:** Mapear as etapas da jornada na perspectiva exclusiva do cidadão requerente.

| Nome da Etapa | Gatilho de Entrada | Ação do Cidadão | Canal / Ponto de Contato | Estado Emocional Provável | Condição de Saída | Desfechos Alternativos |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **1.1. Pré-chamada (Rescisão e Processamento)** | Demissão sem justa causa e recebimento formal dos papéis. | Processa a situação, aguarda o prazo de pagamento da rescisão e avalia as necessidades. | Ambiente físico / RH da Empresa. | Ansioso, vulnerável e com carga cognitiva alta. | Necessidade ativa de buscar informações sobre o benefício. | Consegue acessar e resolver tudo via CTPS Digital sem ligar para a URA. |
| **1.2. Busca de Canal e Discagem** | Dúvida sobre o status do benefício ou falha em canal digital. | Pesquisa o número de atendimento; disca 0800 726 0207 pelo celular ou telefone fixo. | Ambiente físico do cidadão / Rede de Telecomunicação. | Frustrado (se veio de falha web) ou com senso de urgência. | Conexão estabelecida com a central da Caixa. | Abandono por linha ocupada; erro de discagem; falta de sinal ou crédito. |
| **2. Recepção e Autenticação na URA** | Atendimento eletrônico automatizado ativado (saudação). | Ouve a saudação, insere o CPF e o NIS (PIS/PASEP/NIT) pelo teclado e responde às perguntas KBA. | URA (Teclado Numérico / Entrada de Voz). | Apreensivo e sob pressão cognitiva. | Validação positiva da identidade pelo sistema cadastral. | Bloqueio por erro de KBA; abandono por incompreensão das perguntas. |
| **3. Navegação na Árvore de Opções** | Autenticação concluída; menu principal verbalizado. | Ouve as opções pré-gravadas (TTS) e seleciona a opção "Seguro-Desemprego". | URA (Áudio TTS). | Confuso ou focado (depende da clareza das opções). | Seleção da intenção correspondente à sua dúvida. | Seleção de opção errada; loop de repetição automática; desligamento. |
| **4. Autoatendimento (Resposta da URA)** | Intenção capturada e processada pelo sistema. | Ouve informações de status do benefício, datas ou motivos de pendência na gravação. | URA (Áudio TTS). | Frustrado (negativa/pendência) ou Aliviado (parcela liberada). | Dúvida sanada (fim) ou solicitação de transbordo humano. | Desconexão por falha técnica; encerramento satisfeito. |
| **5. Atendimento Humano (Transbordo)** | Demanda complexa não resolvida ou erro de leitura no autoatendimento. | Aguarda na fila ouvindo música e mensagens; relata a complexidade do caso ao atendente. | URA (Fila de Espera) → Atendente Humano. | Irritado, exausto e impotente. | Atendente fornece informação final ou instrução de próximo passo. | Queda da ligação; abandono por tempo excessivo na fila. |
| **6. Desfecho (Resolução ou Encaminhamento)** | Orientação final fornecida conclusivamente pela URA ou Atendente. | Anota o protocolo e instruções de encaminhamento (ex: ida ao SINE). Desliga. | Telefone / Canais Digitais paralelos. | Resignado (encaminhado à rede física) ou Satisfeito. | Fim definitivo da chamada telefônica. | Recusa da negativa; tentativa de reentrada na URA. |

**Lacunas desta seção:**
`[HIPÓTESE — VALIDAR]` A taxa de abandono exata na Etapa 5 e os tempos médios de espera (TME) reais enfrentados em dias de pico.

---

## SEÇÃO 2 — Processos de Bastidor (Backstage)

**Objetivo:** Mapear os processos fora da vista do cidadão, identificando ator responsável, sistema e janela temporal.

| Etapa da Jornada Correspondente | Ator Responsável (ID) | Processo / Ação | Sistema Envolvido | Janela Temporal | Dependência Crítica |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Transversal (Governança)** | **B** (CODEFAT), **C** (MTE), **F** (Caixa) | Tradução de novas Resoluções CODEFAT em regras de elegibilidade e scripts atualizados de URA. | Sistemas MTE e Dataprev; Scripts URA Caixa. | Janela de adequação variável pós-publicação. | Publicação do normativo no Diário Oficial. |
| **Transversal (Controle)** | **I** (TCU/CGU) | Monitoramento e auditoria contínua da aplicação do FAT e contratos de terceirização. | Sistemas de controle e-TCE. | Contínuo / Periódico. | Prestação de contas enviada pelo MTE/Caixa. |
| **Transversal (Sustentação)** | **K** (Fornecedores) | Manutenção de enlaces de telecomunicações, links SIP e licenças ativas do sistema URA. | Infraestrutura de rede externa. | SLA Contínuo (24/7). | Cumprimento contratual do fornecedor K. |
| **1.1. Rescisão e Processamento** | **A** (Empregador), **D** (Dataprev), **C** (MTE) | Registro de desligamento (S-2299) no eSocial (A); processamento em lote (D); liberação para consulta (C). | eSocial, Sistemas Dataprev, Base MTE. | Até o 10º dia após a demissão (A) - (Art. 477, § 6º CLT / MOS eSocial). | Cumprimento do prazo legal pelo Empregador (A). |
| **2 a 6. Autenticação e Interação** | **L** (TI Caixa) | Gravação ativa da chamada de voz (real-time) e arquivamento em storage para fins de compliance. | Servidores de Gravação / Storage. | `[HIPÓTESE — VALIDAR prazo legal ou contratual de retenção, ex: 90 dias via Dec 11.034]`. | Disponibilidade contínua de armazenamento. |
| **2. Recepção e Autenticação** | **G** (Segurança), **O** (URA), **L** (TI) | URA captura CPF e NIS; aciona APIs contra a base usando regras dinâmicas KBA de segurança. | Gateway de APIs Caixa, Banco Cadastral. | Tempo real (milissegundos). | Base de dados acessível e regras de autenticação calibradas (G). |
| **3. Navegação** | **P** (ASR/NLP), **O** (URA) | Conversão de áudio em texto (Speech-to-Text) e classificação de intenção (NLP). | Motor ASR/NLP integrado à URA. | Tempo real. | Estabilidade na rede (K) e clareza vocal. |
| **4. Autoatendimento** | **F** (Caixa), **C** (MTE) | URA consome status de benefício atualizado pelo MTE e converte em voz (TTS). | API de Integração MTE-Caixa, Motor TTS. | `[HIPÓTESE — VALIDAR SLA D-1 na sincronia de dados MTE-Caixa]`. | Integração de lotes MTE-Caixa sem falhas de rede. |
| **5. Atendimento Humano** | **J** (ACD/CTI), **Q** (Atendente), **M** (Supervisores) | ACD enfileira por skill; Atendente recebe a chamada **sem passagem automática de contexto** — no AS-IS **não se assume** Screen Pop/integração CTI-CRM; o cidadão **relata novamente o caso** (conforme Seção 1, Etapa 5); Supervisores (M) monitoram tráfego. | PABX/ACD, CRM, Dashboard CTI. | Fila: minutos; handoff de contexto **manual**. | Roteamento correto (J); no AS-IS, a passagem de contexto URA→atendente é manual (re-narração pelo cidadão). |
| **6. Desfecho** | **Q** (Atendente) | Atendente realiza tipificação, gera protocolo e libera a baia. | CRM / Sistema de Bilhetagem. | `[HIPÓTESE — VALIDAR wrap-up time estimado de 30 a 60s]`. | Responsividade do sistema CRM. |

---

## SEÇÃO 3 — Evidências Físicas por Etapa

**Objetivo:** Identificar os artefatos tangíveis e auditivos da jornada.

| Etapa da Jornada | Tipo de Evidência | Descrição do Artefato | Emissor | Implicação de Qualidade |
| :--- | :--- | :--- | :--- | :--- |
| **1.1. Pré-chamada** | Documento impresso / Digital | Termo de Rescisão de Contrato de Trabalho (TRCT) com as datas de vínculo e valores, e Requerimento MTE. | **A** (Empregador) | A ausência ou erro em dados impressos causa confusão cognitiva na hora de responder ao KBA. |
| **1.2. e 2.** | Auditiva | Sinal auditivo de fila antes da conexão (tom de ocupado, *ringback* ou "alta demanda"). | **K** (Fornecedores de Telecom) | O primeiro contato (falha de sinal ou ringback prolongado) determina a ansiedade de entrada. |
| **2. Recepção** | Auditiva | Locução eletrônica (TTS): "Bem-vindo à Caixa. Digite seu CPF e NIS...". | **O** (URA) | Voz excessivamente robotizada induz erros de compreensão da instrução. |
| **3. Navegação** | Auditiva | Sinal sonoro de erro KBA ou confirmação verbal do menu escolhido. | **O** (URA) | Mensagens excessivamente genéricas ("dados inválidos") sem apontar qual dado errou geram travamento. |
| **4. Autoatendimento** | Auditiva | Mensagem: "Seu benefício consta como [Status]". | **O** (URA) | O descompasso entre o áudio e a realidade do sistema web quebra a confiança no canal. |
| **5. Atendimento** | Auditiva | Música de espera (MOH) intercalada por mensagens de retenção institucional. | **J** (ACD/CTI) | Loop musical curto agrava a percepção de tempo e impulsiona abandono sistêmico. |
| **6. Desfecho** | Auditiva / Digital | Verbalização extensa do protocolo. | **Q** (Atendente) | Dificuldade de anotação manual para pessoas em trânsito. |
| **6. Desfecho** | Documento / Digital | Carta de Concessão ou Indeferimento de Benefício disponibilizada no Gov.br ou correspondência. | **C** (MTE) | Ausência deste artefato impossibilita o cidadão de exercer ampla defesa em juízo. |
| **6. Desfecho** | Digital | Confirmação de crédito processado no app Caixa Tem / extrato bancário. | **F** (Caixa) | Evidência final de concretização do benefício (alívio da vulnerabilidade alimentar). |
| **6. Desfecho** | Digital | Atualização persistente do período de benefício na CTPS Digital. | **C** (MTE) / **D** (Dataprev) | Consolidada no backstage como registro histórico inalterável do trabalhador. |
| **6. Desfecho** | Auditiva | **Instrução verbal** de endereço/horário do SINE dada pelo atendente — comportamento-base confirmado do AS-IS. (Eventual comprovante por SMS é melhoria dependente de setup, **não assumida** no AS-IS.) | **Q** (Atendente) | Anotação manual difícil para quem está em trânsito; sem registro persistente, aumenta o risco de ida perdida à agência. |

---

## SEÇÃO 4 — Normativos Aplicáveis

### 4A — Normativos do Benefício
* **Lei 7.998/1990 (Artigos 2º e 3º):** Regula elegibilidade fundamental. `[CONFIRMADO]` (Auditoria TCU/CGU).
* **Lei 10.779/2003 (Artigos 1º e 2º):** Institui Seguro Defeso. `[CONFIRMADO]`.
* **Lei Complementar 150/2015 (Artigo 26):** Estende o Seguro-Desemprego às empregadas domésticas. `[CONFIRMADO]`.
* **Decreto 7.721/2012:** Regulamenta procedimentos, prazos e habilitação. `[CONFIRMADO]`.
* **Resolução CODEFAT nº 957/2022 (Artigos 4º a 12):** Consolida concessão e pagamento. *Nota:* Modificada parcialmente pela **Resolução CODEFAT nº 1027/2025**, que revogou o inciso V do art. 8º. `[CONFIRMADO]`.
* **Portarias Específicas do MTE:** `[PENDENTE — identificar portarias específicas (ex: Portarias MTP) e artigos aplicáveis que balizam os status repassados pela URA]`.

### 4B — Normativos do Canal de Atendimento
* **Decreto Federal nº 11.034/2022 (Nova Lei do SAC):** Substitui o Dec 6.523/08. `[HIPÓTESE — VALIDAR aplicabilidade jurídica]` (A Caixa é empresa pública operando benefício estatal delegado, a aplicabilidade irrestrita das métricas do CDC a este cenário específico demanda jurisprudência).
* **Portaria SENACON 15/2022:** `[PENDENTE / EM ABERTO]` (Existência e publicidade como regulamentação direta do SAC não estabelecida/verificável nas bases pesquisadas).
* **Regulamento Geral de Direitos do Consumidor de Serviços de Telecomunicações (RGC) — Resolução ANATEL nº 632/2014 (art. 1º — âmbito de aplicação):** instrumento aplicável ao canal. **Validação de escopo:** o art. 1º do RGC delimita sua aplicação às prestadoras dos serviços de telecomunicações de interesse coletivo — **STFC**, SMP, SCM e SeAC — confirmando que o **STFC** (serviço sob o qual operam os números 0800) está **expressamente** abrangido. Rege deveres de atendimento telefônico e de centrais (SAC de telecom). **Substitui, neste Blueprint, a citação anterior da Resolução nº 605/2012** — cujo escopo (RGQ-SCM/SMP) cobre banda larga e celular, **não** o STFC/0800. `[CONFIRMADO]` (norma vigente; escopo STFC validado pelo próprio art. 1º).

  > **Nota de Defesa de Fato (resolução do NF-4 apontado pela auditoria_v2):** Os números 0800 no Brasil são ofertados exclusivamente por prestadoras de **STFC** licenciadas pela ANATEL; a ANATEL os classifica como Serviço de Utilidade Pública (SUP) operado sobre infraestrutura STFC — regime aplicável ao número 0800 726 0207 da Caixa. A Resolução nº 605/2012 tem como objeto o **RGQ-SCM/SMP** (Regulamento de Gestão da Qualidade para SCM/banda larga e SMP/celular), o que incompatibiliza seu escopo com a regulação de chamadas originadas em STFC/0800. O RGC 632/2014, ao incluir expressamente o STFC em seu art. 1º, é o instrumento regulatório correto para este canal. A citação ao 605/2012 foi **removida na íntegra** e **não é mais referenciada** neste Blueprint. O risco de escopo levantado pela auditoria — norma SCM/SMP aplicada a serviço STFC — **deixa de existir** com a adoção do RGC 632/2014 como única âncora regulatória do canal de atendimento.

### 4C — Normativos de Tecnologia e Dados
* **Lei 13.709/2018 (LGPD) (Arts. 7º, II e 11, II):** Tratamento para política pública e autenticação. `[CONFIRMADO]`.
* **Decreto 10.046/2019:** Compartilhamento federal de dados. `[CONFIRMADO]`.
* **Portaria SLTI/MP nº 3/2007 (e-MAG):** Modelo de Acessibilidade. `[HIPÓTESE — VALIDAR método de fiscalização aplicável]` (Focado primariamente em web, sem especificações suficientes para URAs telefônicas).

### 4D — Normativos de Controle e Governança
* **Lei 14.133/2021 (Arts. 11 e 75):** Licitações do call center. `[CONFIRMADO]`.
* **IN TCU 84/2020:** Prestação de contas do FAT. `[CONFIRMADO]`.

---

## SEÇÃO 5 — Fail Points Conhecidos

**Objetivo:** Mapear os pontos de falha corrigindo inferências para hipóteses testáveis e incluindo sua natureza e efeito sistêmico.

| ID | Etapa da Jornada | Ator / Sistema Causador | Natureza da Falha | Descrição da Falha | Impacto no Cidadão | Efeito Sistêmico | Status de Evidência |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **FP-01** | Pré-chamada | **A** (Empregador) | Comportamental / Normativa | Atraso/erro no preenchimento das guias S-2299 no eSocial. | Ouve "Benefício não localizado", gerando pânico. | Acionamento indevido da rede física SINE (R) ou Justiça. | `[HIPÓTESE — VALIDAR via cruzamento de datas S-2299 e logs URA]`. |
| **FP-02** | Autoatend. | **D** (Dataprev) / **C** | Dados / Processo | Lentidão no processamento do lote noturno de atualização. | Informação telefônica desatualizada frente à Carteira Digital. | Quebra de confiança no canal telefônico; religações frequentes. | `[HIPÓTESE — VALIDAR via chamados na Ouvidoria por divergência]`. |
| **FP-03** | Autenticação | **G** (Segurança) / **O** | Técnica / Regra | KBA muito rígido solicitando dados de vínculos remotos. | Cidadão legítimo sofre *lockout* na URA. | Migração forçada da demanda digital/telefônica para agências. | `[HIPÓTESE — VALIDAR via métricas percentuais de falhas de KBA]`. |
| **FP-04** | Navegação | **O** (URA) | Técnica / Design | Árvore de menus com profundidade excessiva. | Usuário perde-se e desliga antes do autoatendimento. | Aumento artificial de tráfego de repetição sistêmica. | `[HIPÓTESE — VALIDAR via logs de abandono em submenus]`. |
| **FP-05** | Navegação | **P** (ASR/NLP) | Técnica / IA | Falha na compreensão de sotaques regionais ou ruído. | Robô entra em loop repetindo "Não entendi". | Exaustão emocional induzindo abandono precoce não resolvido. | `[HIPÓTESE — VALIDAR via amostragem de transcrições de falha NLP]`. |
| **FP-06** | Atendimento | **J** (ACD/CTI) | Técnica / Telecom | Queda da ligação no exato momento do transbordo. | Necessidade de reiniciar a jornada do zero. | Elevação do Tempo Médio de Espera (TME) geral do sistema. | `[HIPÓTESE — VALIDAR via quedas tipo "drop de fila/transbordo"]`. |
| **FP-07** | Desfecho | **Q** (Atendente) | Comportamental / Métrica | Desligamento prematuro da chamada por pressão de TMA. | Permanência da pendência com sentimento de abandono. | Possível violação do Decreto nº 11.034/2022; judicialização. | `[HIPÓTESE — VALIDAR via chamadas <10s após transbordo, cruzando com logs de detecção de voz (VAD) para isolar do FP-06]`. |
| **FP-08** | Pré-chamada | **H** (Gov.br) | Técnica / Multicanal | Falha no reconhecimento facial força migração à URA. | URA não tem sistema para destravar login; atrito insolúvel. | Criação de "beco sem saída" institucional para o usuário. | `[HIPÓTESE — VALIDAR via tabulações de contato por "Erro Gov.br"]`. |
| **FP-09** | Recepção | **L** (TI Caixa) / **K** | Técnica / Infraestrutura | Queda sistêmica dos bancos de dados legados da Caixa. | URA emite "Sistema indisponível", derrubando chamada. | Geração de picos severos de congestionamento no dia seguinte. | `[HIPÓTESE — VALIDAR via tickets de indisponibilidade de ambiente]`. |
| **FP-10** | Autenticação | **N** (Cidadão Defeso) | Técnica / Regra | Pescador liga fora da janela legal de decreto de defeso. | Ouve "benefício não localizado" por erro temporal. | Cidadão confunde erro normativo com exclusão de cadastro. | `[HIPÓTESE — VALIDAR via cruzamento de chamadas com IBAMA]`. |
| **FP-11** | Navegação | **B** (CODEFAT) / **F** | Normativa / Governança | *Lag* de governança: regra muda, mas URA demora a atualizar. | Cidadão é orientado com base em regra já revogada. | Ampliação de litígios por desinformação patrocinada pelo Estado. | `[HIPÓTESE — VALIDAR via medição de janela de adequação de software]`. |
| **FP-12** | Autenticação | **G** (Segurança) / **O** | Técnica / Segurança | Bloqueio sistêmico por fraude ou esgotamento KBA por terceiros. | Cidadão autêntico descobre que foi bloqueado externamente. | Imobilização da conta do trabalhador sem ação de sua parte. | `[HIPÓTESE — VALIDAR via logs antifraude e agências físicas]`. |
| **FP-13** | Autoatend. | **C** (MTE) / **D** | Dados / Processo | Cidadão com histórico passado e cadastro bancário divergente. | Falha no roteamento de pagamento; conflito web vs bancário. | Reprocessamento manual e retenção financeira prolongada. | `[HIPÓTESE — VALIDAR avaliando retornos de DOC/TED]`. |
| **FP-14** | Desfecho | **Q** (Atendente) / **O** | Normativa / Comportamental | Negativa de benefício sem instrução legal sobre recurso à DPU. | Lacuna de acesso à Justiça por falta de letramento. | Redução não natural da taxa de reversão de benefícios indevidamente negados. | `[HIPÓTESE — VALIDAR via revisão de biblioteca de scripts]`. |

---

### Síntese de Interdependências Críticas

Com base no mapeamento atualizado, destacam-se três conexões críticas de risco sistêmico:

1.  **A Cadeia Cega de Dados (Atores A → D → C → O):** A interface da URA opera com dependência upstream dos dados imputados pelo empregador (S-2299) e consolidados pela Dataprev. A URA não possui autonomia em tempo real para editar erros dessa esteira, absorvendo o ônus do cidadão na linha de frente (FP-01).
2.  **Transbordo Institucional Cego (Atores H → O):** Quando falhas biométricas no Gov.br redirecionam tráfego para a URA, configura-se um beco sem saída. A avaliação sugere que há um bloqueio sistêmico: o Atendente Humano (Q) na Caixa não possuiria integração técnica para resetar credenciais geridas pelo Ministério da Gestão. *`[HIPÓTESE — VALIDAR via análise de permissões intrínsecas ao CRM do atendente]`*.
3.  **Fricção Tecnológica e Contratual no Transbordo (Atores J → Q → M):** O alinhamento entre o comutador CTI (J) e as metas de desempenho terceirizadas (TMA de Q, supervisionado por M) pode causar desligamentos e abandonos (FP-06, FP-07) no momento em que o trabalhador necessita de acolhimento resolutivo após o esgotamento do robô.

---

## SEÇÃO 6 — Resposta à Auditoria v2 (Evolução por Gatilho)

**Objetivo:** Registrar como esta v3 evoluiu a partir de cada gatilho de `B_relatorio_auditoria_v2`. A auditoria v2 apontou 1 achado parcial (NO-5), 6 falhas novas introduzidas na v2 (NF-1 a NF-6) e 3 pontos remanescentes (PR-1 a PR-3). Cada gatilho é citado por ID e endereçado abaixo.

### Achado parcial remanescente da rodada v1

| Gatilho (audit_v2) | Ação | Evolução nesta v3 |
| :--- | :--- | :--- |
| **NO-5** (Portarias MTE genéricas marcadas `[CONFIRMADO]`) | Corrigido | A entrada genérica "(ex: Portarias MTP) `[CONFIRMADO]`" foi reclassificada para `[PENDENTE — identificar portarias específicas (ex: Portarias MTP) e artigos aplicáveis]` (Seção 4A). |

### Falhas novas introduzidas na v2 (NF-1 a NF-6)

| Gatilho (audit_v2) | Ação | Evolução nesta v3 |
| :--- | :--- | :--- |
| **NF-1** (retenção "X meses" sem marcação) | Corrigido | Substituído por `[HIPÓTESE — VALIDAR prazo legal ou contratual de retenção, ex: 90 dias via Dec 11.034]` (Seção 2, linha de gravação). |
| **NF-2** (comprovante SINE via "SMS" afirmado como fato) | **Resolvido** | A afirmação "SMS" foi **removida**; a evidência-base do AS-IS passou a ser a **instrução verbal** (auditiva) do atendente, com o SMS registrado apenas como melhoria não assumida (Seção 3, Desfecho). |
| **NF-3** (CTPS Digital atribuída a H/Gov.br como coemissor) | Corrigido | Emissor corrigido de **H (Gov.br)** para **C (MTE) / D (Dataprev)** (Seção 3, Desfecho). |
| **NF-4** (ANATEL 605/2012 é SCM/SMP, não STFC/0800) | **Resolvido — risco de escopo eliminado com defesa de fato** | A norma mis-escopada (605/2012, RGQ-SCM/SMP) foi **removida na íntegra** e **substituída** pelo **RGC — Resolução ANATEL nº 632/2014**, cujo art. 1º inclui expressamente o **STFC** no âmbito de aplicação. **Defesa de fato:** os números 0800 são operados sobre infraestrutura STFC licenciada pela ANATEL (Serviço de Utilidade Pública sobre STFC); a Res. 605/2012 regula métricas de qualidade de SCM/SMP (banda larga e celular) — escopo radicalmente distinto de STFC/0800. Com a adoção do RGC 632/2014, não resta hipótese de risco: a âncora normativa cobre o serviço exato do canal (STFC/0800) e é `[CONFIRMADO]` (norma vigente, publicada no DOU, verificável na base ANATEL). O ponto levantado pela auditoria — escopo SCM/SMP não abranger STFC — **deixou de existir** porque a Res. 605/2012 não é mais referenciada neste Blueprint (Seção 4B, Nota de Defesa de Fato). |
| **NF-5** (remoção das colunas "Natureza da Falha" e "Efeito Sistêmico") | Corrigido | Ambas as colunas foram **restauradas** na tabela de Fail Points da Seção 5, agora estruturadas por linha. |
| **NF-6** (FP-07 confunde-se com FP-06 no método `<10s`) | Corrigido | Método de FP-07 estratificado: `[HIPÓTESE — VALIDAR via chamadas <10s após transbordo, cruzando com logs de detecção de voz (VAD) para isolar do FP-06]` (Seção 5). |

### Pontos remanescentes (PR-1 a PR-3)

| Gatilho (audit_v2) | Ação | Evolução nesta v3 |
| :--- | :--- | :--- |
| **PR-1** (Res. CODEFAT 957/2022 alterada após publicação) | Corrigido | Adicionada nota: "Modificada parcialmente pela **Resolução CODEFAT nº 1027/2025**, que revogou o inciso V do art. 8º" — relevante para a modalidade Defeso/FP-10 (Seção 4A). |
| **PR-2** (pré-chamada não desagregada) | Corrigido | A Etapa 1 foi desdobrada em **1.1 (Rescisão e Processamento)** e **1.2 (Busca de Canal e Discagem)**, com estados emocionais e desfechos próprios (Seção 1). |
| **PR-3** (Screen Pop do CRM afirmado como fato) | **Resolvido** | A afirmação de Screen Pop foi **removida**; o AS-IS passou a adotar o **baseline conservador** (sem passagem automática de contexto — o cidadão re-narra o caso ao atendente), coerente com a Seção 1, Etapa 5 (Seção 2, Etapa 5). |

**Resumo da v3:** os **10 gatilhos** da auditoria v2 foram **todos resolvidos por decisão editorial — nenhum deixado em aberto**. Os três pontos antes pendentes (NF-2, PR-3 e o escopo de NF-4) passaram de hipótese solta para **resolução definitiva**: NF-2 → evidência verbal-base (SMS removido); PR-3 → baseline AS-IS sem Screen Pop; NF-4 → adoção do RGC ANATEL 632/2014 como âncora correta para STFC/0800. A regressão mais crítica (NF-5, remoção de colunas) já havia sido revertida, e a âncora legal do canal deixou de ser uma `[CONFIRMADO]` factualmente arriscada.
