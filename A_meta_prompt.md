# C_metaprompt_blueprint_ASIS
## Meta-Prompt: Pesquisa Estruturada para Service Blueprint AS-IS
### Serviço: Atendimento ao Seguro-Desemprego via URA — Caixa Econômica Federal

---

> **INSTRUÇÕES DE USO**
> Este documento é um meta-prompt autossuficiente. Cole-o integralmente como primeira mensagem em uma nova sessão de IA. Não reformule as perguntas em avulso: o modelo deve entregar as cinco seções do Blueprint completas e na sequência especificada. O ecossistema de atores já foi mapeado em fase anterior (Bloco 2); a pesquisa solicitada deve partir desse mapa para produzir as camadas faltantes do Blueprint — não para redescobrir o que já está aqui.

---

## BLOCO 1 — DESCRIÇÃO DO SERVIÇO

Você é um pesquisador especialista em design de serviços públicos brasileiros. Sua tarefa é produzir uma pesquisa estruturada que sustente a construção do **Service Blueprint AS-IS** do seguinte serviço:

**Serviço:** Atendimento ao Programa Seguro-Desemprego operado pela **Caixa Econômica Federal** por meio de sua **Unidade de Resposta Audível (URA)**, acessada pelo número **0800 726 0207**.

**Natureza:** Serviço público federal de atendimento telefônico automatizado, com transbordo para atendimento humano terceirizado. Opera como canal primário de consulta e orientação para trabalhadores que tiveram o contrato de trabalho rescindido sem justa causa e buscam informações sobre o status de parcelas, habilitação ao benefício e encaminhamentos.

**Características críticas do serviço:**
- O benefício tem caráter de **verba alimentar** (direito constitucional, Art. 7º, II, CF/88), o que impõe alto nível de criticidade emocional e jurídica à jornada de atendimento.
- A cadeia de dados que alimenta a URA **não se origina na Caixa**: ela parte do registro de rescisão feito pelo empregador no **eSocial**, processado pela **Dataprev**, consolidado pelo **MTE** e só então disponibilizado para consulta pela URA.
- O serviço é regulado por normativos de múltiplas esferas (legislação federal, resoluções do CODEFAT, padrões de TI governamentais), criando uma governança fragmentada sem titular único de ponta-a-ponta.
- Existe um **ecossistema multicanal paralelo**: o portal **Gov.br** e a **CTPS Digital** absorvem parte dos requerimentos digitalmente. A URA atua muitas vezes como canal de contingência para quem falha na validação biométrica ou não possui acesso digital.

**Arcabouço teórico deste Blueprint:**
A análise parte da união de duas disciplinas:
- **Sociologia dramatúrgica** de Erving Goffman (1959, *The Presentation of Self in Everyday Life*): divisão analítica entre o que o cidadão vê (*frontstage*) e o que ocorre fora de cena (*backstage*).
- **Service Blueprinting** de G. Lynn Shostack (1984, "Designing Services That Deliver", *Harvard Business Review*): mapeamento sistemático de processos, evidências e pontos de falha ao longo da jornada.

**Objetivo da pesquisa (deep research da operação real):**
Esta tarefa exige uma **pesquisa aprofundada (deep research) de como o serviço opera hoje (AS-IS)** — não uma descrição idealizada. A pesquisa deve sustentar o Service Blueprint AS-IS cobrindo, de forma investigativa e rastreável, as cinco camadas da metodologia:
1. a **jornada real do cidadão** (frontstage) etapa a etapa;
2. os **processos de bastidor (backstage)** — o que sistemas e atores executam fora da vista do cidadão em resposta a cada interação;
3. os **processos de suporte** estruturais que sustentam o serviço de forma permanente (governança normativa, sustentação de infraestrutura, controle/auditoria, gravação/compliance);
4. as **evidências físicas/sensoriais** percebidas em cada etapa;
5. os **fail points** — pontos de falha confirmados ou hipotéticos, com ator causador, natureza, impacto no cidadão e efeito sistêmico.
A pesquisa deve distinguir explicitamente **fato confirmado** de **hipótese a validar**, indicando o método de verificação de cada lacuna, de modo que o Blueprint AS-IS resultante seja auditável.

---

## BLOCO 2 — ECOSSISTEMA DE ATORES (Pré-mapeado — não redescobrir)

