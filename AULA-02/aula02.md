## Aula 02
Para verificar o status e demais informações do banco de dados, utilizamos o comando:
```bash
pg_lsclusters
```
---
![alt text](image.png)

---

Para acesso, via root, sem senha (SOCKET LOCAL), utilizamos o comando:
```bash
sudo -u postgres psql
```
>Com esse comando, não preciso mostrar quem o meu usuário é, o Linux já faz a autentificação.

>`\q` retorna ao usuário anterior `\quit`.

Para alteração de senha do usuário Postgres, utilizamos o comando:
```sql
ALTER USER postgres PASSWORD 'sesi';
```

Apos alteração da senha, o acesso, via localhost (Socket Externo), é feito atraves do comando:
```bash
sudo psql -h 127.0.0.1 -U postgres
```

Configurações iniciais do POSTGRES:
- Para habilitar conexões externas, de outros IPs, foi necessário as seguintes etapas:
1. Navegar ate a pasta do POSTGRESQL (`/etc/postgresql/18/main/`).
2. Editar o arquivo `postgresql.conf` atraves do comando:

```bash
sudo nano postgresql.conf
```

3. Editar a linha listen_adresses = `'*'`;

4. Editar o arquivo **`pg_hba.conf`**

5. Nas ultimas, linhas adicionamos as seguintes configurações:

---
**`host all all 0.0.0.0/24 scram-sha-256`**
**`host all all 10.87.47.0/24 scram-sha-256`**
![alt text](image-1.png)

---

**Criação de banco de dados**

```mermaid
graph TD
A[(Banco de Dados)]
```

Para criar um Banco de dados, utilizamos o comando:
```sql
CREATE DATABASE cena;
```

Para verificar os bancos existentes:
```sql
\l
```

Para entrar no banco de dados:
- Baixar a extensão `PostgreSQL`.
- Colocar seu endereço IP.
- Nome do Banco de Dados.
- Senha do Banco de Dados.
- Conectar no seu Banco de Dados.

>Caso o Banco de Dados **não apareça** na extensão, é preciso **resetar**, com o seguinte comando:
```bash
sudo systemctl restart postgresql
```
