# MODELO DE PROCESSO DE NEGÓCIO EM BPMN
## Submódulo 7.13 – Emissão de Declarações de Atendimento para Integração de Instalações de Geração ao SIN

---

## 1. RAIAS (Pools / Lanes)

O processo é organizado em um **Pool principal** denominado **"Processo de Emissão de Declarações de Atendimento – Submódulo 7.13"**, com as seguintes **lanes (raias)**:

| ID | Ator (Lane) | Descrição |
|----|-------------|-----------|
| L1 | **Agente de Geração** | Responsável pela usina; elabora e encaminha solicitações, declara conformidade, resolve pendências, solicita prorrogações de prazo |
| L2 | **ONS (Operador Nacional do Sistema Elétrico)** | Analisa solicitações, verifica requisitos impeditivos, emite ou recusa declarações, suspende/reinicia processos, informa impedimentos |
| L3 | **ANEEL** | Recebe informações do ONS quando necessário (ex.: revalidação de prazo de pendências não impeditivas da DAPR/P) |

> **Nota:** CCEE e concessionárias de transmissão/distribuição aparecem como entidades externas referenciadas nos dados do Anexo A, mas não executam atividades diretas no fluxo normativo descrito; não constituem lanes ativas no processo.

---

## 2. ATIVIDADES

As atividades são listadas por **subprocesso**, na ordem de execução, com indicação do ator responsável.

---

### SUBPROCESSO 0 – Pré-condição: Classificação da Usina (referência ao Submódulo 7.2)

| Seq. | ID | Atividade | Ator |
|------|----|-----------|------|
| 0.1 | A00 | Verificar a classificação da modalidade de operação da usina (Tipo I, II-A, II-B, II-C ou III) e o ponto de conexão (Rede Básica / ICG / DIT ou Rede de Distribuição), conforme Submódulo 7.2 | Agente de Geração |
| 0.2 | A01 | Verificar se há alteração de características técnicas, mudança de ponto de conexão ou alteração de modalidade que implique acréscimo de requisitos (diretriz 1.1) | Agente de Geração |

---

### SUBPROCESSO 1 – Emissão da DIR (Declaração de Inexistência de Relacionamento Operacional)

*Aplicável a: usinas Tipo III conectadas na Rede de Distribuição; produtores independentes e autoprodutores que operem, por tempo determinado, sem injeção de potência no SIN.*

| Seq. | ID | Atividade | Ator |
|------|----|-----------|------|
| 1.1 | A10 | Elaborar e encaminhar ao ONS a solicitação de emissão de DIR, nos formatos, meios e prazos especificados, contendo o Informe e Dados Técnicos (Anexo A) | Agente de Geração |
| 1.2 | A11 | Receber e analisar a solicitação de DIR, verificando a conformidade com o Ato Autorizativo | ONS |
| 1.3 | A12 | *(se conforme)* Elaborar a DIR | ONS |
| 1.4 | A13 | Encaminhar a DIR ao agente de geração | ONS |
| 1.5 | A14 | *(se não conforme)* Informar ao agente a inviabilidade de expedição da DIR e os impedimentos identificados | ONS |

---

### SUBPROCESSO 2 – Emissão da DAPR/T (Declaração de Atendimento para Início da Operação em Teste)

*Aplicável a: usinas Tipo I, Tipo II (A, B ou C) e Tipo III quando conectadas nas DIT.*

| Seq. | ID | Atividade | Ator |
|------|----|-----------|------|
| 2.1 | A20 | Elaborar e encaminhar ao ONS a solicitação de emissão de DAPR/T, nos formatos, meios e prazos estabelecidos, contendo o Informe e Dados Técnicos (Anexo A) | Agente de Geração |
| 2.2 | A21 | Receber e analisar a solicitação de DAPR/T, avaliando o atendimento aos requisitos impeditivos listados no Anexo B | ONS |
| 2.3 | A22 | *(se sem pendências impeditivas)* Elaborar a DAPR/T | ONS |
| 2.4 | A23 | Encaminhar a DAPR/T ao agente de geração | ONS |
| 2.5 | A24 | *(se com pendências impeditivas)* Informar ao agente a inviabilidade de emissão da DAPR/T e os impedimentos identificados | ONS |
| 2.6 | A25 | Suspender o processo de emissão da DAPR/T | ONS |
| 2.7 | A26 | Solucionar as pendências impeditivas identificadas | Agente de Geração |
| 2.8 | A27 | Confirmar ao ONS a solução das pendências impeditivas e encaminhar nova solicitação de DAPR/T via sistema computacional do ONS | Agente de Geração |
| 2.9 | A28 | Reiniciar o processo de emissão da DAPR/T (retorna à atividade A21) | ONS |

