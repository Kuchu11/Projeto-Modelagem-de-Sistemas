# Especificação de Requisitos de Software (SRS) — Sistema GAC

## 1. Introdução

### 1.1 Objetivo do Documento
Este documento de Especificação de Requisitos de Software (SRS) tem como objetivo descrever de forma detalhada as funcionalidades, restrições e interfaces do sistema GAC. O documento visa alinhar as expectativas do grupo de desenvolvimento com os objetivos acadêmicos e operacionais da instituição, servindo como guia para as etapas de implementação, testes e homologação das Sprints 4 e 5.

### 1.2 Escopo do Produto
O GAC é um sistema de gerenciamento e controle patrimonial focado na otimização do fluxo de empréstimos e devoluções de ativos institucionais (tais como projetores, cabos e chaves de salas). O software substitui controles manuais ou planilhas locais por uma plataforma web centralizada, garantindo rastreabilidade através de assinaturas digitais por PIN, geração automatizada de recibos eletrônicos com hash de segurança e relatórios em tempo real sobre o status de disponibilidade do inventário.

### 1.3 Definições, Acrônimos e Abreviações
*   **SRS:** Software Requirements Specification (Especificação de Requisitos de Software).
*   **CDU:** Caso de Uso.
*   **PIN:** Personal Identification Number (Número de Identificação Pessoal) utilizado para assinatura eletrônica de coautoria.
*   **Ativo/Item Patrimonial:** Qualquer recurso físico gerenciado pelo sistema (projetor, cabo, chave).
*   **GAC:** Gestão de Ativos do CCT.

### 1.4 Visão Geral do Documento
Este documento é dividido em três partes principais: esta Introdução (seção 1); a Descrição Geral do sistema, abordando atores e restrições (seção 2); e os Requisitos Detalhados (seção 3), onde constam as especificações textuais dos Casos de Uso, regras de negócio e mapeamento de interfaces visuais.

---

## 3. Requisitos Detalhados

### 3.1 Especificação de Requisitos Funcionais

#### Histórico de Versões
| Data | Versão | Descrição | Autores |
| :--- | :--- | :--- | :--- |
| 03/05/2026 | 1.0 | Elaboração inicial do documento de visão da demanda para o sistema de locação de projetores. | Emily da Silva Freitas; Salua Rayane Melo; Suyane Pereira Costa; Wesley Amorim Campêlo |
| 28/05/2026 | 2.0 | Refatoração completa para generalização de itens (projetores, cabos, chaves), inclusão de regras de PIN, geração de recibos digitais e alinhamento com os protótipos de alta fidelidade. | Emily da Silva Freitas; Salua Rayane Melo; Suyane Pereira Costa; Wesley Amorim Campêlo |

---

### CDU03 - Processar Empréstimo de Item Patrimonial

#### 1. Nome do Caso de Uso
**CDU03 - Processar Empréstimo de Item Patrimonial**

#### 2. Objetivo
Permitir que o atendente realize a reserva e a liberação física de um ativo patrimonial (projetor, cabo ou chave) para um professor, vinculando a responsabilidade do item à matrícula do solicitante mediante validação de segurança via PIN.

#### 3. Tipo de Caso de Uso
| Item | Valor |
| :--- | :--- |
| **Tipo do Caso de Uso** | Concreto |

#### 4. Atores
*   **4.1 Primário:** Atendente
*   **4.2 Secundários / Interessados:** Professor

#### 5. Precondições
| Código | Descrição |
| :--- | :--- |
| **PRE01** | O atendente deve estar autenticado no sistema GAC. |
| **PRE02** | O item patrimonial solicitado deve estar cadastrado e com status "Disponível" no inventário. |

#### 6. Fluxo Principal
*   **P1. Iniciar solicitação de empréstimo**
    *   **P1.1.** O atendente acessa a aba "Novo Empréstimo" no painel operacional.
    *   **P1.2.** O atendente insere a matrícula do Professor solicitante.
*   **P2. Validar elegibilidade do solicitante**
    *   **P2.1.** O sistema busca o cadastro do professor e verifica que não há pendências críticas ou bloqueios administrativos vigentes.
*   **P3. Selecionar ativos e acessórios**
    *   **P3.1.** O atendente seleciona o item principal disponível (ex: Chave da Sala 203 ou Projetor 02).
    *   **P3.2.** O atendente assinala os acessórios adicionais que estão saindo junto com o item (ex: adaptador de vídeo, controle remoto).
