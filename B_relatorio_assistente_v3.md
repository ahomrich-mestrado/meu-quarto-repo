# Relatório de Pesquisa Estruturada para Service Blueprint AS-IS (v3)

## Serviço: Atendimento ao Seguro-Desemprego via URA — Caixa Econômica Federal

## SEÇÃO 1 — Jornada do Cidadão (Frontstage)

**Objetivo:** Mapear as etapas da jornada na perspectiva exclusiva do cidadão requerente.

| Nome da Etapa | Gatilho de Entrada | Ação do Cidadão | Canal / Ponto de Contato | Estado Emocional Provável | Condição de Saída | Desfechos Alternativos |
| --- | --- | --- | --- | --- | --- | --- |
| **1.1. Pré-chamada (Rescisão e Processamento)** | Demissão sem justa causa e recebimento formal dos papéis rescisórios. | Processa a nova situação de desemprego, aguarda o prazo da rescisão e avalia as necessidades. | Ambiente físico / RH da Empresa. | Ansioso, vulnerável e com carga cognitiva alta. | Necessidade ativa de buscar informações sobre a habilitação. | Consegue acessar e resolver via CTPS Digital sem precisar da URA. |
| **1.2. Busca de Canal e Discagem** | Dúvida sobre status do benefício ou falha bloqueante em canal digital. | Pesquisa o número de atendimento 0800; disca 0800 726 0207 pelo celular ou telefone fixo. | Ambiente físico / Rede de Telecomunicação. | Frustrado (se veio de falha web) ou com senso de urgência. | Conexão estabelecida com a central PABX da Caixa. | Abandono por linha ocupada; erro de discagem; falta de sinal/crédito. |
| **2. Recepção e Autenticação na URA** | Atendimento eletrônico automatizado ativado (saudação). | Ouve a saudação, insere CPF e NIS (PIS/PASEP/NIT) no teclado e responde às perguntas KBA. | URA (Teclado Numérico / Entrada de Voz). | Apreensivo e sob pressão cognitiva de cometer erro. | Validação positiva da identidade pelo sistema de cadastro. | Bloqueio sistêmico por erro de KBA; abandono por incompreensão. |
| **3. Navegação na Árvore de Opções** | Autenticação KBA concluída; menu principal verbalizado. | Ouve as opções pré-gravadas (TTS) e seleciona o fluxo "Seguro-Desemprego". | URA (Áudio TTS). | Confuso ou focado (depende exclusivamente da clareza das opções). | Seleção da intenção correspondente ao status do benefício. | Seleção de opção errada; loop de repetição do menu; desligamento. |
| **4. Autoatendimento (Resposta da URA)** | Intenção capturada e processada na base. | Ouve informações de status (deferido/indeferido), datas de pagamento ou motivos de pendência. | URA (Áudio TTS). | Frustrado (negativa/pendência) ou Aliviado (parcela liberada e agendada). | Dúvida sanada (encerramento da jornada) ou solicitação de transbordo. | Desconexão súbita por falha técnica; encerramento satisfeito da chamada. |
| **5. Atendimento Humano (Transbordo)** | Demanda complexa não resolvida na URA ou erro interpretativo do TTS. | Aguarda na fila ouvindo música e mensagens; re-narra a complexidade do seu caso ao atendente (sem passagem de contexto). | URA (Fila de Espera) → Atendente Humano Terceirizado. | Irritado, exausto e impotente pela repetição. | Atendente fornece informação detalhada final ou instrução de próximo passo. | Queda técnica da ligação (drop); abandono voluntário por TME excessivo na fila. |
| **6. Desfecho (Resolução ou Encaminhamento)** | Orientação final fornecida conclusivamente pela URA ou Atendente. | Anota o longo protocolo verbalizado e eventuais instruções (ex: ida presencial ao SINE). Desliga. | Telefone / Canais Digitais paralelos. | Resignado (se encaminhado à rede física) ou Satisfeito (resolução em linha). | Fim definitivo da chamada telefônica e do protocolo. | Recusa contenciosa da negativa; tentativa agressiva de reentrada na URA. |

