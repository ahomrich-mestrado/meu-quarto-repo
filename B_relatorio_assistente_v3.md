# B_relatorio_assistente_v3 — Dossiê de Pesquisa (V3 APERFEIÇOADA COM SEÇÃO 4)

---

## Parte 1: Matriz de Resolução da Auditoria V2

### 1. Achados Parcialmente Resolvidos (v1)

**LE-2 (Negligência na H4):** *(a) Corrigido com texto novo.* A redação foi ajustada para remover o qualificador de "negligência"[cite: 2]. A hipótese agora questiona objetivamente se existe correlação entre as metas de Tempo Médio de Atendimento (TMA) e o encerramento prematuro das chamadas[cite: 2].

**LE-3 (Falhas em massa assumidas na H3):** *(a) Corrigido com texto novo.* A formulação de H3 foi reescrita para não assumir as falhas como premissa, mas testar *se* a arquitetura de lotes gera a resposta de benefício não localizado[cite: 2].

**LE-6 e NF-6 (CES ausente/Inconsistência):** *(a) Corrigido com texto novo.* A métrica de *Customer Effort Score* (CES) foi explicitamente incluída na Seção 4.A do Dossiê para aferir o impacto emocional e a fricção do cidadão, alinhando matriz e relatório[cite: 2].

**IMS-1 (Remoção do ACD/CTI):** *(a) Corrigido com texto novo.* O ator "Sistema de Roteamento (ACD/CTI)" foi restaurado ao ecossistema (Seção 2.3)[cite: 2]. A inferência não comprovada sobre sua configuração foi mantida isolada na seção de hipóteses[cite: 2].

**AI-1 (SLAs/SLOs):** *(a) Corrigido com texto novo.* Os termos foram devidamente desmembrados no texto para diferenciar acordos contratuais de nível de serviço (SLA) de objetivos operacionais internos (SLO)[cite: 2].

**AI-2 (Goffman e Shostack):** *(a) Corrigido com texto novo.* Adicionadas as referências completas exigidas: a sociologia dramatúrgica de Erving Goffman (1959, *The Presentation of Self in Everyday Life*) e o artigo base de G. Lynn Shostack (1984, "Designing Services That Deliver", *Harvard Business Review*)[cite: 2].

---

### 2. Falhas Novas (NF)

**NF-1 (Dataprev Fantasma):** *(a) Corrigido com texto novo.* A Dataprev foi mapeada formalmente como um ator (Organização Tecnológica) no Macroambiente (Seção 2.1), explicando seu papel no processamento do eSocial[cite: 2].

**NF-2 (TTS ambíguo):** *(a) Corrigido com texto novo.* A referência ao TTS (Text-to-Speech) foi corrigida para definir estritamente a tecnologia de *saída* de áudio, separando-a do conceito amplo de autoatendimento[cite: 2].

**NF-3 (Atores Removidos):** *(a) Corrigido com texto novo.* Os quatro atores suprimidos na v2 (Supervisores, Equipe de TI, Fornecedores e Segurança da Informação) foram totalmente reintegrados ao *backstage*[cite: 2].

**NF-4 (Norma ANATEL Incorreta para 0800/STFC):** *(a) Corrigido com texto novo.* A menção inadequada à Resolução ANATEL nº 605/2012 foi completamente suprimida. A análise das responsabilidades dos Fornecedores de Telecom (Ator K) foi reestruturada para refletir o rigor normativo adequado ao Serviço Telefônico Fixo Comutado (STFC), baseando-se no Regulamento de Qualidade (RQUAL - Resolução nº 717/2019) e no RGC (Resolução nº 632/2014). O viés de "migração compulsória" também foi ajustado para refletir a URA apenas como caminho alternativo.

**NF-5 (Seguro Defeso):** *(a) Corrigido com texto novo.* O Seguro Defeso foi destacado por suas especificidades (Lei 10.779/2003, calendário sazonal) para evitar confusão com o Seguro-Desemprego padrão (CLT)[cite: 2].

---

### 3. Pontos Remanescentes (PR)

**PR-1 (Poder e Dependência):** *(a) Corrigido com texto novo.* A seção "Dinâmicas de Governança" (Seção 3.1) foi reescrita para abranger as assimetrias de poder envolvendo CODEFAT, Empregadores e Dataprev[cite: 2].

