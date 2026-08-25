## Parte 01
Criação de tabela:

```sql
CREATE TABLE produtos(
    id SERIAL PRIMARY KEY,
    nome VARCHAR(60) NOT NULL,
    valor DECIMAL(10,2) NOT NULL,
    categoria VARCHAR(30) NOT NULL,
    estoque INTEGER NOT NULL
)
```

--- 

Em uma base de dados muito grande, é interessante filtrar registros:

```sql
SELECT * FROM produtos LIMIT 5;
```

## Parte 02
Para filtrar por colunas:

```sql
SELECT nome,valor,categoria FROM produtos;
```

---

Filtrar categorias distintas:

```sql
SELECT DISTINCT categoria FROM produtos ORDER BY categoria;
```

---

```sql
SELECT nome,estoque FROM produtos WHERE categoria = 'Redes';
```

---

```sql
SELECT nome,estoque FROM produtos WHERE valor > 1000;
```

---

```sql
SELECT nome,estoque FROM produtos WHERE valor BETWEEN 100 AND 500;
```

---

Busca por trecho de texto:

```sql
SELECT nome,estoque,valor FROM produtos WHERE nome LIKE 'SSD%'
```

