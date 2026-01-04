# Ambiente Docker / Podman Compose – Laboratório de Desenvolvimento

Este repositório contém um ambiente **Docker Compose / Podman Compose** criado para **facilitar o desenvolvimento, testes e prototipação local** de um projeto baseado em automação, integrações e APIs.

A proposta principal deste setup é:

* padronizar o ambiente de desenvolvimento
* reduzir tempo de setup para novos membros do time
* evitar diferenças entre máquinas
* facilitar testes, experimentação e aprendizado
* permitir reprodução fácil do ambiente em qualquer máquina

> ⚠️ **Aviso importante**
> Este ambiente tem foco exclusivo em **desenvolvimento e protótipo**.
> Uso em produção **não é o objetivo deste repositório**, apenas uma possibilidade futura a ser discutida.

---

## 🧩 Serviços incluídos

O ambiente sobe os seguintes serviços:

* **PostgreSQL** – banco de dados principal
* **n8n** – automação e orquestração de fluxos
* **Redis** – cache, filas e suporte a processamento
* **Evolution API** – serviço de integração externa
* **Adminer** – gerenciamento visual do banco de dados PostgreSQL

Todos os serviços são executados em containers isolados e podem ser iniciados, parados ou recriados de forma simples.

---

## 🏗️ Arquitetura do ambiente

* O ambiente utiliza **volumes persistentes** para dados
* Um **container auxiliar (init)** é responsável por ajustar permissões automaticamente
* Compatível com:

  * Docker
  * Docker Compose
  * Podman (rootless)
  * podman-compose

Essa abordagem evita problemas comuns de permissões, especialmente em ambientes Podman.

---

## 📦 Pré-requisitos

Antes de começar, é necessário ter **um dos conjuntos abaixo** instalado:

### Opção 1 – Docker

* Docker
* Docker Compose

### Opção 2 – Podman

* Podman
* podman-compose

---

## 🚀 Como usar

### 1️⃣ Clonar o repositório

```bash
git clone <url-do-repositorio>
cd <nome-do-repositorio>
```

---

### 2️⃣ Criar o arquivo de variáveis de ambiente

Copie o arquivo de exemplo:

```bash
cp .env.example .env
```

> 🔐 O arquivo `.env.example` contém **valores padrão apenas para desenvolvimento**.
> Ajuste conforme necessário para seu ambiente local.

---

### 3️⃣ Subir o ambiente

**Usando Docker:**

```bash
docker compose up -d
```

**Usando Podman:**

```bash
podman-compose up -d
```

O primeiro startup pode levar alguns minutos, pois:

* imagens serão baixadas
* permissões serão ajustadas automaticamente
* migrations de banco podem ser executadas

---

### 🛑 Parar o ambiente

**Usando Docker:**

```bash
docker compose down
```

**Usando Podman:**

```bash
podman-compose down
```

#### ⚠️ Remover volumes (apaga dados persistidos):

```bash
docker compose down -v
```

---

## 🌐 Acessos pelo navegador

Após subir o ambiente, os serviços podem ser acessados pelas seguintes URLs (considerando as portas padrão definidas no `compose.yaml`):

### 🔁 n8n

```text
http://localhost:5678
```

---

### 🧠 Evolution API

```text
http://localhost:8080
```

> A porta pode variar conforme configuração no `.env`.

---

### 🐘 Adminer

```text
http://localhost:8081
```

---

## 📄 Observações importantes

* Este repositório é voltado para **uso educacional, testes e prototipação**
* Não utilize as credenciais de exemplo em ambientes reais
* Nunca versionar arquivos `.env` reais
* Recomenda-se revisar as variáveis antes de qualquer uso avançado

---

## 🤝 Contribuição

Sugestões, melhorias e ajustes são bem-vindos.

---

## 📌 Resumo

✔ Ambiente padronizado
✔ Setup rápido
✔ Compatível com Docker e Podman
✔ Evita problemas de permissão
✔ Ideal para laboratório de desenvolvimento

---

🚀 **Pronto! O ambiente está preparado para ser usado, estudado e evoluído.**
