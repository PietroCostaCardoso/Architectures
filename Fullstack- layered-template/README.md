# Full Stack Layered Template 

### Para que serve essa arquitetura?
Serve para demonstrar a aplicação prática de desenvolvimento do cotidiano real do mercado de tecnologia de ponta a ponta. Este template detalha como o Frontend (focado em experiência, componentes e estado) e o Backend (focado em segurança, regras e persistência robusta) se organizam fisicamente dividindo suas atribuições para produção.

### Estrutura de Pastas e Componentes
```text
📂 Fullstack layered template
├── 📂 frontend
│   └── 📂 src
│       ├── 📂 @types 
│       ├── 📂 api 
│       ├── 📂 assets 
│       ├── 📂 components 
│       ├── 📂 hooks 
│       ├── 📂 pages 
│       ├── 📂 routes 
│       ├── 📂 templates 
│       ├── 📂 themes 
│       ├── 📂 utils 
│       └── 📂 validators
│
└── 📂 backend
    └── 📂 src
        ├── 📂 @types
        ├── 📂 config 
        ├── 📂 controllers
        ├── 📂 helpers 
        ├── 📂 middlewares
        ├── 📂 models 
        ├── 📂 routes 
        ├── 📂 services
        └── 📂 validators
```
## 📂 Frontend (Cliente)

* **`@types`**: Definições de tipos globais do TypeScript.
* **`api`**: Configuração e chamadas HTTP para o backend.
* **`assets`**: Arquivos estáticos (imagens, ícones, fontes).
* **`components`**: Componentes visuais reutilizáveis (botões, inputs).
* **`hooks`**: Lógica de estado compartilhada (Custom Hooks).
* **`pages`**: As telas da aplicação (Login, Dashboard).
* **`routes`**: Definição das rotas e navegação.
* **`templates`**: Layouts estruturais das páginas.
* **`themes`**: Estilização global (cores, fontes).
* **`utils`**: Funções auxiliares gerais (formatadores).
* **`validators`**: Validação de formulários no cliente.

---

## 📂 Backend (Servidor)

* **`@types`**: Tipagens globais do TypeScript para o servidor.
* **`config`**: Configurações gerais (banco de dados, variáveis de ambiente).
* **`controllers`**: Recebe a requisição (HTTP) e envia a resposta ao cliente.
* **`helpers`**: Funções de suporte (criptografia, geração de tokens).
* **`middlewares`**: Interceptadores de requisições (autenticação, erros).
* **`models`**: Estrutura e modelagem das tabelas do banco de dados.
* **`routes`**: Definição dos endpoints da API (`/usuarios`, `/login`).
* **`services`**: Onde fica toda a regra de negócio do sistema.
* **`validators`**: Validação dos dados que entram na API.