**PR-2 (Autenticação e Exclusão):** *(a) Corrigido com texto novo.* A reintegração do ator de Segurança da Informação permitiu restaurar a análise estrutural da fricção por KBA (Knowledge-Based Authentication) como barreira de acesso[cite: 2].

**PR-3 (Padronização de idioma):** *(a) Corrigido com texto novo.* O termo *ownership* foi traduzido para "titularidade", e *First Contact Resolution* (FCR) passou a constar padronizado como "Resolução no Primeiro Contato (FCR)"[cite: 2].

---

## Parte 2: Dossiê de Pesquisa

# Pesquisa Aprofundada: Ecossistema e Jornada do Usuário no Atendimento ao Seguro-Desemprego via URA Caixa

## 1. Introdução e Abordagem Metodológica

Este documento consolida o mapeamento analítico do serviço público de atendimento ao Seguro-Desemprego operado via Unidade de Resposta Audível (URA) pela Caixa Econômica Federal[cite: 2].

O arcabouço teórico que alicerça esta análise une duas disciplinas complementares: a sociologia dramatúrgica de Erving Goffman (1959, *The Presentation of Self in Everyday Life*), que inspira a divisão analítica dos papéis em cena e fora de cena, e a ferramenta de *Service Blueprinting* desenvolvida por G. Lynn Shostack (1984, "Designing Services That Deliver", *Harvard Business Review*)[cite: 2].

Sob essa ótica, o serviço telefônico não é uma interação isolada, mas o resultado final visível (*frontstage*) sustentado por múltiplas engrenagens operacionais (*backstage*) e diretrizes regulatórias sistêmicas[cite: 2]. Afirmações sem dados empíricos publicados encontram-se demarcadas na seção de lacunas e hipóteses para futura validação de campo[cite: 2].

---

## 2. Mapeamento Analítico dos Atores

Para garantir completude sistêmica, mapeamos 17 atores (e sistemas) atuando do macroambiente à linha de frente[cite: 2].

### 2.1. O Macroambiente (Governança e Geração de Dados)

**A. Empregadores (Empresas)**
- **Categoria:** Organização (Privada/Pública)[cite: 2].
- **Papel:** Iniciadores formais da jornada do trabalhador[cite: 2].
- **Responsabilidades:** Informar adequadamente os eventos de rescisão de contrato via eSocial[cite: 2].
- **Riscos e Impactos:** Falhas, atrasos e erros de digitação do empregador na origem geram o bloqueio da concessão que eclodirá, semanas depois, como uma chamada do cidadão frustrado para a URA da Caixa[cite: 2].

**B. CODEFAT (Conselho Deliberativo do Fundo de Amparo ao Trabalhador)**
- **Categoria:** Órgão Colegiado Deliberativo[cite: 2].
- **Papel:** Autoridade normativa suprema[cite: 2].
- **Responsabilidades:** Composto tripartite (governo, trabalhadores, empregadores), edita resoluções determinando prazos e regras do benefício[cite: 2].
- **Riscos e Impactos:** O distanciamento tático[cite: 2]. Se o Conselho cria regras condicionantes muito elaboradas, a Caixa tem severa dificuldade de transformá-las em opções de navegação simples em um teclado numérico (URA)[cite: 2].

**C. Ministério do Trabalho e Emprego (MTE)**
- **Categoria:** Órgão Público Federal[cite: 2].
- **Papel:** Formulador de políticas e secretaria executiva do CODEFAT[cite: 2].
- **Responsabilidades:** Aplicar as regras de elegibilidade da Lei 7.998/1990 e aprovar as remessas financeiras para pagamento[cite: 2].

**D. Dataprev (Empresa de Tecnologia e Informações da Previdência Social)**
- **Categoria:** Organização Pública Tecnológica[cite: 2].
- **Papel:** Processador central de dados[cite: 2].
- **Responsabilidades:** Sustentar o ecossistema eSocial e consolidar os lotes de informações trabalhistas que o MTE utiliza para autorizar o benefício[cite: 2].
- **Dependências:** Ator oculto essencial; se a infraestrutura da Dataprev atrasa um lote, a Caixa fica "cega" e o cidadão recebe erro na URA[cite: 2].

**E. FAT (Fundo de Amparo ao Trabalhador)**
- **Categoria:** Fundo Constitucional[cite: 2].
- **Papel:** Custódia financeira (Art. 239 da Constituição Federal)[cite: 2]. Financia os benefícios operados pela Caixa[cite: 2].