O mapeamento de atores já foi concluído em fase anterior de pesquisa. São **17 atores** organizados em cinco camadas. A pesquisa solicitada no Bloco 3 deve usar este mapa como base, não reescrevê-lo.

### Camada 1 — Macroambiente (Governança e Geração de Dados)
| ID | Ator | Papel-chave |
|----|------|-------------|
| A | Empregadores | Iniciadores formais: comunicam rescisão via eSocial |
| B | CODEFAT | Autoridade normativa tripartite; edita as regras do benefício |
| C | MTE | Secretaria executiva do CODEFAT; aplica elegibilidade e autoriza pagamentos |
| D | Dataprev | Processa os lotes do eSocial que alimentam o MTE e a URA |
| E | FAT | Custódia financeira constitucional (Art. 239 CF) |

### Camada 2 — Instância Operacional Estratégica (Backstage)
| ID | Ator | Papel-chave |
|----|------|-------------|
| F | Caixa Econômica Federal | Agente pagador; opera a URA e contrata terceirizadas |
| G | Segurança da Informação / LGPD | Configura os protocolos KBA (Knowledge-Based Authentication) |
| H | Gov.br / CTPS Digital | Ecossistema digital paralelo; canal primário de autoatendimento |
| I | TCU / CGU | Auditores da aplicação orçamentária e dos contratos de terceirização |

### Camada 3 — Infraestrutura Tecnológica (Backstage)
| ID | Ator | Papel-chave |
|----|------|-------------|
| J | ACD/CTI | Distribui chamadas da URA ao atendente humano (skill-based routing) |
| K | Fornecedores de Infraestrutura | Telecomunicações, nuvem, licenças de URA |
| L | Equipes de TI | Sustentação dos bancos de dados da Caixa |
| M | Supervisores e Gestores da Central | Qualidade, escala e métricas operacionais |

### Camada 4 — Frontstage (Linha de Frente)
| ID | Ator | Papel-chave |
|----|------|-------------|
| N | Cidadão Requerente (multimodalidade) | Usuário final — não monolítico: CLT, doméstico, pescador (Seguro Defeso - Lei 10.779/2003), resgatado |
| O | URA | Triagem, contenção, consulta via API; saída em áudio TTS (Text-to-Speech) |
| P | ASR / NLP | Reconhecimento de voz e mapeamento de intenção (entrada de áudio) |
| Q | Atendente Humano (terceirizado) | Agente de resolução final das demandas não resolvidas pela URA |

### Camada 5 — Transbordo Físico e Judicial (Overflow)
| ID | Ator | Papel-chave |
|----|------|-------------|
| R | SRTEs e SINE | Absorção presencial de impasses documentais não resolvíveis por telefone |
| S | DPU e JEF | Via judicial de último recurso em casos de negativa indevida crônica |

---

## BLOCO 3 — TAREFA DE PESQUISA: AS CINCO SEÇÕES DO BLUEPRINT

Produza as cinco seções a seguir **na ordem apresentada**, com o nível de detalhamento especificado em cada uma. Cada seção deve ser entregue completa antes de passar para a próxima. **Não misture seções.**

---

### SEÇÃO 1 — Jornada do Cidadão (Frontstage)

**Objetivo:** Mapear as etapas nomeadas da jornada na perspectiva exclusiva do cidadão requerente, do momento pré-chamada até o desfecho.

Para cada etapa, entregue:

| Campo | Descrição exigida |
|-------|-------------------|
| **Nome da Etapa** | Rótulo curto e orientado à ação do cidadão (ex: "Disca e aguarda") |
| **Gatilho de Entrada** | O que faz o cidadão iniciar esta etapa |
| **Ação do Cidadão** | O que ele efetivamente faz (não o que o sistema faz) |
| **Canal / Ponto de Contato** | Onde ocorre (telefone, Gov.br, SINE físico, etc.) |
| **Estado Emocional Provável** | Baseado em premissa socioeconômica do benefício ou fonte indicada |
| **Condição de Saída** | O que encerra a etapa e leva à próxima |
| **Desfechos Alternativos** | Caminhos de abandono ou desvio presentes nesta etapa |

