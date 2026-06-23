# MODELO DE PROCESSO DE NEGÓCIO EM BPMN
## Emissão de Declarações de Atendimento (DIR, DAPR/T, DAPR/P, DAPR/D)
### Submódulo 7.13 – Procedimentos de Rede do ONS

---

## 1. RAIAS (POOLS/LANES)

| # | Ator | Descrição |
|---|------|-----------|
| 1 | **Agente de Geração** | Responsável pela usina; encaminha solicitações e documentação ao ONS |
| 2 | **ONS (Operador Nacional do Sistema)** | Analisa solicitações, valida requisitos impeditivos, emite declarações |
| 3 | **ANEEL** | Informada em casos de revalidação de prazos (DAPR/P) |
| 4 | **Sistema Computacional do ONS** | Gerencia intervenções (SGI) e recebe novas solicitações |

---

## 2. ATIVIDADES (NA ORDEM)

### **FLUXO 1: DECLARAÇÃO DE INEXISTÊNCIA DE RELACIONAMENTO (DIR)**

| # | Atividade | Ator | Descrição |
|---|-----------|------|-----------|
| 1.1 | Classificar modalidade de operação | Agente | Usina Tipo III em Rede de Distribuição OU Produtor Independente/Autoprodutor sem injeção no SIN |
| 1.2 | Preparar solicitação DIR | Agente | Preencher ANEXO A com dados técnicos e declaração |
| 1.3 | Encaminhar solicitação DIR ao ONS | Agente | Enviar nos formatos, meios e prazos especificados |
| 1.4 | Receber solicitação DIR | ONS | Protocolar e registrar entrada |
| 1.5 | Analisar conformidade com Ato Autorizativo | ONS | Validar condições de inexistência de relacionamento |
| 1.6 | **[GATEWAY]** Conformidade validada? | ONS | Decisão: SIM → 1.7 / NÃO → 1.8 |
| 1.7 | Elaborar e emitir DIR | ONS | Gerar declaração formal |
| 1.8 | Informar inviabilidade de DIR | ONS | Comunicar impedimentos ao agente |
| 1.9 | Encaminhar DIR ao agente | ONS | Enviar declaração emitida |
| 1.10 | Receber DIR | Agente | Protocolar declaração |

---

### **FLUXO 2: DECLARAÇÃO DE ATENDIMENTO PARA OPERAÇÃO EM TESTE (DAPR/T)**

| # | Atividade | Ator | Descrição |
|---|-----------|------|-----------|
| 2.1 | Classificar modalidade de operação | Agente | Usina Tipo I, II ou III (conectada em DIT) |
| 2.2 | Preparar solicitação DAPR/T | Agente | Preencher ANEXO A com dados técnicos e declaração |
| 2.3 | Encaminhar solicitação DAPR/T ao ONS | Agente | Enviar nos formatos, meios e prazos estabelecidos |
| 2.4 | Receber solicitação DAPR/T | ONS | Protocolar e registrar entrada |
| 2.5 | Avaliar requisitos impeditivos (ANEXO B) | ONS | Verificar conformidade com todos os requisitos impeditivos para DAPR/T |
| 2.6 | **[GATEWAY]** Existem pendências impeditivas? | ONS | Decisão: SIM → 2.7 / NÃO → 2.8 |
| 2.7 | Informar inviabilidade de DAPR/T | ONS | Comunicar impedimentos e motivos ao agente |
| 2.8 | Elaborar DAPR/T | ONS | Gerar declaração formal |
| 2.9 | Encaminhar DAPR/T ao agente | ONS | Enviar declaração emitida |
| 2.10 | Receber DAPR/T | Agente | Protocolar declaração |
| 2.11 | **[EVENTO INTERMEDIÁRIO]** Suspensão do processo | ONS | Processo suspenso até confirmação de solução de pendências |
| 2.12 | Confirmar solução de pendências | Agente | Formalizar resolução das pendências impeditivas |
| 2.13 | Encaminhar nova solicitação DAPR/T | Agente | Submeter via sistema computacional do ONS (reinício) |
| 2.14 | Retornar à atividade 2.4 | ONS | Reiniciar análise |

---

### **FLUXO 3: DECLARAÇÃO DE ATENDIMENTO PARA OPERAÇÃO PROVISÓRIA (DAPR/P)**

