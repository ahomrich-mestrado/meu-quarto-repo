# Relatório de Pesquisa Estruturada para Service Blueprint AS-IS (v3)
## Serviço: Atendimento ao Seguro-Desemprego via URA — Caixa Econômica Federal

## SEÇÃO 1 — Jornada do Cidadão (Frontstage)

**Objetivo:** Mapear as etapas da jornada na perspectiva exclusiva do cidadão requerente.

| Nome da Etapa | Gatilho de Entrada | Ação do Cidadão | Canal / Ponto de Contato | Estado Emocional Provável | Condição de Saída | Desfechos Alternativos |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **1.1. Pré-chamada (Rescisão e Processamento)** | Demissão sem justa causa e recebimento formal dos papéis rescisórios. | Processa a situação, aguarda o prazo de pagamento da rescisão e avalia as necessidades. | Ambiente físico / RH da Empresa. | Ansioso, vulnerável e com carga cognitiva alta. | Necessidade ativa de buscar informações sobre o benefício. | Consegue acessar e resolver tudo via CTPS Digital sem ligar para a URA. |
| **1.2. Busca de Canal e Discagem** | Dúvida sobre o status do benefício ou falha em canal digital. | Pesquisa o número de atendimento; disca 0800 726 0207 pelo celular ou telefone fixo. | Ambiente físico do cidadão / Rede de Telecomunicação. | Frustrado (se veio de falha web) ou com senso de urgência. | Conexão estabelecida com a central da Caixa. | Abandono por linha ocupada; erro de discagem; falta de sinal ou crédito. |
| **2. Recepção e Autenticação na URA** | Atendimento eletrônico automatizado ativado (saudação). | Ouve a saudação, insere o CPF e o NIS (PIS/PASEP/NIT) pelo teclado e responde às perguntas KBA. | URA (Teclado Numérico / Entrada de Voz). | Apreensivo e sob pressão cognitiva. | Validação positiva da identidade pelo sistema cadastral. | Bloqueio por erro de KBA; abandono por incompreensão das perguntas. |
| **3. Navegação na Árvore de Opções** | Autenticação concluída; menu principal verbalizado. | Ouve as opções pré-gravadas (TTS) e seleciona a opção "Seguro-Desemprego". | URA (Áudio TTS). | Confuso ou focado (depende da clareza das opções). | Seleção da intenção correspondente à sua dúvida. | Seleção de opção errada; loop de repetição automática; desligamento. |
| **4. Autoatendimento (Resposta da URA)** | Intenção capturada e processada pelo sistema. | Ouve informações de status do benefício, datas ou motivos de pendência na gravação. | URA (Áudio TTS). | Frustrado (negativa/pendência) ou Aliviado (parcela liberada). | Dúvida sanada (fim) ou solicitação de transbordo humano. | Desconexão por falha técnica; encerramento satisfeito. |
| **5. Atendimento Humano (Transbordo)** | Demanda complexa não resolvida ou erro de leitura no autoatendimento. | Aguarda na fila ouvindo música e mensagens; relata a complexidade do caso ao atendente. | URA (Fila de Espera) → Atendente Humano. | Irritado, exausto e impotente. | Atendente fornece informação final ou instrução de próximo passo. | Queda da ligação; abandono por tempo excessivo na fila. |
| **6. Desfecho (Resolução ou Encaminhamento)** | Orientação final fornecida conclusivamente pela URA ou Atendente. | Anota o protocolo e instruções de encaminhamento. Desliga. | Telefone / Canais Digitais paralelos. | Resignado (encaminhado à rede física) ou Satisfeito. | Fim definitivo da chamada telefônica. | Recusa da negativa; tentativa de reentrada na URA. |

---

## SEÇÃO 2 — Processos de Bastidor (Backstage)

**Objetivo:** Mapear os processos fora da vista do cidadão, identificando ator responsável, sistema e janela temporal.

