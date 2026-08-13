## Aula 03
Para apagar um bando de dados, utilizamos o comando:

```sql
DROP DATABASE nome do banco de dados;
```

>Não esquecer do ;

---

**Modelagem do banco de dados**

```mermaid
erDiagram
PRODUTOS{
    int id PK "Gerado automaticamente"
    varchar nome "Nome do produto"
    numeric valor "Preço do produto em R$"
    int estoque "Ira armazenar a quantidade de produtos no estoque"
}
```
**Apos modelar, iremos executar as etapas de criação e inserção de dados.**
---

Para criar a primeira tabela, usamos os comandos:
```sql
CREATE TABLE produtos(
    id INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    valor NUMERIC(10,2) NOT NULL,
    estoque INT NOT NULL DEFAULT 0 
);
```

---

Para consultar a tabela, usamos o comando:
```sql
SELECT * FROM produtos;
```

---

Para inserir dados na tabela:
```sql
INSERT INTO produtos(nome,valor,estoque)
VALUES('Caneta','1.50','100');
```
![alt text](image.png)
Imagem de exemplo.