| # | Atividade | Ator | Descrição |
|---|-----------|------|-----------|
| 3.1 | Finalizar fase de testes | Agente | Completar operação em teste |
| 3.2 | Preparar solicitação DAPR/P | Agente | Preencher ANEXO A com dados técnicos e declaração |
| 3.3 | Encaminhar solicitação DAPR/P ao ONS | Agente | Enviar nos formatos, meios e prazos especificados |
| 3.4 | Receber solicitação DAPR/P | ONS | Protocolar e registrar entrada |
| 3.5 | Avaliar requisitos impeditivos (ANEXO B) | ONS | Verificar conformidade com todos os requisitos impeditivos para DAPR/P |
| 3.6 | **[GATEWAY]** Existem pendências impeditivas? | ONS | Decisão: SIM → 3.7 / NÃO → 3.8 |
| 3.7 | Informar inviabilidade de DAPR/P | ONS | Comunicar impedimentos ao agente |
| 3.8 | **[GATEWAY]** Existem pendências NÃO impeditivas? | ONS | Decisão: SIM → 3.9 / NÃO → 3.15 |
| 3.9 | Elaborar DAPR/P com pendências não impeditivas | ONS | Gerar declaração com: data de atendimento, requisitos não atendidos, adequações necessárias, prazos acordados, restrições de escoamento |
| 3.10 | Encaminhar DAPR/P ao agente | ONS | Enviar declaração emitida |
| 3.11 | Receber DAPR/P | Agente | Protocolar declaração |
| 3.12 | **[EVENTO INTERMEDIÁRIO]** Até vencimento do prazo | Agente | Monitorar prazos das pendências não impeditivas |
| 3.13 | **[GATEWAY]** Pendência atendida ou extensão solicitada? | Agente | Decisão: ATENDIDA → 3.14 / EXTENSÃO → 3.16 |
| 3.14 | Formalizar atendimento da pendência | Agente | Comunicar conclusão ao ONS |
| 3.15 | Emitir diretamente DAPR/D | ONS | Sem pendências não impeditivas, emitir DAPR/D (ver Fluxo 4) |
| 3.16 | Solicitar revalidação de prazo | Agente | Apresentar justificativas para não atendimento (máx. 2 revalidações) |
| 3.17 | Analisar justificativa | ONS | Avaliar solicitação de extensão |
| 3.18 | **[GATEWAY]** Prazo revalidado? | ONS | Decisão: SIM → 3.19 / NÃO → 3.20 |
| 3.19 | Informar revalidação de prazo | ONS | Comunicar novo prazo ao agente; informar ANEEL se necessário |
| 3.20 | Informar rejeição de extensão | ONS | Comunicar não revalidação ao agente |
| 3.21 | **[EVENTO INTERMEDIÁRIO]** Suspensão do processo | ONS | Processo suspenso até confirmação de solução de pendências impeditivas |
| 3.22 | Confirmar solução de pendências impeditivas | Agente | Formalizar resolução |
| 3.23 | Encaminhar nova solicitação DAPR/P | Agente | Submeter via sistema computacional do ONS (reinício) |
| 3.24 | Retornar à atividade 3.4 | ONS | Reiniciar análise |

---

### **FLUXO 4: DECLARAÇÃO DE ATENDIMENTO PARA OPERAÇÃO DEFINITIVA (DAPR/D)**

