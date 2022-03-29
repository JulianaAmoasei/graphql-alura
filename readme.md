- problema: vários pacotes descontinuados
- tem que instalar `npm i @vscode/sqlite3` pro knex funcionar
- tem que instalar também o json-server em global `npm i -g json-server`
- não esquecer de subir o servidor em 3000 `json-server api/data/dados.json
- abrir conta no heroku
- instalar o `heroku-cli` (https://devcenter.heroku.com/articles/heroku-cli)
- logar com `heroku-login` (abrir no navegador)
heroku: Press any key to open up the browser to login or q to exit: 
Opening browser to https://cli-auth.heroku.com/auth/cli/browser/ec23c83f-1b1d-42d9-a56c-903ead55734e?requestor=SFMyNTY.g2gDbQAAAAwxODkuNjIuNDcuNzFuBgA4cAXWfwFiAAFRgA.b6nT1IK2U9fi_eKawMAhHYH3NpysXlbCJSq5SILjX3k

​​You can’t use the -i option if you have multi-factor authentication enabled due to a technical dependency on web browsers for verification.

- criar `new app`
Escolher EUA
Choose a name your app (this will be your <HEROKU_APP_NAME>) and click Create app.

- Lembrar que para fazer o deploy tem que estar no seu repositório do gh (se só fizer git clone o remote vai estar apontando pra `alura-cursos`)
- o Apollo Server já faz internamente grande parte da configuração para o deploy via Heroku
- Alterações no código: adicionar variáveis de ambiente
```js
server.listen({ port: process.env.PORT || 4000 }).then(({url}) => {
  console.log(`Servidor rodando na porta ${url}`)
})
```

- Criar um `Procfile`
The Procfile is always a simple text file that is named Procfile without a file extension. For example, Procfile.txt is not valid.
The Procfile must live in your app’s root directory. It does not function if placed anywhere else.
```
web: node api/index.js
```
Sendo `api/index.js` o local do arquivo ponto de entrada da aplicação
A Procfile is not required to run Apollo Server on Heroku. If you don't provide a Procfile, attempts to run the start script that's defined in your package.json file.

- Deploy via git/heroku cli
Veja se está logado no `heroku login`
Atualizar repositório na `main`
