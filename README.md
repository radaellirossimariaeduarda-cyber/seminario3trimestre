# seminario3trimestre
Projeto prático do seminário de WEB 1 sobre Svelte e SvelteKit Realizado pelas alunas Maria Eduarda Radaelli Rossi e Luísa Giacomelli WWesterlund.
## Sobre o projeto

Este projeto foi desenvolvido como parte do seminário de WEB 1 do terceiro trimestre, com o objetivo de demonstrar na prática os principais recursos e funcionalidades do ecossistema Svelte e SvelteKit.

A aplicação consiste em uma lista de tarefas (To-do List), permitindo que o usuário adicione, conclua e exclua tarefas.

O projeto demonstra conceitos fundamentais do desenvolvimento de aplicações web modernas, como componentização, propriedades, reatividade, roteamento e carregamento de dados.

## Tecnologias utilizadas

- **Svelte 5:** criação de componentes e gerenciamento de reatividade.
- **SvelteKit:** estruturação das páginas, roteamento e carregamento de dados.
- **JavaScript:** implementação das funcionalidades da aplicação.
- **HTML:** estruturação dos elementos da interface.
- **CSS:** estilização e responsividade.
- **Vite:** ferramenta utilizada no ambiente de desenvolvimento e compilação.

## Estrutura do projeto

```text
seminario3trimestre/
├── src/
│   ├── lib/
│   │   ├── assets/
│   │   ├── index.js
│   │   └── TaskItem.svelte
│   └── routes/
│       ├── +layout.svelte
│       ├── +page.js
│       ├── +page.svelte
│       └── sobre/
│           └── +page.svelte
├── static/
├── app.html
├── package.json
└── README.md
```

## Funcionalidades

A aplicação possui as seguintes funcionalidades:

- Exibição de tarefas iniciais.
- Adição de novas tarefas.
- Marcação de tarefas como concluídas.
- Exclusão de tarefas.
- Contabilização automática das tarefas concluídas.
- Navegação entre a página principal e a página sobre o projeto.

## Conceitos demonstrados

### 1. Componentização

O arquivo `TaskItem.svelte` representa cada tarefa individualmente, permitindo reutilizar o mesmo componente para diferentes elementos da lista.

### 2. Propriedades e comunicação entre componentes

Utilizamos `$props()` para receber informações e funções da página principal, permitindo a comunicação entre os componentes.

### 3. Gerenciamento de estado reativo

Utilizamos `$state()` para armazenar as tarefas e o conteúdo digitado pelo usuário. Quando os valores são modificados, a interface acompanha as alterações automaticamente.

### 4. Valores derivados

Utilizamos `$derived()` para calcular automaticamente a quantidade de tarefas concluídas com base no estado atual da lista.

### 5. Renderização condicional

Utilizamos `{#if}` e `{:else}` para apresentar as tarefas ou uma mensagem informando que não existem tarefas cadastradas.

### 6. Carregamento de dados

O arquivo `+page.js` utiliza a função `load()` para fornecer as tarefas iniciais à página principal.

### 7. Roteamento

O SvelteKit utiliza a organização de arquivos e pastas para definir as rotas da aplicação.

- `/`: página principal com a lista de tarefas.
- `/sobre`: página com informações sobre o projeto.

### 8. Estilização

Utilizamos CSS para organizar os elementos, definir cores, espaçamentos e adaptar a interface a diferentes tamanhos de tela.

## Como executar o projeto

### Pré-requisitos

É necessário ter o Node.js instalado no computador.

### Instalação

Caso as dependências ainda não estejam instaladas, execute:

```bash
npm install
```

### Executando a aplicação

Para iniciar o servidor de desenvolvimento, execute:

```bash
npm run dev
```

Para abrir automaticamente a aplicação no navegador:

```bash
npm run dev -- --open
```

O endereço local será informado pelo terminal, geralmente:

```text
http://localhost:5173
```

## Compilação para produção

Para gerar a versão de produção da aplicação, execute:

```bash
npm run build
```

Para visualizar a versão compilada, utilize:

```bash
npm run preview
```

## Limitações do projeto

Esta aplicação possui finalidade didática e demonstra os principais recursos do Svelte e SvelteKit.

As tarefas são armazenadas apenas no estado da aplicação, não existindo integração com banco de dados ou armazenamento permanente.

Dessa forma, as alterações realizadas pelo usuário não são preservadas após o recarregamento da página.

## Finalidade acadêmica

O projeto faz parte de um seminário sobre o framework Svelte e o meta-framework SvelteKit, apresentando seus conceitos, arquitetura, gerenciamento de estado, componentização e sistema de roteamento.

A demonstração prática busca evidenciar como essas tecnologias podem ser utilizadas na construção de aplicações web organizadas, reativas e reutilizáveis.

## Referências

- SVELTE. Documentação oficial. Disponível em: https://svelte.dev/docs/svelte/overview
- SVELTE. Svelte 5 Migration Guide. Disponível em: https://svelte.dev/docs/svelte/v5-migration-guide
- SVELTEKIT. Documentação oficial. Disponível em: https://svelte.dev/docs/kit/introduction
- SVELTEKIT. Routing. Disponível em: https://svelte.dev/docs/kit/routing
- SV. Svelte CLI. Disponível em: https://github.com/sveltejs/cli

---

**Trabalho de WEB 1 — Seminário do 3º Trimestre**