| # | Atividade | Ator | Descrição |
|---|-----------|------|-----------|
| 4.1 | Estar em operação em teste OU provisória com pendências não impeditivas resolvidas | Agente | Pré-condição: DAPR/T ou DAPR/P emitida |
| 4.2 | Preparar solicitação DAPR/D | Agente | Preencher ANEXO A com dados técnicos e declaração |
| 4.3 | Encaminhar solicitação DAPR/D ao ONS | Agente | Enviar nos formatos, meios e prazos especificados |
| 4.4 | Receber solicitação DAPR/D | ONS | Protocolar e registrar entrada |
| 4.5 | Avaliar requisitos impeditivos (ANEXO B) | ONS | Verificar conformidade com todos os requisitos impeditivos para DAPR/D |
| 4.6 | **[GATEWAY]** Existem pendências impeditivas? | ONS | Decisão: SIM → 4.7 / NÃO → 4.8 |
| 4.7 | Informar inviabilidade de DAPR/D | ONS | Comunicar impedimentos ao agente |
| 4.8 | **[GATEWAY]** Empreendimento em condições de operar integrado ao SIN sem pendências? | ONS | Decisão: SIM → 4.9 / NÃO → 4.7 |
| 4.9 | Elaborar DAPR/D | ONS | Gerar declaração formal com: data de atendimento aos requisitos, restrições de escoamento (se houver) |
| 4.10 | **[GATEWAY]** Todas as instalações de um mesmo estudo pré-operacional integradas sem pendências? | ONS | Decisão conforme Submódulo 7.4: SIM → 4.11 / NÃO → AGUARDAR |
| 4.11 | Encaminhar DAPR/D ao agente | ONS | Enviar declaração emitida |
| 4.12 | Receber DAPR/D | Agente | Protocolar declaração |
| 4.13 | **[EVENTO INTERMEDIÁRIO]** Suspensão do processo | ONS | Processo suspenso até confirmação de solução de pendências impeditivas |
| 4.14 | Confirmar solução de pendências impeditivas | Agente | Formalizar resolução |
| 4.15 | Encaminhar nova solicitação DAPR/D | Agente | Submeter via sistema computacional do ONS (reinício) |
| 4.16 | Retornar à atividade 4.4 | ONS | Reiniciar análise |

---

## 3. GATEWAYS / DECISÕES

| # | Gateway | Condição | Fluxo SIM | Fluxo NÃO |
|---|---------|----------|----------|-----------|
| G1 | Conformidade com Ato Autorizativo (DIR)? | Validação de condições de inexistência de relacionamento | Emitir DIR | Informar inviabilidade |
| G2 | Existem pendências impeditivas (DAPR/T)? | Avaliação de requisitos impeditivos ANEXO B | Informar inviabilidade + Suspender | Elaborar DAPR/T |
| G3 | Existem pendências impeditivas (DAPR/P)? | Avaliação de requisitos impeditivos ANEXO B | Informar inviabilidade + Suspender | Prosseguir para G4 |
| G4 | Existem pendências NÃO impeditivas (DAPR/P)? | Avaliação de requisitos não impeditivos | Elaborar DAPR/P com prazos | Emitir diretamente DAPR/D |
| G5 | Pendência atendida ou extensão solicitada (DAPR/P)? | Monitoramento de prazos | Formalizar atendimento | Solicitar revalidação |
| G6 | Prazo revalidado (DAPR/P)? | Análise de justificativa (máx. 2 vezes) | Informar novo prazo | Informar rejeição |
| G7 | Existem pendências impeditivas (DAPR/D)? | Avaliação de requisitos impeditivos ANEXO B | Informar inviabilidade + Suspender | Prosseguir para G8 |
| G8 | Empreendimento em condições de operar integrado sem pendências (DAPR/D)? | Validação final de conformidade | Elaborar DAPR/D | Informar inviabilidade |
| G9 | Todas as instalações de estudo pré-operacional integradas sem pendências (DAPR/D)? | Verificação conforme Submódulo 7.4 | Encaminhar DAPR/D | Aguardar integração de outras instalações |

---

## 4. EVENTOS

### **Eventos de Início**
- **E1 (DIR):** Agente de Geração inicia processo de solicitação de DIR (usina Tipo III em RD ou PI/AP sem injeção)
- **E2 (DAPR/T):** Agente de Geração inicia processo de solicitação de DAPR/T (usina Tipo I, II ou III em DIT)
- **E3 (DAPR/P):** Agente de Geração finaliza testes e inicia processo de solicitação de DAPR/P
- **E4 (DAPR/D):** Agente de Geração inicia processo de solicitação de DAPR/D (após DAPR/T ou DAPR/P)

### **Eventos de Fim**
- **E5 (DIR Emitida):** ONS encaminha DIR ao agente; processo encerrado com sucesso
- **E6 (DIR Não Emitida):** ONS informa inviabilidade; processo encerrado sem sucesso
- **E7 (DAPR/T Emitida):** ONS encaminha DAPR/T ao agente; processo encerrado com sucesso
- **E8 (DAPR/T Não Emitida):** ONS informa inviabilidade; processo suspenso
- **E9 (DAPR/P Emitida):** ONS encaminha DAPR/P ao agente com prazos; processo em andamento
- **E10 (DAPR/P Não Emitida):** ONS informa inviabilidade; processo suspenso
- **E11 (DAPR/D Emitida):** ONS encaminha DAPR/D ao agente; processo encerrado com sucesso
- **E12 (DAPR/D Não Emitida):** ONS informa inviabilidade; processo suspenso

