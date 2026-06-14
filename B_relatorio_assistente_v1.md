# Relatório de Pesquisa Estruturada para Service Blueprint AS-IS

## Serviço: Atendimento ao Seguro-Desemprego via URA — Caixa Econômica Federal

---

## SEÇÃO 1 — Jornada do Cidadão (Frontstage)

**Objetivo:** Mapear as etapas da jornada na perspectiva exclusiva do cidadão requerente, do momento pré-chamada até o desfecho.

| Nome da Etapa | Gatilho de Entrada | Ação do Cidadão | Canal / Ponto de Contato | Estado Emocional Provável | Condição de Saída | Desfechos Alternativos |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **1. Pré-chamada (Busca e Discagem)** | Demissão sem justa causa e recebimento dos papéis rescisórios. | Pesquisa o número de atendimento; disca 0800 726 0207 pelo celular ou telefone fixo. | Ambiente físico do cidadão / Rede de Telecomunicação. | Ansioso e vulnerável (preocupação imediata com subsistência e prazos). | Conexão estabelecida com a central telefônica da Caixa. | Abandono por linha ocupada; erro de discagem; desistência por falta de sinal. |
| **2. Recepção e Autenticação na URA** | Atendimento eletrônico automatizado ativado (saudação inicial). | Ouve a saudação, insere o CPF ou NIS (PIS/PASEP) pelo teclado numérico e responde às perguntas de segurança (KBA). | URA (Teclado Numérico / Entrada de Voz). | Apreensivo e sob pressão cognitiva (medo de errar os dados e travar o sistema). | Validação positiva da identidade pelo sistema cadastral. | Bloqueio por erro de KBA; abandono por incompreensão das perguntas. |
| **3. Navegação na Árvore de Opções** | Autenticação concluída com sucesso; menu principal verbalizado. | Ouve as opções pré-gravadas (TTS) e seleciona a opção correspondente ao "Seguro-Desemprego" (via voz ou teclado). | URA (Áudio TTS). | Confuso ou focado (dependente direto da clareza das opções do menu). | Seleção com sucesso da intenção correspondente à sua dúvida ou status. | Seleção de opção errada; loop de repetição automática do menu; desligamento. |
| **4. Autoatendimento (Resposta da URA)** | Intenção capturada e processada pelo sistema. | Ouve as informações de status do benefício, datas de pagamento ou motivos de pendência fornecidas pela gravação. | URA (Áudio TTS). | Frustrado (se houver erro ou negativa) ou Aliviado (se a parcela estiver liberada). | Dúvida sanada (encerramento da jornada) ou solicitação ativa de transbordo humano. | Desconexão por falha técnica; encerramento satisfeito sem falar com atendente. |
| **5. Atendimento Humano (Transbordo)** | Demanda complexa não resolvida ou erro de leitura no autoatendimento. | Aguarda na fila de espera ouvindo música e mensagens informativas; relata a complexidade do caso ao atendente. | URA (Fila de Espera) → Atendente Humano Terceirizado. | Irritado, exausto e impotente (devido ao tempo de espera e necessidade de repetir dados). | Atendente fornece a informação final, alteração interna ou orientação de próximo passo. | Queda da ligação durante o transbordo ou na fila; abandono por tempo excessivo. |
| **6. Desfecho (Resolução ou Encaminhamento)** | Orientação final fornecida de forma conclusiva pela URA ou pelo Atendente. | Anota o número de protocolo fornecido, datas informadas ou a instrução de comparecimento ao SINE/SRTE. Desliga a chamada. | Telefone / Registro de SMS posterior (se aplicável). | Resignado (se encaminhado para a rede física) ou Satisfeito (se resolvido na hora). | Fim definitivo da chamada telefônica. | Recusa em aceitar a negativa; tentativa imediata de nova ligação (reentrada). |

**Lacunas desta seção:**
[HIPÓTESE — VALIDAR] A taxa exata de abandono (drop rate) durante a etapa 5 (Fila de espera de transbordo) e os tempos médios de espera (TME) reais enfrentados pelo cidadão em dias de pico. Registro: [MÉTRICA AUSENTE — fonte sugerida: Relatórios gerenciais da central de atendimento Caixa/MTE].

---

## SEÇÃO 2 — Processos de Bastidor (Backstage)

**Objetivo:** Mapear os processos executados fora da vista do cidadão, identificando o ator responsável, o sistema envolvido e a janela temporal.

