## Configuração do servidor educacional
O objetivo é simular um ambiente real de produção
```mermaid
graph LR
A[Cliente]<--<b>Dados-->B[Servidor]
```
---
**Objetivo**:
- Experiencia real de mercado,
- Administração de recursos,
- Experiencia em servidores Linux.

## Servidor de arquivos
Servidor educacional para arquivos, assim não dependendo da rede externa.

```mermaid
graph TD
a[servidor Senai \\10.87.36.10] --Arquivos--> b[Computador]
```
**Credenciais**:
- aluno
- aluno

--- 
## Servidor de Desenvolvimento
Cada aluno recebe seu própio acesso.
Cada maquina recebe um endereço de IP diferente

>**Meu SERVIDOR**: 192.168.10.21

|Recurso|Configuração|
|-------|------------|
|CPU|2 cores|
|RAM|512 MB|
|DISCO|6 GB|
|SISTEMA OPERACIONAL|Ubuntu 26.04 LTS|
|Acesso| SSH (Secure Shell)|

Dados de Acesso
|Campo|Valor|
|-----|-----|
|Ip do container|192.168.10.27|
|Usuario|Root|
|Senha inicial|aluno01

Comando para visualizar os os usos dos recursos:
```bash
htop
```
Comando para alterar a senha:
```bash
passwd
```
---

## Banco de Dados
- **Dados:** Informações isoladas que não dizem muita coisa. **Ex: Jogo, Escola, Dinheiro**
- **Informaçao:** Dados estruturados. **Ex: Joguei na escola por dinheiro**
- **Conhecimento:** O que podemos extrair a partir das informações. **Ex: Ele joga na escola**

```mermaid
graph LR
A[Dado: Celular] --> B[Processamento] --> C[Informaçao: O cliente precisa de um celular]
```
---

O fluxo normal de um banco de dados está representado a seguir:
```mermaid
graph LR
A[Usuario] --Requisição--> B[Aplicação] --> C[(Banco de dados)] --> B --> A
```
---
>Por qual razão, as empresas não salvam os dados em arquivos comuns?

```mermaid
graph TD
A[Guardar dados] --> B[(Banco de Dados)] 
A[Guardar Dados] --> C[Aquivos/Planilhas]
B --> B1[Varios usuários ao mesmo tempo]
B --> B2[Backup e Sincronização]
B --> B3[Consultas otimizadas e rápidas]
C --> C1[Um arquivo por vez]
C --> C2[Backup ineficiente]
```
---

## SGBD
Sistema gerenciador de Banco de Dados

Exemplos:
- PostgreSQL
- MySQL
- MsSQL
- Oracle DB
- SQLite

>POSTGRESQL: SGBD OpenSource e muito completo

Primeiro, começamos atualizando os pacotes:
```bash
sudo apt update && upgrade
```

Para instalação do Postgresql:
```bash
sudo apt install -y postgresql
```