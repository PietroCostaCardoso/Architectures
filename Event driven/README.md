# Event-Driven Architecture (Arquitetura Baseada em Eventos)

### Para que serve essa arquitetura?
Serve para criar sistemas reativos e altamente desacoplados através de interações assíncronas baseadas em fatos históricos (eventos). Os emissores apenas publicam mensagens alertando que algo aconteceu no sistema, sem precisar saber quem vai receber ou processar essa informação.

### Estrutura de Pastas e Componentes
```text
📂 Event driven
└── 📂 src
    ├── 📂 domain
    │   └── 📂 events
    │       └── 📄 event.js
    ├── 📂 application
    │   ├── 📂 handlers
    │   │   └── 📄 handler.js
    │   └── 📂 publishers
    │       └── 📄 publisher.js
    └── 📂 infrastructure
        └── 📂 messaging
            ├── 📂 consumers
            │   └── 📄 consumer.js
            └── 📂 producers/
                └── 📄 producer.js
```

  ### Responsabilidades de Pastas e Arquivos

* **`📂 domain`**: Domínio e regras de negócio da aplicação.
    * **`📂 events`**: Pasta dos objetos de eventos.
        * **`📄 event.js`**: Estrutura imutável de dados representando um fato consolidado que ocorreu no passado (ex: `PedidoCriado`).
* **`📂 application`**: Camada que dita o fluxo reativo do software.
    * **`📂 publishers`**: Pasta de abstrações de envio.
        * **`📄 publisher.js`**: Contrato lógico para publicar eventos sem se acoplar a uma tecnologia de filas específica.
    * **`📂 handlers`**: Pasta dos executores reativos.
        * **`📄 handler.js`**: Código que escuta o evento e executa a lógica de negócio correspondente àquele acontecimento.
* **`📂 infrastructure`**: Camada técnica integrada com os corretores de mensagens (message brokers).
    * **`📂 messaging`**: Pasta de infraestrutura de mensageria.
        * **`📄 producer.js`**: Envia fisicamente o evento estruturado para dentro das filas.
        * **`📄 consumer.js`**: Processo worker em segundo plano que vigia as filas e encaminha as mensagens recebidas para os seus handlers.