---

### SUBPROCESSO 3 – Emissão da DAPR/P (Declaração de Atendimento para Início da Operação Provisória)

*Aplicável a: usinas em operação em teste, após a finalização da fase de testes.*

| Seq. | ID | Atividade | Ator |
|------|----|-----------|------|
| 3.1 | A30 | Após a finalização da fase de testes, elaborar e encaminhar ao ONS a solicitação de emissão de DAPR/P, nos formatos, meios e prazos especificados, contendo o Informe e Dados Técnicos (Anexo A) | Agente de Geração |
| 3.2 | A31 | Receber e analisar a solicitação de DAPR/P, avaliando o atendimento aos requisitos impeditivos listados no Anexo B | ONS |
| 3.3 | A32 | *(se sem pendências impeditivas e sem pendências não impeditivas)* Emitir diretamente a DAPR/D (ver Subprocesso 4) | ONS |
| 3.4 | A33 | *(se sem pendências impeditivas, mas com pendências não impeditivas)* Elaborar a DAPR/P, explicitando: data de atendimento aos requisitos para operação provisória; requisitos não atendidos não impeditivos; adequações necessárias; prazos acordados para solução; eventuais restrições de escoamento da geração | ONS |
| 3.5 | A34 | Encaminhar a DAPR/P ao agente de geração | ONS |
| 3.6 | A35 | *(se com pendências impeditivas)* Informar ao agente a inviabilidade de emissão da DAPR/P e os impedimentos identificados | ONS |
| 3.7 | A36 | Suspender o processo de emissão da DAPR/P | ONS |
| 3.8 | A37 | Solucionar as pendências impeditivas identificadas | Agente de Geração |
| 3.9 | A38 | Confirmar ao ONS a solução das pendências impeditivas e encaminhar nova solicitação de DAPR/P via sistema computacional do ONS | Agente de Geração |
| 3.10 | A39 | Reiniciar o processo de emissão da DAPR/P (retorna à atividade A31) | ONS |
| 3.11 | A40 | *(gestão de pendências não impeditivas – antes do vencimento do prazo)* Formalizar junto ao ONS o atendimento à pendência não impeditiva constante na DAPR/P **OU** solicitar novo prazo, apresentando justificativas para o não atendimento | Agente de Geração |
| 3.12 | A41 | Analisar a justificativa apresentada pelo agente de geração para extensão de prazo | ONS |
| 3.13 | A42 | *(se revalidação aprovada, até 2 vezes)* Revalidar o prazo para atendimento ao requisito | ONS |
| 3.14 | A43 | *(se necessário)* Informar a ANEEL sobre a situação das pendências e prazos | ONS |
| 3.15 | A44 | *(caso especial – usinas Tipo II-C)* Processar solicitação de DAPR/P para mais de um circuito de forma concomitante | ONS |

---

### SUBPROCESSO 4 – Emissão da DAPR/D (Declaração de Atendimento para Início da Operação Definitiva)

*Aplicável a: usinas em operação em teste ou integradas em caráter provisório com pendências não impeditivas já solucionadas.*

| Seq. | ID | Atividade | Ator |
|------|----|-----------|------|
| 4.1 | A50 | Elaborar e encaminhar ao ONS a solicitação de emissão de DAPR/D, nos formatos, meios e prazos especificados, contendo o Informe e Dados Técnicos (Anexo A) | Agente de Geração |
| 4.2 | A51 | Receber e analisar a solicitação de DAPR/D, avaliando o atendimento aos requisitos impeditivos listados no Anexo B | ONS |
| 4.3 | A52 | *(se sem pendências)* Verificar se a emissão da DAPR/D está vinculada à conclusão e integração sem pendências de todas as instalações abrangidas por um mesmo estudo pré-operacional (conforme Submódulo 7.4) | ONS |
| 4.4 | A53 | *(se condição de vínculo atendida)* Elaborar a DAPR/D, explicitando: data de atendimento aos requisitos para operação integrada definitiva ao SIN; eventuais restrições de escoamento | ONS |
| 4.5 | A54 | Encaminhar a DAPR/D ao agente de geração | ONS |
| 4.6 | A55 | *(se com pendências)* Informar ao agente a inviabilidade de emissão da DAPR/D e os impedimentos identificados | ONS |
| 4.7 | A56 | Suspender o processo de emissão da DAPR/D | ONS |
| 4.8 | A57 | Solucionar as pendências identificadas | Agente de Geração |
| 4.9 | A58 | Confirmar ao ONS a solução das pendências e encaminhar nova solicitação de DAPR/D via sistema computacional do ONS | Agente de Geração |
| 4.10 | A59 | Reiniciar o processo de emissão da DAPR/D (retorna à atividade A51) | ONS |

