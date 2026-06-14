# Relatório de Pesquisa Estruturada para Service Blueprint AS-IS (v2)
## Serviço: Atendimento ao Seguro-Desemprego via URA — Caixa Econômica Federal

## SEÇÃO 1 — Jornada do Cidadão (Frontstage)

**Objetivo:** Mapear as etapas da jornada na perspectiva exclusiva do cidadão requerente.

| Nome da Etapa | Gatilho de Entrada | Ação do Cidadão | Canal / Ponto de Contato | Estado Emocional Provável | Condição de Saída | Desfechos Alternativos |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **1. Pré-chamada (Busca e Discagem)** | Demissão sem justa causa e recebimento formal dos papéis rescisórios. | Pesquisa o número; disca 0800 726 0207 pelo celular ou telefone fixo. | Ambiente físico do cidadão / Rede de Telecomunicação. | Ansioso e vulnerável (preocupação imediata com subsistência). | Conexão estabelecida com a central da Caixa. | Abandono por linha ocupada; erro de discagem; falta de sinal. |
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
| **1. Pré-chamada** | **A** (Empregador), **D** (Dataprev), **C** (MTE) | Registro de desligamento (S-2299) no eSocial (A); processamento em lote (D); liberação para consulta (C). | eSocial, Sistemas Dataprev, Base MTE. | Até o 10º dia após a demissão (A) - (Art. 477, § 6º CLT / MOS eSocial). | Cumprimento do prazo legal pelo Empregador (A). |
| **2 a 6. Autenticação e Interação** | **L** (TI Caixa) | Gravação ativa da chamada de voz (real-time) e arquivamento em storage para fins de compliance. | Servidores de Gravação / Storage. | Tempo real; retenção de X meses. | Disponibilidade contínua de armazenamento. |
| **2. Recepção e Autenticação** | **G** (Segurança), **O** (URA), **L** (TI) | URA captura CPF e NIS; aciona APIs contra a base usando regras dinâmicas KBA de segurança. | Gateway de APIs Caixa, Banco Cadastral. | Tempo real (milissegundos). | Base de dados acessível e regras de autenticação calibradas (G). |
| **3. Navegação** | **P** (ASR/NLP), **O** (URA) | Conversão de áudio em texto (Speech-to-Text) e classificação de intenção (NLP). | Motor ASR/NLP integrado à URA. | Tempo real. | Estabilidade na rede (K) e clareza vocal. |
| **4. Autoatendimento** | **F** (Caixa), **C** (MTE) | URA consome status de benefício atualizado pelo MTE e converte em voz (TTS). | API de Integração MTE-Caixa, Motor TTS. | `[HIPÓTESE — VALIDAR SLA D-1 na sincronia de dados MTE-Caixa]`. | Integração de lotes MTE-Caixa sem falhas de rede. |
| **5. Atendimento Humano** | **J** (ACD/CTI), **Q** (Atendente), **M** (Supervisores) | ACD enfileira por skill; Atendente recebe Screen Pop; Supervisores (M) realizam escuta e monitoram tráfego. | PABX/ACD, CRM, Dashboard CTI. | Fila: minutos; Screen Pop: milissegundos. | Roteamento correto (J) e passagem de contexto URA → CRM. |
| **6. Desfecho** | **Q** (Atendente) | Atendente realiza tipificação, gera protocolo e libera a baia. | CRM / Sistema de Bilhetagem. | `[HIPÓTESE — VALIDAR wrap-up time estimado de 30 a 60s]`. | Responsividade do sistema CRM. |

---

## SEÇÃO 3 — Evidências Físicas por Etapa

**Objetivo:** Identificar os artefatos tangíveis e auditivos da jornada.