**Lacunas desta seção:**
`[HIPÓTESE — VALIDAR via extração de CDRs do PABX]` A taxa de abandono (drop rate) exata na Etapa 5 e os Tempos Médios de Espera (TME) reais enfrentados em dias de pico (ex: 5º dia útil).

---

## SEÇÃO 2 — Processos de Bastidor (Backstage)

**Objetivo:** Mapear os processos fora da vista do cidadão, identificando ator responsável, sistema e janela temporal.

| Etapa da Jornada Correspondente | Ator Responsável (ID) | Processo / Ação | Sistema Envolvido | Janela Temporal | Dependência Crítica |
| --- | --- | --- | --- | --- | --- |
| **Transversal (Governança)** | **B** (CODEFAT), **C** (MTE), **F** (Caixa) | Tradução e parametrização de novas Resoluções CODEFAT em regras e scripts de atendimento da URA. | Sistemas MTE, Dataprev; Scripts URA Caixa. | Janela de adequação sistêmica pós-DOU. | Publicação técnica e normativa no Diário Oficial. |
| **Transversal (Controle)** | **I** (TCU / CGU) | Monitoramento e auditoria permanente da aplicação do FAT e de contratos de call center terceirizado. | Sistemas e-TCE (Controle Externo). | Contínuo / Ciclos Periódicos. | Prestação de contas fiscal enviada pelo MTE e Caixa. |
| **Transversal (Sustentação)** | **K** (Fornecedores de Infra) | Sustentação de enlaces de telecomunicações, rotas SIP e licenciamento ativo dos nós de URA. | Infraestrutura externa de rede e comutação. | Contínuo (SLA 24/7). | Cumprimento contratual de *uptime* e banda pelo Ator K. |
| **1.1. Rescisão e Processamento** | **A** (Empregador), **D** (Dataprev), **C** (MTE) | Registro do evento de desligamento (S-2299) no eSocial (A); processamento noturno em lote (D); liberação final (C). | eSocial, Dataprev, Base Caged/MTE. | Até o 10º dia após a demissão (A) - (Art. 477, § 6º CLT). | Cumprimento tempestivo do prazo legal pelo Empregador (A). |
| **2 a 6. Autenticação e Interação** | **L** (TI Caixa / Segurança) | Gravação integral da chamada de voz (real-time) e arquivamento compulsório no storage de compliance. | Servidores de Gravação / Storage de Arquivo. | Retenção mandatória de 90 dias (Art. 16, Decreto 11.034/2022). | Disponibilidade elástica de armazenamento no Data Center. |
| **2. Recepção e Autenticação** | **G** (Segurança Info), **O** (URA), **L** (TI) | Captura das chaves CPF e NIS; disparo de APIs KBA dinâmicas contra a base de dados centralizada. | Gateway API Caixa, Banco de Dados Cadastral. | Tempo real de milissegundos. | Base de dados responsiva e motores de KBA ativos e calibrados. |
| **3. Navegação** | **P** (ASR/NLP), **O** (URA) | Conversão STT (Speech-to-Text) do áudio da linha e inferência NLP para classificação de intenção do cidadão. | Motor ASR/NLP cognitivo acoplado à URA. | Tempo real de processamento de voz. | Estabilidade acústica da rede (K) e clareza fonética do cidadão. |
| **4. Autoatendimento** | **F** (Caixa Econômica), **C** (MTE) | URA consome *payload* de status do benefício da base MTE e verbaliza via conversão Text-to-Speech (TTS). | API Integração MTE-Caixa, Engine TTS. | `[HIPÓTESE — VALIDAR SLA D-1 na sincronia de dados]` | Fluxo de mensageria MTE-Caixa operando sem congestionamento. |
| **5. Atendimento Humano** | **J** (ACD/CTI), **Q** (Atendente Humano), **M** (Supervisão) | ACD comuta a chamada. **Não há Screen Pop de contexto configurado**; o Atendente (Q) atende de forma limpa e requer redigitação/renarração. | PABX/ACD, CRM Legado da Terceirizada. | Fila: minutos; Comutação: segundos. | Disponibilidade livre de baias (PAs) gerenciadas pelo Ator M. |
| **6. Desfecho** | **Q** (Atendente Terceirizado) | Atendente preenche formulário de tipificação, gera protocolo normativo e derruba o status para liberar a PA. | CRM Operacional / Sistema de Bilhetagem. | `[HIPÓTESE — VALIDAR Wrap-up/TMA real via relatórios de BI]` | Interface do CRM livre de travamentos durante o *wrap-up*. |