---

## 3. GATEWAYS / DECISÕES

| ID | Gateway | Tipo BPMN | Condição avaliada | Ator que avalia | Saídas possíveis |
|----|---------|-----------|-------------------|-----------------|------------------|
| G00 | Tipo de declaração necessária | Gateway Exclusivo (XOR) | Qual declaração se aplica ao perfil da usina e à fase do processo? | Agente de Geração | → DIR / → DAPR/T / → DAPR/P / → DAPR/D |
| G01 | Usina elegível para DIR? | Gateway Exclusivo (XOR) | A usina é Tipo III na Rede de Distribuição, ou produtor independente/autoprodutor sem injeção no SIN por tempo determinado? | Agente de Geração | Sim → Subprocesso 1; Não → Subprocesso 2 ou 3 ou 4 |
| G02 | Conformidade com Ato Autorizativo (DIR) | Gateway Exclusivo (XOR) | A solicitação de DIR está em conformidade com o Ato Autorizativo? | ONS | Sim → Emitir DIR (A12); Não → Informar inviabilidade (A14) |
| G03 | Existência de pendências impeditivas (DAPR/T) | Gateway Exclusivo (XOR) | Existem requisitos impeditivos não atendidos (Anexo B – coluna DAPR/T)? | ONS | Não → Elaborar DAPR/T (A22); Sim → Informar inviabilidade e suspender (A24, A25) |
| G04 | Solução de pendências impeditivas confirmada (DAPR/T) | Gateway Exclusivo (XOR) | O agente confirmou a solução das pendências e encaminhou nova solicitação? | ONS | Sim → Reiniciar processo DAPR/T (A28); Não → Aguardar |
| G05 | Existência de pendências impeditivas (DAPR/P) | Gateway Exclusivo (XOR) | Existem requisitos impeditivos não atendidos (Anexo B – coluna DAPR/P)? | ONS | Não → G06; Sim → Informar inviabilidade e suspender (A35, A36) |
| G06 | Existência de pendências não impeditivas (DAPR/P) | Gateway Exclusivo (XOR) | Existem requisitos não atendidos que não sejam impeditivos para a operação integrada? | ONS | Sim → Elaborar DAPR/P (A33); Não → Emitir diretamente DAPR/D (A53) |
| G07 | Solução de pendências impeditivas confirmada (DAPR/P) | Gateway Exclusivo (XOR) | O agente confirmou a solução das pendências e encaminhou nova solicitação? | ONS | Sim → Reiniciar processo DAPR/P (A39); Não → Aguardar |
| G08 | Atendimento à pendência não impeditiva (DAPR/P) | Gateway Exclusivo (XOR) | O agente atendeu à pendência não impeditiva antes do vencimento do prazo? | Agente de Geração | Sim → Formalizar atendimento (A40 – via atendimento); Não → Solicitar novo prazo (A40 – via prorrogação) |
| G09 | Revalidação de prazo aprovada pelo ONS (DAPR/P) | Gateway Exclusivo (XOR) | O ONS aprova a extensão do prazo solicitada pelo agente? | ONS | Sim → Revalidar prazo (A42); Não → Informar ANEEL se necessário (A43) |
| G10 | Número de revalidações de prazo atingiu o limite (DAPR/P) | Gateway Exclusivo (XOR) | O agente já solicitou revalidação de prazo 2 vezes? | ONS | Não (< 2 vezes) → Permitir nova solicitação; Sim (= 2 vezes) → Não permitir nova revalidação; informar ANEEL se necessário |
| G11 | Existência de pendências (DAPR/D) | Gateway Exclusivo (XOR) | Existem pendências (impeditivas ou não) não atendidas (Anexo B – coluna DAPR/D)? | ONS | Não → G12; Sim → Informar inviabilidade e suspender (A55, A56) |
| G12 | Vínculo com estudo pré-operacional (DAPR/D) | Gateway Exclusivo (XOR) | A emissão da DAPR/D está vinculada à conclusão de todas as instalações de um mesmo estudo pré-operacional (Submódulo 7.4)? | ONS | Vínculo atendido → Elaborar DAPR/D (A53); Vínculo não atendido → Aguardar conclusão das demais instalações |
| G13 | Solução de pendências confirmada (DAPR/D) | Gateway Exclusivo (XOR) | O agente confirmou a solução das pendências e encaminhou nova solicitação? | ONS | Sim → Reiniciar processo DAPR/D (A59); Não → Aguardar |
| G14 | Usina Tipo II-C – múltiplos circuitos (DAPR/P) | Gateway Paralelo ou Inclusivo | A usina é Tipo II-C e há mais de um circuito a ser integrado concomitantemente? | Agente de Geração / ONS | Sim → Processar DAPR/P para múltiplos circuitos em paralelo (A44); Não → Fluxo padrão |