| Etapa da Jornada | Tipo de Evidência | Descrição do Artefato | Emissor | Implicação de Qualidade |
| :--- | :--- | :--- | :--- | :--- |
| **1. Pré-chamada** | Documento impresso / Digital | Termo de Rescisão de Contrato de Trabalho (TRCT) com as datas de vínculo e valores, e Requerimento MTE. | **A** (Empregador) | A ausência ou erro em dados impressos causa confusão cognitiva na hora de responder ao KBA da Caixa. |
| **1 e 2. Pré/Recepção** | Auditiva | Sinal auditivo de fila antes da conexão (tom de ocupado, *ringback* ou "alta demanda"). | **K** (Fornecedores de Telecom) | O primeiro contato (falha de sinal ou ringback prolongado) determina a ansiedade de entrada. |
| **2. Recepção** | Auditiva | Locução eletrônica (TTS): "Bem-vindo à Caixa. Digite seu CPF e NIS...". | **O** (URA) | Voz excessivamente robotizada induz erros de compreensão da instrução. |
| **3. Navegação** | Auditiva | Sinal sonoro de erro KBA ou confirmação verbal do menu escolhido. | **O** (URA) | Mensagens excessivamente genéricas ("dados inválidos") sem apontar qual dado errou geram travamento. |
| **4. Autoatendimento** | Auditiva | Mensagem: "Seu benefício consta como [Status]". | **O** (URA) | O descompasso entre o áudio e a realidade do sistema web quebra a confiança no canal. |
| **5. Atendimento** | Auditiva | Música de espera (MOH) intercalada por mensagens de retenção institucional. | **J** (ACD/CTI) | Loop musical curto agrava a percepção de tempo e impulsiona abandono sistêmico. |
| **6. Desfecho** | Auditiva / Digital | Verbalização extensa do protocolo. | **Q** (Atendente) | Dificuldade de anotação manual para pessoas em trânsito. |
| **6. Desfecho** | Documento / Digital | Carta de Concessão ou Indeferimento de Benefício disponibilizada no Gov.br ou correspondência. | **C** (MTE) | Ausência deste artefato impossibilita o cidadão de exercer ampla defesa em juízo. |
| **6. Desfecho** | Digital | Confirmação de crédito processado no app Caixa Tem / extrato bancário. | **F** (Caixa) | Evidência final de concretização do benefício (alívio da vulnerabilidade alimentar). |
| **6. Desfecho** | Digital | Atualização persistente do período de benefício na CTPS Digital. | **C** (MTE) / **H** (Gov.br) | Consolidada no backstage como registro histórico inalterável do trabalhador. |
| **6. Desfecho** | Digital (Notificação) | Comprovante de agendamento (SMS) quando o cidadão é encaminhado ao atendimento físico no SINE. | **Q** (Atendente) / **F** | Evita idas perdidas às agências físicas lotadas. |

---

## SEÇÃO 4 — Normativos Aplicáveis

### 4A — Normativos do Benefício
* **Lei 7.998/1990 (Artigos 2º e 3º):** Regula elegibilidade fundamental. `[CONFIRMADO]` (Auditoria TCU/CGU).
* **Lei 10.779/2003 (Artigos 1º e 2º):** Institui Seguro Defeso. `[CONFIRMADO]`.
* **Lei Complementar 150/2015 (Artigo 26):** Estende o Seguro-Desemprego às empregadas domésticas. `[CONFIRMADO]`.
* **Decreto 7.721/2012:** Regulamenta procedimentos, prazos e habilitação. `[CONFIRMADO]`.
* **Resolução CODEFAT nº 957/2022 (Artigos 4º a 12):** Consolida concessão e pagamento. *Nota de auditoria (Defesa de Fato):* Normativo real publicado no DOU em 23/09/2022, revogou a antiga Res. 467/2005. `[CONFIRMADO]`.
* **Portarias Específicas do MTE (ex: Portarias MTP):** Detalham exigências documentais específicas que balizam os status repassados pela URA. `[CONFIRMADO]`.

### 4B — Normativos do Canal de Atendimento
* **Decreto Federal nº 11.034/2022 (Nova Lei do SAC):** Substitui o Dec 6.523/08. `[HIPÓTESE — VALIDAR aplicabilidade jurídica]` (A Caixa é empresa pública operando benefício estatal delegado, a aplicabilidade irrestrita das métricas do CDC a este cenário específico demanda jurisprudência).
* **Portaria SENACON 15/2022:** `[PENDENTE / EM ABERTO]` (Existência e publicidade como regulamentação direta do SAC não estabelecida/verificável nas bases pesquisadas).
* **Resolução ANATEL nº 605/2012 (RGQ-SCM/SMP):** Regula níveis de completamento e qualidade técnica de serviços 0800 repassados pelo Ator K. `[CONFIRMADO]`.

### 4C — Normativos de Tecnologia e Dados
* **Lei 13.709/2018 (LGPD) (Arts. 7º, II e 11, II):** Tratamento para política pública e autenticação. `[CONFIRMADO]`.
* **Decreto 10.046/2019:** Compartilhamento federal de dados. `[CONFIRMADO]`.
* **Portaria SLTI/MP nº 3/2007 (e-MAG):** Modelo de Acessibilidade. `[HIPÓTESE — VALIDAR método de fiscalização aplicável]` (Focado primariamente em web, sem especificações suficientes para URAs telefônicas).

