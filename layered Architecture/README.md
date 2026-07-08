# Layered Architecture (Arquitetura em Camadas / DDD Patterned)

### Para que serve essa arquitetura?
Serve para organizar o sistema dividindo as responsabilidades de desenvolvimento em grupos horizontais (camadas) bem definidos. Cada camada possui um papel técnico e conceitual específico no ciclo de vida do software, facilitando a manutenção e a divisão de tarefas em equipes.

### Estrutura de Pastas e Componentes
```text
📂 layered Architecture
└── 📂 src
    ├── 📂 presentation
    │   ├── 📄 controller.py
    │   └── 📄 middleware.py
    ├── 📂 application
    │   └── 📄 usuario_service.py
    ├── 📂 domain
    │   ├── 📂 entities
    │   │   └── 📄 entity.py
    │   └── 📂 services
    │       └── 📄 domain_service.py
    └── 📂 infrastructure
        └── 📂 repositories
            └── 📄 databaseRepository.py
```

### Responsabilidades de Pastas e Arquivos

* **`📂 presentation`**: Camada responsável pelo contato inicial com o cliente ou requisições externas.
    * **`📄 controller.py`**: Captura os parâmetros HTTP da requisição e envia para a camada de aplicação.
    * **`📄 middleware.py`**: Intercepta a requisição para realizar tarefas técnicas como checar autenticação.
* **`📂 application`**: Camada que orquestra o fluxo da aplicação.
    * **`📄 usuario_service.py`**: Coordena o fluxo: chama os repositórios, aciona o domínio e finaliza transações.
* **`📂 domain`**: Camada onde vivem os modelos conceituais puros e regras de negócio essenciais.
    * **`📂 entities`**: Pasta das entidades do negócio.
        * **`📄 entity.py`**: Objeto rico que possui identificação única, atributos e comportamentos de domínio.
    * **`📂 services`**: Pasta de serviços de domínio.
        * **`📄 domain_service.py`**: Executa lógicas complexas de negócio que envolvem mais de uma entidade.
* **`📂 infrastructure`**: Fornece os recursos técnicos e implementações de infraestrutura.
    * **`📂 repositories`**: Pasta de comunicação com dados.
        * **`📄 databaseRepository.py`**: Executa os comandos físicos SQL ou operações do ORM no banco de dados.