# SQL-Business-Insights
Este projeto tem como objetivo praticar SQL por meio da análise de dados de uma loja fictícia de informática.  O banco de dados foi desenvolvido no MySQL e contém informações sobre clientes ficticios, produtos, categorias, pedidos e itens vendidos.

# Objetivo

Utilizar comandos SQL para responder a perguntas de negócio, organizar informações e identificar padrões nos dados.

# Tecnologias utilizadas

MySQL
SQL

# Estrutura do banco de dados

O banco de dados loja_sql contém as tabelas:

Clientes: informações dos clientes.
Categorias: categorias dos produtos.
Produtos: nomes e preços dos produtos.
Pedidos: datas e status dos pedidos.
Itens pedido: produtos e quantidades associados a cada pedido.

# Casos de negocio

Caso 1: Quais produtos custam mais de R$ 100?
# Comando SQL:
SELECT nome, preco
FROM produtos
WHERE preco > 100;

# Objetivo: Selecionar o nome e o preço dos produtos cadastrados e filtrar os registros para exibir apenas aqueles onde preço seja superior a R$ 100.

Caso 2: Quais são os produtos mais caros?
# Comando SQL:
SELECT nome, preco
FROM produtos
ORDER BY preco DESC;

# Objetivo: Selecionar o nome e o preço dos produtos cadastrados e ordenar pelo preço em ordem decrescente, onde vai ser exibido primeiro os produtos mais caros.

Caso 3: Quantos pedidos existem em cada status?
# Comando SQL:
SELECT status, COUNT(*) AS total_pedidos
FROM pedidos
GROUP BY status
ORDER BY total_pedidos DESC;

# Objetivo: Agrupar os pedidos por status, contar quantos pedidos existem em cada grupo e ordenar os resultados em ordem decrescente  atraves da quantidade de pedidos.

Caso 4: Quantos produtos existem em cada categoria?
# Comando SQL:
SELECT
    c.nome_categoria,
    COUNT(p.id_produto) AS total_produtos
FROM categorias c
LEFT JOIN produtos p
    ON c.id_categoria = p.id_categoria
GROUP BY c.id_categoria, c.nome_categoria
ORDER BY total_produtos DESC;

# Objetivo: Contar quantos produtos tem em cada categoria, incluindo os produtos que não possuem cadastro e ordenar os resultados em ordem decrescente pela quantidade.

Caso 5: Quais clientes realizaram pedidos?
# Comando SQL:
SELECT
    c.nome,
    p.id_pedido,
    p.data_pedido,
    p.status
FROM clientes c
JOIN pedidos p
    ON c.id_cliente = p.id_cliente
ORDER BY p.data_pedido DESC;

# Objetivo: Consultar os clientes que realizaram pedidos com a exibição dos seus nomes, id dos pedidos, datas e os status, colocando em ordem do pedido mais recente para o mais antigo.

Caso 6: Quais produtos aparecem nos pedidos e em quais quantidades?
# Comando SQL:
SELECT
    p.nome AS produto,
    ip.id_pedido,
    ip.quantidade
FROM itens_pedido ip
JOIN produtos p
    ON ip.id_produto = p.id_produto
ORDER BY ip.id_pedido;

# Objetivo: Fazer a relação dos produtos aos seus respectivos pedidos, exibindo o nome do produto, o id do pedido e a quantas unidades de cada produto, ordenados pelo id do pedido.

Caso 7: Quais clientes fizeram mais pedidos?
# Comando SQL:
SELECT
    c.nome AS cliente,
    COUNT(p.id_pedido) AS total_pedidos
FROM clientes c
JOIN pedidos p
    ON c.id_cliente = p.id_cliente
GROUP BY c.id_cliente, c.nome
ORDER BY total_pedidos DESC;

# Objetivo: Agrupar os pedidos por cliente, contar quantos pedidos cada cliente realizou e ordenar os resultados em ordem decrescente pela quantidade de pedidos realizados.



# Obervação: em cada caso é utilizado um comando no MySql para localizar as informações. 

# Projeto autoral para fins de estudo, desenvolvido com dados fictícios.
