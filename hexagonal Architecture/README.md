# Ports and Adapters (Arquitetura Hexagonal)

### Para que serve essa arquitetura?
Serve para criar uma aplicação totalmente modular através do conceito de "encaixes". O core do negócio fica isolado dentro de um "hexágono" central protegido por Portas (Interfaces) e se comunica com o mundo de fora através de Adaptadores (Implementações), permitindo trocar tecnologias (como o banco ou framework) sem mexer nas regras de negócio.

### Estrutura de Pastas e Componentes
```text
📂 hexagonal architecture
└── 📂 src
    ├── 📂 domain
    │   └── 📄 domain.model.js
    ├── 📂 ports
    │   ├── 📂 inbound
    │   │   └── 📄 inbound.port.js
    │   └── 📂 outbound
    │       └── 📄 outbound.port.js
    └── 📂 adapters
        ├── 📂 inbound
        │   └── 📄 api.controller.js
        └── 📂 outbound
            └── 📄 database.js
```

### Responsabilidades de Pastas e Arquivos

* **`📂 domain`**: O centro do hexágono onde vive o modelo de negócio estável.
    * **`📄 domain.model.js`**: Define os modelos, comportamentos e lógicas do domínio puras, sem herdar nada de frameworks externos.
* **`📂 ports`**: Define os contratos lógicos (interfaces) de entrada e saída do hexágono.
    * **`📂 inbound`**: Pasta de Portas de Entrada.
        * **`📄 inbound.port.js`**: Interface que especifica como os componentes externos podem interagir com o negócio da aplicação.
    * **`📂 outbound`**: Pasta de Portas de Saída.
        * **`📄 outbound.port.js`**: Interface que dita de quais serviços externos (ex: banco de dados) o hexágono necessita para funcionar.
* **`📂 adapters`**: Contém as implementações tecnológicas reais que se conectam nas portas.
    * **`📂 inbound`**: Pasta de Adaptadores de Entrada.
        * **`📄 api.controller.js`**: Recebe a requisição externa do framework (ex: Express), converte os dados e injeta na porta de entrada.
    * **`📂 outbound`**: Pasta de Adaptadores de Saída.
        * **`📄 database.js`**: Código técnico que implementa o acesso ao banco de dados físico, seguindo o contrato da porta de saída.