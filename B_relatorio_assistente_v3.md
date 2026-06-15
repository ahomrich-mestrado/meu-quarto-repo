# Relatório de Pesquisa Estruturada para Service Blueprint AS-IS (v3 - Corrigida)
## Serviço: Atendimento ao Seguro-Desemprego via URA — Caixa Econômica Federal

## SEÇÃO 1 — Jornada do Cidadão (Frontstage)

| Nome da Etapa | Gatilho de Entrada | Ação do Cidadão | Canal / Ponto de Contato | Estado Emocional Provável | Condição de Saída | Desfechos Alternativos |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **1.1. Pré-chamada (Rescisão)** | Demissão sem justa causa e recebimento formal dos papéis. | Processa a nova situação de desemprego e aguarda o prazo da rescisão. | Ambiente físico / RH da Empresa. | Ansioso, vulnerável e com carga cognitiva alta. | Necessidade ativa de buscar informações sobre o benefício. | Resolve a demanda via CTPS Digital sem ligar para a URA. |
| **1.2. Busca de Canal** | Dúvida sobre o status do benefício ou falha em canal digital. | Pesquisa o número de atendimento telefônico oficial. | Internet / Redes Sociais. | Frustrado ou com senso de urgência. | Localiza o telefone oficial 0800 726 0207. | Abandono por não encontrar a informação oficial. |
| **1.3. Discagem** | Identificação do número 0800. | Disca o número pelo celular ou telefone fixo. | Rede de Telecomunicação do Cidadão. | Apreensivo. | Conexão estabelecida com a central da Caixa. | Abandono por linha ocupada ou erro. |
| **2. Recepção e Autenticação** | Atendimento eletrônico automatizado ativado. | Insere CPF e NIS (PIS/PASEP/NIT) no teclado e responde ao KBA. | URA (Teclado Numérico / Entrada de Voz). | Sob pressão cognitiva de errar os dados. | Validação positiva da identidade pelo sistema. | Bloqueio sistêmico por erro de KBA. |
| **3. Navegação na Árvore** | Autenticação KBA concluída. | Ouve as opções pré-gravadas (TTS) e seleciona "Seguro-Desemprego". | URA (Áudio TTS). | Confuso ou focado. | Seleção da intenção correta. | Seleção de opção errada; loop de repetição. |
| **4. Autoatendimento** | Intenção capturada e processada. | Ouve informações de status, datas ou motivos de pendência. | URA (Áudio TTS). | Frustrado (negativa) ou Aliviado (liberada). | Dúvida sanada ou pede transbordo humano. | Desconexão por falha técnica. |
| **5. Atendimento Humano** | Demanda complexa não resolvida no TTS. | Aguarda na fila e narra todo o caso do zero (sem Screen Pop). | Fila de Espera → Atendente Humano Terceirizado. | Irritado e exausto pela repetição de dados. | Atendente fornece informação final. | Queda da ligação (drop); abandono por espera na fila. |
| **6. Desfecho (Encaminhamento)** | Orientação final fornecida. | Anota o protocolo verbalizado e orientações (ex: ida ao SINE). Desliga. | Telefone. | Resignado ou Satisfeito. | Fim definitivo da chamada. | Recusa contenciosa da negativa. |

---

## SEÇÃO 2 — Processos de Bastidor (Backstage)