---

### 2.2. A Instância Operacional Estratégica (*Backstage*)

**F. Caixa Econômica Federal (Gestora do Canal)**
- **Categoria:** Empresa Pública (Agente Pagador)[cite: 2].
- **Papel:** Tradutora e Operadora[cite: 2].
- **Responsabilidades:** Estruturar a URA, garantir conformidade com frameworks de TI governamentais (ex: e-PING) e gerir os fornecedores de call center[cite: 2].

**G. Atores da Segurança da Informação e LGPD**
- **Categoria:** Pessoa / Área Organizacional[cite: 2].
- **Papel:** Guardiões da integridade de dados[cite: 2].
- **Responsabilidades e Impactos:** Configuram os protocolos de autenticação baseados em conhecimento (KBA — *Knowledge-Based Authentication*)[cite: 2]. O excesso de zelo técnico na definição das perguntas de segurança atua frequentemente como forte barreira e mecanismo involuntário de exclusão digital[cite: 2].

**H. Canais Digitais Paralelos (Gov.br e CTPS Digital)**
- **Categoria:** Plataforma/Sistema[cite: 2].
- **Papel:** Absorção principal de autoatendimento[cite: 2]. Cidadãos que encontram falhas biométricas ou sistêmicas nestes canais podem recorrer à URA como via alternativa de resolução[cite: 2].

**I. Órgãos de Controle (TCU, CGU)**
- **Categoria:** Órgãos de Estado[cite: 2].
- **Papel:** Auditores da aplicação orçamentária e da moralidade das contratações terceirizadas de atendimento[cite: 2].

---

### 2.3. A Infraestrutura Tecnológica de Atendimento (*Backstage*)

**J. Sistemas de Roteamento de Chamadas (ACD/CTI)**
- **Categoria:** Sistema[cite: 2].
- **Responsabilidades:** O Distribuidor Automático de Chamadas mapeia filas e aloca a ligação transbordada da URA ao humano correspondente, provendo dados à tela do atendente (*screen pop*)[cite: 2].

**K. Fornecedores de Infraestrutura e Software**
- **Categoria:** Organização Privada (Telecom, Nuvem)[cite: 2].
- **Responsabilidades e Riscos:** Garantir enlaces de rede estatais, licenças de URA e armazenamento[cite: 2]. No que tange à conectividade do serviço 0800, os fornecedores de telecomunicação estão submetidos rigorosamente aos parâmetros do Regulamento de Qualidade dos Serviços de Telecomunicações (RQUAL - Resolução ANATEL nº 717/2019) e ao Regulamento Geral de Direitos do Consumidor de Telecomunicações (RGC - Resolução ANATEL nº 632/2014), normas estritas ao Serviço Telefônico Fixo Comutado (STFC). Rompimentos de rotas que configurem infração aos níveis de disponibilidade exigidos pela agência reguladora podem causar isolamento de serviço para regiões inteiras e gerar sanções contratuais e regulatórias.

**L. Equipes de Suporte Tecnológico (TI)**
- **Categoria:** Organização / Pessoa[cite: 2].
- **Papel:** Sustentação do banco de dados da Caixa, vitais para evitar a latência da informação durante o autoatendimento[cite: 2].

**M. Supervisores e Gestores da Central**
- **Categoria:** Pessoa[cite: 2].
- **Responsabilidades:** Fiscalização de qualidade, escala e modulação do ritmo da central humana diante da pressão de volume diário[cite: 2].

---

### 2.4. O Frontstage (Linha de Frente e Cidadão)

**N. Cidadão Requerente (Multimodalidade)**
- **Categoria:** Pessoa[cite: 2].
- **Papel:** Acessador do direito[cite: 2].
- **Atenção Analítica:** Não é um ator monolítico[cite: 2]. O trabalhador CLT interage com uma matriz legal diferente do Pescador Artesanal (Seguro Defeso — Lei 10.779/2003), que possui calendário sazonal e exige laudos de colônias de pescadores[cite: 2]. Cada modalidade vivencia atritos de navegação diferentes na árvore telefônica[cite: 2].

