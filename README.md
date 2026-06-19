# aws-gft-desafio-01
Aprendizados Sobre AWS IAM, AWS CLI, AWS Console, S3, EC2, Lambda, EBS e RDS

## IAM (Identity and Access Management)

O IAM é o serviço responsável pelo controle de acesso dentro da AWS.

Com ele é possível:

* Criar usuários
* Criar grupos
* Definir permissões
* Aplicar políticas de segurança
* Controlar quem pode acessar quais recursos

### Boas práticas

Uma boa prática é **não utilizar o usuário Root para atividades do dia a dia**.

O usuário Root possui acesso total à conta e deve ser utilizado apenas para tarefas administrativas críticas.

O ideal é:

1. Criar um usuário administrador pelo IAM.
2. Utilizar esse usuário para o trabalho diário.
3. Criar usuários específicos para cada equipe.
4. Aplicar o princípio do menor privilégio (*Least Privilege*), onde cada usuário acessa apenas o que precisa.

### Automação com AWS CLI

Também é possível automatizar tarefas do IAM utilizando a AWS CLI.

Exemplos:

* Criar usuários automaticamente
* Criar grupos
* Associar permissões
* Gerar credenciais
* Forçar alteração de senha no primeiro acesso

---

# AWS CLI

A AWS CLI é uma ferramenta de linha de comando que permite gerenciar recursos da AWS sem utilizar a Console Web.

Exemplos de comandos:

```bash
aws s3 ls
aws ec2 describe-instances
aws iam list-users
```

### Principais usos

* Automações
* Scripts
* Pipelines CI/CD
* Infraestrutura como Código (IaC)

---

# EC2 (Elastic Compute Cloud)

O EC2 é o principal serviço de computação da AWS.

Ele permite criar servidores virtuais na nuvem.

Essas máquinas podem possuir diferentes configurações de:

* CPU
* Memória RAM
* Armazenamento
* Rede

### Casos de uso

* APIs
* Sistemas Web
* Bancos de dados
* Microsserviços
* Aplicações corporativas

Na prática, o EC2 funciona como um computador alugado dentro da AWS.

---

# S3 (Simple Storage Service)

> O S3 não é um banco de dados.

O S3 é um serviço de armazenamento de objetos.

Ele é utilizado para armazenar:

* Imagens
* Vídeos
* PDFs
* Backups
* Logs
* Arquivos em geral

Os dados ficam organizados em **Buckets**.

Exemplo:

```text
Bucket
 ├── foto.jpg
 ├── contrato.pdf
 └── backup.zip
```

---

# Classes de Armazenamento do S3

Existem diferentes classes de armazenamento para reduzir custos conforme a frequência de acesso aos dados.

## S3 Standard

Arquivos acessados frequentemente.

Exemplos:

* Imagens de um site
* Arquivos de uma aplicação

---

## S3 Standard-IA

(*Infrequent Access*)

Arquivos acessados poucas vezes.

Exemplos:

* Relatórios antigos
* Documentos pouco consultados

---

## Glacier

Arquivos raramente acessados.

Exemplos:

* Documentação legal
* Backups históricos
* Arquivos de compliance

O armazenamento é muito mais barato, porém a recuperação dos arquivos pode demorar.

---

# EBS (Elastic Block Store)

O EBS é um disco virtual conectado a uma instância EC2.

Ele funciona como o SSD ou HD de um computador.

É nele que ficam armazenados:

* Sistema operacional
* Aplicação
* Logs
* Dados persistentes

---

# Snapshots

Os Snapshots são backups dos volumes EBS.

Eles permitem salvar o estado de um disco em determinado momento.

Exemplo:

```text
EC2
 ↓
EBS
 ↓
Snapshot
```

Se ocorrer um problema, como:

* Falha na aplicação
* Corrupção de dados
* Exclusão acidental

É possível restaurar um estado anterior do disco.

---

# RDS (Relational Database Service)

O RDS é o serviço gerenciado de banco de dados relacional da AWS.

Ele permite utilizar bancos como:

* PostgreSQL
* MySQL
* MariaDB
* Oracle
* SQL Server

A AWS cuida de:

* Backups
* Atualizações
* Monitoramento
* Alta disponibilidade

Enquanto a equipe se preocupa apenas com os dados e a aplicação.

---

# Lambda

O Lambda é um serviço *serverless* que executa código sob demanda.

Você envia uma função e ela é executada quando um evento acontece.

### Exemplos de gatilhos

* Upload de arquivo no S3
* Chamada HTTP
* Mensagem em fila
* Evento agendado

### Fluxo comum

```text
Upload no S3
      ↓
Evento
      ↓
Lambda
      ↓
Processamento
```

### Principais vantagens

* Não é necessário administrar servidores
* Escala automaticamente
* Pagamento apenas pelo tempo de execução
* Fácil integração com outros serviços da AWS

```
```
