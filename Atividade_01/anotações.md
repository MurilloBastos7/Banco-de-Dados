# Atividade de Banco de Dados — Livros

## Sobre a atividade

Nesta atividade, eu criei uma tabela para guardar informações de vários livros. Meu objetivo foi aprender um pouco mais sobre banco de dados e praticar comandos básicos de SQL.

Eu cadastrei livros de vários gêneros, como romance brasileiro, clássicos, ficção científica, fantasia, terror, policial, técnico, história, biografia, autoajuda e infantil.

Depois disso, eu fiz várias consultas para visualizar, filtrar, contar e organizar os livros. No começo, alguns comandos pareceram um pouco complicados, mas fazendo os testes ficou bem mais fácil de entender.

## Criação da tabela

Primeiro, eu criei uma tabela chamada `livros`:

```sql
CREATE TABLE livros(
    id SERIAL PRIMARY KEY,
    nome VARCHAR(60) NOT NULL,
    autor VARCHAR(30) NOT NULL,
    preco DECIMAL(10,2) NOT NULL,
    genero VARCHAR(30) NOT NULL,
    estoque INT NOT NULL,
    ano_publicacao INT NOT NULL
);
```

Nessa parte, eu defini quais informações seriam guardadas:

- `id`: identifica cada livro;
- `nome`: guarda o nome do livro;
- `autor`: guarda o nome do autor;
- `preco`: guarda o preço;
- `genero`: guarda o gênero literário;
- `estoque`: guarda a quantidade disponível;
- `ano_publicacao`: guarda o ano de publicação.

Eu usei o `SERIAL` para gerar o `id` automaticamente e o `PRIMARY KEY` para definir essa coluna como a identificação principal de cada livro.

Também usei o `NOT NULL` para impedir que alguma informação importante fosse deixada vazia.

## Cadastro dos livros

Depois de criar a tabela, eu usei o comando `INSERT INTO` para cadastrar os livros:

```sql
INSERT INTO livros
(nome, autor, preco, genero, estoque, ano_publicacao)
VALUES
('Dom Casmurro', 'Machado de Assis', 29.90, 'Romance Brasileiro', 45, 1899),
('Duna', 'Frank Herbert', 89.90, 'Ficção Científica', 25, 1965),
('O Hobbit', 'J. R. R. Tolkien', 79.90, 'Fantasia', 35, 1937);
```

No `INSERT INTO`, eu informei primeiro quais colunas receberiam os dados. Depois, dentro do `VALUES`, coloquei as informações de cada livro na mesma ordem.

Por exemplo, no livro **Dom Casmurro**, eu coloquei o autor, o preço, o gênero, a quantidade no estoque e o ano em que ele foi publicado.

## Bloco 1 — Conhecendo a tabela

No primeiro bloco, eu fiz consultas mais básicas para visualizar e conhecer melhor os dados cadastrados.

### Mostrando os primeiros livros

```sql
SELECT *
FROM livros
LIMIT 10;
```

Eu usei o `SELECT *` para selecionar todas as colunas da tabela. Depois, usei o `LIMIT 10` para mostrar somente os 10 primeiros livros.

### Mostrando informações específicas

```sql
SELECT nome, autor, preco
FROM livros;
```

Nessa consulta, eu escolhi mostrar somente o nome, o autor e o preço. Isso é útil quando eu não preciso visualizar todas as informações da tabela.

### Mostrando os gêneros sem repetir

```sql
SELECT DISTINCT genero
FROM livros
ORDER BY genero;
```

Eu usei o `DISTINCT` para não mostrar gêneros repetidos. O `ORDER BY` organizou os gêneros em ordem alfabética.

### Contando todos os livros

```sql
SELECT COUNT(*) AS total_livros
FROM livros;
```

O `COUNT(*)` conta todos os registros da tabela. Eu usei o `AS total_livros` para dar um nome mais fácil de entender para o resultado.

### Contando os autores diferentes

```sql
SELECT COUNT(DISTINCT autor) AS total_autores
FROM livros;
```

Nesse comando, eu juntei o `COUNT` com o `DISTINCT`. Assim, consegui contar os autores sem repetir aqueles que possuem mais de um livro cadastrado.

Essa parte foi um pouco mais complicada no começo, mas depois entendi que o `DISTINCT` remove as repetições antes de o `COUNT` fazer a contagem.

