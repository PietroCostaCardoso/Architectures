# software architecture

[Português](#versão-em-português) | [English](#english-version)

---

## Versão em Português

Este repositório foi criado para centralizar, organizar e documentar a estrutura de pastas e as responsabilidades técnicas das arquiteturas mais cobradas pelo mercado de tecnologia..

### Aviso Importante:
Este projeto foi desenvolvido com foco estrito em **design de software e estudo conceitual**. As arquiteturas de nível avançado e distribuído (como *CQRS, Event-Driven e Saga Pattern*) estão documentadas aqui para fins de aprendizado teórico e de boas práticas de mercado. Elas representam meu interesse em entender problemas, não refletindo necessariamente ferramentas que implemento de olhos fechados em produção no meu dia a dia técnico.

---

## A Minha Jornada:

Quando comecei a estudar essas arquiteturas, tive uma grande dificuldade que quase todo desenvolvedor enfrenta: **"Se todas as pastas parecem iguais por fora (quase todas têm `src`, `infra`, `domain`), qual é a real diferença entre elas e qual eu devo usar para cada problema?"**

Depois de quebrar a cabeça e analisar os fluxos de dependência, consegui mapear o propósito real de cada uma para acabar com essa confusão:

### Padrões de Framework e Produtividade (Nível Fundamental)
* **MVC & MVT:** Foram feitos para resolver a entrada e saída da Web rápida. O código nasce colado no framework (Django, Express, Spring). O foco é velocidade de entrega, separando o banco (Model), a lógica (Controller/View) e a tela (View/Template).

### Isolamento e Proteção do Negócio (Nível Corporativo)
* **Clean Architecture & Hexagonal (Ports & Adapters):** Resolvem o problema do acoplamento. Se amanhã eu decidir trocar o banco de dados (ex: mudar do Prisma para o Sequelize, ou do PostgreSQL para o MongoDB), a minha regra de negócio central não sofre nenhuma alteração. O foco aqui é criar muros de isolamento usando interfaces e contratos.
* **Layered Architecture (DDD Patterned):** Organiza o sistema em grupos horizontais de responsabilidade técnica (Apresentação, Aplicação, Domínio, Infraestrutura), ideal para manter a ordem quando o sistema começa a crescer em uma única base de código.

### Performance e Alta Escalabilidade (Nível Avançado)
* **CQRS:** Divide o código no meio com uma linha rígida. Se o seu sistema tem muitos acessos de leitura e poucas escritas (como uma linha do tempo de rede social), o CQRS separa o banco e a lógica de consulta do banco de alteração, otimizando a velocidade ao máximo.
* **Event-Driven & Saga Pattern:** Resolvem a comunicação assíncrona e sistemas distribuídos. Em vez de uma parte do sistema travar esperando a outra responder, eles usam eventos históricos ("algo aconteceu") e filas de mensageria para processar dados em segundo plano com segurança.

### Organização por Contexto do Negócio
* **Vertical Slice:** Batem de frente com a organização tradicional. Em vez de agrupar o código por "tipo de arquivo" (todas as rotas juntas, todos os modelos juntos), o código é agrupado por **funcionalidade** (tudo o que é de `pedido` fica na pasta pedido, tudo de `produto` fica na pasta produto). Isso faz com que as pastas do projeto "ganhem" o que o seu negócio faz de verdade.

### Cotidiano
* **Fullstack layered template** Possui o Frontend (focado em experiência, componentes e estado) e o Backend (focado em segurança, regras e persistência robusta) se organizam fisicamente dividindo suas atribuições para produção.

---

## Guia de Navegação do Repositório
* **📂 Clean Architecture** - Isolamento total do core de negócio.
* **📂 layered Architecture** - Divisão horizontal por atribuições.
* **📂 Cqrs Architecture** - Segregação física de escrita e leitura.
* **📂 Saga pattern** - Consistência em fluxos distribuídos.
* **📂 hexagonal Architecture** - Sistema baseado em plug-ins e portas.
* **📂 Event driven** - Arquitetura reativa baseada em eventos.
* **📂 Fullstack-layered-template**
* **📂 MVC** - Padrão clássico Model-View-Controller.
* **📂 MVT** - Padrão clássico Model-View-Template.
* **📂 Vertical Slice Architecture** - Organização focada em fatias de negócio.

---

## English Version

This repository was created to centralize, organize, and document the folder structure and technical responsibilities of the architectures most demanded by the technology market.

### Important Notice:
This project was developed with a strict focus on **software design and conceptual study**. Advanced and distributed architectures (such as *CQRS, Event-Driven, and Saga Pattern*) are documented here for theoretical learning purposes and market best practices. They represent my interest in understanding problems, not necessarily tools that I implement blindly in production in my technical day-to-day work.

---

## My Journey:

When I started studying these architectures, I faced a major difficulty that almost every developer encounters: **"If all folders look the same from the outside (almost all have `src`, `infra`, `domain`), what is the real difference between them and which one should I use for each problem?"**

After racking my brain and analyzing the dependency flows, I managed to map out the real purpose of each one to clear up this confusion:

### Framework and Productivity Patterns (Foundational Level)
* **MVC & MVT:** They were made to solve fast Web input and output. The code is born closely tied to the framework (Django, Express, Spring). The focus is delivery speed, separating the database (Model), the logic (Controller/View), and the user interface (View/Template).

### Business Isolation and Protection (Enterprise Level)
* **Clean Architecture & Hexagonal (Ports & Adapters):** They solve the coupling problem. If tomorrow I decide to change the database (e.g., switch from Prisma to Sequelize, or from PostgreSQL to MongoDB), my core business rule remains completely unchanged. The focus here is to create isolation barriers using interfaces and contracts.
* **Layered Architecture (DDD Patterned):** Organizes the system into horizontal groups of technical responsibility (Presentation, Application, Domain, Infrastructure), ideal for maintaining order when the system starts to grow within a single codebase.

### Performance and High Scalability (Advanced Level)
* **CQRS:** Splits the code right down the middle with a hard line. If your system has many read operations and few writes (like a social media timeline), CQRS separates the database and the query logic from the mutation logic, optimizing speed to the maximum.
* **Event-Driven & Saga Pattern:** They solve asynchronous communication and distributed systems. Instead of one part of the system freezing while waiting for another to respond, they use historical events ("something happened") and messaging queues to process data safely in the background.

### Organization by Business Context
* **Vertical Slice:** They go against traditional organization. Instead of grouping code by "file type" (all routes together, all models together), the code is grouped by **feature** (everything related to `order` stays in the order folder, everything related to `product` stays in the product folder). This makes the project folders truly reflect what your business actually does.

### Everyday Use
* **Fullstack layered template** Features the Frontend (focused on experience, components, and state) and the Backend (focused on security, rules, and robust persistence) physically organized by dividing their responsibilities for production.

---

## Repository Navigation Guide
* **📂 Clean Architecture** - Total isolation of the business core.
* **📂 layered Architecture** - Horizontal division by responsibilities.
* **📂 Cqrs Architecture** - Physical segregation of write and read.
* **📂 Saga pattern** - Consistency in distributed workflows.
* **📂 hexagonal Architecture** - Plugin and port-based system.
* **📂 Event driven** - Event-driven reactive architecture.
* **📂 Fullstack-layered-template**
* **📂 MVC** - Classic Model-View-Controller pattern.
* **📂 MVT** - Classic Model-View-Template pattern.
* **📂 Vertical Slice Architecture** - Organization focused on business slices.


## 👤 Autor

Desenvolvido com dedicação por **Pietro Costa Cardoso**.  
Se este projeto te ajudou, considere dar uma ⭐ no repositório!

Link original: https://github.com/PietroCostaCardoso/Software-Architecture

Pietro Costa Cardoso. Todos os direitos reservados sob a Licença MIT.
