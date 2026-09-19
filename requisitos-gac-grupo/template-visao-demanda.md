# Visão da Demanda (VD)

## Histórico de Versões

| Data | Versão | Descrição | Autor |
| --- | --- | --- | --- |
| 03/05/2026 | 1.0 | Elaboração inicial do documento de visão da demanda para o sistema de locação de projetores | Emily da Silva Freitas; Salua Rayane Melo; Suyane Pereira Costa; Wesley Amorim Campêlo |
|  |  |  |  |

---

## Autores

- Emily da Silva Freitas  
- Salua Rayane Melo  
- Suyane Pereira Costa  
- Wesley Amorim Campêlo  

---

## 1. Objetivo

Este documento tem como objetivo apresentar a visão da demanda para o desenvolvimento de um sistema informatizado de controle e locação de projetores e equipamentos audiovisuais, visando otimizar processos operacionais, aumentar a rastreabilidade dos ativos e melhorar a eficiência no atendimento aos usuários.

---

## 2. Proposta de Valor

A implementação da solução proposta permitirá a substituição do controle manual atualmente realizado por meio de registros físicos, promovendo maior agilidade no atendimento e redução significativa de filas em horários de pico.

Adicionalmente, o sistema proporcionará maior controle e transparência no uso dos equipamentos, garantindo rastreabilidade completa dos ativos, segurança na transferência de responsabilidade entre usuários e suporte à tomada de decisão por meio de relatórios e indicadores de uso.

Além disso, o sistema permitirá a emissão e consulta de recibos digitais de retirada, devolução e transferência de equipamentos, aumentando a transparência, segurança e rastreabilidade das operações realizadas.

---

## 3. Descrição da Demanda

Atualmente, o processo de empréstimo de projetores é realizado por meio de um único caderno físico, o que ocasiona filas, especialmente em períodos de troca de turno. Além disso, a prática informal de repasse de equipamentos entre professores compromete a rastreabilidade, uma vez que a responsabilidade permanece vinculada ao primeiro usuário registrado.

Diante desse cenário, propõe-se o desenvolvimento de um sistema no domínio de locação de equipamentos, com as seguintes funcionalidades principais:

- Cadastro e gerenciamento de ativos (projetores e cabos)  
- Registro e controle de empréstimos  
- Verificação de disponibilidade em tempo real  
- Solicitação e agendamento de uso  
- Repasse digital de responsabilidade entre usuários  
- Registro de histórico de manutenção  
- Geração de relatórios gerenciais e estatísticos
- Emissão e consulta de recibos digitais

O sistema deverá atender diferentes perfis de usuários, contemplando funcionalidades específicas para cada papel envolvido no processo.

### 3.1 Processo de Elicitação e Entrevistas

Para o entendimento real das dores operacionais e levantamento dos requisitos do sistema, a equipe realizou entrevistas estruturadas com as principais partes interessadas (Equipe operacional do CCT e corpo docente).

**Roteiro de Perguntas Aplicadas:**
- Como funciona o fluxo atual de empréstimo de projetores desde a retirada até a devolução?
- Quais são os principais gargalos enfrentados nos horários de troca de turno?
- Como é feito o controle quando um professor precisa passar o equipamento diretamente para outro colega?
- O que acontece se houver algum erro de anotação ou sumiço de componentes no modelo atual?

**Resultados e Conclusões das Entrevistas:**
- **Gargalo de Atendimento:** Confirmou-se que a maioria dos professores finaliza as aulas no mesmo horário, gerando um tumulto nas devoluções. Como a secretaria possui apenas um caderno de anotações para uso manual dos funcionários, o processo trava, causando filas, atrasos e erros de preenchimento.
- **Perda de Rastreabilidade:** Os professores admitiram que repassam os projetores diretamente para outros colegas sem comunicar a secretaria. Isso quebra a garantia de responsabilidade, pois impede que se saia quem realmente causou algum dano ao equipamento ou o extravio de componentes essenciais, como cabos VGA e USB.
- **Necessidade de Segurança e Automação:** Apontou a necessidade urgente de automatizar o processo para identificar com precisão qual projetor está com defeito e precisa de manutenção, eliminando de vez a transferência informal e sem registro entre os docentes.

---

## 4. Partes Interessadas

| Nome | Papel | Responsabilidades | Representante |
| -------------------- | --------------- | ----------------------------------- | ---------------- |
| Professores | Usuários finais | Solicitar, utilizar, transferir e devolver equipamentos | - |
| Equipe do CCT | Operacional | Gerenciar empréstimos, validar retiradas e devoluções e reportar manutenção | - |
| Diretor do CCT | Cliente | Aprovar cadastros, acompanhar relatórios e supervisionar ativos | Prof. Jackson |
| DTEC | Suporte técnico | Garantir infraestrutura, manutenção e integração tecnológica | - |
| Atendentes | Stakeholders | Assegurar a disponibilidade de recursos para as atividades acadêmicas | - |

