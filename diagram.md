```mermaid

---
title: Diagrama de Caso de Uso - E-commerce de Eletrônicos
---
left to right direction
actor Visitante
actor Cliente
actor Administrador
actor "Sistema de\nPagamento Externo" as SistemaPagamento

rectangle "Sistema de E-commerce" {
  usecase "Navegar no Catálogo" as UC1
  usecase "Pesquisar Produtos" as UC2
  usecase "Ver Detalhes do Produto" as UC3
  usecase "Adicionar Produto ao Carrinho" as UC4
  usecase "Criar Conta" as UC5
  usecase "Realizar Login" as UC6
  usecase "Gerenciar Carrinho" as UC7
  usecase "Efetuar Pedido" as UC8
  usecase "Processar Pagamento" as UC9
  usecase "Acompanhar Status da Entrega" as UC10
  usecase "Deixar Avaliação/Comentário" as UC11
  usecase "Cadastrar Produto" as UC12
  usecase "Atualizar Produto" as UC13
  usecase "Gerenciar Categorias" as UC14
  usecase "Processar Pedidos (Admin)" as UC15
  usecase "Analisar Vendas (Relatórios)" as UC16
}

' Atores e suas interações
Visitante -- UC1
Visitante -- UC2
Visitante -- UC3
Visitante -- UC4

Cliente --|> Visitante ' Generalização: Cliente é um tipo de Visitante

Cliente -- UC5
Cliente -- UC6
Cliente -- UC7
Cliente -- UC8
Cliente -- UC10
Cliente -- UC11
Cliente -- UC4 ' Cliente também adiciona ao carrinho

Administrador -- UC6 ' Admin também precisa logar
Administrador -- UC12
Administrador -- UC13
Administrador -- UC14
Administrador -- UC15
Administrador -- UC16

' Relacionamentos entre Casos de Uso
UC8 ..> UC9 : <<include>> ' Efetuar Pedido inclui Processar Pagamento
UC8 ..> UC7 : <<include>> ' Efetuar Pedido inclui Gerenciar/Usar Carrinho
UC11 ..> UC6 : <<include>> ' Para avaliar, precisa estar logado (implícito/dependência)
UC11 ..> UC8 : <<depends>> ' Depende de ter feito um pedido (Restrição)

' Interação com Sistema Externo
UC9 -- SistemaPagamento ' Processar Pagamento interage com o Sistema Externo

```