---

## 4. EVENTOS

### 4.1 Eventos de Início

| ID | Evento | Tipo BPMN | Descrição |
|----|--------|-----------|-----------|
| E01 | Início do Processo Global | Evento de Início (Start Event) – Nenhum | Necessidade de integração de instalação de geração ao SIN (nova usina, alteração de características técnicas, mudança de ponto de conexão ou alteração de modalidade com acréscimo de requisitos – diretriz 1.1) |
| E02 | Início do Subprocesso DIR | Evento de Início de Subprocesso | Agente identifica que a usina se enquadra nos critérios de DIR (Tipo III / Rede de Distribuição / sem injeção no SIN) |
| E03 | Início do Subprocesso DAPR/T | Evento de Início de Subprocesso | Agente identifica que a usina requer DAPR/T (Tipo I, II ou III/DIT) e está pronta para solicitar início de operação em teste |
| E04 | Início do Subprocesso DAPR/P | Evento de Início de Subprocesso | Finalização da fase de testes da usina; agente pronto para solicitar operação provisória |
| E05 | Início do Subprocesso DAPR/D | Evento de Início de Subprocesso | Usina em operação em teste ou provisória com pendências não impeditivas solucionadas; agente pronto para solicitar operação definitiva |

### 4.2 Eventos Intermediários

| ID | Evento | Tipo BPMN | Descrição |
|----|--------|-----------|-----------|
| EI01 | Recebimento da solicitação de DIR pelo ONS | Evento Intermediário de Mensagem (Catch) | ONS recebe o Informe e Dados Técnicos (Anexo A) para DIR |
| EI02 | Recebimento da solicitação de DAPR/T pelo ONS | Evento Intermediário de Mensagem (Catch) | ONS recebe o Informe e Dados Técnicos (Anexo A) para DAPR/T |
| EI03 | Suspensão do processo DAPR/T | Evento Intermediário de Temporização / Sinal | ONS suspende o processo após identificar pendências impeditivas |
| EI04 | Confirmação de solução de pendências DAPR/T pelo agente | Evento Intermediário de Mensagem (Catch) | ONS recebe confirmação do agente e nova solicitação via sistema computacional |
| EI05 | Recebimento da solicitação de DAPR/P pelo ONS | Evento Intermediário de Mensagem (Catch) | ONS recebe o Informe e Dados Técnicos (Anexo A) para DAPR/P após finalização dos testes |
| EI06 | Suspensão do processo DAPR/P | Evento Intermediário de Temporização / Sinal | ONS suspende o processo após identificar pendências impeditivas |
| EI07 | Confirmação de solução de pendências DAPR/P pelo agente | Evento Intermediário de Mensagem (Catch) | ONS recebe confirmação do agente e nova solicitação via sistema computacional |
| EI08 | Vencimento do prazo de pendência não impeditiva (DAPR/P) | Evento Intermediário de Temporização (Timer) | Prazo acordado na DAPR/P para solução de pendência não impeditiva se aproxima do vencimento |
| EI09 | Solicitação de extensão de prazo pelo agente (DAPR/P) | Evento Intermediário de Mensagem (Catch) | ONS recebe solicitação de novo prazo com justificativas do agente |
| EI10 | Informação à ANEEL | Evento Intermediário de Mensagem (Throw) | ONS encaminha informação à ANEEL sobre situação de pendências/prazos, se necessário |
| EI11 | Recebimento da solicitação de DAPR/D pelo ONS | Evento Intermediário de Mensagem (Catch) | ONS recebe o Informe e Dados Técnicos (Anexo A) para DAPR/D |
| EI12 | Suspensão do processo DAPR/D | Evento Intermediário de Temporização / Sinal | ONS suspende o processo após identificar pendências |
| EI13 | Confirmação de solução de pendências DAPR/D pelo agente | Evento Intermediário de Mensagem (Catch) | ONS recebe confirmação do agente e nova solicitação via sistema computacional |
| EI14 | Reunião entre agentes e ONS (se necessário) | Evento Intermediário de Sinal | Realização de reunião entre agentes de operação e ONS durante o processo de integração (diretriz 1.2) – pode ocorrer em qualquer ponto do processo |

### 4.3 Eventos de Fim