### **Eventos Intermediários**
- **E13 (Suspensão de Processo):** Processo suspenso por pendências impeditivas (DAPR/T, DAPR/P, DAPR/D)
- **E14 (Reinício de Processo):** Agente confirma solução de pendências e resubmete solicitação via sistema computacional do ONS
- **E15 (Vencimento de Prazo):** Prazo de pendência não impeditiva (DAPR/P) vence
- **E16 (Revalidação de Prazo):** Agente solicita extensão de prazo (máx. 2 vezes)
- **E17 (Informação à ANEEL):** ONS informa ANEEL sobre revalidação de prazo (se necessário)
- **E18 (Emissão Direta de DAPR/D):** ONS emite DAPR/D diretamente após DAPR/P (sem pendências não impeditivas)
- **E19 (Aguardamento de Integração):** DAPR/D aguarda integração de todas as instalações de estudo pré-operacional (Submódulo 7.4)

---

## 5. FLUXOS DE EXCEÇÃO

### **Fluxo de Exceção 1: Não Emissão de DIR**
```
Agente encaminha solicitação DIR 
  → ONS analisa conformidade com Ato Autorizativo
    → [CONDIÇÃO NÃO ATENDIDA]
      → ONS informa inviabilidade de DIR
      → ONS comunica impedimentos específicos
      → Processo encerrado SEM sucesso
      → Agente pode corrigir condições e resubmeter
```

### **Fluxo de Exceção 2: Suspensão e Reinício de DAPR/T**
```
Agente encaminha solicitação DAPR/T
  → ONS avalia requisitos impeditivos (ANEXO B)
    → [PENDÊNCIAS IMPEDITIVAS IDENTIFICADAS]
      → ONS informa inviabilidade de DAPR/T
      → ONS comunica impedimentos específicos
      → **PROCESSO SUSPENSO**
      → Agente resolve pendências impeditivas
      → Agente confirma solução e resubmete via sistema computacional
      → ONS reinicia análise (volta à atividade 2.4)
```

### **Fluxo de Exceção 3: Suspensão e Reinício de DAPR/P**
```
Agente encaminha solicitação DAPR/P
  → ONS avalia requisitos impeditivos (ANEXO B)
    → [PENDÊNCIAS IMPEDITIVAS IDENTIFICADAS]
      → ONS informa inviabilidade de DAPR/P
      → ONS comunica impedimentos específicos
      → **PROCESSO SUSPENSO**
      → Agente resolve pendências impeditivas
      → Agente confirma solução e resubmete via sistema computacional
      → ONS reinicia análise (volta à atividade 3.4)
```

### **Fluxo de Exceção 4: Revalidação de Prazo (DAPR/P)**
```
DAPR/P emitida com pendências não impeditivas
  → Prazo de pendência vence
    → [PENDÊNCIA NÃO ATENDIDA]
      → Agente solicita revalidação de prazo
      → Agente apresenta justificativas
      → ONS analisa justificativa
        → [REVALIDAÇÃO APROVADA] (máx. 2 vezes)
          → ONS informa novo prazo
          → ONS informa ANEEL (se necessário)
          → Processo continua com novo prazo
        → [REVALIDAÇÃO REJEITADA]
          → ONS informa rejeição
          → Agente deve atender pendência ou solicitar nova revalidação (até 2 vezes)
```

### **Fluxo de Exceção 5: Emissão Direta de DAPR/D após DAPR/P**
```
Agente encaminha solicitação DAPR/P
  → ONS avalia requisitos impeditivos (ANEXO B)
    → [SEM PENDÊNCIAS IMPEDITIVAS]
      → ONS verifica pendências não impeditivas
        → [SEM PENDÊNCIAS NÃO IMPEDITIVAS]
          → **ONS EMITE DIRETAMENTE DAPR/D**
          → Pula etapa de DAPR/P com prazos
          → Processo avança para operação definitiva
```