Cubra obrigatoriamente as seguintes etapas macro (desdobrando em sub-etapas quando necessário):
1. Pré-chamada (rescisão → busca de canal → discagem)
2. Recepção e autenticação na URA
3. Navegação na árvore de opções
4. Autoatendimento (resposta da URA) ou transbordo para atendente
5. Atendimento humano (quando ocorre)
6. Desfecho: resolução, encaminhamento ou abandono

---

### SEÇÃO 2 — Processos de Bastidor (Backstage)

**Objetivo:** Para cada etapa da Seção 1, mapear os processos executados fora da vista do cidadão, identificando o ator responsável (usar IDs A–S do Bloco 2), o sistema envolvido e a janela temporal quando conhecida.

A pesquisa deve distinguir e detalhar **dois níveis** de bastidor, separados pela linha de interação interna de Shostack:
- **(i) Backstage propriamente dito** — processos acionados *em resposta à interação* (tempo real): captura e autenticação na URA, consulta de APIs, ASR/NLP, roteamento ACD/CTI, geração de TTS.
- **(ii) Processos de suporte estruturais** — processos permanentes que sustentam o serviço independentemente de uma chamada específica. É **obrigatório** detalhar, no mínimo: **governança normativa** (tradução de Resoluções CODEFAT em regras e scripts de URA), **sustentação de infraestrutura** (enlaces de telecom, licenças e disponibilidade de banco de dados), **controle/auditoria** (monitoramento contínuo de TCU/CGU sobre o FAT e os contratos) e **gravação/compliance** (registro e retenção das chamadas, com implicações de LGPD).

Para cada processo de bastidor, entregue:

| Campo | Descrição exigida |
|-------|-------------------|
| **Etapa da Jornada Correspondente** | Vincular à etapa nomeada na Seção 1 |
| **Nível de Bastidor** | Classificar **obrigatoriamente** como `Backstage` (processo acionado em resposta à interação) ou `Processo de Suporte` (processo estrutural/permanente), conforme a linha de interação interna de Shostack |
| **Ator Responsável** | ID e nome do ator (Bloco 2) |
| **Processo / Ação** | O que ocorre operacionalmente |
| **Sistema Envolvido** | Nome da plataforma ou sistema (eSocial, Dataprev, ACD, etc.) |
| **Janela Temporal** | Duração estimada ou frequência (ex: lote noturno, tempo real, semanal) |
| **Dependência Crítica** | De qual dado ou ação anterior este processo depende |

**Atenção especial obrigatória (Backstage — resposta à interação):**
- O fluxo de dados eSocial → Dataprev → MTE → URA Caixa (cadeia de geração do dado consultado)
- O processo de autenticação KBA configurado pela área de Segurança da Informação (Ator G)
- O algoritmo de roteamento do ACD/CTI (Ator J) no momento do transbordo
- O processo de tabulação e encerramento de chamada pelo atendente terceirizado

**Atenção especial obrigatória (Processos de Suporte — estruturais):** é obrigatório pesquisar e detalhar, com ator, sistema e janela temporal, cada um dos quatro processos de suporte abaixo (não tratá-los apenas como contexto):
- **Governança normativa:** o processo pelo qual novas Resoluções do CODEFAT (Ator B) são traduzidas em regras de elegibilidade e scripts da URA pelo MTE/Caixa, incluindo a janela de descompasso entre publicação no DOU e atualização dos sistemas.
- **Sustentação de infraestrutura:** manutenção dos enlaces de telecom, links SIP, licenças de URA (Ator K) e disponibilidade dos bancos de dados legados da Caixa (Ator L), com seus SLAs e janelas de manutenção.
- **Controle e auditoria:** o monitoramento contínuo e reativo de TCU/CGU (Ator I) sobre a aplicação do FAT e os contratos de terceirização, e como ele realimenta as regras de design do serviço.
- **Gravação e compliance:** o processo permanente de gravação das chamadas em tempo real, armazenamento e período de retenção (Ator L), com as implicações de LGPD.

---

### SEÇÃO 3 — Evidências Físicas por Etapa

**Objetivo:** Identificar todos os artefatos tangíveis (físicos, digitais ou auditivos) que o cidadão encontra em cada etapa da jornada. Em serviços de atendimento telefônico, "evidência física" inclui elementos auditivos, digitais e documentais.

Para cada evidência, entregue:

| Campo | Descrição exigida |
|-------|-------------------|
| **Etapa da Jornada** | Vincular à etapa da Seção 1 |
| **Tipo de Evidência** | Auditiva / Digital / Documento impresso / Notificação |
| **Descrição do Artefato** | O que o cidadão ouve, vê ou recebe concretamente |
| **Emissor** | Qual ator do sistema produz esta evidência |
| **Implicação de Qualidade** | O que a ausência ou degradação desta evidência causa na experiência |

Exemplos obrigatórios a cobrir (não limitar a estes):
- Locução da URA (qualidade do TTS, clareza da linguagem)
- Música de espera e mensagens de fila
- Mensagens de erro ("benefício não localizado", "tente mais tarde")
- Confirmações verbais de agendamento ou status
- SMS / push do aplicativo Caixa Tem após resolução
- Notificações no Gov.br / CTPS Digital
- Carta ou comunicação escrita de concessão ou negativa do benefício

---

### SEÇÃO 4 — Normativos Aplicáveis

**Objetivo:** Produzir o mapeamento regulatório completo e ordenado que governa cada dimensão do serviço, citando obrigatoriamente número, ano e dispositivo específico relevante.

Organize a entrega em quatro sub-blocos:

#### 4A — Normativos do Benefício (o que a URA consulta e informa)
Legislação que rege a concessão, elegibilidade, prazos e modalidades do Seguro-Desemprego. Incluir obrigatoriamente:
- Lei 7.998/1990 e suas alterações relevantes
- Lei 13.134/2015 (modalidades ampliadas)
- Lei 10.779/2003 (Seguro Defeso)
- Decreto 7.721/2012
- Resoluções do CODEFAT relevantes à operação

#### 4B — Normativos do Canal de Atendimento (como a URA deve operar)
Regras que disciplinam o atendimento telefônico e o serviço 0800. Incluir:
- Decreto 6.523/2008 (Lei do SAC) e sua aplicabilidade ao serviço público
- Portarias e regulamentos ANATEL sobre serviços 0800
- Resoluções aplicáveis ao tempo máximo de espera e transbordo obrigatório

#### 4C — Normativos de Tecnologia e Dados (como os sistemas devem ser construídos)
Padrões que regem a arquitetura tecnológica e proteção de dados. Incluir:
- e-PING (Padrões de Interoperabilidade de Governo Eletrônico) — versão vigente
- e-MAG (Modelo de Acessibilidade em Governo Eletrônico)
- LGPD — Lei 13.709/2018 — dispositivos aplicáveis à autenticação e ao armazenamento de dados da jornada
- Decreto 10.046/2019 (compartilhamento de dados no governo federal)

#### 4D — Normativos de Controle e Governança
Instrumentos que regem a fiscalização e as contratações. Incluir:
- Lei 8.666/1993 / Lei 14.133/2021 (licitações aplicáveis aos contratos de call center)
- Instruções Normativas relevantes do TCU sobre prestação de contas do FAT

Para cada normativo, entregue:

| Campo | Descrição exigida |
|-------|-------------------|
| **Instrumento** | Tipo, número e ano |
| **Dispositivo Específico** | Artigo(s) ou inciso(s) relevantes |
| **O que regula no serviço** | A qual aspecto do Blueprint se aplica |
| **Processo vinculado** | **Obrigatório:** vincular o normativo ao processo de **Backstage** ou de **Suporte** (Seção 2) ou à etapa da jornada (Seção 1) que ele governa — ex.: LGPD → processo de gravação/compliance; Lei 14.133/2021 → sustentação contratada; Resolução CODEFAT → governança normativa/scripts da URA |
| **Status de Cumprimento Verificável** | Indicar se há mecanismo de aferição pública do cumprimento |

---

### SEÇÃO 5 — Fail Points Conhecidos

**Objetivo:** Mapear os pontos de falha confirmados ou hipotéticos, vinculando cada um à etapa da jornada, ao ator causador, ao impacto no cidadão e ao status de evidência.

Para cada fail point, entregue:

| Campo | Descrição exigida |
|-------|-------------------|
| **ID do Fail Point** | FP-01, FP-02... |
| **Etapa da Jornada** | Onde na jornada (Seção 1) a falha se manifesta |
| **Ator / Sistema Causador** | Quem ou o quê origina a falha (usar IDs A–S) |
| **Natureza da Falha** | Técnica / Normativa / Comportamental / Dados |
| **Descrição** | O que ocorre concretamente |
| **Impacto no Cidadão** | Consequência direta na jornada |
| **Efeito Sistêmico** | Onde a falha se propaga no ecossistema |
| **Status de Evidência** | `CONFIRMADO` (fonte citada) ou `[HIPÓTESE — VALIDAR]` (método de validação sugerido) |

Cubra obrigatoriamente os seguintes fail points já sinalizados no mapeamento anterior (adicionar outros identificados na pesquisa):

| ID | Origem | Descrição resumida |
|----|--------|-------------------|
| FP-01 | Ator A (Empregador) | Erro ou atraso no registro de rescisão no eSocial → "benefício não localizado" |
| FP-02 | Ator D (Dataprev) | Atraso no processamento de lote → URA consulta base desatualizada |
| FP-03 | Ator G (Segurança da Informação) | KBA excessivamente restritivo → cidadão legítimo bloqueado na autenticação |
| FP-04 | Ator O (URA) | Árvore de navegação com profundidade excessiva ou becos sem saída → abandono |
| FP-05 | Ator P (ASR/NLP) | Falha de reconhecimento de sotaque → ciclos de repetição até exaustão |
| FP-06 | Ator J (ACD/CTI) | Queda de ligação no transbordo URA → atendente humano |
| FP-07 | Ator Q (Atendente) | Encerramento prematuro de chamada por pressão de TMA |
| FP-08 | Ator H (Gov.br) | Falha biométrica no canal digital → migração forçada para URA ou rede física |

---

## BLOCO 4 — PROTOCOLO DE RIGOR ANALÍTICO

Estas regras são obrigatórias e se sobrepõem a qualquer outra instrução:

**Regra 1 — Separação de fato e hipótese:**
Toda afirmação operacional, comportamental ou arquitetural deve ser classificada como:
- `[CONFIRMADO]` — quando amparada por fonte citada (lei, decreto, auditoria pública, pesquisa publicada)
- `[HIPÓTESE — VALIDAR]` — quando baseada em raciocínio inferencial ou conhecimento de domínio geral, acompanhada de método de validação sugerido

**Regra 2 — Citação de normativos:**
Todo normativo deve ser citado com tipo, número, ano e artigo específico. Citações genéricas do tipo "a legislação prevê" são inaceitáveis.

**Regra 3 — Proibição de dados inventados:**
Nenhum dado quantitativo (volume de chamadas, taxa de abandono, TMA, FCR) deve ser apresentado sem fonte verificável. Na ausência de dado público, registrar como `[MÉTRICA AUSENTE — fonte sugerida: relatórios TCU / DIEESE / Ouvidor Caixa]`.

**Regra 4 — Escopo dos atores:**
Não reescrever nem renomear os atores do Bloco 2. Se a pesquisa identificar um ator não presente no mapa, incluí-lo com a marcação `[ATOR NOVO — não constava no mapeamento anterior]` e justificar a inclusão.

**Regra 5 — Integralidade das seções:**
Entregar todas as cinco seções. Não suprimir sub-itens por falta de informação: registrar a lacuna explicitamente com a marcação adequada.

---

## BLOCO 5 — FORMATO DE SAÍDA REQUERIDO

- Cada seção deve ser iniciada com cabeçalho de nível 2 (`##`) e seu número e título exatos.
- Usar tabelas para todos os campos estruturados especificados nas seções.
- Fail points devem ser numerados sequencialmente (FP-01, FP-02...).
- Normativos devem ser listados em ordem de hierarquia: Constituição → Lei → Decreto → Portaria → Resolução → Instrução Normativa.
- Ao final de cada seção, incluir um parágrafo sintético intitulado **"Lacunas desta seção"** listando o que não foi possível confirmar e por quê.
- Ao final de todas as cinco seções, incluir uma seção **"Síntese de Interdependências Críticas"** apontando as três conexões entre atores que concentram maior risco sistêmico para o cidadão, com base no Blueprint AS-IS mapeado.

---

*Meta-prompt produzido com base no mapeamento analítico de atores v3 (Ecossistema URA Caixa Seguro-Desemprego) e nas auditorias de rigor v1 e v2 conduzidas sobre o dossiê de pesquisa.*