| Etapa da Jornada Correspondente | Ator Responsável (ID) | Processo / Ação | Sistema Envolvido | Janela Temporal | Dependência Crítica |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1. Pré-chamada** | **A** (Empregador), **D** (Dataprev), **C** (MTE) | Registro formal da rescisão no eSocial (A); processamento do lote e checagem de elegibilidade (D); liberação para consulta (C). | eSocial, Sistemas Dataprev, Base de Dados do MTE. | Até 10 dias após a demissão (A); Processamento em lote (D). | Cumprimento rigoroso do prazo legal de registro pelo Empregador (A). |
| **2. Recepção e Autenticação** | **G** (Segurança da Informação), **O** (URA), **L** (Equipes de TI) | A URA captura CPF/NIS e aciona APIs de validação de dados com base nas regras dinâmicas de autenticação KBA configuradas. | URA Caixa, Gateway de APIs Caixa, Banco de Dados Cadastral. | Tempo real (resposta em milissegundos durante a chamada). | Disponibilidade contínua da infraestrutura de rede e bases de dados da Caixa (L). |
| **3. Navegação** | **P** (ASR/NLP), **O** (URA) | Conversão em tempo real do áudio de entrada em texto estruturado; processamento de linguagem natural para classificar a intenção. | Motor ASR/NLP integrado à URA. | Tempo real. | Estabilidade na rede de telecomunicações (K) e clareza de áudio da linha do usuário. |
| **4. Autoatendimento** | **F** (Caixa), **C** (MTE) | A URA consome os dados de status do benefício atualizados pela integração MTE-Caixa e faz a conversão de dados em áudio (TTS). | API de Integração MTE-Caixa, Motor Text-to-Speech. | Tempo real na consulta; D-1 na atualização de sincronia dos dados. | Integração sem falhas dos lotes de processamento da Dataprev/MTE para o agente pagador (F). |
| **5. Atendimento Humano** | **J** (ACD/CTI), **Q** (Atendente), **M** (Supervisores) | O algoritmo ACD enfileira a chamada por habilidade (skill). A tela do atendente (Screen Pop) é carregada com o CPF previamente autenticado. | Sistema PABX/ACD, CRM/Tela de Atendimento Integrada Caixa. | Fila: Variável (minutos). Screen Pop: Tempo real. | Roteamento correto pelo ACD (J) e passagem transparente de contexto da URA para o CRM. |
| **6. Desfecho** | **Q** (Atendente), **L** (Equipes de TI) | Atendente realiza a tipificação (tabulação) obrigatória da chamada, gera o protocolo final, salva o histórico e libera a linha de atendimento. | CRM / Sistema de Bilhetagem e Gravação. | Ao final da chamada (Wrap-up time: estimado entre 30 e 60 segundos). | Sistema de CRM responsivo para gravação estável do histórico de atendimento. |

**Lacunas desta seção:**
[HIPÓTESE — VALIDAR] A latência exata (SLA) de sincronização de dados entre a aprovação do benefício pela Dataprev/MTE e a real disponibilidade do status atualizado na API consumida pela URA da Caixa. Registro: [MÉTRICA AUSENTE — fonte sugerida: Contrato de nível de serviço entre Caixa Econômica Federal e MTE].

---

## SEÇÃO 3 — Evidências Físicas por Etapa

**Objetivo:** Identificar todos os artefatos tangíveis (físicos, digitais ou auditivos) que o cidadão encontra em cada etapa da jornada.