---

## SEÇÃO 3 — Evidências Físicas por Etapa

**Objetivo:** Identificar os artefatos tangíveis, auditivos e digitais consolidados na jornada.

| Etapa da Jornada | Tipo de Evidência | Descrição do Artefato | Emissor | Implicação de Qualidade |
| --- | --- | --- | --- | --- |
| **1.1. Pré-chamada** | Documento / Digital | Termo de Rescisão de Contrato de Trabalho (TRCT) validado, contendo CNPJ e datas, mais Requerimento MTE. | **A** (Empregador) | Divergências impressas induzem a respostas falhas no questionário de KBA da central. |
| **1.2. e 2. Recepção** | Auditiva | Sinal elétrico de chamada em curso (*ringback tone*) ou tom rápido de ocupado/congestionamento da rede. | **K** (Fornecedores de Infra/Telecom) | Falhas aqui barram o acesso básico do cidadão ao Estado (esgotamento de rotas SIP). |
| **2. Recepção** | Auditiva | Locução eletrônica (TTS) de *greeting*: "Bem-vindo à Caixa. Digite seu CPF e NIS...". | **O** (URA Caixa) | Qualidade robótica extrema reduz a inteligibilidade das regras de digitação. |
| **3. Navegação** | Auditiva | Sinal sonoro abrupto de falha KBA ou confirmação verbal cadenciada da árvore de menu principal. | **O** (URA Caixa) | Retornos cegos (ex: "Dados inválidos") sem apontar qual dado específico falhou geram *lockouts* e frustração aguda. |
| **4. Autoatendimento** | Auditiva | Mensagem verbalizada: "Seu benefício consta como [Deferido/Indeferido/Retido]". | **O** (URA Caixa) | O descompasso entre o áudio da URA e a visualização no portal web fratura a credibilidade governamental. |
| **5. Atendimento** | Auditiva | Música repetitiva de espera (MOH) cortada por frases de *hold* institucional ("Nossos atendentes estão ocupados..."). | **J** (Motor ACD/CTI) | Um loop musical de curta duração afeta a percepção do tempo, elevando fortemente o abandono voluntário. |
| **6. Desfecho** | Auditiva | Verbalização numérica longa e ininterrupta do protocolo de atendimento gerado. | **Q** (Atendente Terceirizado) | Alta fricção para trabalhadores em trânsito, sem acesso rápido a material para registro físico. |
| **6. Desfecho** | Digital / Híbrida | Carta formal de Concessão ou Indeferimento de Benefício disponibilizada no Gov.br ou correspondência postal. | **C** (MTE) | Ausência documental absoluta inviabiliza que o cidadão recorra ao Judiciário ou à DPU para ampla defesa. |
| **6. Desfecho** | Digital (Financeira) | Confirmação explícita de crédito depositado no extrato bancário ou notificação push no aplicativo Caixa Tem. | **F** (Caixa Econômica) | Representa a evidência máxima de encerramento resolutivo (superação primária da vulnerabilidade alimentar). |
| **6. Desfecho** | Digital (Registral) | Atualização persistente do período de recebimento do Seguro-Desemprego averbado no registro do trabalhador. | **C** (MTE) e **D** (Dataprev) | Evidência histórica vitalícia inalterável que compõe o patrimônio e os vínculos do Cidadão (N). |
| **6. Desfecho** | Auditiva (Encaminhamento) | Instrução verbal e auditiva do atendente com endereço e horário para comparecimento presencial na rede SINE. | **Q** (Atendente Terceirizado) | Risco de esquecimento dos dados do agendamento, causando idas perdidas a agências não habilitadas. |

---

## SEÇÃO 4 — Normativos Aplicáveis

### 4A — Normativos do Benefício