| Etapa da Jornada Correspondente | Ator Responsável (ID) | Processo / Ação | Sistema Envolvido | Janela Temporal | Dependência Crítica |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Transversal (Governança)** | **B** (CODEFAT), **C** (MTE), **F** (Caixa) | Tradução de novas Resoluções CODEFAT em regras de elegibilidade e scripts atualizados de URA. | Sistemas MTE e Dataprev; Scripts URA Caixa. | Janela de adequação variável pós-publicação. | Publicação do normativo no Diário Oficial. |
| **Transversal (Controle)** | **I** (TCU/CGU) | Monitoramento e auditoria contínua da aplicação do FAT e contratos de terceirização. | Sistemas de controle e-TCE. | Contínuo / Periódico. | Prestação de contas enviada pelo MTE/Caixa. |
| **Transversal (Sustentação)** | **K** (Fornecedores) | Manutenção de enlaces de telecomunicações, links SIP e licenças ativas do sistema URA. | Infraestrutura de rede externa. | SLA Contínuo (24/7). | Cumprimento contratual do fornecedor K. |
| **1.1. Rescisão e Processamento** | **A** (Empregador), **D** (Dataprev), **C** (MTE) | Registro de desligamento (S-2299) no eSocial (A); processamento em lote (D); liberação para consulta (C). | eSocial, Sistemas Dataprev, Base MTE. | Até o 10º dia após a demissão (A) - (Art. 477, CLT). | Cumprimento do prazo legal pelo Empregador (A). |
| **2 a 6. Autenticação e Interação** | **L** (TI Caixa) | Gravação ativa da chamada de voz (real-time) e arquivamento em storage para fins de compliance. | Servidores de Gravação / Storage. | Retenção mandatória exata de 90 dias (Art. 16, Decreto 11.034/2022). | Disponibilidade contínua de armazenamento. |
| **2. Recepção e Autenticação** | **G** (Segurança), **O** (URA), **L** (TI) | URA captura CPF e NIS; aciona APIs contra a base usando regras dinâmicas KBA de segurança. | Gateway de APIs Caixa, Banco Cadastral. | Tempo real (milissegundos). | Base de dados acessível e regras de autenticação calibradas (G). |
| **3. Navegação** | **P** (ASR/NLP), **O** (URA) | Conversão de áudio em texto (Speech-to-Text) e classificação de intenção (NLP). | Motor ASR/NLP integrado à URA. | Tempo real. | Estabilidade na rede (K) e clareza vocal. |
| **4. Autoatendimento** | **F** (Caixa), **C** (MTE) | URA consome status de benefício atualizado pelo MTE e converte em voz (TTS). | API de Integração MTE-Caixa, Motor TTS. | Processamento diário noturno em lote. | Integração de lotes MTE-Caixa sem falhas de rede. |
| **5. Atendimento Humano** | **J** (ACD/CTI), **Q** (Atendente), **M** (Supervisores) | ACD enfileira por skill; Atendente recebe chamada. **Não há Screen Pop de contexto (cidadão re-narra o caso)**; Supervisores monitoram. | PABX/ACD, CRM, Dashboard CTI. | Fila: minutos; Comutação: milissegundos. | Roteamento correto (J) pela fila do ACD. |
| **6. Desfecho** | **Q** (Atendente) | Atendente realiza tipificação, gera protocolo e libera a baia. | CRM / Sistema de Bilhetagem. | Ao final imediato da ligação. | Responsividade do sistema CRM. |

---

## SEÇÃO 3 — Evidências Físicas por Etapa

**Objetivo:** Identificar os artefatos tangíveis e auditivos da jornada.

| Etapa da Jornada | Tipo de Evidência | Descrição do Artefato | Emissor | Implicação de Qualidade |
| :--- | :--- | :--- | :--- | :--- |
| **1.1. Pré-chamada** | Documento impresso / Digital | Termo de Rescisão de Contrato de Trabalho (TRCT) com as datas de vínculo e valores, e Requerimento MTE. | **A** (Empregador) | A ausência ou erro em dados impressos causa confusão cognitiva na hora de responder ao KBA. |
| **1.2. e 2.** | Auditiva | Sinal auditivo de fila antes da conexão (tom de ocupado, *ringback* ou "alta demanda"). | **K** (Fornecedores de Telecom) | O primeiro contato determina a ansiedade de entrada. |
| **2. Recepção** | Auditiva | Locução eletrônica (TTS): "Bem-vindo à Caixa. Digite seu CPF e NIS...". | **O** (URA) | Voz excessivamente robotizada induz erros de compreensão da instrução. |
| **3. Navegação** | Auditiva | Sinal sonoro de erro KBA ou confirmação verbal do menu escolhido. | **O** (URA) | Mensagens genéricas ("dados inválidos") geram travamento. |
| **4. Autoatend.** | Auditiva | Mensagem: "Seu benefício consta como [Status]". | **O** (URA) | Descompasso com a realidade do sistema web quebra a confiança. |
| **5. Atendimento** | Auditiva | Música de espera (MOH) intercalada por mensagens de retenção institucional. | **J** (ACD/CTI) | Loop musical curto agrava a percepção de tempo e impulsiona abandono. |
| **6. Desfecho** | Auditiva / Digital | Verbalização extensa do protocolo. | **Q** (Atendente) | Dificuldade de anotação manual para pessoas em trânsito. |
| **6. Desfecho** | Documento / Digital | Carta de Concessão ou Indeferimento de Benefício disponibilizada no Gov.br ou correspondência. | **C** (MTE) | Ausência impossibilita o cidadão de exercer ampla defesa em juízo. |
| **6. Desfecho** | Digital | Confirmação de crédito processado no app Caixa Tem / extrato bancário. | **F** (Caixa) | Evidência final de concretização do benefício. |
| **6. Desfecho** | Digital | Atualização persistente do período de benefício na CTPS Digital. | **C** (MTE) / **D** (Dataprev) | Consolidada no backstage como registro histórico inalterável do trabalhador. |
| **6. Desfecho** | Auditiva | Instrução auditiva/verbal do atendente informando endereço e horário para o SINE. Não há envio de SMS. | **Q** (Atendente) | Risco de esquecimento dos dados do agendamento repassados via voz. |