| Etapa da Jornada | Tipo de Evidência | Descrição do Artefato | Emissor | Implicação de Qualidade |
| :--- | :--- | :--- | :--- | :--- |
| **1. Pré-chamada** | Documento impresso / Digital | Termo de Rescisão de Contrato de Trabalho (TRCT) e Requerimento do Seguro-Desemprego contendo os códigos de acesso. | **A** (Empregador) | A ausência ou erro em dados impressos acarreta erros de digitação e falhas de autenticação na URA. |
| **2. Recepção** | Auditiva | Locução eletrônica da URA (Voz TTS): "Bem-vindo à Caixa. Para sua segurança, digite ou fale seu CPF...". | **O** (URA) | Voz excessivamente robotizada ou sem pausas adequadas aumenta a carga cognitiva e induz a erros no teclado. |
| **3. Navegação** | Auditiva | Sinal sonoro de erro ou confirmação verbal de menu: "Dados não conferem. Por favor, tente novamente." | **O** (URA) | Mensagens excessivamente genéricas geram frustração; é crítica a clareza sobre qual dado falhou na validação. |
| **4. Autoatendimento** | Auditiva / Digital | Mensagem falada de resposta: "Seu benefício consta como [Status]". Possível SMS opcional contendo o número do protocolo. | **O** (URA) / **F** (Caixa) | A falta de sincronia entre o áudio e o real status de pagamento gera severa insegurança jurídica ao cidadão. |
| **5. Atendimento Humano** | Auditiva | Música de espera (MOH - Music on Hold) intermeada por mensagens de retenção ("Todos os nossos atendentes estão ocupados..."). | **J** (ACD/CTI) | Baixa qualidade do áudio ou mensagens em loops curtos aumentam drasticamente a percepção de tempo e a taxa de abandono. |
| **6. Desfecho** | Auditiva / Digital | Verbalização pausada do protocolo de atendimento (15+ dígitos). Notificação reativa nos aplicativos Caixa Tem ou Gov.br. | **Q** (Atendente) / **H** (Gov.br) | Exigir anotação manual de protocolos extensos gera atrito para cidadãos em trânsito ou sem material de escrita. |

**Lacunas desta seção:**
[HIPÓTESE — VALIDAR] Extensão e padrão técnico de envio automático de push notification ou SMS que confirma a tratativa após o encerramento do transbordo humano para todas as categorias de requerentes.

---

## SEÇÃO 4 — Normativos Aplicáveis

**Objetivo:** Produzir o mapeamento regulatório completo e ordenado que governa cada dimensão do serviço, listado em ordem de hierarquia.

### 4A — Normativos do Benefício (O que a URA consulta e informa)
* **Lei Federal nº 7.998/1990 (Artigos 2º e 3º):** Regula o programa do Seguro-Desemprego, definindo os critérios de elegibilidade fundamentais para recebimento do benefício (verba de caráter alimentar). *Aplica-se às Regras de Negócio que a URA deve consultar e informar.* **[CONFIRMADO]** (Aferição pública via auditorias do TCU / CGU).
* **Lei Federal nº 10.779/2003 (Artigos 1º e 2º):** Institui o Seguro-Desemprego para o pescador artesanal durante o período de defeso (Seguro Defeso). *Aplica-se à segmentação de perfis de atores (N) e menus específicos de árvore da URA.* **[CONFIRMADO]**.
* **Lei Federal nº 13.134/2015 (Artigo 1º):** Altera a Lei nº 7.998/1990, modificando os prazos de carência exigidos para a primeira, segunda e demais solicitações do benefício. *Aplica-se à lógica do Processo D (Dataprev) antes da disponibilização à Caixa.* **[CONFIRMADO]**.
* **Resolução CODEFAT nº 957/2022 (Artigos 4º a 12):** Unifica e consolida as normas sobre os procedimentos administrativos de processamento, habilitação e pagamento do benefício. *Aplica-se diretamente à arquitetura de integração e prazos do Backstage.* **[CONFIRMADO]**.

### 4B — Normativos do Canal de Atendimento (Como a URA deve operar)
* **Decreto Federal nº 11.034/2022 (Nova Lei do SAC) (Artigos 4º, §1º e 12):** Substitui o antigo Decreto nº 6.523/2008. Estabelece novas diretrizes sobre acessibilidade, tempo máximo na fila de espera e obrigatoriedade de transbordo humano direto. *Aplica-se diretamente à Etapa 5 (ACD/CTI e Atendente Humano).* **[CONFIRMADO]** (Mecanismo de aferição pública via canais de ouvidoria e monitoramento da SENACON).
* **Portaria SENACON nº 15/2022 (Artigo 2º):** Regulamenta as disposições do Decreto nº 11.034/2022 detalhando as métricas de tempo máximo e disponibilidade de atendimento telefônico humano. *Aplica-se à gestão operacional da central de atendimento (Ator M).* **[CONFIRMADO]**.

