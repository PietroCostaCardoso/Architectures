# Saga Pattern Architecture

### Para que serve essa arquitetura?
Serve para garantir a consistência dos dados em transações que passam por múltiplos microsserviços de forma assíncrona. Se alguma etapa falhar no meio do processo, a arquitetura garante a execução de ações compensatórias automáticas para desfazer os passos anteriores e impedir a corrupção do sistema.

### Estrutura de Pastas e Componentes
```text
📂 4-saga-pattern/
└── 📂 src/
    ├── 📂 saga/
    │   ├── 📂 compensations/
    │   │   └── 📄 CompensationAction.java
    │   ├── 📂 orchestrator/
    │   │   └── 📄 SagaOrchestrator.java
    │   └── 📂 steps/
    │       ├── 📄 StepOne.java
    │       └── 📄 StepTwo.java
    └── 📂 modules/
        ├── 📄 ExternalClientA.java
        └── 📄 ExternalClientB.java
```

### Responsabilidades de Pastas e Arquivos

* **`📂 saga`**: Concentra o núcleo de gerenciamento do fluxo transacional distribuído.
    * **`📂 orchestrator`**: Pasta do controlador central da transação.
        * **`📄 SagaOrchestrator.java`**: O cérebro do fluxo. Conhece a ordem das etapas e decide quando avançar ou reverter o processo.
    * **`📂 steps`**: Pasta dos passos operacionais.
        * **`📄 StepOne.java` e `📄 StepTwo.java`**: Contêm a lógica que comanda a execução de um passo específico em um serviço remoto.
    * **`📂 compensations`**: Pasta de tratamento de erros e reversões.
        * **`📄 CompensationAction.java`**: Código responsável por desfazer ou estornar o que o passo fez caso a transação falhe mais adiante.
* **`📂 modules`**: Camada que abstrai o contato e chamadas de rede com outros microsserviços.
    * **`📄 ExternalClientA.java` e `📄 ExternalClientB.java`**: Clientes HTTP, gRPC ou de mensageria que enviam fisicamente as requisições para fora da aplicação.