### **Fluxo de Exceção 6: Suspensão e Reinício de DAPR/D**
```
Agente encaminha solicitação DAPR/D
  → ONS avalia requisitos impeditivos (ANEXO B)
    → [PENDÊNCIAS IMPEDITIVAS IDENTIFICADAS]
      → ONS informa inviabilidade de DAPR/D
      → ONS comunica impedimentos específicos
      → **PROCESSO SUSPENSO**
      → Agente resolve pendências impeditivas
      → Agente confirma solução e resubmete via sistema computacional
      → ONS reinicia análise (volta à atividade 4.4)
```

### **Fluxo de Exceção 7: Aguardamento de Integração Pré-Operacional (DAPR/D)**
```
Agente encaminha solicitação DAPR/P ou DAPR/D
  → ONS avalia requisitos impeditivos
    → [SEM PENDÊNCIAS IMPEDITIVAS]
      → ONS verifica se todas as instalações de um mesmo estudo pré-operacional 
        estão integradas sem pendências (conforme Submódulo 7.4)
        → [NEM TODAS INTEGRADAS]
          → **PROCESSO AGUARDA INTEGRAÇÃO DE OUTRAS INSTALAÇÕES**
          → DAPR/D não é emitida até conclusão de todas as instalações
        → [TODAS INTEGRADAS]
          → ONS emite DAPR/D
```

### **Fluxo de Exceção 8: Reuniões Operacionais (Opcional)**
```
Durante processo de integração
  → [CONSIDERADO NECESSÁRIO]
    → ONS pode convocar reuniões entre agentes de operação envolvidos
    → Discussão de requisitos, pendências, prazos
    → Processo continua após reunião
```

### **Fluxo de Exceção 9: Múltiplos Circuitos (DAPR/P para Usinas Tipo II-C)**
```
Agente de usina Tipo II-C solicita DAPR/P
  → [MÚLTIPLOS CIRCUITOS]
    → Agente pode solicitar DAPR/P para mais de um circuito de forma concomitante
    → ONS analisa cada circuito conforme requisitos impeditivos
    → Cada circuito pode ter DAPR/P emitida independentemente
```

---

## 6. FLUXO DE SEQUÊNCIA