* **Lei nº 7.998/1990 (Artigos 2º e 3º):** Regula a elegibilidade estrutural e carências do programa do Seguro-Desemprego. [CONFIRMADO]
* **Lei nº 10.779/2003 (Artigos 1º e 2º):** Institui o Seguro-Desemprego para a modalidade Pescador Artesanal (Seguro Defeso). [CONFIRMADO]
* **Lei Complementar nº 150/2015 (Artigo 26):** Estende oficialmente o benefício à categoria das empregadas domésticas. [CONFIRMADO]
* **Decreto nº 7.721/2012:** Regulamenta procedimentos administrativos, prazos e habilitação. [CONFIRMADO]
* **Resolução CODEFAT nº 957/2022:** Consolida ritos de concessão. **Modificada explicitamente pela Resolução CODEFAT nº 1027/2025**, que revogou o inciso V do art. 8º (prazos do pescador). [CONFIRMADO]
* **Portarias MTE:** [PENDENTE — identificar número/ano/artigo específico das portarias que regulam minúcias do deferimento repassado à URA].

### 4B — Normativos do Canal de Atendimento

* **Decreto Federal nº 11.034/2022 (Nova Lei do SAC):** Substitui o Dec. 6.523/08. [HIPÓTESE — VALIDAR aplicabilidade estrita à Caixa na operação de um fundo soberano/estatal delegado].
* **Portaria SENACON nº 15/2022:** [PENDENTE / EM ABERTO — evidência não ratificada nos diários e repositórios diretos].
* **Resolução ANATEL nº 632/2014 (RGC):** Regulamento Geral de Direitos do Consumidor de Telecomunicações. O Art. 1º delimita que suas disposições se aplicam integralmente à prestação do STFC, abrangendo a qualidade técnica das chamadas receptivas em números 0800 contratadas pela central. [CONFIRMADO]

### 4C — Normativos de Tecnologia e Dados

* **Lei nº 13.709/2018 (LGPD) (Arts. 7º, II e 11, II):** Exceções legais de tratamento de dados sensíveis e pessoais para viabilização de políticas públicas e aplicação de KBA. [CONFIRMADO]
* **Decreto nº 10.046/2019:** Regula o intercâmbio transversal de bases de dados do Governo Federal. [CONFIRMADO]
* **Portaria SLTI/MP nº 3/2007 (e-MAG):** Diretrizes de Acessibilidade. [HIPÓTESE — VALIDAR a existência de parâmetros de fiscalização exequíveis e não-ambíguos do e-MAG sobre fluxos puramente telefônicos DTMF/Voice].

### 4D — Normativos de Controle e Governança

* **Lei nº 14.133/2021 (Arts. 11 e 75):** Framework licitatório incidente sobre a formatação e as metas da contratação do call center terceirizado. [CONFIRMADO]
* **IN TCU nº 84/2020:** Baliza os relatórios de governança e prestação de contas sobre a integridade e destinação de rubricas do FAT. [CONFIRMADO]

---

## SEÇÃO 5 — Fail Points Conhecidos

**Objetivo:** Mapear todos os gargalos sistêmicos contendo Identificação, Causalidade, Natureza do atrito, Efeitos Locais e Propagação Sistêmica integral.