### 4D — Normativos de Controle e Governança
* **Lei 14.133/2021 (Arts. 11 e 75):** Licitações do call center. `[CONFIRMADO]`.
* **IN TCU 84/2020:** Prestação de contas do FAT. `[CONFIRMADO]`.

---

## SEÇÃO 5 — Fail Points Conhecidos

**Objetivo:** Mapear os pontos de falha corrigindo inferências para hipóteses testáveis.

| ID | Etapa da Jornada | Ator / Sistema Causador | Descrição da Falha | Impacto no Cidadão | Status de Evidência |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **FP-01** | Pré-chamada | **A** (Empregador) | Atraso/erro no preenchimento das guias S-2299 no eSocial. | Ouve "Benefício não localizado", gerando pânico e idas indevidas ao SINE. | `[HIPÓTESE — VALIDAR via cruzamento de datas de transmissão S-2299 e consultas no log da URA]`. |
| **FP-02** | Autoatendimento | **D** (Dataprev) / **C** | Lentidão no processamento do lote noturno de atualização. | Informação telefônica desatualizada frente à Carteira Digital. | `[HIPÓTESE — VALIDAR via chamados abertos na Ouvidoria por divergência de saldo]`. |
| **FP-03** | Autenticação | **G** (Segurança) / **O** | KBA muito rígido solicitando dados de vínculos remotos. | Cidadão legítimo tem acesso bloqueado (Lockout) na URA. | `[HIPÓTESE — VALIDAR via métricas percentuais de falhas de KBA na central]`. |
| **FP-04** | Navegação | **O** (URA) | Árvore de menus com profundidade excessiva (becos sem saída). | Usuário perde-se e desliga; gera rediscagem artificial. | `[HIPÓTESE — VALIDAR via extração de logs de abandono em submenus específicos]`. |
| **FP-05** | Navegação | **P** (ASR/NLP) | Falha na compreensão de sotaques regionais ou ruído de rua. | O robô entra em loop repetindo "Não entendi". | `[HIPÓTESE — VALIDAR via auditoria por amostragem das transcrições (fallbacks) do NLP]`. |
| **FP-06** | Atendimento | **J** (ACD/CTI) | Queda técnica da ligação no exato momento do transbordo. | Necessidade de reiniciar a jornada do zero; raiva aguda. | `[HIPÓTESE — VALIDAR via volume de quedas classificadas como "drop de fila/transbordo" pelo fornecedor de Telecom]`. |
| **FP-07** | Desfecho | **Q** (Atendente) | Desligamento prematuro da chamada por pressão individual de TMA. | Permanência com pendência; possível violação pendente de aplicabilidade do Dec. 11.034. | `[HIPÓTESE — VALIDAR monitorando picos de chamadas com duração <10s após transbordo]`. |
| **FP-08** | Pré-chamada | **H** (Gov.br) | Falha no reconhecimento facial digital força migração à URA. | URA não tem sistema para destravar login Gov.br; atrito insolúvel. | `[HIPÓTESE — VALIDAR via tabulações de contato por "Erro Gov.br"]`. |
| **FP-09** | Recepção | **L** (TI Caixa) e **K** (Fornecedores) | Queda sistêmica ou lentidão severa dos bancos de dados internos da Caixa. | URA emite aviso fatal: "Sistema indisponível", derrubando a chamada do cidadão. | `[HIPÓTESE — VALIDAR via tickets de indisponibilidade de ambiente (Sustentação)]`. |
| **FP-10** | Autenticação | **N** (Cidadão - Defeso) | Cidadão (modalidade Pescador) liga fora da janela legal publicada por decreto de defeso. | Ouve "benefício não localizado" por questão temporal, não cadastral. | `[HIPÓTESE — VALIDAR via cruzamento de chamadas com calendário IBAMA/MPA]`. |
| **FP-11** | Navegação | **B** (CODEFAT) / **F** | *Lag* de governança: o CODEFAT publica nova regra, mas a URA demora semanas para atualizar scripts. | Cidadão é orientado com base em regra já revogada na data da chamada. | `[HIPÓTESE — VALIDAR via medição da janela de adequação de software pós-DOU]`. |
| **FP-12** | Autenticação | **G** (Segurança) / **O** | Bloqueio sistêmico prévio do CPF por tentativa externa de fraude e esgotamento KBA por terceiros. | Cidadão autêntico descobre que foi bloqueado sem ter feito ligações anteriores. | `[HIPÓTESE — VALIDAR via logs antifraude e registros em agências físicas]`. |
| **FP-13** | Autoatend. | **C** (MTE) / **D** | Cidadão possui histórico passado com cadastro bancário desatualizado ou divergente no ciclo atual. | Falha no roteamento de pagamento; conflito entre o informado e o depositado. | `[HIPÓTESE — VALIDAR avaliando a taxa de retornos de DOC/TED por dados divergentes]`. |
| **FP-14** | Desfecho | **Q** (Atendente) / **O** | Negativa do benefício informada sem nenhuma instrução legal sobre recurso à DPU (Defensoria) ou JEF. | Lacuna de acesso à Justiça; trabalhador desiste por falta de letramento sobre seus direitos. | `[HIPÓTESE — VALIDAR via revisão da biblioteca de scripts normativos do Ator Q]`. |

