# Clean Architecture (Arquitetura Limpa)

### Para que serve essa arquitetura?
Serve para isolar completamente as regras de negócio centrais da aplicação de qualquer detalhe técnico, framework, servidor web ou banco de dados. Isso garante que o core do seu software seja testável e imune a mudanças tecnológicas externas.

### Uma Pequena observação:
A dependência de código só aponta para dentro. As camadas mais externas conhecem as internas, mas a camada central de Domínio é isolada e proibida de dar `import` em qualquer arquivo da camada de infraestrutura.

### Estrutura de Pastas e Componentes
```text
📂 Clean Architecture
└── 📂 src
    ├── 📂 core
    │   ├── 📂 domain
    │   │   └── 📄 entity.py
    │   └── 📂 use_cases
    │       └── 📄 use_case.py
    ├── 📂 shared
    │   ├── 📂 contracts
    │   │   ├── 📄 repository.py
    │   │   └── 📄 token_interface.py
    │   └── 📂 dtos
    │       └── 📄 dto.py
    └── 📂 infrastructure
        ├── 📂 database
        │   └── 📄 database.repository.py
        └── 📂 http
            ├── 📄 controller.py
            └── 📄 routes.py
```

### Responsabilidades de Pastas e Arquivos

* **`📂core`**: Pasta que centraliza o coração do software.
    * **`📄 entity.py`**: Contém as regras de negócio fundamentais e validações estruturais das entidades do sistema.
    * **`📄 use_case.py`**: Implementa as regras de fluxo do negócio, ditando o passo a passo de uma ação.
* **`📂 shared`**: Camada que guarda contratos, tipos e objetos de transferência compartilhados.
    * **`📂 contracts`**: Pasta de contratos abstratos (interfaces).
        * **`📄 repository_contract.py`**: Define quais métodos o banco de dados deve expor sem se acoplar a um banco real.
        * **`📄 token_interface.py`**: Define o contrato para geração e validação de chaves.
    * **`📂 dtos`**: Pasta de objetos de transferência.
        * **`📄 dto.py`**: Data Transfer Object. Limpa, tipa e valida a estrutura dos dados que chegam de fora.
* **`📂 infrastructure`**: Camada externa que lida com o mundo real, frameworks e bibliotecas.
    * **`📂 database`**: Pasta de persistência de dados.
        * **`📄 database_repository.py`**: Implementa la comunicación física y queries con el banco usando ORMs.
    * **`📂 http`**: Pasta do servidor web.
        * **`📄 controller.py`**: Recebe a requisição HTTP, aciona o caso de uso e retorna o status HTTP adequado.
        * **`📄 routes.py`**: Mapeia as URLs da API e direciona as requisições para seus controllers.