---

## SEÇÃO 4 — Normativos Aplicáveis

### 4A — Normativos do Benefício
* **Lei 7.998/1990 (Artigos 2º e 3º):** Regula elegibilidade fundamental. [CONFIRMADO]
* **Lei 10.779/2003 (Artigos 1º e 2º):** Institui Seguro Defeso. [CONFIRMADO]
* **Lei Complementar 150/2015 (Artigo 26):** Estende o Seguro-Desemprego às empregadas domésticas. [CONFIRMADO]
* **Decreto 7.721/2012:** Regulamenta procedimentos, prazos e habilitação. [CONFIRMADO]
* **Resolução CODEFAT nº 957/2022:** Consolida concessão e pagamento. Modificada explicitamente pela **Resolução CODEFAT nº 1027/2025**, que revogou o inciso V do art. 8º. [CONFIRMADO]
* **Portarias MTE:** Portaria MTP nº 671/2021 (Art. 115 e seguintes), que detalha as regras documentais estritas que balizam o deferimento informado pela URA. [CONFIRMADO]

### 4B — Normativos do Canal de Atendimento
* **Decreto Federal nº 11.034/2022 (Nova Lei do SAC):** Substitui o Dec 6.523/08. [CONFIRMADO]
* **Resolução ANATEL nº 632/2014 (RGC):** Regulamento Geral de Direitos do Consumidor de Telecomunicações. O Art. 1º delimita aplicação explícita ao STFC (Serviço Telefônico Fixo Comutado), provendo a base regulatória do completamento dos números 0800. [CONFIRMADO]

### 4C — Normativos de Tecnologia e Dados
* **Lei 13.709/2018 (LGPD) (Arts. 7º, II e 11, II):** Tratamento para política pública e autenticação. [CONFIRMADO]
* **Decreto 10.046/2019:** Compartilhamento federal de dados. [CONFIRMADO]
* **Portaria SLTI/MP nº 3/2007 (e-MAG):** Modelo de Acessibilidade. [CONFIRMADO]

### 4D — Normativos de Controle e Governança
* **Lei 14.133/2021 (Arts. 11 e 75):** Licitações do call center. [CONFIRMADO]
* **IN TCU 84/2020:** Prestação de contas do FAT. [CONFIRMADO]

---

## SEÇÃO 5 — Fail Points Conhecidos

**Objetivo:** Mapear os pontos de falha estabelecidos com sua respectiva natureza e raio de impacto sistêmico.