| ID | Etapa da Jornada | Ator / Sistema Causador | Natureza da Falha | Descrição da Falha Operacional | Impacto no Cidadão | Efeito Sistêmico | Status de Evidência / Validação |
| --- | --- | --- | --- | --- | --- | --- | --- |
| **FP-01** | Pré-chamada | **A** (Empregador) | Comportamental / Normativa | Atraso/omissão no preenchimento do evento de desligamento (S-2299) no eSocial. | Ouve da URA a sentença de "Benefício não localizado", gerando pânico financeiro. | Desvia demanda ilegítima de suporte para a Caixa, acionando a rede física SINE (R) indevidamente. | `[HIPÓTESE — VALIDAR cruzando *timestamps* de transmissão S-2299 e consultas no log de navegação da URA]`. |
| **FP-02** | Autoatend. | **D** (Dataprev) e **C** (MTE) | Processos e Dados | Instabilidade/Lentidão no processamento do lote noturno de atualização das parcelas. | Ouve informação telefônica defasada em relação ao status atual da CTPS Digital. | Quebra severa de confiança no canal 0800, impulsionando a reentrada crônica no IVR. | `[HIPÓTESE — VALIDAR volumetria via chamados de Ouvidoria categorizados por "Divergência de Saldo"]`. |
| **FP-03** | Autenticação | **G** (Segurança) e **O** (URA) | Técnica / Regra de Negócio | Motor KBA hiper-rígido requerendo dados mnemônicos obsoletos de vínculos rescisórios muito antigos. | Cidadão plenamente autêntico sofre *lockout* defensivo da URA e tem a conta imobilizada. | Migração forçada da triagem telefônica digital de baixo custo para as agências físicas (transbordo de camada). | `[HIPÓTESE — VALIDAR estatisticamente via percentual absoluto de abandono na sub-etapa de KBA]`. |
| **FP-04** | Navegação | **O** (URA Caixa) | Técnica / Design | Arquitetura de informação (menus) com profundidade excessiva, formando "becos sem saída" falados. | Usuário fica isolado em loops cognitivos até desistir e desligar o aparelho. | Inflação nas métricas da central gerada puramente por tráfego falso de rediscagem. | `[HIPÓTESE — VALIDAR via extração primária de logs de desligamento confinados em submenus sem intenção final]`. |
| **FP-05** | Navegação | **P** (Motor NLP / ASR) | Técnica / IA | Incapacidade aguda de processamento linguístico diante de sotaques locais fechados ou ruído de rua (obras/trânsito). | O motor conversacional retrocede incessantemente com "Desculpe, não entendi". | Esgotamento emocional do cidadão, que desliga a chamada antes da fase resolutiva. | `[HIPÓTESE — VALIDAR via amostragem de auditoria sobre transcrições classificadas com fallback repetitivo]`. |
| **FP-06** | Atendimento | **J** (ACD/CTI) | Técnica / Telecom | Subita interrupção do tráfego SIP (queda real) da ligação no milissegundo de comutação URA → Atendente. | Perda instantânea de toda a *timeline* de espera; raiva e necessidade de reiniciar todo o ciclo. | Falso positivo na disponibilidade do canal, elevando o Tempo Médio de Espera (TME) no *pool* geral da fila de atendimento. | `[HIPÓTESE — VALIDAR isoladamente mapeando flags de desconexão classificadas como "drop de fila/comutação" pelo *vendor* do CTI]`. |
| **FP-07** | Desfecho | **Q** (Atendente Terceirizado) | Comportamental / Meta | Desligamento deliberado e precoce da chamada por pressão gerencial para reprimir o indicador TMA. | Sensação de repulsa/abandono pelo Estado; permanência em status de pendência não orientada. | Risco latente de autuação/multa por violação flagrante do Decreto 11.034/2022 e judicialização secundária. | `[HIPÓTESE — VALIDAR isolando chamadas com duração <10s após a comutação e cruzando obrigatoriamente com logs de detecção de voz (VAD) confirmando áudio originado no PA]`. |
| **FP-08** | Pré-chamada | **H** (Gov.br) | Técnica / Multicanal | Quebra sistêmica no motor de validação de reconhecimento facial impede o uso de canal web. | O cidadão recorre ao 0800 em pânico, mas a URA não tem prerrogativa sistêmica para intervir em senhas Gov.br. | Arquitetura de "beco sem saída" institucional: canal digital ejeta o cidadão para o canal analógico que não tem alçada de solução. | `[HIPÓTESE — VALIDAR dimensionando a tabulação de chamadas ativas encerradas sob o rótulo "Erro/Dúvida Gov.br"]`. |
| **FP-09** | Recepção | **L** (TI Caixa) e **K** (Fornec.) | Técnica / Infraestrutura Legada | Apagão ou exaustão do *throughput* de comunicação dos bancos de dados internos (Mainframe) em dias de pico de depósito. | A URA processa o CPF e emite instantaneamente a barreira: "Sistema indisponível", ejetando a chamada. | Geração sucessiva de "ondas de choque" de congestionamento telefônico na janela de operação do dia seguinte. | `[HIPÓTESE — VALIDAR via triangulação retroativa de tickets de incidente crítico/indisponibilidade abertos pelo monitoramento NOC]`. |
| **FP-10** | Autenticação | **N** (Cidadão - Pescador) | Técnica / Calendário | O trabalhador liga buscando a parcela Defeso em datas marginalmente fora do calendário do decreto normativo local. | O sistema devolve negativa ("Não localizado") como se o cidadão não existisse, mascarando o erro temporal. | O cidadão interpreta equivocadamente a negativa temporal como sumiço de dados cadastrais vitais. | `[HIPÓTESE — VALIDAR realizando o cruzamento de séries temporais de rejeição versus o calendário das portarias do IBAMA]`. |
| **FP-11** | Navegação | **B** (CODEFAT) e **F** (Caixa) | Normativa / Governança | *Lag* ou latência desregulada de governança: regra de negócio é oficializada em Resolução, mas a URA demora meses para traduzir o script de áudio. | Cidadão é orientado legalmente na URA com base em regra jurídica e carências já mortas/revogadas. | Multiplicação exponencial de litígios fundamentados em desinformação material oficialmente patrocinada pelo Estado. | `[HIPÓTESE — VALIDAR aferindo em histórico o *lead time* exato de publicação no DOU até o *deploy* em produção da respectiva URA]`. |
| **FP-12** | Autenticação | **G** (Segurança) e **O** (URA) | Técnica / Antifraude | Suspensão e bloqueio preventivo global do CPF por sucessivas tentativas de acesso pirata/esgotamento KBA por fraudadores. | O trabalhador titular, no primeiro contato genuíno, descobre a imobilização irrevogável de seu canal. | Inibe o autoatendimento legítimo e superlota a intervenção de alto custo das agências físicas de contingência. | `[HIPÓTESE — VALIDAR via mineração dos logs de tentativas KBA bloqueadas versus ocorrências posteriores nas catracas físicas do banco]`. |
| **FP-13** | Autoatend. | **C** (MTE) e **D** (Dataprev) | Dados / Processo | Cidadão obteve o benefício, mas os dados bancários resgatados de vínculo passado estão fechados ou divergentes (TED fail). | O URA narra a liberação, mas ocorre falha no roteamento financeiro da parcela depositada, atrasando o sustento. | Exige intervenção manual dispendiosa da retaguarda de pagamentos (reprocessamento de lote). | `[HIPÓTESE — VALIDAR isolando no *pipeline* contábil o índice de retornos de DOC/TED rejeitados do respectivo fundo]`. |
| **FP-14** | Desfecho | **Q** (Atendente) e **O** (URA) | Normativa / Comportamental | A comunicação da negativa/indeferimento omite deliberadamente qualquer script legal informando o cidadão sobre o direito a recurso administrativo, JEF ou DPU. | O desempregado desprovido de letramento jurídico acata a rescisão injusta sem contestação e perde a assistência financeira. | Induz a uma sub-representação judicial severa, suprimindo o amplo acesso à defesa no contexto da lei social. | `[HIPÓTESE — VALIDAR executando inspeção integral e decodificação analítica da base de conhecimento e scripts mandatórios aplicados na tela do PA]`. |