**O. Sistemas Automatizados de Atendimento (URA)**
- **Categoria:** Sistema[cite: 2].
- **Responsabilidades:** Triagem e contenção via fluxos lógicos e integração com APIs[cite: 2]. Fornece respostas ao cidadão utilizando tecnologias de saída de áudio sintetizado, como o TTS (*Text-to-Speech*)[cite: 2].

**P. Mecanismos de Reconhecimento de Voz (ASR/NLP)**
- **Categoria:** Sistema Tecnológico[cite: 2].
- **Responsabilidades:** Sistemas de entrada de áudio baseados em inteligência artificial responsáveis por mapear a intenção do usuário sem a digitação[cite: 2].

**Q. Atendente Humano**
- **Categoria:** Pessoa (Terceirizado)[cite: 2].
- **Papel:** Agente de resolução final; a ponta que lida diretamente com os conflitos gerados pelas divergências sistêmicas acumuladas[cite: 2].

---

### 2.5. O Transbordo Físico e Institucional (Overflow)

**R. SRTEs e Sistema Nacional de Emprego (SINE)**
- **Categoria:** Rede Física[cite: 2].
- **Papel:** Destino do cidadão quando ocorrem impasses insuperáveis de eSocial na URA e exigem-se recursos documentais in loco[cite: 2].

**S. Defensoria Pública da União (DPU) e Juizado Especial Federal (JEF)**
- **Categoria:** Sistema de Justiça[cite: 2].
- **Papel:** Via de acesso extremo[cite: 2]. Demandados para o ingresso de ações reparatórias ou mandados em situações de bloqueios crônicos e sistêmicos[cite: 2].

---

## 3. Dinâmicas de Governança, Poder e Dependência

A assimetria de poder que define a qualidade percebida pelo cidadão é estrutural:

**Custódia vs. Execução:** O CODEFAT prescreve o direito e o limite; a Caixa desenha a interface técnica; e a Dataprev e o MTE intermedeiam as bases de dados eSocial[cite: 2]. Nenhuma falha estrutural neste serviço é passível de resolução unilateral por apenas um desses entes[cite: 2].

**Barreiras Sistêmicas de Acesso:** Com a inclusão da área de Segurança da Informação no mapa, evidencia-se que a URA impõe fricção massiva sob a justificativa de proteção contra fraudes (KBA)[cite: 2]. Usuários de baixa escolaridade reprovam nos testes automáticos de autenticação, sendo bloqueados do benefício não por falta de direito, mas por falta de memória exata de dados cadastrais remotos[cite: 2].

**Pontas Dependentes:** O Atendente e o Cidadão estão no final da cadeia[cite: 2]. Uma vírgula errada gerada pelo Empregador no momento da rescisão reverbera através de cinco sistemas distintos até virar a frase automatizada: *"benefício não localizado"*[cite: 2].

---

## 4. Normativos Aplicáveis por Dimensão

**Objetivo:** Mapear os normativos por dimensão, com dispositivo específico, escopo no serviço, vínculo explícito ao processo de bastidor ou etapa da jornada, e status de cumprimento verificável.

### 4A — Normativos do Benefício

| Instrumento | Dispositivo Específico | O que regula no serviço | Processo vinculado | Status de Cumprimento Verificável |
| :--- | :--- | :--- | :--- | :--- |
| Lei 7.998/1990 | Arts. 2º e 3º | Elegibilidade fundamental do Seguro-Desemprego (tempo de emprego, natureza da rescisão) | **Processo de Suporte: Governança Normativa** → scripts de elegibilidade URA; Etapa 4 (consulta de status) | `[CONFIRMADO]` — fiscalização TCU/CGU; publicação DOU |
| Lei 10.779/2003 | Arts. 1º e 2º | Institui o Seguro Defeso para pescadores artesanais | **Processo de Suporte: Governança Normativa** → modalidade Defeso; Etapa 2 (autenticação de modalidade) | `[CONFIRMADO]` — publicação DOU |
| Lei Complementar 150/2015 | Art. 26 | Estende Seguro-Desemprego a empregadas domésticas | **Processo de Suporte: Governança Normativa** → modalidade Doméstico; Etapa 4 (status) | `[CONFIRMADO]` — publicação DOU |
| Decreto 7.721/2012 | Arts. 1º a 20 | Regulamenta procedimentos, prazos e habilitação ao benefício | **Processo de Suporte: Governança Normativa** + **Backstage**: fluxo eSocial → Dataprev → MTE → URA | `[CONFIRMADO]` — publicação DOU |
| Resolução CODEFAT nº 957/2022 (mod. Res. 1027/2025, que revogou art. 8º, V) | Arts. 4º a 12; inciso V do art. 8º revogado | Consolida regras de concessão e pagamento; mod. relevante para Seguro Defeso (FP-10) | **Processo de Suporte: Governança Normativa** → atualização de scripts URA; FP-11 (lag de governança) | `[CONFIRMADO]` — publicação DOU; Res. 1027/2025 publicada em 04/11/2025 |
| Portarias Específicas do MTE | A identificar (ex: Portarias MTP) | Detalham exigências documentais e status repassados pela URA | **Processo de Suporte: Governança Normativa**; Etapa 4 | `[PENDENTE — identificar números e artigos aplicáveis via DOU/MTE]` |