---

### Síntese de Interdependências Críticas

Com base no mapeamento atualizado, destacam-se três conexões críticas de risco sistêmico:

1.  **A Cadeia Cega de Dados (Atores A → D → C → O):** A interface da URA opera com dependência upstream dos dados imputados pelo empregador (S-2299) e consolidados pela Dataprev. A URA não possui autonomia em tempo real para editar erros dessa esteira, absorvendo o ônus do cidadão na linha de frente (FP-01).
2.  **Transbordo Institucional Cego (Atores H → O):** Quando falhas biométricas no Gov.br redirecionam tráfego para a URA, configura-se um beco sem saída. A avaliação sugere que há um bloqueio sistêmico: o Atendente Humano (Q) na Caixa não possuiria integração técnica para resetar credenciais geridas pelo Ministério da Gestão. *`[HIPÓTESE — VALIDAR via análise de permissões intrínsecas ao CRM do atendente]`*.
3.  **Fricção Tecnológica e Contratual no Transbordo (Atores J → Q → M):** O alinhamento entre o comutador CTI (J) e as metas de desempenho terceirizadas (TMA de Q, supervisionado por M) pode causar desligamentos e abandonos (FP-06, FP-07) no momento em que o trabalhador necessita de acolhimento resolutivo após o esgotamento do robô.

---

## SEÇÃO 6 — Resposta à Auditoria v1 (Changelog de Tratamento dos 39 Achados)

**Objetivo:** Registrar, achado por achado, como esta v2 tratou cada um dos 39 pontos levantados em `B_relatorio_auditoria_v1`. Cada achado recebe uma das três ações: **Corrigido** (conteúdo alterado), **Defendido** (mantido com justificativa de fato) ou **Aberto** (reclassificado como `[HIPÓTESE]` / `[PENDENTE]`).

### 1. Erros Factuais (9)

| Achado | Ação | Tratamento nesta v2 |
| :--- | :--- | :--- |
| **EF-1** | Corrigido | "CPF ou NIS (PIS/PASEP)" passou a "CPF **e** o NIS (PIS/PASEP/NIT)" como par de autenticação, com NIT incluído (Seção 1, Etapa 2). |
| **EF-2** | Corrigido | Removida a expressão "códigos de acesso"; o TRCT é descrito por datas de vínculo e valores (Seção 3, Etapa 1). |
| **EF-3** | Corrigido | Prazo passou a citar o normativo: "Art. 477, § 6º CLT / MOS eSocial" (Seção 2, Pré-chamada). |
| **EF-4** | Aberto | "D-1" reclassificado para `[HIPÓTESE — VALIDAR SLA D-1 na sincronia MTE-Caixa]` (Seção 2, Etapa 4). |
| **EF-5** | Aberto | Wrap-up time reclassificado para `[HIPÓTESE — VALIDAR 30 a 60s]` (Seção 2, Etapa 6). |
| **EF-6** | Corrigido | Removido o rótulo `[ATOR NOVO]`; FP-09 atribuído aos atores existentes **L** e **K** (Seção 5). |
| **EF-7** | Defendido | Mantida a Res. CODEFAT 957/2022 com Nota de Defesa de Fato: publicada no DOU em 23/09/2022, revogou a Res. 467/2005 (Seção 4A). |
| **EF-8** | Aberto | Portaria SENACON 15/2022 reclassificada para `[PENDENTE / EM ABERTO]` (Seção 4B). |
| **EF-9** | Aberto | Aplicabilidade do Dec. 11.034/2022 reclassificada para `[HIPÓTESE — VALIDAR aplicabilidade jurídica]` (Seção 4B). |

### 2. Etapas de Bastidor Omitidas (6)