---

## 5. Personas

### 5.1. Coordernador do CCT 
- **Descrição:** Responsável administrativo pela supervisão do sistema e validação das operações críticas.
- **Objetivo:** Garantir o correto funcionamento do sistema, aprovar cadastros e acompanhar indicadores operacionais.

### 5.2. Professor

- **Descrição:** Docente que depende do uso de recursos audiovisuais para execução de suas atividades acadêmicas.  
- **Objetivo:** Realizar a solicitação de equipamentos de forma ágil, confiável e com garantia de disponibilidade, além de possibilitar a transferência de responsabilidade quando necessário.  

### 5.3. Atendente do CCT

- **Descrição:** Profissional responsável pela gestão operacional dos equipamentos e atendimento aos usuários.  
- **Objetivo:** Controlar empréstimos com eficiência, reduzir filas e assegurar a integridade e rastreabilidade dos ativos.  

---

## 6. Necessidades e Funcionalidades

### Necessidade 1: Controle de acesso ao sistema

#### F1.1 Autenticação de usuários

- **Descrição:** Permitir a autenticação de usuários por meio de credenciais válidas, garantindo segurança no acesso ao sistema.  
- **Incluída**  
- **Atores:** Atendente, Professor e Coordenador
- **Frequência:** Alta  
- **Valor:** Alto
- 

#### F1.2 Validação por PIN Digital 
- **Descrição:** Permitir confirmação de ações críticas por meio de PIN individual de 4 ou 6 dígitos.  
- **Incluída**  
- **Atores:** Atendente e Professor
- **Frequência:** Alta  
- **Valor:** Alto
- 

#### F1.3 Cadastro de usuários

- **Descrição:** Permitir o cadastro de professores, atendentes e diretores no sistema, de acordo com os níveis de acesso definidos.  
- **Incluída**  
- **Atores:** Atendente, Diretor  
- **Frequência:** Média  
- **Valor:** Alto  

#### F1.4 Aprovação de usuários

- **Descrição:** Permitir validação e aprovação de novos usuários antes da liberação de acesso ao sistema.  
- **Incluída**  
- **Atores:** Diretor  
- **Frequência:** Média  
- **Valor:** Alto  

#### F1.5 Controle de permissões de acesso

- **Descrição:** Permitir definição e gerenciamento dos níveis de acesso conforme o perfil de cada usuário do sistema.  
- **Incluída**  
- **Atores:** Diretor  
- **Frequência:** Média  
- **Valor:** Alto  

#### F1.6 Emissão e consulta de recibos digitais

- **Descrição:** Permitir a geração e consulta de recibos digitais relacionados às operações de retirada, devolução e transferência de equipamentos, garantindo rastreabilidade e registro das ações realizadas.  
- **Incluída**  
- **Atores:** Atendente, Professor e Diretor  
- **Frequência:** Alta  
- **Valor:** Alto

---

### Necessidade 2: Gestão de ativos

#### F2.1 Cadastro de equipamentos

- **Descrição:** Permitir o registro de projetores, cabos  e demais equipamentos com identificação patrimonial.  
- **Incluída**  
- **Atores:** Atendente e Diretor
- **Frequência:** Média  
- **Valor:** Alto  

#### F2.2 Aprovação de cadastros de itens 

- **Descrição:** Permitir que os Atendentes valide o cadastro de novos equipamentos antes da disponibilização.  
- **Incluída**  
- **Atores:** Atendente  
- **Frequência:** Média  
- **Valor:** Alto  

#### F2.3 Gerenciamento e monitoramento de ativos

- **Descrição:** Permitir atualização, remoção e acompanhamento da disponibilidade e status dos equipamentos em tempo real, incluindo situações como disponível, reservado, emprestado, indisponível ou em manutenção.  
- **Incluída**  
- **Atores:** Atendentes, Professor, Coordenador  
- **Frequência:** Alta  
- **Valor:** Alto  

---

### Necessidade 3: Processo de locação

#### F3.1 Solicitação e agendamento de equipamentos

- **Descrição:** Permitir que os professores realizem solicitações de empréstimo de equipamentos.  
- **Incluída**  
- **Atores:** Professor  
- **Frequência:** Alta  
- **Valor:** Alto  

#### F3.2 Aprovação de solicitações

- **Descrição:** Permitir que os atendentes aprovem ou rejeitem solicitações e agendamentos.  
- **Incluída**  
- **Atores:** Atendente  
- **Frequência:** Alta  
- **Valor:** Alto  

#### F3.3 Liberação de retirada

