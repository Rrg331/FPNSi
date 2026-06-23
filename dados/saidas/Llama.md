Aqui está o modelo de processo de negócio em notação BPMN para a emissão das declarações de atendimento (DIR, DAPR/T, DAPR/P e DAPR/D) para integração de instalações de geração ao SIN:

**1. RAIAS (pools/lanes)**

* Agente de Geração
* Operador Nacional do Sistema Elétrico (ONS)
* ANEEL (Agência Nacional de Energia Elétrica)

**2. ATIVIDADES**

1. Solicitação de emissão de DIR (Agente de Geração)
2. Análise da solicitação de DIR (ONS)
3. Emissão de DIR (ONS)
4. Solicitação de emissão de DAPR/T (Agente de Geração)
5. Análise da solicitação de DAPR/T (ONS)
6. Emissão de DAPR/T (ONS)
7. Solicitação de emissão de DAPR/P (Agente de Geração)
8. Análise da solicitação de DAPR/P (ONS)
9. Emissão de DAPR/P (ONS)
10. Solicitação de emissão de DAPR/D (Agente de Geração)
11. Análise da solicitação de DAPR/D (ONS)
12. Emissão de DAPR/D (ONS)

**3. GATEWAYS / DECISOES**

1. Existência de pendências impeditivas para emissão de DIR (ONS)
2. Existência de pendências impeditivas para emissão de DAPR/T (ONS)
3. Existência de pendências impeditivas para emissão de DAPR/P (ONS)
4. Existência de pendências impeditivas para emissão de DAPR/D (ONS)

**4. EVENTOS**

1. Início do processo de emissão de DIR
2. Fim do processo de emissão de DIR
3. Início do processo de emissão de DAPR/T
4. Fim do processo de emissão de DAPR/T
5. Início do processo de emissão de DAPR/P
6. Fim do processo de emissão de DAPR/P
7. Início do processo de emissão de DAPR/D
8. Fim do processo de emissão de DAPR/D

**5. FLUXOS DE EXCECAO**

1. Não emissão de DIR devido a pendências impeditivas
2. Não emissão de DAPR/T devido a pendências impeditivas
3. Não emissão de DAPR/P devido a pendências impeditivas
4. Não emissão de DAPR/D devido a pendências impeditivas
5. Suspensão do processo de emissão de DAPR/T, DAPR/P ou DAPR/D devido a pendências impeditivas
6. Reinício do processo de emissão de DAPR/T, DAPR/P ou DAPR/D após solução das pendências impeditivas

**6. FLUXO DE SEQUENCIA**

1. O Agente de Geração solicita a emissão de DIR.
2. O ONS analisa a solicitação e emite a DIR se não houver pendências impeditivas.
3. O Agente de Geração solicita a emissão de DAPR/T.
4. O ONS analisa a solicitação e emite a DAPR/T se não houver pendências impeditivas.
5. O Agente de Geração solicita a emissão de DAPR/P.
6. O ONS analisa a solicitação e emite a DAPR/P se não houver pendências impeditivas.
7. O Agente de Geração solicita a emissão de DAPR/D.
8. O ONS analisa a solicitação e emite a DAPR/D se não houver pendências impeditivas.

Observação: O fluxo de sequência pode variar dependendo das pendências impeditivas e das decisões tomadas pelo ONS.