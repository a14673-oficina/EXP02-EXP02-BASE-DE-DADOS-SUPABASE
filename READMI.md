# Projeto: Futebol App (com Logos)

## Descrição Geral

Este projeto é uma versão aprimorada da aplicação web de gestão de clubes e jogadores de futebol, desenvolvida com HTML, CSS e JavaScript. Mantém a integração com o Supabase para a persistência de dados e operações CRUD (Criar, Ler, Atualizar, Apagar) sobre jogadores, mas agora incorpora a exibição de logótipos de clubes para uma experiência visual mais rica. A interface é responsiva e permite aos utilizadores interagir com os dados de forma dinâmica, com um foco visual nos clubes.

O projeto inclui:

*   Interface de utilizador (UI) para adicionar, editar, apagar e filtrar jogadores.
*   Exibição de listas de clubes e jogadores, com logótipos associados aos clubes.
*   Conexão com o Supabase para gestão de dados.
*   Estilização aprimorada com CSS para suportar a exibição de logótipos e cartões de clubes personalizados.

## Funcionalidades

1.  **Interface HTML (index.html)**
    *   Campos de entrada para adicionar novos jogadores (Nome, País, Idade, Posição, Clube).
    *   Botões para adicionar jogadores, filtrar por país ou clube, e mostrar todos os jogadores.
    *   Um modal para edição de dados de jogadores existentes.
    *   Secções para exibir a lista de clubes e jogadores, com a novidade de exibir os logótipos dos clubes.

2.  **Lógica JavaScript (script.js)**
    *   Inicialização do cliente Supabase com URL e chave de API.
    *   **Mapeamento de Logótipos:** Um objeto `logoMap` que associa nomes de clubes a caminhos de ficheiros de logótipos (`logos/`).
    *   Funções assíncronas para carregar dados de clubes (`carregarClubes()`) e jogadores (`carregarJogadores()`) do Supabase.
    *   Função para adicionar um novo jogador (`adicionarJogador()`).
    *   Função para apagar um jogador existente (`apagarJogador(id)`).
    *   Funções para abrir (`abrirModalEditar(jogador)`) e fechar (`fecharModal()`) o modal de edição.
    *   Função para guardar as edições de um jogador (`guardarEdicao()`).
    *   Funções para filtrar jogadores por país (`filtrarPorPais()`) e por clube (`filtrarPorClube()`).
    *   Função auxiliar (`mostrarJogadores(data)`) para renderizar a lista de jogadores na UI, agora incluindo a lógica para exibir o logótipo correto com base no clube do jogador.

3.  **Base de Dados (Supabase)**
    A aplicação interage com uma base de dados Supabase, que contém as seguintes tabelas (estrutura idêntica à versão anterior):

    *   **`clube`**
        *   `nomeclube` (VARCHAR, Chave Primária)
        *   `pais` (VARCHAR)
        *   `idade` (INTEGER)
        *   `estadio` (VARCHAR)

    *   **`jogador`**
        *   `numatleta` (BIGINT, Chave Primária, gerado automaticamente)
        *   `nomejogador` (VARCHAR, Não Nulo)
        *   `pais` (VARCHAR)
        *   `idade` (INTEGER)
        *   `posicao` (VARCHAR)
        *   `nomeclube` (VARCHAR, Chave Estrangeira referenciando `clube.nomeclube`)

    A base de dados inclui dados iniciais para clubes e jogadores. As políticas de segurança de nível de linha (RLS) estão ativadas para permitir leitura pública.

4.  **Recursos Visuais (logos/)**
    *   A pasta `logos/` contém ficheiros de imagem (`.png`) para os logótipos dos clubes, que são dinamicamente carregados e exibidos na interface.

## Como Usar

1.  **Configuração do Supabase:** O projeto já vem configurado com as credenciais de um projeto Supabase. Não é necessária configuração adicional, a menos que se deseje usar uma instância Supabase própria.
2.  **Abrir a Aplicação:** Abra o ficheiro `index.html` num navegador web.
3.  **Interagir com a UI:**
    *   **Adicionar Jogador:** Preencha os campos na secção "Adicionar Jogador" e clique em "Adicionar jogador".
    *   **Filtrar Jogadores:** Utilize os campos "Filtrar por país" ou "Filtrar por clube" e clique nos respetivos botões para aplicar filtros. Clique em "Mostrar todos" para remover os filtros.
    *   **Editar/Apagar Jogador:** Na lista de jogadores, clique em "Editar" para abrir o modal de edição ou em "Apagar" para remover um jogador. Observe que os cartões de jogador agora exibem o logótipo do clube.

## Pontos de Aprendizagem

*   **Integração Frontend-Backend:** Demonstra como uma aplicação frontend (HTML, CSS, JS) pode interagir com um serviço backend (Supabase) para gerir dados.
*   **Operações CRUD:** Implementação de operações de Criar, Ler, Atualizar e Apagar dados.
*   **Manipulação do DOM Aprimorada:** Uso de JavaScript para atualizar dinamicamente a interface do utilizador, incluindo a inserção de elementos de imagem (logótipos) com base nos dados.
*   **Gestão de Recursos Estáticos:** Organização e utilização de recursos visuais (logótipos) dentro do projeto.
*   **Estilização Condicional:** Aplicação de estilos CSS específicos para cartões de clubes com base no nome do clube, proporcionando uma diferenciação visual.

## Melhorias Futuras

*   **Autenticação de Utilizadores:** Implementar um sistema de login/registo para proteger as operações de escrita (adicionar, editar, apagar) e permitir que apenas utilizadores autorizados modifiquem os dados.
*   **Gestão de Logótipos:** Criar uma funcionalidade para carregar e gerir logótipos de clubes diretamente pela aplicação, em vez de depender de ficheiros estáticos.
*   **Validação de Dados:** Adicionar validação de entrada nos campos do formulário para garantir a integridade dos dados antes de enviá-los para o Supabase.
*   **Melhoria da UI/UX:** Aprimorar o design e a experiência do utilizador, incluindo feedback visual para campos incorretos, animações e um layout mais moderno.
*   **Paginação/Pesquisa Avançada:** Para grandes volumes de dados, implementar paginação ou opções de pesquisa mais avançadas para melhorar a navegação.
*   **Tratamento de Erros:** Implementar um tratamento de erros mais robusto e amigável ao utilizador.