*   **P4. Confirmar operação e invocar PIN**
    *   **P4.1.** O atendente clica em "Confirmar Saída".
    *   **P4.2.** O sistema dispara a validação e invoca o caso de uso **CDU09 - Validar Identidade por PIN**.
    *   **P4.3.** O Professor digita seu PIN para aceitar a responsabilidade patrimonial pelo ativo.
*   **P5. Atualizar inventário e emitir recibo de saída**
    *   **P5.1.** O sistema altera o status do item de "Disponível" para "Em Uso".
    *   **P5.2.** O sistema invoca o caso de uso **CDU12 - Emitir Recibo Digital**, gerando o comprovante de retirada.
    *   **P5.3.** O caso de uso é encerrado.

#### 7. Fluxos Alternativos
*   **A1. Solicitante com Pendências Ativas**
    *   **A1.1.** No passo P2.1, o sistema detecta que o professor possui um item retido in atraso crônico.
    *   **A1.2.** O sistema exibe um alerta na tela detalhando a pendência.
    *   **A1.3.** O atendente pode, mediante justificativa registrada em campo de texto, prosseguir com a liberação em caráter excepcional ou abortar o fluxo.

#### 8. Fluxos de Exceção
*   **E1. Item Patrimonial Indisponível**
    *   **E1.1.** No passo P3.1, o item físico desejado encontra-se com o status "Em Manutenção" ou já está emprestado para outro docente.
    *   **E1.2.** O sistema impede a seleção do ativo e exibe uma mensagem de erro. A operação é cancelada sem gerar movimentação.

#### 9. Pós-condições
| Código | Descrição |
| :--- | :--- |
| **POS01** | O status do item passa para "Em Uso" no banco de dados. |
| **POS02** | O registro de empréstimo ativo é gerado contendo a data/hora exata e associado à matrícula do Professor. |

---

### CDU04 - Processar Devolução de Item Patrimonial

#### 1. Nome do Caso de Uso
**CDU04 - Processar Devolução de Item Patrimonial**

#### 2. Objetivo
Permitir que o atendente realize o recebimento físico e a conferência de equipamentos (projetores, cabos ou chaves), registrando as condições do item através de um checklist de inspeção e encerrando a movimentação mediante a validação de segurança via PIN e a emissão obrigatória de um recibo digital.

#### 3. Tipo de Caso de Uso
| Item | Valor |
| :--- | :--- |
| **Tipo do Caso de Uso** | Concreto |

#### 4. Atores
*   **4.1 Primário:**
    *   **Atendente:** Realiza a inspeção visual, preenche o checklist de devolução no painel operacional e encerra o empréstimo no sistema.
*   **4.2 Secundários / Interessados:**
    *   **Professor:** Responsável pela devolução física do equipamento e pela inserção do PIN de segurança para confirmação de coautoria na devolução.
    *   **Coordenador / Diretor:** Atua como auditor institucional, podendo consultar os recibos digitais gerados e fiscalizar a cadeia de custódia dos ativos.

#### 5. Precondições
| Código | Descrição |
| :--- | :--- |
| **PRE01** | O atendente deve estar autenticado no sistema e possuir permissões ativas no painel da coordenação. |
| **PRE02** | O item patrimonial (projetor, cabo ou chave) deve estar associado a um empréstimo ativo ("Em Uso" ou "Em Atraso"). |

#### 6. Fluxo Principal
*   **P1. Acessar painel de controle e selecionar item**
    *   **P1.1.** O atendente accesses a aba "Em Uso" ou "Em Atraso" do Painel de Controle da coordenação.
    *   **P1.2.** O atendente localiza o registro de empréstimo do professor e clica na opção para processar a devolução.
*   **P2. Apresentar dados do empréstimo**
    *   **P2.1.** O sistema carrega a tela de conferência de devolução, exibindo a identificação do Item Principal, seus acessórios vinculados (ex: Projetor + Cabo HDMI) e o nome/matrícula do Professor responsável.
*   **P3. Realizar checklist de inspeção**
    *   **P3.1.** O atendente realiza a verificação física dos componentes entregues no balcão.
    *   **P3.2.** O atendente preenche o Checklist de Inspeção em tela, assinalando os itens de conformidade apresentados (ex: Cabo HDMI incluso, Controle incluso, Equipamento ligando).
*   **P4. Confirmar devolução e invocar validação por PIN**
    *   **P4.1.** O atendente aciona a opção para finalizar a devolução e gerar o recibo.
    *   **P4.2.** O sistema dispara a regra de negócio **RN03** e invoca o caso de uso **CDU09 - Validar Identidade por PIN** para garantir a segurança da operação.
    *   **P4.3.** O Professor insere e valida seu PIN de segurança no terminal.
