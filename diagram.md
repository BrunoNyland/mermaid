```mermaid
classDiagram
    class Produto {
        +String nome
        +String descricao
        +Decimal preco
        +Integer quantidadeEmEstoque
        +String categoria
        +String marca
        +List~Avaliacao~ avaliacoes
    }

    class Cliente {
        +String nomeCompleto
        +String email
        +String senha
        +List~Endereco~ enderecos
        +List~Telefone~ telefones
        +List~Pedido~ historicoPedidos
        +List~Avaliacao~ avaliacoes
    }

    class Endereco {
        +String rua
        +String cidade
        +String estado
        +String cep
    }

    class Telefone {
        +String tipo
        +String numero
    }

    class Pedido {
        +Integer id
        +DateTime dataPedido
        +Cliente cliente
        +String status
        +String metodoPagamento
        +List~ItemPedido~ itensPedido
    }

    class ItemPedido {
        +Integer quantidade
        +Decimal valorUnitario
        +Produto produto
        +Pedido pedido
    }

    class Avaliacao {
        +Integer id
        +Integer nota
        +String comentario
        +Cliente cliente
        +Produto produto
    }

    Produto "1..*" -- "*" ItemPedido : Contém
    Pedido "*" -- "1..*" Produto : Produtos
    Pedido "1" -- "*" ItemPedido : itensPedido
    Cliente "1" -- "*" Pedido : realiza
    Cliente "*" -- "*" Avaliacao : avalia
    Produto "*" -- "*" Avaliacao : recebe
    Cliente "1" -- "*" Endereco : possui
    Cliente "1" -- "*" Telefone : possui
    ItemPedido "*" -- "1" Pedido : pedido
    ItemPedido "*" -- "1" Produto : produto
    Avaliacao "*" -- "1" Cliente : cliente
    Avaliacao "*" -- "1" Produto : produto