### **SEQUÊNCIA GERAL DO PROCESSO**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    INÍCIO: AGENTE CLASSIFICA MODALIDADE                      │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
                    ┌─────────────────┼─────────────────┐
                    │                 │                 │
            ┌───────▼────────┐  ┌────▼────────┐  ┌────▼────────┐
            │  Tipo III em   │  │ Tipo I, II  │  │ Tipo I, II  │
            │  RD ou PI/AP   │  │ ou III em   │  │ ou III em   │
            │  sem injeção   │  │ DIT (Teste) │  │ DIT (Prov.) │
            └────────────────┘  └─────────────┘  └─────────────┘
                    │                 │                 │
                    │                 │                 │
            ┌───────▼────────┐  ┌────▼────────┐  ┌────▼────────┐
            │   FLUXO DIR    │  │ FLUXO DAPR/T│  │ FLUXO DAPR/P│
            └────────────────┘  └─────────────┘  └─────────────┘
                    │                 │                 │
                    │                 │                 │
            ┌───────▼────────────────────────────────────▼────────┐
            │  Agente prepara solicitação (ANEXO A)               │
            │  Encaminha ao ONS (formatos, meios, prazos)         │
            └────────────────────────────────────────────────────┘
                                      │
            ┌─────────────────────────▼─────────────────────────┐
            │  ONS recebe e protocola solicitação               │
            └────────────────────────────────────────────────────┘
                                      │
            ┌─────────────────────────▼─────────────────────────┐
            │  ONS avalia requisitos impeditivos (ANEXO B)      │
            └────────────────────────────────────────────────────┘
                                      │
                    ┌─────────────────┼─────────────────┐
                    │                 │                 │
            ┌───────▼────────┐  ┌────▼────────┐  ┌────▼────────┐
            │ Pendências     │  │ Sem         │  │ Sem          │
            │ Impeditivas?   │  │ Pendências? │  │ Pendências   │
            │ (DIR, DAPR/T)  │  │ (DAPR/T)    │  │ Impeditivas? │
            │                │  │             │  │ (DAPR/P)     │
            └────────────────┘  └─────────────┘  └──────────────┘
                    │                 │                 │
            ┌───────▼────────┐  ┌────▼────────┐  ┌────▼────────┐
            │ Informar       │  │ Elaborar    │  │ Existem      │
            │ Inviabilidade  │  │ Declaração  │  │ Pendências   │
            │ + Suspender    │  │ + Encaminhar│  │ Não Impedit? │
            └────────────────┘  └─────────────┘  └──────────────┘
                    │                 │                 │
                    │                 │         ┌───────┴────────┐
                    │                 │         │                │
                    │                 │    ┌────▼────────┐  ┌───▼────────┐
                    │                 │    │ SIM: Emitir │  │ NÃO: Emitir│
                    │                 │    │ DAPR/P com  │  │ DAPR/D     │
                    │                 │    │ prazos      │  │ diretamente│
                    │                 │    └─────────────┘  └────────────┘
                    │                 │         │                │
                    │                 │    ┌────▼────────────────▼────┐
                    │                 │    │ Encaminhar ao Agente     │
                    │                 │    └──────────────────────────┘
                    │                 │         │
                    │                 │    ┌────▼────────────────────┐
                    │                 │    │ Agente recebe           │
                    │                 │    │ Monitora prazos (DAPR/P)│
                    │                 │    └──────────────────────────┘
                    │                 │         │
                    │                 │    ┌────▼────────────────────┐
                    │                 │    │ Até vencimento prazo:   │
                    │                 │    │ Atender ou Solicitar    │
                    │                 │    │ Revalidação (máx. 2x)   │
                    │                 │    └──────────────────────────┘
                    │                 │         │
                    │                 │    ┌────▼────────────────────┐
                    │                 │    │ Formalizar atendimento  │
                    │                 │    │ ou Revalidação aprovada │
                    │                 │    └──────────────────────────┘
                    │                 │         │
                    │                 │    ┌────▼────────────────────┐
                    │                 │    │ Solicitar DAPR/D        │
                    │                 │    └──────────────────────────┘
                    │                 │         │
                    │                 └─────────┼─────────────────┐
                    │                           │                 │
                    │                    ┌──────▼──────────────────▼──┐
                    │                    │ ONS avalia requisitos       │
                    │                    │ impeditivos para DAPR/D     │
                    │                    └─────────────────────────────┘
                    │                           │
                    │                    ┌──────▼──────────────────────┐
                    │                    │ Pendências Impeditivas?     │
                    │                    └─────────────────────────────┘
                    │                           │
                    │                    ┌──────┴──────────────────────┐
                    │                    │                             │
                    │            ┌───────▼────────┐          ┌────────▼────┐
                    │            │ SIM: Informar  │          │ NÃO: Todas  │
                    │            │ Inviabilidade  │          │ instalações │
                    │            │ + Suspender    │          │ integradas? │
                    │            └────────────────┘          └─────────────┘
                    │                    │                           │
                    │                    │                    ┌──────┴──────┐
                    │                    │                    │             │
                    │                    │            ┌───────▼────┐  ┌────▼────┐
                    │                    │            │ SIM: Emitir│  │ NÃO:    │
                    │                    │            │ DAPR/D     │  │ Aguardar│
                    │                    │            └────────────┘  └─────────┘
                    │                    │                    │             │
                    │                    │            ┌───────▼─────────────▼──┐
                    │                    │            │ Encaminhar DAPR/D      │
                    │                    │            │ ao Agente              │
                    │                    │            └────────────────────────┘
                    │                    │                    │
                    │                    │            ┌───────▼─────────────────┐
                    │                    │            │ Agente recebe DAPR/D    │
                    │                    │            │ Operação Definitiva     │
                    │                    │            │ Iniciada                │
                    │                    │            └────────────────────────┘
                    │                    │                    │
                    │                    │                    │
                    └────────────────────┴────────────────────┴──────────────┐
                                                                              │
                                    ┌─────────────────────────────────────────▼──┐
                                    │ FLUXO DE EXCEÇÃO: SUSPENSÃO E REINÍCIO    │
                                    │ Agente confirma solução de pendências      │
                                    │ Resubmete solicitação via sistema ONS      │
                                    │ Processo reinicia (volta à análise)        │
                                    └──────────────────────────────────────────┘
                                                      │
                                    ┌─────────────────▼──────────────────────┐
                                    │ FIM: Declaração Emitida com Sucesso    │
                                    │ ou Processo Encerrado sem Sucesso      │
                                    └────────────────────────────────────────┘