| ID | Evento | Tipo BPMN | Descrição |
|----|--------|-----------|-----------|
| EF01 | DIR emitida e encaminhada | Evento de Fim (End Event) – Mensagem | ONS encaminha a DIR ao agente; processo de emissão de DIR concluído |
| EF02 | DIR não emitida | Evento de Fim (End Event) – Erro / Terminação | ONS informa inviabilidade de expedição da DIR ao agente; processo encerrado sem emissão |
| EF03 | DAPR/T emitida e encaminhada | Evento de Fim de Subprocesso – Mensagem | ONS encaminha a DAPR/T ao agente; usina autorizada a iniciar operação em teste |
| EF04 | DAPR/P emitida e encaminhada | Evento de Fim de Subprocesso – Mensagem | ONS encaminha a DAPR/P ao agente; usina autorizada a iniciar operação provisória |
| EF05 | DAPR/D emitida e encaminhada (via DAPR/P) | Evento de Fim de Subprocesso – Mensagem | ONS emite diretamente DAPR/D ao constatar ausência de qualquer pendência durante análise de DAPR/P |
| EF06 | DAPR/D emitida e encaminhada (via solicitação direta) | Evento de Fim (End Event) – Mensagem | ONS encaminha a DAPR/D ao agente; usina autorizada a operar de forma integrada definitiva ao SIN |
| EF07 | Processo encerrado sem emissão de DAPR/D | Evento de Fim (End Event) – Erro | ONS informa inviabilidade de emissão da DAPR/D; processo suspenso aguardando solução |

---

## 5. FLUXOS DE EXCEÇÃO

### FE01 – Não emissão da DIR (item 2.3)
- **Gatilho:** ONS identifica que alguma das condições para emissão da DIR não é válida (não conformidade com o Ato Autorizativo).
- **Fluxo:** A11 → G02 (Não) → A14 (ONS informa inviabilidade e impedimentos ao agente) → **EF02** (processo encerrado sem emissão).
- **Observação:** O normativo não prevê ciclo de correção e reenvio para a DIR; o processo é encerrado.

### FE02 – Suspensão e reinício do processo DAPR/T por pendências impeditivas (item 3.1.3 e 3.1.3.1)
- **Gatilho:** ONS identifica pendências impeditivas durante análise da solicitação de DAPR/T.
- **Fluxo:** A21 → G03 (Sim) → A24 (informar inviabilidade) → A25 (suspender processo) → **EI03** (processo suspenso) → A26 (agente soluciona pendências) → A27 (agente confirma solução e encaminha nova solicitação via sistema computacional) → **EI04** → G04 (Sim) → A28 (ONS reinicia processo) → retorna a A21.
- **Observação:** O ciclo pode se repetir quantas vezes forem necessárias até a eliminação de todas as pendências impeditivas.

### FE03 – Suspensão e reinício do processo DAPR/P por pendências impeditivas (item 3.2.4 e 3.2.4.1)
- **Gatilho:** ONS identifica pendências impeditivas durante análise da solicitação de DAPR/P.
- **Fluxo:** A31 → G05 (Sim) → A35 (informar inviabilidade) → A36 (suspender processo) → **EI06** → A37 (agente soluciona pendências) → A38 (agente confirma solução e encaminha nova solicitação via sistema computacional) → **EI07** → G07 (Sim) → A39 (ONS reinicia processo) → retorna a A31.

### FE04 – Emissão direta de DAPR/D durante análise de DAPR/P (item 3.2.5)
- **Gatilho:** ONS verifica que não existem pendências (nem impeditivas nem não impeditivas) para a operação integrada da central geradora durante a análise da solicitação de DAPR/P.
- **Fluxo:** A31 → G05 (Não) → G06 (Não) → A53 (elaborar DAPR/D) → A54 (encaminhar DAPR/D) → **EF05**.
- **Observação:** Neste caso, o subprocesso DAPR/P é suprimido e o processo avança diretamente para a emissão da DAPR/D.

### FE05 – Gestão de pendências não impeditivas e extensão de prazo na DAPR/P (itens 3.2.3.1 e 3.2.3.2)
- **Gatilho:** Vencimento (ou iminência de vencimento) do prazo acordado na DAPR/P para solução de pendência não impeditiva, sem que o agente tenha concluído as adequações.
- **Fluxo:** **EI08** (timer) → G08 (Não atendido) → A40 (agente solicita novo prazo com justificativas) → **EI09** → A41 (ONS analisa justificativa) → G09:
  - **G09 (Sim – revalidação aprovada):** G10 (< 2 vezes) → A42 (ONS revalida prazo) → retorna ao monitoramento do prazo.
  - **G09 (Não – revalidação não aprovada) ou G10 (= 2 vezes – limite atingido):** A43 (ONS informa ANEEL, se necessário).
- **Observação:** O agente pode solicitar revalidação de prazo **até duas vezes** (item 3.2.3.2). Após o atendimento da pendência, o agente formaliza o atendimento junto ao ONS (A40 – via atendimento).