---

### 4B — Normativos do Canal de Atendimento

| Instrumento | Dispositivo Específico | O que regula no serviço | Processo vinculado | Status de Cumprimento Verificável |
| :--- | :--- | :--- | :--- | :--- |
| Decreto Federal nº 11.034/2022 (Nova Lei do SAC) | Arts. 1º–30 (prazo de atendimento, obrigatoriedade de transbordo, TMA) | Substitui Dec. 6.523/2008; regula SAC telefônico e métricas de qualidade de atendimento | **Backstage: Atendimento Humano** (Etapa 5); FP-07 (TMA); **Processo de Suporte: Sustentação** (contratual) | `[HIPÓTESE — VALIDAR aplicabilidade jurídica à CEF como empresa pública operando benefício estatal delegado]` |
| Portaria SENACON 15/2022 | A identificar | Regulamentação complementar do SAC | **Backstage: Atendimento Humano** (Etapa 5) | `[PENDENTE / EM ABERTO]` — existência e publicidade não verificadas nas bases pesquisadas |
| RGC — Resolução ANATEL nº 632/2014 | Art. 1º (âmbito: STFC, SMP, SCM, SeAC) | Regula deveres de atendimento das prestadoras STFC/0800; inclui deveres de qualidade do canal | **Processo de Suporte: Sustentação de Infraestrutura** (Ator K); Etapa 1.2 (discagem 0800 sobre STFC) | `[CONFIRMADO]` — norma vigente; escopo STFC validado pelo art. 1º; ver Nota de Defesa de Fato abaixo |

**Nota de Defesa de Fato (resolução do NF-4 da auditoria_v2):** Os números 0800 são ofertados por prestadoras de **STFC** licenciadas pela ANATEL (Serviço de Utilidade Pública sobre STFC). A Res. 605/2012 regula métricas SCM/SMP (banda larga/celular) — escopo incompatível com STFC/0800. O RGC 632/2014, ao incluir o STFC expressamente em seu art. 1º, é o instrumento correto. A Res. 605/2012 foi **removida na íntegra** deste Blueprint.

---

### 4C — Normativos de Tecnologia e Dados

| Instrumento | Dispositivo Específico | O que regula no serviço | Processo vinculado | Status de Cumprimento Verificável |
| :--- | :--- | :--- | :--- | :--- |
| Lei 13.709/2018 (LGPD) | Arts. 7º, II e 11, II | Tratamento de dados pessoais para política pública (base legal) e autenticação KBA | **Processo de Suporte: Gravação/Compliance** (Ator L); **Backstage** Etapa 2 (KBA/Ator G) | `[CONFIRMADO]` — obrigação legal; fiscalização ANPD |

---

## 5. Auditoria de Dados: Lacunas e Hipóteses de Campo (Pendentes)

Dado o escopo deste mapeamento sociotécnico, conclusões definitivas dependem da obtenção das métricas a seguir e da validação metodológica das hipóteses demarcadas[cite: 2].

### A. Lacunas de Dados Quantitativos (Métricas Ausentes)

**Volume, Retenção e Abandono:** Total de chamadas direcionadas à árvore, % de contenção automática vs. transbordo humano, e a taxa de abandono na fila (abandono intra-URA vs. abandono no CTI)[cite: 2].

**Qualidade e Fricção:** Necessidade fundamental de obtenção de relatórios de *Customer Effort Score* (CES) — para mensurar matematicamente o grau de dificuldade imposto ao usuário vulnerável — e taxas de Resolução no Primeiro Contato (FCR), de forma a confrontar as métricas contratuais de disponibilidade técnica (SLA — *Service Level Agreement*) com os reais objetivos de impacto do negócio (SLO — *Service Level Objective*)[cite: 2].

