---
title: "Trilha Cypress #1: O que é Cypress, iniciando projeto novo e visitando a primeira página web"
date: 2026-01-25 20:00 -0300
categories: [cypress]
tags: [cypress, automacao_de_testes, trilha_cypress]
---

Olá, leitor(a)! Como vai?

Hoje inicio oficialmente a trilha Cypress e, antes de qualquer coisa, para que esta jornada seja proveitosa, é importante que você tenha uma leve bagagem sobre sistemas operacionais e execução de comandos no terminal, pois nem tudo será extremamente detalhado. A ideia é que seja uma jornada direto ao ponto e sem muita enrolação.

Vamos lá?

## O que é o Cypress?

[Cypress](https://www.cypress.io/#create) é um framework de testes end-to-end (E2E), construído especificamente para aplicações web.

## Pré-requisitos de ambiente

- **Node.js** (versão 18 ou superior)
- **npm** ou **yarn**
- **Editor de código** da sua preferência (usarei o clássico [VS Code](https://code.visualstudio.com/))

> Observação: Os exemplos serão feitos baseados no sistema operacional Linux, portanto, pode ser que você note algumas diferenças de comandos se estiver utilizando Windows. Neste caso, recomendo utilizar o [git bash](https://git-scm.com/install/windows) para conseguir acompanhar o passo a passo da melhor forma.
{: .prompt-info }

Para verificar se já tem instalado o **node** e **npm** instalado, execute no terminal:

```bash
node --version
npm --version
```

Se não tiver, instale o Node.js pelo [site oficial](https://nodejs.org/) (npm já vem junto com o node)

## Criando o projeto

Vamos criar um projeto do zero. Abra o terminal e execute os comandos abaixo ou então crie os diretórios pela interface do seu sistema operacional.

```bash
# Crie uma pasta para o projeto
mkdir cypress-trilha
cd cypress-trilha

# Inicialize o projeto Node.js
npm init -y
```

Acesse o diretório com o seu editor de código e então execute: 

```bash 
npm init -y 
```

O comando `npm init -y` cria um arquivo `package.json` com configurações padrão.

## Instalando o Cypress

Nesta trilha vamos utilizar o Cypress na versão 15.9.0 por ser a versão mais recente na data deste post. Execute o seguinte comando:

```bash
npm install cypress@15.9.0 --save-dev
```

## Abrindo o Cypress pela primeira vez

Após a instalação, execute:

```bash
npx cypress open
```

Se tudo certo, você deverá visualizar uma tela semelhante à esta:

![Tela inicial do Cypress pós instalação](/assets/img/trilha-cypress-01/01.png)

Avance pelo botão de continuar, selecione a opção **E2E Testing** e avance novamente até a página que mostra os navegadores instalados na sua máquina.

Por padrão, o Cypress já vem com o [Electron](https://www.electronjs.org/pt/docs/latest/) instalado, que é útil para usarmos em ambiente de desenvolvimento, mas confesso que prefiro utilizar navegadores reais como Chrome ou Firefox.

Se chegou até esta etapa sem maiores problemas, você já está praticamente com o ambiente pronto para começar a desenvolver cenários.

## Visitando a primeira página web

Como primeiro teste da ferramenta, faremos um cenário bem simples, baseado nesta aplicação: [Sauce Demo](https://www.saucedemo.com/). Descrição do cenário:

```
1 - Acessar a página web
2 - Validar que o texto Swag Labs está visível
3 - Validar que o campo de usuário está visível e habilitado
4 - Validar que o campo de senha está visível e habilitado
5 - Validar que o botão de login está visível e habilitado
```

Dentro do diretório cypress, crie um novo diretório chamado **e2e**. Dentro do diretório e2e, crie um arquivo chamado **login.cy.js**.

Dentro deste arquivo, copie o seguinte conteúdo:

```javascript
context('Login', () => {
  it('Deve acessar a página de login', () => {
    cy.visit('https://www.saucedemo.com/')

    cy.get('.login_logo')
      .should('be.visible')
      .and('have.text', 'Swag Labs')
    
    cy.get('[data-test="username"]')
      .should('be.visible')
      .and('be.enabled')

    cy.get('[data-test="password"]')
      .should('be.visible')
      .and('be.enabled')

    cy.get('[data-test="login-button"]')
      .should('be.visible')
      .and('be.enabled')
  })
})
```

Após copiar, execute o comando `npx cypress open` novamente. Selecione um navegador da sua preferência e então selecione este arquivo que acabamos de criar. 

![Visitando a primeira página web](/assets/img/trilha-cypress-01/02.png)

Não focarei na explicação de cada comando, pois o foco deste post é apenas garantir que a ferramenta funcionou corretamente e de que possamos avançar para a próxima etapa: comandos básicos do Cypress.

Até o próximo post!