### FE06 – Suspensão e reinício do processo DAPR/D por pendências (item 3.3.2 e 3.3.2.1)
- **Gatilho:** ONS identifica pendências durante análise da solicitação de DAPR/D.
- **Fluxo:** A51 → G11 (Sim) → A55 (informar inviabilidade) → A56 (suspender processo) → **EI12** → A57 (agente soluciona pendências) → A58 (agente confirma solução e encaminha nova solicitação via sistema computacional) → **EI13** → G13 (Sim) → A59 (ONS reinicia processo) → retorna a A51.

### FE07 – Aguardo de conclusão de instalações vinculadas ao mesmo estudo pré-operacional (item 3.3.3.2)
- **Gatilho:** ONS verifica que a emissão da DAPR/D está vinculada à conclusão e integração sem pendências de todas as instalações abrangidas por um mesmo estudo pré-operacional (Submódulo 7.4), e nem todas foram concluídas.
- **Fluxo:** A51 → G11 (Não) → A52 → G12 (Vínculo não atendido) → Aguardar conclusão das demais instalações → retorna a G12 quando todas as instalações estiverem integradas sem pendências → G12 (Vínculo atendido) → A53 → A54 → **EF06**.

### FE08 – Reunião entre agentes e ONS (diretriz 1.2)
- **Gatilho:** ONS ou agente considera necessária a realização de reunião durante o processo de integração.
- **Fluxo:** Evento intermediário **EI14** pode ser inserido em qualquer ponto do processo (DAPR/T, DAPR/P ou DAPR/D), sem interromper o fluxo principal; trata-se de atividade de suporte ao processo.

### FE09 – Tratamento especial para usinas Tipo II-C com múltiplos circuitos (item 3.2.6)
- **Gatilho:** Usina classificada como Tipo II-C solicita DAPR/P para mais de um circuito simultaneamente.
- **Fluxo:** G14 (Sim) → A44 (ONS processa DAPR/P para múltiplos circuitos de forma concomitante) → fluxo padrão de análise e emissão para cada circuito.

---

## 6. FLUXO DE SEQUÊNCIA

O fluxo de sequência completo é descrito abaixo, integrando todos os subprocessos e desvios:

---

### FASE 0 – Determinação do tipo de declaração aplicável

```
[E01 – Início do Processo]
    ↓
[A00 – Verificar classificação da usina e ponto de conexão]
    ↓
[A01 – Verificar se há alteração que implique acréscimo de requisitos]
    ↓
[G00 – Qual declaração se aplica?]
    ├── → DIR  ──────────────────────────────────────────→ FASE 1
    ├── → DAPR/T ────────────────────────────────────────→ FASE 2
    ├── → DAPR/P (usina já em operação em teste) ────────→ FASE 3
    └── → DAPR/D (usina já em operação provisória) ──────→ FASE 4
```

---

### FASE 1 – Emissão da DIR

```
[E02 – Início do Subprocesso DIR]
    ↓
[A10 – Agente elabora e encaminha solicitação de DIR ao ONS (Anexo A)]
    ↓
[EI01 – ONS recebe solicitação de DIR]
    ↓
[A11 – ONS analisa solicitação, verificando conformidade com Ato Autorizativo]
    ↓
[G02 – Conformidade com Ato Autorizativo?]
    ├── SIM →
    │       [A12 – ONS elabora a DIR]
    │           ↓
    │       [A13 – ONS encaminha DIR ao agente]
    │           ↓
    │       [EF01 – DIR emitida e encaminhada ✓]
    │
    └── NÃO →
            [A14 – ONS informa inviabilidade e impedimentos ao agente]
                ↓
            [EF02 – DIR não emitida ✗]
```

---

### FASE 2 – Emissão da DAPR/T

```
[E03 – Início do Subprocesso DAPR/T]
    ↓
[A20 – Agente elabora e encaminha solicitação de DAPR/T ao ONS (Anexo A)]
    ↓
[EI02 – ONS recebe solicitação de DAPR/T]
    ↓
[A21 – ONS analisa solicitação, avaliando requisitos impeditivos (Anexo B – coluna DAPR/T)]
    ↓
[G03 – Existem pendências impeditivas?]
    │
    ├── NÃO →
    │       [A22 – ONS elabora a DAPR/T]
    │           ↓
    │       [A23 – ONS encaminha DAPR/T ao agente]
    │           ↓
    │       [EF03 – DAPR/T emitida ✓ → Usina inicia operação em teste → FASE 3]
    │
    └── SIM →
            [A24 – ONS informa inviabilidade e impedimentos ao agente]
                ↓
            [A25 – ONS suspende o processo de emissão da DAPR/T]
                ↓
            [EI03 – Processo suspenso]
                ↓
            [A26 – Agente soluciona pendências impeditivas]
                ↓
            [A27 – Agente confirma solução e encaminha nova solicitação via sistema computacional do ONS]
                ↓
            [EI04 – ONS recebe confirmação e nova solicitação]
                ↓
            [G04 – Confirmação recebida?]
                ├── SIM → [A28 – ONS reinicia processo] → retorna a [A21] ↺
                └── NÃO → Aguardar ↺
```

