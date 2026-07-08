# MVC (Model-View-Controller)

### Para que serve essa arquitetura?
Serve para estruturar o desenvolvimento de aplicações dividindo o software em três camadas de responsabilidade técnica estrita. Ele separa a regra de persistência de dados (Model), a lógica de orquestração de requisições (Controller) e a renderização da interface visual exibida para o usuário final (View). É o padrão base fundamental da web tradicional.

### Estrutura de Pastas e Componentes
```text
📂 MVC
└── 📂 src
    ├── 📂 controllers
    │   └── 📄 controller.js
    ├── 📂 models
    │   └── 📄 model.js
    └── 📂 views
        └── 📄 view.html

```

### Responsabilidades de Pastas e Arquivos

* **`📂 controllers`**: Camada que intercepta as interações e gerencia o fluxo da aplicação.
    * **`📄 controller.js`**: Recebe os inputs do usuário, chama os modelos correspondentes para buscar/salvar os dados e seleciona qual visualização (View) deve ser exibida de volta.
* **`📂 models`**: Camada de dados e acesso ao banco.
    * **`📄 model.js`**: Define os esquemas de dados, validações e manipula diretamente as leituras e gravações no banco de dados.
* **`📂 views`**: Camada de apresentação visual e interface gráfica.
    * **`📄 view.html`**: Arquivo de marcação (HTML/CSS) que recebe os dados prontos do controller e os renderiza na tela do usuário.