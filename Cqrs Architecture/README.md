# CQRS (Command Query Responsibility Segregation)

### Para que serve essa arquitetura?
Serve para separar completamente as operações que alteram o estado dos dados (Escrita/Commands) das operações que apenas consultam dados (Leitura/Queries). Esse padrão é ideal para sistemas de altíssima escala, pois permite otimizar, indexar e até usar bancos de dados diferentes para leitura e escrita de forma independente.

### Estrutura de Pastas e Componentes
```text
📂 Cqrs Architecture
└── 📂 src
    ├── 📂 application
    │   ├── 📂 commands
    │   │   ├── 📄 Command.java
    │   │   └── 📄 Handler.java
    │   └── 📂 queries
    │       ├── 📄 query.java
    │       └── 📄 QueryHandler.java
    └── 📂 infrastructure
        ├── 📂 persistence
        │   ├── 📄 CacheConfig.java
        │   └── 📄 SqlConfig.java
        └── 📂 repositories
            ├── 📄 ReadRepository.java
            └── 📄 WriteRepository.java
```

### Responsabilidades de Pastas e Arquivos

* **`📂 application`**: Camada que divide as intenções lógicas do usuário entre alterar ou buscar.
    * **`📂 commands`**: Pasta das operações de escrita e alteração.
        * **`📄 Command.java`**: Objeto de dados simples (DTO) que carrega os dados necessários para executar uma mudança.
        * **`📄 Handler.java`**: Código responsável por executar, validar e salvar a alteração descrita no Command.
    * **`📂 queries`**: Pasta das operações de leitura e busca.
        * **`📄 Query.java`**: Objeto contendo filtros, paginações ou argumentos de pesquisa.
        * **`📄 QueryHandler.java`**: Busca os dados diretamente nas fontes de leitura rápida, pulando lógicas complexas de escrita.
* **`📂 infrastructure`**: Camada que gerencia os recursos físicos de armazenamento de dados.
    * **`📂 persistence`**: Pasta de conexão com drivers de persistência.
        * **`📄 SqlConfig.java`**: Configuração do banco de dados relacional (ex: PostgreSQL) voltado para escritas seguras.
        * **`📄 CacheConfig.java`**: Configuração do banco em memória (ex: Redis) focado em buscas velozes.
    * **`📂 repositories`**: Pasta de isolamento das queries de banco.
        * **`📄 WriteRepository.java`**: Implementa comandos físicos de gravação (INSERT, UPDATE, DELETE).
        * **`📄 ReadRepository.java`**: Implementa comandos físicos de projeção e listagem veloz (SELECT).