---

### FASE 3 – Emissão da DAPR/P

```
[E04 – Início do Subprocesso DAPR/P]
(Pré-condição: usina em operação em teste; fase de testes finalizada)
    ↓
[G14 – Usina Tipo II-C com múltiplos circuitos concomitantes?]
    ├── SIM → [A44 – Processar DAPR/P para múltiplos circuitos concomitantemente]
    │              ↓ (fluxo paralelo por circuito, cada um segue o fluxo abaixo)
    └── NÃO → (fluxo padrão)
    ↓
[A30 – Agente elabora e encaminha solicitação de DAPR/P ao ONS (Anexo A)]
    ↓
[EI05 – ONS recebe solicitação de DAPR/P]
    ↓
[A31 – ONS analisa solicitação, avaliando requisitos impeditivos (Anexo B – coluna DAPR/P)]
    ↓
[G05 – Existem pendências impeditivas?]
    │
    ├── SIM →
    │       [A35 – ONS informa inviabilidade e impedimentos ao agente]
    │           ↓
    │       [A36 – ONS suspende o processo de emissão da DAPR/P]
    │           ↓
    │       [EI06 – Processo suspenso]
    │           ↓
    │       [A37 – Agente soluciona pendências impeditivas]
    │           ↓
    │       [A38 – Agente confirma solução e encaminha nova solicitação via sistema computacional do ONS]
    │           ↓
    │       [EI07 – ONS recebe confirmação e nova solicitação]
    │           ↓
    │       [G07 – Confirmação recebida?]
    │           ├── SIM → [A39 – ONS reinicia processo] → retorna a [A31] ↺
    │           └── NÃO → Aguardar ↺
    │
    └── NÃO →
            [G06 – Existem pendências não impeditivas?]
                │
                ├── NÃO → (nenhuma pendência)
                │       [A53 – ONS elabora DAPR/D diretamente]
                │           ↓
                │       [A54 – ONS encaminha DAPR/D ao agente]
                │           ↓
                │       [EF05 – DAPR/D emitida diretamente ✓] ← FE04
                │
                └── SIM → (pendências não impeditivas existem)
                        [A33 – ONS elabora DAPR/P com:
                               - data de atendimento aos requisitos para operação provisória
                               - requisitos não atendidos não impeditivos
                               - adequações necessárias e prazos acordados
                               - eventuais restrições de escoamento]
                            ↓
                        [A34 – ONS encaminha DAPR/P ao agente]
                            ↓
                        [EF04 – DAPR/P emitida ✓ → Usina inicia operação provisória]
                            ↓
                        ┌─────────────────────────────────────────────────────┐
                        │  LOOP DE GESTÃO DE PENDÊNCIAS NÃO IMPEDITIVAS       │
                        │                                                     │
                        │  [EI08 – Timer: vencimento do prazo da pendência]   │
                        │      ↓                                              │
                        │  [G08 – Agente atendeu à pendência?]                │
                        │      ├── SIM →                                      │
                        │      │   [A40 – Agente formaliza atendimento ao ONS]│
                        │      │       ↓                                      │
                        │      │   Pendência encerrada → FASE 4               │
                        │      │                                              │
                        │      └── NÃO →                                      │
                        │          [A40 – Agente solicita novo prazo          │
                        │                com justificativas ao ONS]           │
                        │              ↓                                      │
                        │          [EI09 – ONS recebe solicitação de prazo]   │
                        │              ↓                                      │
                        │          [A41 – ONS analisa justificativa]          │
                        │              ↓                                      │
                        │          [G09 – ONS aprova revalidação?]            │
                        │              ├── SIM →                              │
                        │              │   [G10 – Já solicitou 2 vezes?]      │
                        │              │       ├── NÃO →                      │
                        │              │       │   [A42 – ONS revalida prazo] │
                        │              │       │       ↓ retorna a EI08 ↺     │
                        │              │       └── SIM →                      │
                        │              │           Limite atingido →          │
                        │              │           [A43 – ONS informa ANEEL]  │
                        │              │                                      │
                        │              └── NÃO →                              │
                        │                  [A43 – ONS informa ANEEL          │
                        │                         se necessário]              │
                        └─────────────────────────────────────────────────────┘
                            ↓ (após solução de todas as pendências não impeditivas)
                        FASE 4
```