```

---

### **SEQUÊNCIA DETALHADA POR TIPO DE DECLARAÇÃO**

#### **SEQUÊNCIA DIR (Declaração de Inexistência de Relacionamento)**
```
1. Agente classifica usina como Tipo III em RD OU PI/AP sem injeção
2. Agente prepara solicitação DIR (ANEXO A)
3. Agente encaminha ao ONS (formatos, meios, prazos especificados)
4. ONS recebe e protocola
5. ONS analisa conformidade com Ato Autorizativo
   ├─ SIM: Elabora DIR → Encaminha ao Agente → FIM (Sucesso)
   └─ NÃO: Informa inviabilidade → FIM (Sem Sucesso)
```

#### **SEQUÊNCIA DAPR/T (Operação em Teste)**
```
1. Agente classifica usina como Tipo I, II ou III em DIT
2. Agente prepara solicitação DAPR/T (ANEXO A)
3. Agente encaminha ao ONS (formatos, meios, prazos estabelecidos)
4. ONS recebe e protocola
5. ONS avalia requisitos impeditivos (ANEXO B para DAPR/T)
   ├─ Pendências Impeditivas Encontradas:
   │  ├─ ONS informa inviabilidade
   │  ├─ ONS comunica impedimentos
   │  ├─ PROCESSO SUSPENSO
   │  ├─ Agente resolve pendências
   │  ├─ Agente resubmete via sistema ONS
   │  └─ Volta ao passo 4 (Reinício)
   └─ Sem Pendências Impeditivas:
      ├─ ONS elabora DAPR/T
      ├─ ONS encaminha ao Agente
      └─ FIM (Sucesso)
```

#### **SEQUÊNCIA DAPR/P (Operação Provisória)**
```
1. Agente finaliza fase de testes
2. Agente prepara solicitação DAPR/P (ANEXO A)
3. Agente encaminha ao ONS (formatos, meios, prazos especificados)
4. ONS recebe e protocola
5. ONS avalia requisitos impeditivos (ANEXO B para DAPR/P)
   ├─ Pendências Impeditivas Encontradas:
   │  ├─ ONS informa inviabilidade
   │  ├─ ONS comunica impedimentos
   │  ├─ PROCESSO SUSPENSO
   │  ├─ Agente resolve pendências
   │  ├─ Agente resubmete via sistema ONS
   │  └─ Volta ao passo 4 (Reinício)
   └─ Sem Pendências Impeditivas:
      ├─ Verifica pendências NÃO impeditivas
      │  ├─ Existem pendências NÃO impeditivas:
      │  │  ├─ ONS elabora DAPR/P com:
      │  │  │  ├─ Data de atendimento aos requisitos
      │  │  │  ├─ Requisitos não atendidos (não impeditivos)
      │  │  │  ├─ Adequações necessárias
      │  │  │  ├─ Prazos acordados
      │  │  │  └─ Restrições de escoamento
      │  │  ├─ ONS encaminha DAPR/P ao Agente
      │  │  ├─ Agente recebe e monitora prazos
      │  │  ├─ Até vencimento do prazo:
      │  │  │  ├─ Agente formaliza atendimento da pendência, OU
      │  │  │  └─ Agente solicita revalidação de prazo (máx. 2x)
      │  │  │     ├─ Agente apresenta justificativas
      │  │  │     ├─ ONS analisa justificativa
      │  │  │     ├─ Revalidação aprovada:
      │  │  │     │  ├─ ONS informa novo prazo
      │  │  │     │  ├─ ONS informa ANEEL (se necessário)
      │  │  │     │  └─ Processo continua com novo prazo
      │  │  │     └─ Revalidação rejeitada:
      │  │  │        └─ ONS informa rejeição
      │  │  └─ Agente formaliza atendimento
      │  │     └─ Solicita DAPR/D
      │  └─ Sem pendências NÃO impeditivas:
      │     ├─ ONS emite DAPR/D diretamente
      │     └─ Pula etapa de DAPR/P com prazos
      └─ FIM (Sucesso)
