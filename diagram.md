```mermaid
graph LR;
    Visitante[Visitante];
    Cliente[Cliente];
    Administrador[Administrador];
    SistemaPagamento["Sistema de Pagamento Externo"];

    subgraph System [Sistema de E-commerce]
        direction LR
        UC1("Navegar no Catálogo");
        UC2("Pesquisar Produtos");
        UC3("Ver Detalhes do Produto");
        UC4("Adicionar Produto ao Carrinho");
        UC5("Criar Conta");
        UC6("Realizar Login");
        UC7("Gerenciar Carrinho");
        UC8("Efetuar Pedido");
        UC9("Processar Pagamento");
        UC10("Acompanhar Status da Entrega");
        UC11("Deixar Avaliação/Comentário");
        UC12("Cadastrar Produto");
        UC13("Atualizar Produto");
        UC14("Gerenciar Categorias");
        UC15("Processar Pedidos (Admin)");
        UC16("Analisar Vendas (Relatórios)");
    end

    Visitante --> UC1;
    Visitante --> UC2;
    Visitante --> UC3;
    Visitante --> UC4;

    Cliente -- "herda de" --> Visitante; 

    Cliente --> UC5;
    Cliente --> UC6;
    Cliente --> UC7;
    Cliente --> UC8;
    Cliente --> UC10;
    Cliente --> UC11;
    Cliente --> UC4;

    Administrador --> UC6; 
    Administrador --> UC12;
    Administrador --> UC13;
    Administrador --> UC14;
    Administrador --> UC15;
    Administrador --> UC16;

    UC8 -.-> |"<<include>>"| UC9; %% Usando seta tracejada para include
    UC8 -.-> |"<<include>>"| UC7;
    UC11 -.-> |"<<include>>"| UC6;

    UC9 --> SistemaPagamento;