- **Descrição:** Permitir que o funcionário realize a confirmação da retirada do equipamento mediante autenticação digital.  
- **Incluída**  
- **Atores:** Atendente  
- **Frequência:** Alta  
- **Valor:** Alto 

#### F3.4 Confirmação de recebimento

- **Descrição:** Permitir que o professor confirme digitalmente o recebimento do equipamento. 
- **Incluída**  
- **Atores:** Professor 
- **Frequência:** Alta  
- **Valor:** Alto 

#### F3.5 Registro de devolução

- **Descrição:** Permitir que o registro e confirmação digital da devolução dos equipamentos. 
- **Incluída**  
- **Atores:** Atendente e Professor 
- **Frequência:** Alta  
- **Valor:** Alto 

---

### Necessidade 4: Transferência de responsabilidade

#### F4.1 Solicitação de transferência

- **Descrição:** Permitir que um professores transfira a responsabilidade de um equipamento para outro usuário.
- **Incluída**  
- **Atores:** Professor 
- **Frequência:** Média  
- **Valor:** Alto  

#### F4.2 Confirmação de recebimento da transferência

- **Descrição:** Permitir que o professor destinatário confirme digitalmente o recebimento do equipamento transferido.
- **Incluída**  
- **Atores:** Professor 
- **Frequência:** Média  
- **Valor:** Alto

#### F4.3 Registro da cadeia de responsabilidade

- **Descrição:** Manter histórico completo das transferências e responsáveis pelo equipamento.
- **Incluída**  
- **Atores:** Atendente e Professor 
- **Frequência:** Alta  
- **Valor:** Alto



---

### Necessidade 5: Monitoramento e controle

#### F5.1 Controle de manutenção e indisponibilidade

- **Descrição:** Permitir o registro de defeitos, manutenções corretivas e preventivas, além do bloqueio automático de equipamentos indisponíveis para empréstimo ou reserva.  
- **Incluída**  
- **Atores:** Professor, Atendente  
- **Frequência:** Média  
- **Valor:** Alto  
---

## 6.1 Requisitos Não Funcionais

### RNF01 — Autenticação segura

O sistema deverá permitir autenticação apenas mediante credenciais válidas.

### RNF02 — PIN de validação

O sistema deverá exigir PIN individual de 4 ou 6 dígitos para confirmação de operações críticas.

### RNF03 — Controle de acesso

O sistema deverá restringir funcionalidades de acordo com o perfil do usuário:
- Professor
- Atendente
- Diretor

### RNF04 — Rastreabilidade

O sistema deverá manter histórico completo de empréstimos, devoluções, transferências e manutenções.

### RNF05 — Tempo de resposta

O sistema deverá responder operações comuns em até 10 segundos.

### RNF06 — Disponibilidade em tempo real

As informações de disponibilidade dos equipamentos deverão ser atualizadas em tempo real.

### RNF07 — Interface intuitiva

O sistema deverá possuir interface simples e de fácil utilização.

### RNF08 — Compatibilidade

O sistema deverá funcionar em computadores, tablets e smartphones.

### RNF09 — Facilidade operacional

As operações principais deverão ser executadas com poucos passos para reduzir filas e tempo de atendimento.

### RNF10 — Integridade dos dados

O sistema deverá garantir que os registros não sejam alterados sem autorização.

### RNF11 — Confirmação digital

Toda retirada, devolução e transferência deverá possuir confirmação digital registrada.

### RNF12 — Escalabilidade

O sistema deverá permitir inclusão futura de novos tipos de equipamentos e funcionalidades.

### RNF13 — Modularidade

O sistema deverá ser dividido em módulos independentes para facilitar manutenção e evolução.

### RNF14 — Registro de logs

O sistema deverá armazenar logs das operações realizadas pelos usuários.

### RNF15 — Persistência documental

O sistema deverá armazenar recibos digitais de operações realizadas, permitindo consulta posterior pelos usuários autorizados.

## 7. Arquitetura da Demanda

A solução será estruturada com base no domínio de locação de equipamentos, contemplando os seguintes módulos:

- Módulo de autenticação e controle de acesso  
- Módulo de gestão de ativos  
- Módulo de locação e agendamento  
- Módulo de transferências  
- Módulo de manutenção  
- Módulo de relatórios e monitoramento
- Módulo de recibos digitais

O sistema deverá funcionar em ambiente web, permitindo acesso por diferentes perfis de usuários através de autenticação segura.

Adicionalmente, o sistema contará com mecanismos de validação digital por PIN para confirmação de operações críticas, como retirada, devolução e transferência de equipamentos.

### Requisitos não funcionais relacionados à arquitetura