*   **P5. Atualizar inventário e emitir recibo digital**
    *   **P5.1.** O sistema valida as credenciais, altera o status do patrimônio para "Disponível" no módulo de Gerenciamento de Inventário e remove o vínculo de responsabilidade do Professor.
    *   **P5.2.** O sistema invoca o caso de uso **CDU12 - Emitir Recibo Digital** (executando a regra **RN09**), gerando o documento com hash de rastreabilidade.
    *   **P5.3.** O caso de uso é encerrado com sucesso.

#### 7. Fluxos Alternativos
*   **A1. Equipamento com Avaria Identificada**
    *   **A1.1.** No passo P3.2, o atendente constata que um item falhou no checklist (ex: equipamento não liga ou possui dano físico).
    *   **A1.2.** O atendente preenche o campo de observações detalhando a falha ou a avaria encontrada.
    *   **A1.3.** O fluxo prossegue normalmente para a validação do PIN no passo P4.
    *   **A1.4.** Após a confirmação bem-sucedida, o sistema altera o status final do item para "Em Manutenção" e bloqueia novas reservas operacionais para este ativo.

#### 8. Fluxos de Exceção
*   **E1. PIN Inválido ou Recusado**
    *   **E1.1.** No passo P4.3, o PIN inserido pelo professor está incorreto ou a autenticação falha.
    *   **E1.2.** O sistema exibe uma mensagem de erro de autenticação e mantém a tela de devolução retida.
    *   **E1.3.** O status do empréstimo permanece inalterado e o recibo de baixa não é emitido até que uma credencial válida seja fornecida.
*   **E2. Ausência Crítica de Componente (Quebra de Acordo)**
    *   **E2.1.** O atendente identifica que um acessório obrigatório não foi devolvido e o professor não aceita a responsabilidade da avaria em tela.
    *   **E2.2.** O atendente cancela a operação clicando no botão de retorno.
    *   **E2.3.** O sistema mantém o item com status "Em Uso" ou "Em Atraso", gerando um alerta no painel de pendências para tratamento administrativo pela coordenação.

#### 9. Pós-condições
| Código | Descrição |
| :--- | :--- |
| **POS01** | O status do item é atualizado no inventário para "Disponível" (ou "Em Manutenção" se houver avaria reportada). |
| **POS02** | O vínculo de responsabilidade patrimonial ativa sai do nome do Professor no sistema GAC. |
| **POS03** | O Recibo Digital com assinatura por PIN é persistido no banco de dados para consultas futuras de auditoria por professores, atendentes e diretores. |

#### 10. Regras de Negócio Associadas
| Código | Nome | Descrição |
| :--- | :--- | :--- |
| **RN03** | Validação por PIN na Devolução | Toda devolução exige obrigatoriamente a inclusão e validação do PIN Digital do usuário para garantir que o equipamento saiu de seu nome com consentimento explícito. |
| **RN09** | Emissão Automatizada de Recibo | O encerramento de qualquer movimentação ativa (Retirada, Devolução ou Transferência) dispara de forma nativa e síncrona a geração de um recibo digital criptografado. |

#### 11. Interface Visual
##### IV1. Tela de Confirmação de Devolução
| Campo / Elemento | Tipo | Obrigatório | Descrição / Regra |
| :--- | :--- | :--- | :--- |
| **Card do Equipamento** | Visualizador de Texto | Sim | Exibe o nome do item principal e a lista de acessórios detectados no empréstimo (Ex: Projetor 05 + Acessórios). |
| **Checklist de Inspeção** | Checkbox Group | Não | Caixa de seleção rápida contendo componentes padrão: Cabo HDMI incluso, Controle incluso e Equipamento ligando. |
| **Observações** | Caixa de Texto Longo | Não | Campo multilinha reservado para detalhamento de inconformidades ou avarias físicas. |
| **Botão "Finalizar Devolução"** | Botão de Ação | Sim | Submete os dados inseridos, invoca o modal de validação de PIN e conclui a operação de baixa patrimonial. |

#### 12. Checklist de Validação do Artefato (CDU)
*   [x] Nome do caso de uso condizente com a ação de encerramento de pendência.
*   [x] Inclusão explícita (`«include»`) da chamada ao caso de uso de validação por PIN digital em conformidade com o diagrama UML.
*   [x] Inclusão explícita (`«include»`) da chamada ao caso de uso de geração do Recibo Digital.
*   [x] Flexibilização do fluxo para aceitar chaves, projetores e cabos de maneira genérica.
*   [x] Campos e botões validados e mapeados linha por linha de acordo com as telas reais do sistema.