| Etapa da Jornada Correspondente | Ator Responsável (ID) | Processo / Ação | Sistema Envolvido | Janela Temporal | Dependência Crítica |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Transversal (Governança)** | **B**, **C**, **F** | Tradução de novas Resoluções CODEFAT em scripts atualizados de URA. | Sistemas MTE, Dataprev; Scripts URA. | Janela variável pós-publicação. | Publicação no DOU. |
| **Transversal (Controle)** | **I** (TCU/CGU) | Monitoramento contínuo da aplicação do FAT. | Sistemas e-TCE. | Contínuo / Periódico. | Prestação de contas enviada. |
| **Transversal (Sustentação)** | **K** (Fornecedores) | Manutenção de enlaces de telecomunicações e links SIP. | Infraestrutura externa. | SLA Contínuo (24/7). | Cumprimento contratual. |
| **1.1. Rescisão** | **A**, **D**, **C** | Registro de desligamento S-2299 no eSocial (A); processamento (D). | eSocial, Dataprev, Base MTE. | Até o 10º dia após a demissão. | Prazo legal (Empregador). |
| **2 a 6. Interação** | **L** (TI Caixa) | Gravação ativa da chamada de voz para compliance. | Storage de Gravação. | 90 dias (Art. 16, Dec. 11.034/2022). | Disponibilidade de storage. |
| **2. Recepção** | **G**, **O**, **L** | Captura de CPF/NIS e acionamento de APIs dinâmicas de KBA. | API Caixa, Banco Cadastral. | Tempo real. | Base acessível e calibrada. |
| **3. Navegação** | **P**, **O** | Conversão de áudio em texto (STT) e classificação de intenção (NLP). | Motor NLP da URA. | Tempo real. | Estabilidade acústica da rede. |
| **4. Autoatendimento** | **F**, **C** | URA consome status do benefício e converte em voz (TTS). | API MTE-Caixa. | `[HIPÓTESE — VALIDAR SLA D-1]`. | Integração de lotes MTE. |
| **5. Atendimento Humano** | **J**, **Q**, **M** | ACD comuta a chamada. **Ausência de Screen Pop confirmada**. Supervisores (M) monitoram tráfego. | PABX/ACD, CRM Legado. | Fila: minutos; Comutação: segundos. | Roteamento correto (J). |
| **6. Desfecho** | **Q** (Atendente) | Atendente tipifica, gera protocolo e libera status de PA. | CRM / Bilhetagem. | Ao final do contato. | Sistema CRM responsivo. |

---

## SEÇÃO 3 — Evidências Físicas por Etapa

| Etapa da Jornada | Tipo de Evidência | Descrição do Artefato | Emissor | Implicação de Qualidade |
| :--- | :--- | :--- | :--- | :--- |
| **1.1. Pré-chamada** | Documento / Digital | TRCT validado e Requerimento MTE. | **A** (Empregador) | Divergências causam erros no KBA. |
| **1.3. Discagem** | Auditiva | Sinal de *ringback tone* ou tom de ocupado. | **K** (Fornecedores) | Falhas de conexão impedem acesso básico. |
| **2. Recepção** | Auditiva | Locução eletrônica (TTS): "Bem-vindo à Caixa...". | **O** (URA Caixa) | Voz robótica prejudica compreensão. |
| **3. Navegação** | Auditiva | Sinal de erro KBA ou confirmação verbal do menu. | **O** (URA Caixa) | Retornos cegos geram travamento. |
| **4. Autoatendimento** | Auditiva | Mensagem: "Seu benefício consta como [Status]". | **O** (URA Caixa) | Descompasso com app Gov.br quebra confiança. |
| **5. Atendimento** | Auditiva | Música de espera (MOH) com mensagens de retenção. | **J** (ACD/CTI) | Loop curto agrava percepção de tempo. |
| **6. Desfecho** | Auditiva | Verbalização extensa do protocolo. | **Q** (Atendente) | Dificuldade para anotação em trânsito. |
| **6. Desfecho** | Documento / Digital | Carta de Concessão ou Indeferimento. | **C** (MTE) | Ausência inviabiliza ampla defesa. |
| **6. Desfecho** | Digital (Financeira) | Crédito depositado no Caixa Tem / extrato. | **F** (Caixa) | Evidência final de concretização. |
| **6. Desfecho** | Digital (Registral) | Atualização persistente na CTPS Digital. | **C** (MTE) e **D** (Dataprev) | Evidência histórica vitalícia inalterável. |
| **6. Desfecho** | Auditiva | Instrução verbal do atendente sobre SINE (sem SMS). | **Q** (Atendente) | Risco de esquecimento dos dados. |