```

#### **SEQUÊNCIA DAPR/D (Operação Definitiva)**
```
1. Agente em operação em teste (DAPR/T) OU provisória (DAPR/P)
2. Agente prepara solicitação DAPR/D (ANEXO A)
3. Agente encaminha ao ONS (formatos, meios, prazos especificados)
4. ONS recebe e protocola
5. ONS avalia requisitos impeditivos (ANEXO B para DAPR/D)
   ├─ Pendências Impeditivas Encontradas:
   │  ├─ ONS informa inviabilidade
   │  ├─ ONS comunica impedimentos
   │  ├─ PROCESSO SUSPENSO
   │  ├─ Agente resolve pendências
   │  ├─ Agente resubmete via sistema ONS
   │  └─ Volta ao passo 4 (Reinício)
   └─ Sem Pendências Impeditivas:
      ├─ Verifica se todas as instalações de um mesmo estudo 
      │  pré-operacional estão integradas sem pendências (Submódulo 7.4)
      │  ├─ Nem todas integradas:
      │  │  └─ PROCESSO AGUARDA integração de outras instalações
      │  └─ Todas integradas:
      │     ├─ ONS elabora DAPR/D com:
      │     │  ├─ Data de atendimento aos requisitos
      │     │  └─ Restrições de escoamento (se houver)
      │     ├─ ONS encaminha DAPR/D ao Agente
      │     ├─ Agente recebe DAPR/D
      │     └─ FIM (Sucesso) - Operação Definitiva Iniciada
```

---

### **DESVIOS E CAMINHOS ALTERNATIVOS**

| Desvio | Condição | Ação | Resultado |
|--------|----------|------|-----------|
| **D1** | Pendências impeditivas em DAPR/T | Suspender processo | Agente resolve e resubmete |
| **D2** | Pendências impeditivas em DAPR/P | Suspender processo | Agente resolve e resubmete |
| **D3** | Pendências NÃO impeditivas em DAPR/P | Emitir DAPR/P com prazos | Agente monitora e atende prazos |
| **D4** | Prazo de pendência vence sem atendimento (DAPR/P) | Agente solicita revalidação | ONS aprova (máx. 2x) ou rejeita |
| **D5** | Sem pendências NÃO impeditivas em DAPR/P | Emitir DAPR/D diretamente | Pula etapa de DAPR/P com prazos |
| **D6** | Pendências impeditivas em DAPR/D | Suspender processo | Agente resolve e resubmete |
| **D7** | Nem todas instalações de estudo pré-operacional integradas | Aguardar integração | DAPR/D não emitida até conclusão |
| **D8** | Múltiplos circuitos em usina Tipo II-C | Solicitar DAPR/P concomitante | Cada circuito analisado independentemente |
| **D9** | Reunião operacional necessária | Convocar agentes | Discussão de requisitos e prazos |
| **D10** | Conformidade não validada em DIR | Informar inviabilidade | Agente pode corrigir e resubmeter |

---

## RESUMO EXECUTIVO

O processo de emissão de declarações de atendimento (DIR, DAPR/T, DAPR/P, DAPR/D) segue uma estrutura hierárquica e sequencial:

1. **DIR**: Simples validação de conformidade com Ato Autorizativo para usinas sem relacionamento operacional com ONS.

2. **DAPR/T**: Validação de requisitos impeditivos para início de operação em teste; suspensão e reinício se pendências encontradas.

3. **DAPR/P**: Validação de requisitos impeditivos; emissão com prazos para pendências não impeditivas; revalidação de prazos (máx. 2x); possível emissão direta de DAPR/D se sem pendências não impeditivas.

4. **DAPR/D**: Validação de requisitos impeditivos; aguardamento de integração de todas as instalações de estudo pré-operacional; emissão com data de atendimento e restrições de escoamento.

**Fluxos de Exceção Críticos:**
- Suspensão e reinício por pendências impeditivas (todos os tipos)
- Revalidação de prazos em DAPR/P (máx. 2 vezes)
- Emissão direta de DAPR/D após DAPR/P (sem pendências não impeditivas)
- Aguardamento de integração pré-operacional para DAPR/D

**Atores Principais:**
- Agente de Geração (solicitante)
- ONS (analisador e emissor)
- ANEEL (informada em revalidações)
- Sistema Computacional do ONS (gerenciador de intervenções)