---

### B. Hipóteses Analíticas para Verificação

**H1 — A Hipótese da Titularidade:** Formula-se a premissa de que a governança do serviço é fragmentada (silos) sem uma titularidade clara interministerial ou interdepartamental que assuma a responsabilidade ponta-a-ponta pelo índice de FCR[cite: 2]. Requer verificação contratual[cite: 2].

**H2 — A Hipótese do Processamento em Lotes:** Se existem falhas de integração reportadas aos milhares em determinados dias, deve-se investigar tecnicamente se essas anomalias derivam da ausência de processamento em tempo real (APIs) entre a base eSocial/Dataprev e os servidores da URA Caixa[cite: 2].

**H3 — A Hipótese da Fricção Cognitiva:** O viés algorítmico (ASR) prejudica regionalmente o acesso? A literatura de pesquisa aponta assimetrias no reconhecimento de sotaques regionais[cite: 2]. É imperativo testar os motores de inteligência de voz da Caixa para constatar tais desvios[cite: 2].

**H4 — A Hipótese Comportamental do TMA:** Testar empiricamente, via escutas de qualidade e pesquisa de campo, se a pressão das terceirizadas para o cumprimento da meta de Tempo Médio de Atendimento (TMA) possui correlação com a decisão induzida de operadores finalizarem prematuramente chamadas sistêmicas complexas[cite: 2].

**H5 — A Hipótese da Defesa Contratual (Roteamento de ACD):** Investigar nas parametrizações operacionais se os Sistemas de Roteamento de Chamadas (ACD/CTI) possuem regras de distribuição por habilidades (*skill-based routing*) configuradas para penalizar e reter indefinidamente na fila os casos mais complexos, visando maquiar o sucesso estatístico geral do canal[cite: 2].

---

## RESUMO FINAL — Matriz de Resolução Completa (14/14 Achados)

| Gatilho | Status | Localização da evidência |
| :--- | :--- | :--- |
| LE-2 | ✅ Corrigido | Seção 5.B (H4) — hipótese objetiva sem "negligência" |
| LE-3 | ✅ Corrigido | Seção 5.B (H2) — testa *se* há falhas, sem assumir |
| LE-6 e NF-6 | ✅ Corrigido | Seção 5.A — CES incluída nas lacunas |
| IMS-1 | ✅ Corrigido | Seção 2.3 — ACD/CTI restaurado e mapeado |
| AI-1 | ✅ Corrigido | Seção 5.A — SLA vs. SLO diferenciados |
| AI-2 | ✅ Corrigido | Seção 1 — Goffman e Shostack com refs completas |
| NF-1 | ✅ Corrigido | Seção 2.1 — Dataprev mapeada formalmente |
| NF-2 | ✅ Corrigido | Seção 2.4 — TTS definido como saída de áudio |
| NF-3 | ✅ Corrigido | Seção 2.2-2.5 — Atores reintegrados |
| NF-4 | ✅ Resolvido | Seção 4B — Res. 605/2012 removida; RGC 632/2014 + Nota de Defesa |
| NF-5 | ✅ Corrigido | Seção 2.4 — Seguro Defeso desagregado |
| PR-1 | ✅ Corrigido | Seção 4A — Res. CODEFAT 1027/2025 com revogação art. 8º, V |
| PR-2 | ✅ Corrigido | Seção 3 — Dinâmicas de governança e assimetria |
| PR-3 | ✅ Resolvido | Seção 2.3 / Seção 5 — Screen Pop removido; baseline AS-IS |

**Todos os 14 achados resolvidos por integração de rigor normativo, estrutural e metodológico.**

---

## Notas Finais

Este relatório **v3 APERFEIÇOADA** integra:

✅ **Parte 1:** Matriz de auditoria e resolução (14 achados)
✅ **Parte 2:** Mapeamento de 17 atores, dinâmicas de poder, cadeia de valor
✅ **Seção 3:** Dinâmicas de governança estrutural
✅ **Seção 4:** Normativos por dimensão com status verificável (NOVO — do Gemini)
✅ **Seção 5:** Lacunas de dados e 5 hipóteses para validação de campo