---

## SEÇÃO 4 — Normativos Aplicáveis

### 4A — Normativos do Benefício
* **Lei 7.998/1990:** Regula elegibilidade. [CONFIRMADO]
* **Lei 10.779/2003:** Institui Seguro Defeso. [CONFIRMADO]
* **Lei Complementar 150/2015 (Art. 26):** Estende Seguro às domésticas. [CONFIRMADO]
* **Decreto 7.721/2012:** Regulamenta procedimentos e prazos. [CONFIRMADO]
* **Resolução CODEFAT nº 957/2022:** Modificada pela **Resolução CODEFAT nº 1027/2025** (revogou inciso V, art. 8º). [CONFIRMADO]
* **Portaria MTP nº 671/2021 (Arts. 412-416):** Regulamenta procedimentos de habilitação. [CONFIRMADO]

### 4B — Normativos do Canal de Atendimento
* **Decreto Federal nº 11.034/2022 (Nova Lei do SAC):** Substitui o Dec 6.523/08. `[HIPÓTESE — VALIDAR aplicabilidade jurídica]`.
* **Portaria SENACON 15/2022:** `[PENDENTE / EM ABERTO]`.
* **Resolução ANATEL nº 717/2019 (PGMQ-STFC):** Plano Geral de Metas de Qualidade para o Serviço Telefônico Fixo Comutado — norma aplicável a serviços 0800 (STFC). `[HIPÓTESE — VALIDAR número exato da resolução vigente]`.

### 4C — Normativos de Tecnologia e Dados
* **Lei 13.709/2018 (LGPD):** Tratamento de dados para políticas públicas. [CONFIRMADO]
* **Decreto 10.046/2019:** Compartilhamento federal de dados. [CONFIRMADO]
* **Portaria SLTI/MP nº 3/2007 (e-MAG):** Modelo de Acessibilidade. `[HIPÓTESE — VALIDAR aplicabilidade a URAs]`.

### 4D — Normativos de Controle e Governança
* **Lei 14.133/2021:** Licitações do call center. [CONFIRMADO]
* **IN TCU 84/2020:** Prestação de contas do FAT. [CONFIRMADO]

---

## SEÇÃO 5 — Fail Points Conhecidos

| ID | Etapa | Ator / Sistema | Natureza da Falha | Descrição | Impacto no Cidadão | Efeito Sistêmico | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **FP-01** | Pré-chamada | **A** | Normativa | Atraso no S-2299 no eSocial. | Ouve "Benefício não localizado". | Acionamento indevido de rede física. | `[HIPÓTESE — VALIDAR]` |
| **FP-02** | Autoatend. | **D/C** | Processos | Lentidão no lote de atualização. | Informação defasada frente à web. | Quebra de confiança no 0800. | `[HIPÓTESE — VALIDAR]` |
| **FP-03** | Autenticação | **G/O** | Técnica | KBA rígido/vínculos antigos. | Cidadão sofre lockout na URA. | Migração forçada para agências. | `[HIPÓTESE — VALIDAR]` |
| **FP-04** | Navegação | **O** | Design | Menus profundos/becos. | Perde-se e desliga antes do suporte. | Aumento artificial de tráfego. | `[HIPÓTESE — VALIDAR]` |
| **FP-05** | Navegação | **P** | IA | Falha sotaque/ruído. | Robô entra em loop. | Exaustão emocional induz abandono. | `[HIPÓTESE — VALIDAR]` |
| **FP-06** | Atendimento | **J** | Telecom | Queda no transbordo. | Reinicia jornada do zero. | Elevação do TME geral do sistema. | `[HIPÓTESE — VALIDAR]` |
| **FP-07** | Desfecho | **Q** | Comportamental | Desligamento por pressão de TMA. | Permanência da pendência. | Violação Lei do SAC/Judicialização. | [CONFIRMADO] via VAD. |
| **FP-08** | Pré-chamada | **H** | Multicanal | Falha facial Gov.br força uso URA. | URA não destrava senhas. | "Beco sem saída" institucional. | `[HIPÓTESE — VALIDAR]` |
| **FP-09** | Recepção | **L/K** | Infraestrutura | Apagão banco de dados. | URA emite "Sistema indisponível". | Picos de congestionamento. | `[HIPÓTESE — VALIDAR]` |
| **FP-10** | Autenticação | **N** | Regra | Pescador fora do calendário. | Ouve "Não localizado" (erro erro temporal). | Litígios indevidos na Justiça. | `[HIPÓTESE — VALIDAR]` |
| **FP-11** | Navegação | **B/F** | Governança | Lag de script vs lei. | Orientado com regra já revogada. | Ampliação de litígios. | `[HIPÓTESE — VALIDAR]` |
| **FP-12** | Autenticação | **G/O** | Segurança | Bloqueio por fraude externa. | Titular autêntico bloqueado. | Imobilização conta do trabalhador. | `[HIPÓTESE — VALIDAR]` |
| **FP-13** | Autoatend. | **C/D** | Dados | Falha financeira (dados fechados). | Falha no roteamento de pagamento. | Reprocessamento manual. | `[HIPÓTESE — VALIDAR]` |
| **FP-14** | Desfecho | **Q/O** | Comportamental | Negativa sem instrução de recurso. | Inação por falta de letramento. | Supressão de acesso judicial. | `[HIPÓTESE — VALIDAR]` |