- Usabilidade: interface simples e intuitiva  
- Desempenho: respostas rápidas às operações do usuário  
- Segurança: proteção de dados, autenticação confiável e validação por PIN  
- Disponibilidade: acesso contínuo ao sistema  
- Rastreabilidade: histórico completo de operações e transferências  
- Compatibilidade: funcionamento em computadores, tablets e smartphones  
- Integridade dos dados: proteção contra alterações não autorizadas  

---

### 7.1 Diagramas UML

#### 7.1.1 Diagrama de Caso de Uso

**Casos de uso principais:**

- CU1: Realizar login  
- CU2: Solicitar equipamento  
- CU3: Aprovar solicitação  
- CU4: Confirmar retirada  
- CU5: Confirmar devolução  
- CU6: Transferir responsabilidade  
- CU7: Registrar manutenção  
- CU8: Emitir recibos
- CU9: Consultar Recibos   
- CU10: Gerar relatórios  

![Diagrama de Casos de Uso](./diagrama-casos-de-uso.png/diagrama.jpeg)
---

#### 7.1.2 Diagrama de Componentes

**Componentes principais:**

- Módulo de autenticação  
- Módulo de gerenciamento de ativos  
- Módulo de empréstimos  
- Módulo de transferências  
- Módulo de manutenção  
- Módulo de relatórios  
- Banco de dados  

---

#### 7.1.3 Diagrama de Implantação

**Ambiente de execução:**

- Aplicação Web  
- Servidor de aplicação  
- Banco de dados  
- Rede institucional do CCT  
- Dispositivos clientes (computadores e smartphones)  

## 8. Regras de Negócio

- **RN01:** Usuários não poderão realizar novas solicitações enquanto houver pendências de devolução.  
- **RN02:** Toda retirada de equipamento deverá possuir confirmação digital por PIN.  
- **RN03:** Toda devolução deverá ser validada digitalmente pelo responsável pela entrega.  
- **RN04:** Transferências de responsabilidade somente poderão ocorrer mediante confirmação das duas partes envolvidas.  
- **RN05:** Equipamentos em manutenção ou com defeito não poderão ser reservados ou emprestados.  
- **RN06:** Apenas diretores poderão aprovar cadastros de usuários e equipamentos.  
- **RN07:** Todos os equipamentos deverão possuir identificação patrimonial única.  
- **RN08:** O sistema deverá registrar automaticamente o histórico completo de empréstimos, devoluções, transferências e manutenções.
- **RN09:** Toda retirada, devolução e transferência deverá gerar um recibo digital automaticamente.  
- **RN10:** Recibos digitais deverão permanecer disponíveis para consulta pelos usuários autorizados.  

---

## 9. Priorização (MoSCoW)

### Must Have (Obrigatórios)

- Autenticação de usuários  
- Cadastro e gestão de equipamentos  
- Solicitação, agendamento e aprovação de empréstimos  
- Controle de disponibilidade  
- Confirmação digital por PIN  
- Controle de transferências de responsabilidade  
- Registro de devolução  
- Histórico de operações  
- Emissão e consulta de recibos digitais

### Should Have (Importantes)

- Relatórios de uso  
- Controle de manutenção   
- Histórico de manutenção

### Could Have (Desejáveis)

- Indicadores avançados de desempenho  
- Melhorias de interface e experiência do usuário  
- Notificações automáticas para devolução e manutenção  

### Won’t Have (Não contemplados neste momento)

- Integração com aplicativos externos  
- Controle financeiro de locações  
- Aplicativo mobile dedicado  

---

## 10. Validação e Verificação

O documento deverá passar por processo de revisão em grupo, assegurando conformidade com o padrão estabelecido e qualidade das informações descritas.

As funcionalidades e requisitos definidos deverão ser analisados quanto à clareza, consistência, viabilidade e alinhamento com as necessidades dos stakeholders envolvidos.

Eventuais divergências identificadas durante as revisões deverão ser discutidas e registradas, priorizando impacto, urgência e viabilidade técnica da solução.

---

## 11. Pré-Validação

A versão final do documento será submetida à validação junto aos stakeholders, garantindo alinhamento com as necessidades reais do cliente e viabilidade da solução proposta.

A pré-validação deverá confirmar se as funcionalidades previstas atendem adequadamente aos processos de empréstimo, transferência, devolução e rastreabilidade dos equipamentos audiovisuais.

Também deverá ser avaliada a adequação dos mecanismos de autenticação, confirmação digital e controle operacional definidos para o sistema.

---

## Checklist de Validação do Documento de Visão

- [x] Objetivo claramente definido  
- [x] Proposta de valor consistente e relevante  
- [x] Stakeholders identificados  
- [x] Personas descritas  
- [x] Funcionalidades associadas a atores  
- [x] Valor e frequência definidos  
- [x] Arquitetura descrita  
- [x] Linguagem formal, clara e objetiva
