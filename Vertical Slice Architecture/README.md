# Vertical Slice Architecture (Arquitetura em Fatias Verticais)

### Para que serve essa arquitetura?
Serve para organizar a árvore de pastas de um projeto de acordo com as funcionalidades ou módulos de negócios do mundo real em vez de agrupamentos estritamente técnicos. Em vez de espalhar os arquivos de uma única funcionalidade de "Pedido" por várias pastas distantes do sistema, todas as ferramentas técnicas necessárias para que o "Pedido" funcione vivem juntas e auto-contidas na sua respectiva pasta de contexto.

### 📁 Estrutura de Pastas e Componentes
```text
📂 Vertical slice architecture
└── 📂 src
    ├── 📂 loja
    ├── 📂 pedido
    ├── 📂 produto
    ├──📂 perfil
    └── 📂 templates
    
```
### Observação:
   O nome de cada uma já orienta o que deve ser feito.