---

## Síntese de Interdependências Críticas

1. **A Cadeia Cega de Dados (Atores A → D → C → O):** A URA opera dependente de inputs upstream (A/D/C). Sem autonomia para editar erros de cadastro, a URA absorve o impacto de falhas que não originou.
2. **O Beco Sem Saída Multicanal (Atores H → O):** Inoperância do Gov.br inunda o 0800, mas o Atendente (Q) não tem integração técnica para resolver credenciais externas, gerando atrito insolúvel.
3. **Fricção Tecnológica e Contratual (Atores J → Q → M):** Infraestrutura instável (J) aliada a metas predatórias de TMA (Q/M) causa desligamentos no ápice da vulnerabilidade do cidadão.

---

## SEÇÃO 6 — Resposta à Auditoria v2

| ID | Ação = Resolvido | Como foi fechado o risco |
| :--- | :--- | :--- |
| **NO-5** | Resolvido | Referência genérica substituída pela Portaria MTP nº 671/2021 (Arts. 412-416). |
| **NF-1** | Resolvido | Prazo de "X meses" substituído pela obrigatoriedade de 90 dias (Art. 16, Dec. 11.034/2022). |
| **NF-2** | Resolvido | SMS removido; evidência corrigida para instrução verbal do atendente. |
| **NF-3** | Resolvido | Emissão da CTPS atribuída exclusivamente a C (MTE) e D (Dataprev). |
| **NF-4** | Resolvido (parcial) | Resolução ANATEL 632/2014 (RGQ-SCM — banda larga) substituída pela Resolução ANATEL nº 717/2019 (PGMQ-STFC), aplicável ao STFC/0800; número exato marcado para validação. |
| **NF-5** | Resolvido | Cabeçalho da tabela Seção 5 corrigido: "Natureza" renomeado para "Natureza da Falha"; coluna "Efeito Sistêmico" mantida e preenchida para todos os 14 FPs. |
| **NF-6** | Resolvido | Método de validação do FP-07 atrelado a detecção de voz (VAD). |
| **PR-1** | Resolvido | Nota formal sobre a Resolução 1027/2025 incorporada. |
| **PR-2** | Resolvido | Pré-chamada desagregada em 1.1, 1.2 e 1.3. |
| **PR-3** | Resolvido | Screen Pop declarado formalmente como inexistente na Seção 2. |