| Achado | Ação | Tratamento nesta v2 |
| :--- | :--- | :--- |
| **BO-1** | Corrigido | Adicionada linha **Transversal (Governança)** — tradução de Resoluções CODEFAT em regras/scripts (Seção 2). |
| **BO-2** | Corrigido | Adicionada linha **Transversal (Controle)** — TCU/CGU (Ator I) auditando FAT e contratos (Seção 2). |
| **BO-3** | Corrigido | Adicionada linha **Transversal (Sustentação)** — Fornecedores (Ator K), enlaces e licenças URA (Seção 2). |
| **BO-4** | Corrigido | Supervisores (M) agora com processo descrito: "escuta e monitoram tráfego" (Seção 2, Etapa 5). |
| **BO-5** | Corrigido | Processo de tradução normativa CODEFAT → scripts URA contemplado na linha de Governança (Seção 2). |
| **BO-6** | Corrigido | Adicionado processo de gravação/arquivamento de chamadas pelo Ator L para compliance (Seção 2). |

### 3. Evidências Físicas Ausentes (5)

| Achado | Ação | Tratamento nesta v2 |
| :--- | :--- | :--- |
| **EFA-1** | Corrigido | Adicionada Carta de Concessão/Indeferimento (Seção 3, Desfecho). |
| **EFA-2** | Corrigido | Adicionada confirmação de crédito no Caixa Tem / extrato (Seção 3, Desfecho). |
| **EFA-3** | Corrigido | Adicionada atualização da CTPS Digital (Seção 3, Desfecho). |
| **EFA-4** | Corrigido | Adicionado sinal auditivo de fila/ringback/"alta demanda" antes da conexão (Seção 3, Etapas 1 e 2). |
| **EFA-5** | Corrigido | Adicionado comprovante de agendamento no SINE (Seção 3, Desfecho). |

### 4. Normativos Ausentes (5)

| Achado | Ação | Tratamento nesta v2 |
| :--- | :--- | :--- |
| **NO-1** | Corrigido | Decreto 7.721/2012 incluído na Seção 4A. |
| **NO-2** | Corrigido | LC 150/2015 (art. 26) incluída na Seção 4A. |
| **NO-3** | Corrigido | e-MAG movido para a Seção 4C com `[HIPÓTESE — VALIDAR fiscalização]`. |
| **NO-4** | Corrigido | Adicionada norma ANATEL para 0800 (Res. 605/2012) na Seção 4B. *(escopo revisitado na v3 após NF-4 da auditoria v2.)* |
| **NO-5** | Corrigido | Adicionadas Portarias do MTE na Seção 4A. *(verificabilidade revisitada na v3 após NO-5 parcial da auditoria v2.)* |

### 5. Fail Points Não Identificados (5)

| Achado | Ação | Tratamento nesta v2 |
| :--- | :--- | :--- |
| **FPO-1** | Corrigido | Adicionado **FP-10** — Defeso fora da janela temporal (Seção 5). |
| **FPO-2** | Corrigido | Adicionado **FP-11** — lag de governança CODEFAT → scripts (Seção 5). |
| **FPO-3** | Corrigido | Adicionado **FP-12** — bloqueio de CPF legítimo por fraude de terceiros (Seção 5). |
| **FPO-4** | Corrigido | Adicionado **FP-13** — cidadão recorrente com cadastro divergente (Seção 5). |
| **FPO-5** | Corrigido | Adicionado **FP-14** — negativa sem instrução sobre DPU/JEF (Seção 5). |

### 6. Inferências Mal-Suportadas / Fontes Fracas (9)

| Achado | Ação | Tratamento nesta v2 |
| :--- | :--- | :--- |
| **IF-1 a IF-7** | Corrigido | Os 7 fail points com `[CONFIRMADO]` em fontes genéricas foram **todos** reclassificados para `[HIPÓTESE — VALIDAR]` com método de validação específico por FP (Seção 5). |
| **IF-8** | Defendido/Atenuado | "Violação explícita do Dec. 11.034" suavizado para "possível violação **pendente de aplicabilidade**" (Seção 5, FP-07). |
| **IF-9** | Aberto | "URA como canal cego sem alçada de reset" reclassificado para `[HIPÓTESE — VALIDAR permissões do CRM]` (Síntese de Interdependências). |

**Resumo da v2:** dos 39 achados, **32 Corrigidos**, **2 Defendidos** (EF-7, IF-8) e **5 Abertos** como hipótese/pendência (EF-4, EF-5, EF-8, EF-9, IF-9 — reclassificações honestas). Nenhum achado foi ignorado.