---

## Síntese de Interdependências Críticas

O Blueprint evidencia um ecossistema estressado onde os atritos frontstage são predominantemente sintomas de desajustes em três arranjos interinstitucionais e de base técnica de bastidor:

1. **A Cadeia Cega de Formação do Dado (Atores A → D → C → O):** A interface telefônica da URA (**Ator O**) suporta uma dependência upstream incontornável dos dados iniciados pelo empregador na base eSocial e processados lentamente via Dataprev. Na linha de frente, a URA absorve mecanicamente todo o impacto emocional de erros e atrasos de cadastro (FP-01 e FP-02) sem dispor de alçada ou ferramentas para promover edições saneadoras em tempo real, gerando imobilismo sistêmico.
2. **O Aprisionamento / Transbordo Cego Multicanal (Atores H → O):** Como a URA 0800 atua informalmente como dreno contingencial de problemas sistêmicos do Gov.br (**Ator H**), os travamentos severos em biometria facial empurram as vítimas digitais para a telefonia. Entretanto, o motor da URA e a baia do Atendente Humano (**Ator Q**) na Caixa não possuem pontes lógicas ou autorizações de segurança integradas ao Ministério da Gestão, materializando um "beco sem saída" onde o Governo federal repele formalmente sua própria demanda de suporte (FP-08).
3. **A Ruptura Técnica e Contratual no Transbordo (Atores J → Q → M):** A passagem do funil robótico para o suporte humano encerra o segmento mais tenso da jornada de prestação. O descompasso entre a saúde operacional da infraestrutura comutadora CTI (**Ator J**, gerando FP-06) e o foco estrito em metas redutoras de Tempo Médio de Atendimento estipuladas ao terceiro e ao supervisor (**Atores Q e M**, induzindo FP-07) convergem para precipitar o *drop* voluntário ou tecnológico da chamada no exato ápice de exaustão e fragilidade psicológica do trabalhador assistido.