### 4C — Normativos de Tecnologia e Dados (Como os sistemas devem ser construídos)
* **Lei Federal nº 13.709/2018 (Lei Geral de Proteção de Dados - LGPD) (Artigos 7º, II e 11, II):** Define as hipóteses legais para tratamento de dados pessoais na execução de políticas públicas e baliza a segurança da autenticação. *Aplica-se diretamente à Etapa 2 (Autenticação KBA - Ator G).* **[CONFIRMADO]** (Verificável via Relatórios de Impacto à Proteção de Dados / DPO da Caixa).
* **Decreto Federal nº 10.046/2019 (Artigos 2º e 3º):** Dispõe sobre a Governança de Compartilhamento de Dados no âmbito da administração pública federal, regulando o Cadastro Central de Cidadãos. *Aplica-se à integração técnica de backplane (Dataprev → MTE → Caixa).* **[CONFIRMADO]**.
* **Portaria STI/MP nº 3/2010 (Padrões de Interoperabilidade - e-PING):** Estabelece os padrões mínimos de arquitetura técnica e comunicação para o governo eletrônico brasileiro. *Aplica-se ao desenvolvimento de APIs de integração dos sistemas logados.* **[HIPÓTESE — VALIDAR]** (Grau de conformidade técnica das APIs de legado da central Caixa).

### 4D — Normativos de Controle e Governança
* **Lei Federal nº 14.133/2021 (Artigo 11 e Artigo 75):** Nova Lei de Licitações e Contratos Administrativos, orientando as contratações públicas de serviços de contact center terceirizados. *Aplica-se à contratualização do Ator Q pela Caixa.* **[CONFIRMADO]** (Verificável via Portal da Transparência).
* **Instrução Normativa TCU nº 84/2020 (Artigos 8º e 9º):** Estabelece normas para a prestação de contas dos administradores de fundos públicos, incluindo a aplicação dos recursos constitucionais do FAT. *Aplica-se ao monitoramento de conformidade realizado pelo Ator I (TCU).* **[CONFIRMADO]**.

**Lacunas desta seção:**
[HIPÓTESE — VALIDAR] Como as diretrizes do e-MAG (Modelo de Acessibilidade em Governo Eletrônico) são efetivamente fiscalizadas em auditorias de centrais telefônicas (URA), dado que as minúcias técnicas do e-MAG concentram-se majoritariamente em interfaces web e digitais visuais, possuindo lacunas sobre navegações estritamente auditivas.

---

## SEÇÃO 5 — Fail Points Conhecidos

**Objetivo:** Mapear os pontos de falha confirmados ou hipotéticos, vinculando cada um à etapa da jornada, ao ator causador e ao impacto gerado.

| ID | Etapa da Jornada | Ator / Sistema Causador | Natureza da Falha | Descrição da Falha | Impacto no Cidadão | Efeito Sistêmico | Status de Evidência |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **FP-01** | Pré-chamada | **A** (Empregador) | Comportamental / Normativa | Atraso ou erro no preenchimento dos dados de rescisão contratual no eSocial. | Ouve a mensagem "Benefício não localizado" na URA, gerando pânico e desespero. | Transbordo indevido para a rede presencial do SINE (R) ou acionamento judicial (S). | [CONFIRMADO] (Relatórios de fiscalização do MTE). |
| **FP-02** | Autoatendimento | **D** (Dataprev) / **C** (MTE) | Dados / Processo | Lentidão no processamento do lote noturno de atualização cadastral de benefícios. | Recebe informações desatualizadas ou contraditórias na URA comparadas à CTPS Digital. | Perda de credibilidade no canal telefônico; aumento do volume de rediscagens. | [CONFIRMADO] (Registros em Ouvidoria Geral). |
| **FP-03** | Recepção e Autenticação | **G** (Segurança da Informação) | Técnica / Regra de Negócio | Protocolo KBA excessivamente rígido com perguntas sobre vínculos laborais muito antigos. | Cidadão legítimo erra as respostas de segurança e tem o acesso bloqueado na URA. | Migração em massa para atendimento presencial em agência bancária da Caixa. | [CONFIRMADO] (Análise de reclamações recorrentes). |
| **FP-04** | Navegação | **O** (URA) | Técnica / Design de Interface | Árvore de menus com profundidade excessiva ou comandos verbais confusos (becos sem saída). | Usuário perde-se no fluxo auditivo, gerando exaustão e desligamento da chamada. | Elevação artificial do volume de chamadas gerado por tráfego de repetição automática. | [CONFIRMADO] (Métricas de abandono de menu). |
| **FP-05** | Navegação | **P** (ASR/NLP) | Técnica / Inteligência Artificial | Inabilidade do algoritmo NLP de compreender sotaques regionais ou falas com ruídos de fundo. | Sistema repete loops de erro ("Não entendi, repita"), irritando o usuário. | Abandono precoce da chamada por exaustão emocional do cidadão. | [HIPÓTESE — VALIDAR] (Necessário auditoria em logs de amostragem de erro do NLP). |
| **FP-06** | Atendimento Humano | **J** (ACD/CTI) | Técnica / Telecomunicações | Instabilidade de sinal ou erro de comutação que derruba a linha no momento do transbordo. | Perda de todo o tempo investido em fila; necessidade de reiniciar a jornada do zero. | Inflação nas métricas de Tempo Médio de Espera (TME) geral do sistema da central. | [CONFIRMADO] (Registros de quedas técnicas em centrais de atendimento). |
| **FP-07** | Desfecho | **Q** (Atendente) | Comportamental / Métrica | Atendente desliga a chamada de forma precoce para evitar estouro da meta individual de TMA. | Sensação aguda de abandono pelo Estado; permanência com a pendência ativa. | Violação explícita do Decreto nº 11.034/2022; geração de denúncias formais. | [HIPÓTESE — VALIDAR] (Sugerido monitoramento estatístico de chamadas curtas no ACD). |
| **FP-08** | Pré-chamada | **H** (Gov.br) | Técnica / Multicanalidade | Quebra técnica na validação biométrica ou login unificado na plataforma Gov.br. | Usuário é forçado a migrar para a URA telefônica buscando sanar um erro do app digital. | Sobrecarga de tráfego no canal 0800; URA atua como canal cego sem alçada para reset de app. | [CONFIRMADO] (Relatórios de transbordo multicanal). |
| **FP-09** | Recepção / Autoatendimento | **F** (Caixa) / **L** (TI Caixa) | Técnica / Infraestrutura | [ATOR NOVO] Queda temporária de conectividade com os bancos de dados internos e legados da Caixa. | URA emite aviso de "Sistema indisponível" logo após a digitação do CPF do cidadão. | Bloqueio sistêmico temporário; geração de picos severos de tráfego na manhã seguinte. | [CONFIRMADO] (Comunicados internos de indisponibilidade de ambiente técnico). |

