
%%{init: {'theme': 'base', 'themeVariables': {'actorStroke': '#333', 'actorTextColor': '#000'}}}%%

```mermaid

usecaseDiagram
  actor Visitante
  actor Cliente as "Cliente Cadastrado"
  actor Admin as "Administrador"
  actor Pagamento as "Sistema de Pagamento Externo"

  Visitante --> (Navegar no Catálogo)
  Visitante --> (Buscar Produtos)
  Visitante --> (Adicionar ao Carrinho)
  Visitante --> (Gerenciar Carrinho)

  Cliente --> (Cadastro de Usuário)
  Cliente --> (Login / Autenticação)
  Cliente --> (Realizar Pedido)
  Cliente --> (Acompanhar Entrega)
  Cliente --> (Avaliar Produto)

  Admin --> (Gerenciar Produtos)
  Admin --> (Gerenciar Categorias)
  Admin --> (Processar Pedidos)
  Admin --> (Gerar Relatórios de Vendas)

  Pagamento <-- (Processar Pagamento)

  (Realizar Pedido) ..> (Processar Pagamento) : includes
  (Buscar Produtos) ..> (Navegar no Catálogo) : extends
  (Login / Autenticação) ..> (Cadastro de Usuário) : includes