---

## SEÇÃO 6 — Resposta à Auditoria v2

O presente relatório evoluiu processando as falhas da auditoria anterior, consolidando a matriz de resolução analítica de rigor abaixo:

| ID | Ação Adotada | Como foi fechado o risco no presente documento |
| --- | --- | --- |
| **NO-5** | Resolvido | O risco apontado deixa de existir porque a generalização indevida (usada como confirmação) foi removida e o item reclassificado honestamente de forma estrita como `[PENDENTE — identificar número/ano/artigo específico]`, neutralizando a âncora incorreta e blindando a aplicação do protocolo rigoroso. |
| **NF-1** | Resolvido | O risco apontado deixa de existir porque o termo vago "X meses" foi completamente substituído pela exigência verificável de retenção de 90 dias com base e âncora material legal citada diretamente (Art. 16, Decreto 11.034/2022). |
| **NF-2** | Resolvido | O risco apontado deixa de existir porque a evidência inventada sem base ou fonte documental explícita (SMS via sistema) foi removida, sendo retificada em definitivo para "instrução verbal e auditiva do atendente" com total coerência à realidade de bastidor de *call centers*. |
| **NF-3** | Resolvido | O risco apontado deixa de existir porque a atribuição falha de coemissão da evidência foi corrigida estritamente para os Atores C (MTE) e D (Dataprev), saneando a confusão entre o portal front-end (Gov.br) e o real órgão custodiante gerador do dado. |
| **NF-4** | Resolvido | O risco apontado deixa de existir porque a Resolução 605/2012 (direcionada a provedores SCM/SMP) foi inteiramente erradicada do documento e substituída pela normativa materialmente correta, Resolução ANATEL nº 632/2014, cujo Art. 1º impõe aplicabilidade taxativa à rede STFC, base do 0800. |
| **NF-5** | Resolvido | O risco apontado deixa de existir porque a estrutura integral requerida para a Seção 5 foi reconstituída e respeitada por completo. As colunas estruturais vitais "Natureza da Falha" e "Efeito Sistêmico" foram efetivamente preenchidas e restituídas em todos os registros tabulares, sem evasão sistêmica. |
| **NF-6** | Resolvido | O risco apontado deixa de existir porque o teste lógico sobre o FP-07 foi aperfeiçoado de modo irrefutável e isolado: a métrica exige, agora, atrelar as quedas curtas em TMA ao cruzamento condicionado dos logs com motores detentores de captação acústica/VAD (*Voice Activity Detection*), separando de maneira estanque as sabotagens comportamentais do *drop* de comutação técnica (FP-06). |
| **PR-1** | Resolvido | O risco apontado deixa de existir porque o acompanhamento intertemporal do normativo-âncora foi plenamente atualizado; as seções normativas consignam menção formal incontornável à Resolução CODEFAT nº 1027/2025 revogando o inciso V, art. 8º da norma pretérita (Res. 957/2022). |
| **PR-2** | Resolvido | O risco apontado deixa de existir porque a jornada frontstage preambular foi submetida a uma decomposição lógica obrigatória, convertendo-se de forma explícita nas sub-etapas segmentadas e não-lineares "1.1 Pré-chamada/Rescisão" e "1.2 Busca de Canal e Discagem". |
| **PR-3** | Resolvido | O risco apontado deixa de existir porque a inferência desautorizada e infundada sobre a integração sistêmica (o trânsito do *Screen Pop*) foi permanentemente neutralizada da cadeia de bastidor, declarando formalmente, em texto puro, sua ausência. A jornada determina que não há passagem em rampa suave de contexto e o trabalhador repete do zero a sua argumentação narrativa de necessidade. |