### Mostrando os livros mais caros

```sql
SELECT nome, preco
FROM livros
ORDER BY preco DESC
LIMIT 5;
```

Eu usei o `DESC` para organizar os preços do maior para o menor. Depois, usei o `LIMIT 5` para mostrar somente os 5 livros mais caros.

### Mostrando os livros com menor estoque

```sql
SELECT nome, estoque
FROM livros
ORDER BY estoque ASC
LIMIT 5;
```

Nesse caso, eu usei o `ASC` para organizar o estoque do menor para o maior. Dessa forma, os livros com menos unidades aparecem primeiro.

Essa consulta pode ajudar a descobrir quais livros estão mais próximos de acabar.

## Bloco 2 — Filtros numéricos

No segundo bloco, eu comecei a usar o `WHERE`. Esse comando permite criar condições e mostrar somente os livros que atendem ao filtro.

### Livros do gênero Técnico

```sql
SELECT nome, estoque
FROM livros
WHERE genero = 'Técnico';
```

Eu usei o `WHERE` para mostrar somente os livros que possuem o gênero Técnico. No resultado, aparecem apenas o nome e a quantidade no estoque.

### Livros que custam mais de R$ 200,00

```sql
SELECT nome, preco
FROM livros
WHERE preco > 200;
```

O sinal `>` significa “maior que”. Por isso, essa consulta mostra somente os livros com preço acima de R$ 200,00.

### Livros entre R$ 40,00 e R$ 70,00

```sql
SELECT nome, preco
FROM livros
WHERE preco BETWEEN 40 AND 70;
```

Eu usei o `BETWEEN` para buscar os preços que estão dentro de um intervalo. Nesse caso, ele mostra os livros que custam entre R$ 40,00 e R$ 70,00.

### Livros com estoque abaixo de 5 unidades

```sql
SELECT *
FROM livros
WHERE estoque < 5;
```

O sinal `<` significa “menor que”. Com essa consulta, eu consegui encontrar os livros que possuem menos de 5 unidades no estoque.

Isso pode ser usado para identificar quais livros precisam de reposição urgente.

### Livros publicados antes de 1900

```sql
SELECT *
FROM livros
WHERE ano_publicacao < 1900
ORDER BY ano_publicacao ASC;
```

Primeiro, eu usei o `WHERE` para selecionar os livros publicados antes de 1900. Depois, usei o `ORDER BY` com `ASC` para organizar do mais antigo para o mais recente.

### Livros publicados entre 2010 e 2020

```sql
SELECT nome, ano_publicacao, genero
FROM livros
WHERE ano_publicacao BETWEEN 2010 AND 2020
ORDER BY ano_publicacao ASC;
```

Eu usei o `BETWEEN` para selecionar somente os livros publicados entre 2010 e 2020.

Depois, usei o `ORDER BY` com `ASC` para organizar os anos do menor para o maior. No resultado, mostrei somente o nome, o ano de publicação e o gênero de cada livro.

## Principais comandos que eu aprendi

Durante a atividade, eu pratiquei os seguintes comandos:

- `CREATE TABLE`: usei para criar a tabela;
- `INSERT INTO`: usei para cadastrar os livros;
- `SELECT`: usei para consultar os dados;
- `WHERE`: usei para aplicar filtros;
- `ORDER BY`: usei para organizar os resultados;
- `ASC`: organizei do menor para o maior;
- `DESC`: organizei do maior para o menor;
- `LIMIT`: limitei a quantidade de resultados;
- `COUNT`: contei os registros;
- `DISTINCT`: removi os resultados repetidos;
- `BETWEEN`: procurei valores dentro de um intervalo;
- `AS`: coloquei um nome mais fácil de entender no resultado.

## Conclusão

Com essa atividade, eu consegui entender melhor como funciona uma tabela dentro de um banco de dados. Aprendi a criar a tabela, cadastrar vários livros e fazer consultas diferentes.

Também pratiquei como selecionar informações específicas, organizar os resultados, fazer contagens e aplicar filtros.

Alguns comandos foram um pouco mais difíceis no começo, principalmente o `COUNT` junto com o `DISTINCT`. Porém, depois de fazer, consegui entender melhor.

No geral, essa atividade foi importante para eu aprender o básico de SQL e perceber como os dados podem ser guardados e consultados de uma forma mais organizada.