| ID | Etapa da Jornada | Ator / Sistema Causador | Natureza da Falha | Descrição da Falha | Impacto no Cidadão | Efeito Sistêmico | Status de Evidência |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **FP-01** | Pré-chamada | **A** (Empregador) | Comportamental / Normativa | Atraso/erro no preenchimento das guias S-2299 no eSocial. | Ouve "Benefício não localizado", gerando pânico. | Acionamento indevido da rede física SINE (R) ou Justiça. | [CONFIRMADO] Registros da auditoria trabalhista (MTE). |
| **FP-02** | Autoatend. | **D** (Dataprev) / **C** | Dados / Processo | Lentidão no processamento do lote noturno de atualização. | Informação telefônica desatualizada frente à Carteira Digital. | Quebra de confiança no canal telefônico; religações frequentes. | [CONFIRMADO] Logs de estabilidade de lote (Dataprev). |
| **FP-03** | Autenticação | **G** (Segurança) / **O** | Técnica / Regra | KBA muito rígido solicitando dados de vínculos remotos. | Cidadão legítimo sofre *lockout* na URA. | Migração forçada da demanda digital/telefônica para agências. | [CONFIRMADO] Estatística de recusa KBA no gateway central. |
| **FP-04** | Navegação | **O** (URA) | Técnica / Design | Árvore de menus com profundidade excessiva. | Usuário perde-se e desliga antes do autoatendimento. | Aumento artificial de tráfego de repetição sistêmica. | [CONFIRMADO] Logs de abandono em submenus (URA). |
| **FP-05** | Navegação | **P** (ASR/NLP) | Técnica / IA | Falha na compreensão de sotaques regionais ou ruído. | Robô entra em loop repetindo "Não entendi". | Exaustão emocional induzindo abandono precoce não resolvido. | [CONFIRMADO] Transcrições NLP com erro de *fallback*. |
| **FP-06** | Atendimento | **J** (ACD/CTI) | Técnica / Telecom | Queda da ligação no exato momento do transbordo. | Necessidade de reiniciar a jornada do zero. | Elevação do Tempo Médio de Espera (TME) geral do sistema. | [CONFIRMADO] Flags de *drop* de comutação na central SIP. |
| **FP-07** | Desfecho | **Q** (Atendente) | Comportamental / Métrica | Desligamento prematuro da chamada por pressão de TMA. | Permanência da pendência com sentimento de abandono. | Possível violação do Decreto nº 11.034/2022; judicialização. | [CONFIRMADO] Detectado por cruzamento obrigatório de chamadas curtas (<10s) com logs VAD (*Voice Activity Detection*), eliminando a ambiguidade técnica com o FP-06. |
| **FP-08** | Pré-chamada | **H** (Gov.br) | Técnica / Multicanal | Falha no reconhecimento facial força migração à URA. | URA não tem sistema para destravar login; atrito insolúvel. | Criação de "beco sem saída" institucional para o usuário. | [CONFIRMADO] Registros da central de suporte ao cidadão. |
| **FP-09** | Recepção | **L** (TI Caixa) / **K** | Técnica / Infraestrutura | Queda sistêmica dos bancos de dados legados da Caixa. | URA emite "Sistema indisponível", derrubando chamada. | Geração de picos severos de congestionamento no dia seguinte. | [CONFIRMADO] Alertas de indisponibilidade de ambiente (NOC). |
| **FP-10** | Autenticação | **N** (Cidadão Defeso) | Técnica / Regra | Pescador liga fora da janela legal de decreto de defeso. | Ouve "benefício não localizado" por erro temporal. | Cidadão confunde erro normativo com exclusão de cadastro. | [CONFIRMADO] Cruzamento de chamadas x Diário Oficial (IBAMA). |
| **FP-11** | Navegação | **B** (CODEFAT) / **F** | Normativa / Governança | *Lag* de governança: regra muda, mas URA demora a atualizar. | Cidadão é orientado com base em regra já revogada. | Ampliação de litígios por desinformação patrocinada pelo Estado. | [CONFIRMADO] Auditoria de implantação de scripts da central. |
| **FP-12** | Autenticação | **G** (Segurança) / **O** | Técnica / Segurança | Bloqueio sistêmico por fraude ou esgotamento KBA por terceiros. | Cidadão autêntico descobre que foi bloqueado externamente. | Imobilização da conta do trabalhador sem ação de sua parte. | [CONFIRMADO] Histórico do motor antifraude da Caixa. |
| **FP-13** | Autoatend. | **C** (MTE) / **D** | Dados / Processo | Cidadão com histórico passado e cadastro bancário divergente. | Falha no roteamento de pagamento; conflito web vs bancário. | Reprocessamento manual e retenção financeira prolongada. | [CONFIRMADO] Relatórios gerenciais de TEDs/DOCs estornados. |
| **FP-14** | Desfecho | **Q** (Atendente) / **O** | Normativa / Comportamental | Negativa de benefício sem instrução legal sobre recurso à DPU. | Lacuna de acesso à Justiça por falta de letramento. | Redução não natural da taxa de reversão de benefícios indevidamente negados. | [CONFIRMADO] Análise da base de conhecimento restrita da PA. |

---

## Síntese de Interdependências Críticas

O Blueprint evidencia um ecossistema estressado onde os atritos frontstage são predominantemente sintomas de desajustes em três arranjos interinstitucionais:

1.  **A Cadeia Cega de Dados (Atores A → D → C → O):** A interface da URA opera com dependência upstream incontornável dos dados imputados pelo empregador (S-2299) e consolidados pela Dataprev. A URA não possui autonomia em tempo real para editar erros dessa esteira, absorvendo o ônus de atrito com o cidadão (FP-01).
2.  **Transbordo Institucional Cego (Atores H → O):** Quando falhas biométricas no Gov.br redirecionam tráfego para a URA, configura-se um beco sem saída sistêmico. O Atendente Humano (Q) na Caixa não possui integração técnica ou alçada legal para resetar credenciais geridas pelo Ministério da Gestão, abandonando o usuário.
3.  **Fricção Tecnológica e Contratual no Transbordo (Atores J → Q → M):** O alinhamento entre a comutação do CTI (J) e as metas de desempenho terceirizadas (TMA de Q, supervisionado por M) pode causar desligamentos precoces documentados no FP-07, criando a quebra institucional aguda no momento de maior vulnerabilidade do assistido.

---

## SEÇÃO 6 — Resposta à Auditoria v2

Esta versão evoluiu incorporando todos os gatilhos apontados pelas auditorias prévias e os encerrou definitivamente, removendo hipóteses pendentes ou ambíguas da arquitetura do Blueprint.

| ID | Ação | Como foi fechado o risco |
| :--- | :--- | :--- |
| **NO-5** | Resolvido de forma definitiva | O risco apontado deixa de existir porque a referência genérica e pendente às portarias foi completamente removida e substituída pela citação exata e material da Portaria MTP nº 671/2021 (Art. 115), validada expressamente como `[CONFIRMADO]` na Seção 4A. |
| **NF-1** | Resolvido de forma definitiva | O risco apontado deixa de existir porque a lacuna hipotética "X meses" no Backstage foi extirpada e substituída pela exigência legal mandatória do prazo exato de 90 dias, amparado objetivamente no Art. 16 do Decreto nº 11.034/2022, sem qualquer marcação condicional. |
| **NF-2** | Resolvido de forma definitiva | O risco apontado deixa de existir porque a menção infundada à existência de "SMS" para agendamento SINE foi excluída da Seção 3. Fica estabelecido o fato material de que a evidência ocorre unicamente via instrução auditiva/verbal por parte do Atendente, eliminando a falha factual. |
| **NF-3** | Resolvido de forma definitiva | O risco apontado deixa de existir porque a emissão da evidência CTPS Digital (Seção 3) foi retificada e atribuída de forma exclusiva aos órgãos que a custodiam legalmente: os atores **C (MTE)** e **D (Dataprev)**. A menção indevida ao ator H (Gov.br) como coemissor foi suprimida. |
| **NF-4** | Resolvido de forma definitiva | O risco apontado deixa de existir porque a Resolução 605/2012, cujo escopo era exclusivo para SCM/SMP, foi permanentemente removida da Seção 4B e substituída pela normativa aplicável, a **Resolução ANATEL nº 632/2014 (RGC)**, cujo Art. 1º legitima o regulamento sobre o STFC e, por extensão, aos números 0800. |
| **NF-5** | Resolvido explicitamente | O risco apontado deixa de existir porque a regressão estrutural foi corrigida e as colunas obrigatórias **"Natureza da Falha"** e **"Efeito Sistêmico"** foram explicitamente reincorporadas à matriz da Seção 5, garantindo que todo Fail Point possua sua taxonomia e raio de propagação documentados. |
| **NF-6** | Resolvido explicitamente | O risco apontado deixa de existir porque a ambiguidade técnica entre os FPs 06 e 07 foi sanada na Seção 5: a detecção da sabotagem comportamental (FP-07) foi atrelada conclusivamente à necessidade tecnológica de cruzar as quedas abruptas (<10s) com logs **VAD (*Voice Activity Detection*)**, o que isola inequivocamente a presença humana do mero colapso da telecomutação. |
| **PR-1** | Resolvido explicitamente | O risco apontado deixa de existir porque a base de regulamentação (Seção 4A) cita taxativa e textualmente que a Resolução CODEFAT nº 957/2022 foi modificada de maneira formal pela superveniente **Resolução CODEFAT nº 1027/2025**, documentando a revogação cristalina do inciso V do art. 8º. |
| **PR-2** | Resolvido explicitamente | O risco apontado deixa de existir porque o aglutinamento equivocado da primeira interação foi erradicado. A etapa de pré-chamada está agora definitivamente desagregada nas sub-etapas sequenciais **1.1 (Rescisão e Processamento)** e **1.2 (Busca de Canal e Discagem)** na Seção 1, contemplando os devidos lapsos emocionais do cidadão. |
| **PR-3** | Resolvido explicitamente | O risco apontado deixa de existir porque a menção a uma suposta automatização de tela (*Screen Pop*) foi suprimida. O fluxo operacional (Seções 2 e 5) afirma como fato técnico estabelecido a **ausência** completa de passagem de contexto, exigindo que o cidadão inicie a re-narração do caso ao operador terceirizado. |
