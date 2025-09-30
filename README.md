# 📊 Banco API - Testes de Performance com k6

Este repositório contém testes de performance automatizados para a [Banco API](https://github.com/juliodelimas/banco-api), utilizando o [k6](https://k6.io/) como ferramenta principal.
O objetivo é validar a escalabilidade, resiliência e tempo de resposta dos endpoints da API sob diferentes cargas de usuários.

---

## 🚀 Tecnologias Utilizadas

- **JavaScript (ES6+)** → Linguagem utilizada para escrever os cenários de teste.
- **[k6](https://k6.io/)** → Ferramenta de carga e performance de APIs e serviços.
- **[GJSON]** → Para extração de dados em respostas JSON.
→ Variáveis de ambiente para configuração dinâmica (ex: `BASE_URL`).

---

## 📂 Estrutura do Repositório

```plaintext
banco-api-performance/
├── fixtures/              # Dados de entrada para os testes (ex: uduários, payloads)
├── helpers/               # Funções utilitárias reutilizavéis para interação com a API
├── tests/                 # Contém os arquivos de teste organizados por módulo da API
│   ├── transferencias.test.js
│   ├── login.test.js
│
├── config                 # Arquivo de configuração de variáveis de ambiente
├── utils/                 # Funções utilitárias reutilizavéis (ex.: variáveis, funções de apoio)
│   └── variaveis.js
│
└── README.md              # Documentação do projeto
```

---

## 🎯 Objetivo de Cada Grupo de Arquivos

- **`fixtures/`** → Dados de entrada para os testes (ex: uduários, payloads).
- **`helpers/`** → Funções utilitárias reutilizavéis para interação com a API.
- **`tests/`** → Contém os arquivos de teste organizados por módulo da API (ex.: login, transferências).
- **`utils/`** → Armazena variáveis globais e funções auxiliares para facilitar a reutilização de código.
- **`config`** → Arquivo de configuração de variáveis de ambiente.

---

## ⚙️ Instalação do Projeto

1. **Clone este repositório**:
   ```bash
   git clone https://github.com/conectef/banco-api-performance.git
   cd banco-api-performance
   ```

2. **Configure as Variáveis de Ambiente**:
   Altere o arquivo `config.local.json` e defina a URL base da API a ser testada:

```json
{
    "baseUrl": "http://localhost:3000"
}
```

> Essas variáveis serão usadas dinamicamente nos testes para montar as requisições.
---

## ▶️ Execução dos Testes

Para rodar os testes de performance, utilize o **k6** passando o arquivo desejado, por exemplo:

```bash
k6 run tests/transferencias.test.js
```

> 🔑 **Importante**: todos os testes utilizam a variável de ambiente `BASE_URL` como base para os endpoints, caso não esteja usando um `config.local.json` ou uma abordagem de carregamento automático:

```bash
k6 run tests/transferencias.test.js -e BASE_URL=http://localhost:3000"
```

---

## 📈 Relatórios em Tempo Real e Exportação

O k6 permite acompanhar os resultados **em tempo real via dashboard web** e também exportar relatórios automaticamente.
Para isso, utilize as variáveis de ambiente do próprio k6:

```bash
K6_WEB_DASHBOARD=true \ K6_WEB_DASHBOARD_EXPORT=html-report.html \ k6 run tests/transferencias.test.js \  -e BASE_URL="http://localhost:3000"
```

- **`K6_WEB_DASHBOARD=true`** → habilita o relatório em tempo real via navegador.
- **`K6_WEB_DASHBOARD_EXPORT=html-report.html`** → exporta o relatório final em formato HTML.

Após a execução, basta abrir o arquivo `html-report.html` no navegador para visualizar os resultados detalhados.

---

📌 **Repositório oficial**: [banco-api-performance](https://github.com/conectef/banco-api-performance)
