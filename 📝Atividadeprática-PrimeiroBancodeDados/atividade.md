## Criação de tabela:
<!-- Criando tabela -->
```mermaid
erDiagram
Cidades{
    int id PK "Gerado automaticamente"
    varchar nome "Nome da cidade"
    numeric populacao "Numero da população Mlhões"
    varchar pais "País"
}
```

---
>Para consultar a tabela:
<p>Segue o código abaixo:<p>

```sql
SELECT * FROM produtos;
```
![alt text](<Captura de tela 2026-08-13 104650.png>)
---
>Para colocar dados na tabela:
<p>Segue o código:<p>

```sql
INSERT INTO produtos(nome,pais,populacao)
VALUES('Jacarta','Indonésia','41913860');
```
![alt text](<Captura de tela 2026-08-13 111022.png>)
---

## Moba

>Para entrar no postgres:

```sql
sudo -u postgres psql
```

No postgres segue as instruções para criar o **banco de dados**:
```sql
CREATE DATABASE "nome do banco de dados";
```