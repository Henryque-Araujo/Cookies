# Criando e Utilizando Cookies com JavaScript

Produza um cookie dinamicamente a partir de um formulário, utilizando JavaScript, e mostre os valores do cookie em uma página HTML. Para fazer isso, siga os passos abaixo:

## Passos:

1. **Crie uma página HTML de arquivo único:**
   - O arquivo conterá tanto o HTML quanto o JavaScript.

2. **Adicione um formulário na página:**
   - Insira um campo simples para inserção de valores de texto.
   - Exemplo:
     ```html
     <form>
       <label for="valor">Digite um valor:</label>
       <input type="text" id="valor" name="valor">
     </form>
     ```

3. **Melhore a usabilidade com CSS (opcional):**
   - Você pode estilizar o formulário e a página com CSS para torná-los mais agradáveis visualmente.

4. **Adicione um botão para criar o cookie:**
   - Inclua um botão na página para chamar a função que criará o cookie.
     ```html
     <button onclick="criarCookie()">Criar Cookie</button>
     ```

5. **Implemente as funções JavaScript:**
   - Crie as funções `getCookie()` e `setCookie()` conforme explicado em aula.
     ```javascript
     function setCookie(nome, valor, dias) {
       const d = new Date();
       d.setTime(d.getTime() + (dias * 24 * 60 * 60 * 1000));
       let expires = "expires=" + d.toUTCString();
       document.cookie = `${nome}=${valor};${expires};path=/`;
     }

     function getCookie(nome) {
       const cookies = document.cookie.split(';');
       for (let i = 0; i < cookies.length; i++) {
         const c = cookies[i].trim();
         if (c.startsWith(nome + '=')) {
           return c.substring(nome.length + 1);
         }
       }
       return "";
     }
     ```

   - Crie a função `criarCookie()` que:
     - Obtém o valor do campo de texto.
     - Cria o cookie usando `setCookie()`.
     - Exibe o valor do cookie em um elemento HTML.
     ```javascript
     function criarCookie() {
       const valor = document.getElementById('valor').value;
       setCookie('meuCookie', valor, 7);
       document.getElementById('resultado').innerHTML = `Cookie criado: ${getCookie('meuCookie')}`;
     }
     ```

6. **Adicione um elemento para exibir o resultado:**
   - Use uma tag HTML como `h1`, `p` ou `div` para mostrar o valor do cookie.
     ```html
     <div id="resultado"></div>
     ```

7. **Teste a funcionalidade:**
   - Abra o arquivo em um navegador.
   - Preencha o formulário com um valor.
   - Clique no botão para chamar a função `criarCookie()`.

8. **Verifique no navegador se o cookie foi criado:**
   - No navegador, acesse as ferramentas de desenvolvimento (geralmente F12) e procure pelos cookies armazenados no domínio local.

## Exemplo de estrutura básica:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Trabalhando com Cookies</title>
  <style>
    /* Adicione seu CSS aqui */
  </style>
</head>
<body>
  <form>
    <label for="valor">Digite um valor:</label>
    <input type="text" id="valor" name="valor">
    <button type="button" onclick="criarCookie()">Criar Cookie</button>
  </form>
  <div id="resultado"></div>
  <script>
    /* Adicione as funções JavaScript aqui */
  </script>
</body>
</html>