---

### FASE 4 – Emissão da DAPR/D

```
[E05 – Início do Subprocesso DAPR/D]
(Pré-condição: usina em operação em teste OU em operação provisória com pendências não impeditivas solucionadas)
    ↓
[A50 – Agente elabora e encaminha solicitação de DAPR/D ao ONS (Anexo A)]
    ↓
[EI11 – ONS recebe solicitação de DAPR/D]
    ↓
[A51 – ONS analisa solicitação, avaliando requisitos impeditivos (Anexo B – coluna DAPR/D)]
    ↓
[G11 – Existem pendências?]
    │
    ├── SIM →
    │       [A55 – ONS informa inviabilidade e impedimentos ao agente]
    │           ↓
    │       [A56 – ONS suspende o processo de emissão da DAPR/D]
    │           ↓
    │       [EI12 – Processo suspenso]
    │           ↓
    │       [A57 – Agente soluciona pendências]
    │           ↓
    │       [A58 – Agente confirma solução e encaminha nova solicitação via sistema computacional do ONS]
    │           ↓
    │       [EI13 – ONS recebe confirmação e nova solicitação]
    │           ↓
    │       [G13 – Confirmação recebida?]
    │           ├── SIM → [A59 – ONS reinicia processo] → retorna a [A51] ↺
    │           └── NÃO → Aguardar ↺
    │
    └── NÃO → (sem pendências)
            [A52 – ONS verifica vínculo com estudo pré-operacional (Submódulo 7.4)]
                ↓
            [G12 – Vínculo com estudo pré-operacional atendido?
                   (todas as instalações do mesmo estudo integradas sem pendências)]
                ├── NÃO → Aguardar conclusão das demais instalações ↺ → retorna a G12
                │
                └── SIM →
                        [A53 – ONS elabora DAPR/D com:
                               - data de atendimento aos requisitos para operação integrada definitiva
                               - eventuais restrições de escoamento]
                            ↓
                        [A54 – ONS encaminha DAPR/D ao agente de geração]
                            ↓
                        [EF06 – DAPR/D emitida e encaminhada ✓]
                            ↓
                        [Fim do Processo Global]
```

---

### VISÃO CONSOLIDADA DO FLUXO PRINCIPAL (Caminho Feliz)

```
E01 → A00 → A01 → G00
                    │
         ┌──────────┼──────────────────────────────────┐
         ↓          ↓                                  ↓
      [DIR]      [DAPR/T]                          [DAPR/D]
      A10→A11    A20→A21→A22→A23→EF03              (direto)
      →G02→A12   (usina em teste)
      →A13→EF01       ↓
                  [DAPR/P]
                  A30→A31→G05→G06→A33→A34→EF04
                  (usina em operação provisória)
                  Gestão de pendências não impeditivas
                       ↓
                  [DAPR/D]
                  A50→A51→G11→A52→G12→A53→A54→EF06
                  (operação definitiva)
```

---

## NOTAS FINAIS DE MODELAGEM

| # | Nota |
|---|------|
| 1 | O **Anexo A** (Informe e Dados Técnicos) é o documento que acompanha **todas** as solicitações (DIR, DAPR/T, DAPR/P e DAPR/D); sua elaboração está incorporada nas atividades A10, A20, A30 e A50. |
| 2 | O **Anexo B** (Requisitos Impeditivos) é a base de análise do ONS para DAPR/T, DAPR/P e DAPR/D; sua consulta está incorporada nas atividades A21, A31 e A51. |
| 3 | A **suspensão e reinício** do processo (FE02, FE03, FE06) é um padrão recorrente nos três subprocessos DAPR; o mecanismo é idêntico: ONS suspende → agente soluciona → agente confirma via sistema computacional → ONS reinicia. |
| 4 | A **revalidação de prazo** para pendências não impeditivas (FE05) é exclusiva da DAPR/P e limitada a **duas solicitações** pelo agente. |
| 5 | A **emissão direta de DAPR/D** durante a análise de DAPR/P (FE04) é um atalho normativo que elimina a fase de operação provisória quando não há nenhuma pendência. |
| 6 | O **vínculo com o estudo pré-operacional** (G12) é uma condição de espera que pode atrasar a emissão da DAPR/D mesmo quando a usina solicitante não tem pendências próprias. |
| 7 | A **ANEEL** (L3) é acionada apenas como destinatária de informações do ONS (EI10/A43), não executando atividades ativas no fluxo do processo. |
| 8 | O processo para **usinas Tipo II-C** com múltiplos circuitos (G14/A44) representa um fluxo paralelo dentro do subprocesso DAPR/P, onde cada circuito segue o fluxo padrão de análise. |