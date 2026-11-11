# AGENTS.md — Projeto Ergon

## 1. Objetivo do projeto

Desenvolver um sistema de automação baseado em ESP32 para a empresa Ergon.

O projeto será desenvolvido de forma modular, permitindo incorporar novas funcionalidades conforme as regras de negócio e os requisitos técnicos forem definidos.

Tecnologias iniciais:
- ESP32.
- Framework Arduino (C++).
- PlatformIO.
- VS Code com Codex.
- Wokwi para simulação.
- Interface web local em HTML, CSS e JavaScript.

## 2. Estrutura do repositório

Repositório: `GSYSTech/Prot-tipo-Ergon`

- `main`: versão principal, estável e aprovada.
- `dev`: desenvolvimento e testes.

O firmware inicial está localizado em `Ergon-ESP32/`.

## 3. Regras obrigatórias do Git

1. Trabalhar exclusivamente na branch `dev`.
2. Nunca modificar diretamente a branch `main`.
3. Nunca executar commit, push, merge, rebase, reset destrutivo ou deploy sem autorização explícita do usuário.
4. Nunca excluir arquivos ou descartar alterações existentes sem autorização.
5. Antes de alterar arquivos, verificar a branch ativa e o estado do repositório.
6. Caso a branch ativa não seja `dev`, interromper a implementação e informar o usuário.
7. Após cada implementação, disponibilizar as alterações locais para revisão, sem publicá-las automaticamente.

## 4. Processo de desenvolvimento

Para cada solicitação:

1. Analisar as regras de negócio apresentadas.
2. Identificar os arquivos que precisarão ser modificados.
3. Implementar somente o escopo autorizado.
4. Preservar as funcionalidades existentes.
5. Compilar o firmware com PlatformIO, quando aplicável.
6. Executar os testes disponíveis.
7. Informar claramente os testes que não puderam ser realizados.
8. Entregar um relatório para auditoria.

Não implementar funcionalidades adicionais sem autorização.

## 5. Relatório obrigatório

Ao finalizar cada tarefa, apresentar:

### Resumo da implementação
Descrever o que foi desenvolvido.

### Arquivos modificados
Relacionar os arquivos criados, alterados ou excluídos.

### Regras implementadas
Explicar como cada requisito foi atendido.

### Testes realizados
Informar os comandos, resultados e eventuais falhas.

### Riscos e pendências
Apresentar limitações, dúvidas técnicas e funcionalidades ainda não validadas.

### Git
Informar a branch ativa e confirmar se houve ou não commit, push ou merge.

## 6. Segurança da automação

O sistema poderá controlar equipamentos elétricos e dosagem de produtos químicos.

Por isso:

- Adotar estados seguros durante inicialização e reinicialização.
- Manter saídas de acionamento desabilitadas em situações de falha.
- Não permitir dosagem sem confirmação das condições de segurança.
- Prever limite máximo de dosagem por ciclo e por período.
- Prever temporização e supervisão dos acionamentos.
- Implementar tratamento para falhas de sensores e sinais inconsistentes.
- Separar claramente modo de simulação e funcionamento real.
- Não considerar uma compilação bem-sucedida como validação de segurança.
- Não liberar operação real sem testes físicos e validação técnica.

Não presumir que uma leitura de ORP representa diretamente a concentração de cloro livre.

## 7. Arquitetura do software

Priorizar:

- Código modular e organizado.
- Funções com responsabilidades definidas.
- Configurações centralizadas.
- Máquina de estados para sequências operacionais.
- Temporizadores não bloqueantes, preferencialmente utilizando `millis()`.
- Separação entre controle, interface web e comunicação.
- Registro de eventos e falhas.
- Código comentado em português quando necessário para facilitar a compreensão do usuário.

Evitar o uso de `delay()` em rotinas que precisam responder continuamente a eventos e condições de segurança.

## 8. Interface web

O ESP32 deverá disponibilizar uma interface web local, sem depender de hospedagem ou conexão com a internet.

Funcionalidades previstas:

- Configuração dos parâmetros operacionais.
- Visualização do estado dos equipamentos.
- Consulta de alarmes.
- Histórico de operações.
- Autenticação para alterações de parâmetros.
- Armazenamento persistente das configurações.

A interface não deverá comprometer a execução das rotinas de controle.

## 9. Simulação

Durante o desenvolvimento inicial, utilizar o Wokwi ou recursos equivalentes para testar a lógica sem hardware físico.

Representar bombas e outros atuadores por saídas virtuais.

Simular sinais dos sensores, condições normais e situações de falha.

Toda funcionalidade destinada à operação real deverá passar posteriormente por validação com os equipamentos físicos.

## 10. Autoridade e aprovação

O Codex é responsável pela implementação técnica solicitada.

O ChatGPT será utilizado pelo usuário como apoio à análise das regras de negócio e à auditoria técnica.

O usuário é responsável por autorizar alterações, publicação de código e integração entre branches.

Nenhuma recomendação ou aprovação de código substitui as validações técnicas e de segurança necessárias para operação do equipamento.

## 11. Regras de comunicação

- Responder em português brasileiro.
- Utilizar linguagem clara e objetiva.
- Explicar decisões técnicas relevantes.
- Não presumir requisitos que ainda não foram definidos.
- Solicitar esclarecimento quando uma decisão técnica essencial estiver indefinida.
- Não alterar o escopo aprovado sem informar o usuário.