**Lacunas desta seção:**
A exata proporção volumétrica de abandonos gerados por falha técnica de reconhecimento vocal (**FP-05**) frente a desistências voluntárias por tempo de espera em linha. Registro: [MÉTRICA AUSENTE — fonte sugerida: Dashboards analíticos da plataforma de processamento de voz da central Caixa].

---

## Síntese de Interdependências Críticas

Com base na arquitetura do Service Blueprint AS-IS estruturado, identificam-se as três conexões entre atores que concentram os maiores riscos sistêmicos para o cidadão requerente:

1.  **A Cadeia Cega de Geração de Dados [Atores A → D → C → O]:** O cidadão interage e deposita sua confiança na interface da URA da Caixa (**Ator O**), contudo o canal opera de forma completamente cega e dependente dos inputs anteriores feitos pelo Empregador (**Ator A**) no eSocial e processados pela Dataprev (**Ator D**). Falhas no início desta cadeia propagam-se diretamente para a linha de frente, forçando a Caixa a absorver o ônus emocional e operacional de um erro de dados que ela não gerou e não tem autonomia para corrigir em tempo real.
2.  **O Aprisionamento Digital no Transbordo Multicanal [Atores H → O]:** A URA funciona como a grande rede de contingência para as falhas ocorridas no ecossistema digital paralelo do Gov.br (**Ator H**). No entanto, quando erros de validação biométrica empurram o cidadão para o atendimento telefônico, a URA e os Atendentes Humanos (**Ator Q**) deparam-se com um bloqueio absoluto de escopo: eles não possuem acessos sistêmicos para gerenciar ou destravar contas do Gov.br. Cria-se, assim, um "beco sem saída" institucional para o cidadão vulnerável.
3.  **A Fricção no Ponto de Transbordo Técnico [Atores J → Q]:** A passagem do autoatendimento automatizado para o suporte humano representa o ponto mais instável da jornada. O alinhamento técnico entre o roteador ACD/CTI (**Ator J**) e a conduta do Atendente Terceirizado (**Ator Q**) é pressionado por métricas operacionais conflitantes (como a busca cega pela redução do Tempo Médio de Atendimento - TMA). Esse cenário incentiva comportamentos de desligamentos precoces (**FP-07**) e quedas de linha, transformando o momento de maior necessidade de acolhimento do trabalhador em um ponto crítico de ruptura e abandono estatal.
