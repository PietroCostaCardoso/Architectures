# MVT (Model-View-Template)

###  Para que serve essa arquitetura?
Uma variação do padrão MVC amplamente difundida pelo ecossistema do framework Django (Python). Ele foca em alta velocidade de desenvolvimento, delegando a função clássica do Controller para o roteador nativo do próprio framework e deixando o desenvolvedor focado apenas em mapear dados, criar lógicas de exibição e templates dinâmicos.

### Estrutura de Pastas e Componentes
```text
📂 MVT
└── 📂 src
    ├── 📂 templates
    │   └── 📄 template.html
    ├── 📄 models.js
    └── 📄 views.js
```

### Responsabilidades de Pastas e Arquivos

* **`📄 views.js`**: Equivale ao Controller clássico do MVC. Intercepta requisições vindas do framework, requisita informações ao modelo e renderiza os templates passando as variáveis adequadas.
* **`📄 models.js`**: Mapeia as tabelas, estruturas e relacionamentos do banco de dados utilizando a sintaxe do ORM do framework.
* **`📂 templates`**: Camada visual dinâmica da aplicação.
    * **`📄 template.html`**: Arquivo HTML enriquecido com tags lógicas que o servidor processa dinamicamente antes de enviar a página pronta para o navegador.