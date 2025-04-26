```mermaid
graph LR; %% Declara um fluxograma da Esquerda para Direita

    %% Definindo os Atores como nós
    Visitante[Visitante]; %% Nó retangular para Ator
    Cliente[Cliente];
    Administrador[Administrador];
    SistemaPagamento["Sistema de Pagamento Externo"]; %% Colocar entre aspas se tiver espaços/quebra de linha

    %% Definindo o Sistema como um Subgraph
    subgraph System [Sistema de E-commerce]
        direction LR
        %% Definindo Casos de Uso como nós (usando parênteses para forma ovalada/arredondada)
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

    %% Conectando Atores aos Casos de Uso (Associações)
    Visitante --> UC1;
    Visitante --> UC2;
    Visitante --> UC3;
    Visitante --> UC4;

    %% Relação Cliente - Visitante (Generalização representada como link simples)
    %% Nota: Flowchart não tem seta específica para generalização UML
    Cliente -- "herda de" --> Visitante; %% Usando label na seta para indicar relação

    %% Conectando Cliente aos Casos de Uso
    Cliente --> UC5;
    Cliente --> UC6;
    Cliente --> UC7;
    Cliente --> UC8;
    Cliente --> UC10;
    Cliente --> UC11;
    Cliente --> UC4; %% Cliente também usa UC4

    %% Conectando Administrador aos Casos de Uso
    Administrador --> UC6; %% Admin também precisa logar
    Administrador --> UC12;
    Administrador --> UC13;
    Administrador --> UC14;
    Administrador --> UC15;
    Administrador --> UC16;

    %% Relações entre Casos de Uso (Include/Extend com setas tracejadas e label)
    UC8 -.-> |"<<include>>"| UC9; %% Usando seta tracejada para include
    UC8 -.-> |"<<include>>"| UC7;
    UC11 -.-> |"<<include>>"| UC6;
    %% UC11 -.-> |"depende de"| UC8; %% Relação de dependência pode ser implícita ou anotada

    %% Conectando Caso de Uso ao Sistema Externo
    UC9 --> SistemaPagamento;
