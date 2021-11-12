![](https://i.imgur.com/xG74tOh.png)

### Aesse o Link para conferir o resultado ;): 
https://anacarlaalmeida-s.github.io.

* Projeto concluído utilizando apenas Html, Css e JS.

# Desafio | Front-end - Módulo 2

Sua primeira tarefa como desenvolvedor é criar uma aplicação para um serviço de streaming (pense num Netflix).

Seu papel é construir um website com [o seguinte design](https://www.figma.com/file/AL6hZ3Lq16Uj8mw1o4BzAK/Desafio-front-academy-2?node-id=0%3A1) que permita: (funcionalidades com * ao lado são obrigatórias)

- Visualização de filmes (*)
- Paginação de filmes (*)
- Busca de filmes (*)
- "Filme do dia" (*)
- Modal de filme (*)
- Mudança de tema

Os dados do website serão requisitados da [seguinte API](https://tmdb-proxy.cubos-academy.workers.dev/3/)

## Detalhamentos de Requisitos

### Visualização de filmes

Assim que o website for aberto, a listagem de filmes deverá ser preenchida com as informações do [seguinte endpoint](https://tmdb-proxy.cubos-academy.workers.dev/3/discover/movie?language=pt-BR&include_adult=false)



A estrutura HTML deverá ser a seguinte:
![](https://i.imgur.com/s8j6m3E.png)

Informações do retorno da API necessárias para o preenchimento:
- background-image da `<div class="movie">` === poster_path
- texto do `<span class="movie__title">` === title
- texto do `<span class="movie__rating">` === vote_average

Essa estrutura terá que ser criada para **cada filme** poderá ser construida dinamicamente pela DOM, porém, isso **não é obrigatório**.

Cada filme deverá ser colocado dentro da `<div class="movies">`

### Paginação de filmes

Você poderá assumir que sempre existirão 4 páginas (0, 1, 2, 3) por conta do número de filmes em média ser 20 e, seu website sempre irá mostrar no máximo 5 por vez.

O `<button class="btn-prev">`, quando clicado, se não estiver na página 0, terá que voltar 1 página, se não, levará o usuário para a página 3
O `<button class="btn-next">`, quando clicado, se não estiver na página 3, terá que avançar 1 página, se não, levará o usuário para a página 0

Ao voltar ou avançar uma página, os filmes em tela serão atualizados corretamente.

### Busca de filmes

O usuário poderá buscar um filme por meio do `<input class="input">`

Quando o usuário pressionar a tecla "Enter" enquanto estiver com foco no inputm, algumas coisas teram que acontecer:
- O usuário terá que ser levado para a página 0
- Se o input possuir algum valor, você deverá realizar uma busca [no endpoint](https://tmdb-proxy.cubos-academy.workers.dev/3/search/movie?language=pt-BR&include_adult=false) passando um parametro de query "query" com o valor do input. Ex: Buscando por Matrix https://tmdb-proxy.cubos-academy.workers.dev/3/search/movie?language=pt-BR&include_adult=false&**query=Matrix**
- Se o input não possuir valor nenhum, você deverá realizar a mesma busca que é feita para preencher os filmes iniciais (Visualização de filmes)
- O valor do input terá que ser limpo

### "Filme do dia"

Assim que o website for aberto, o filme do dia deverá ser preenchido com as informações do [endpoint geral](https://tmdb-proxy.cubos-academy.workers.dev/3/movie/436969?language=pt-BR) e do [endpoint de videos](https://tmdb-proxy.cubos-academy.workers.dev/3/movie/436969/videos?language=pt-BR).

A estrutura HTML deverá ser a seguinte:
![](https://i.imgur.com/72ixMvR.png)

Informações do retorno do **Endpoint Geral** necessárias para o preenchimento:
- background-image da `<div class="highlight__video">` === backdrop_path
- texto do `<h3 class="highlight__title">` === title
- texto do `<span class="highlight__rating">` === vote_average
- texto do `<span class="highlight__genres">` === genres (como genres é um array de objetos, você deverá criar uma string concatenando todos os valores de genre.name e separando-os por vírgula)
- texto do `<span class="highlight__launch">` === release_date (como release_date é uma data, você **poderá** transforma-lá em outro formato)
- texto do `<p class="highlight__description">` === overview

Informações do retorno do **Endpoint de vídeos** necessárias para o preenchimento:
- href do `<a class="highlight__video-link">` === concatene a string "https://www.youtube.com/watch?v=" com o valor de **key** (como o Endpoint de vídeos retorna um array, você deverá pegar o valor de **key** do primeiro item)

### Modal de filme

Ao clicar na `<div class="movie">` a `<div class="modal hidden">` deverá perder a classe "hidden" (isso irá **abrir** o modal)

Assim que o modal for **aberto**, ele deverá ser preenchido com as informações do [seguinte endpoint](https://tmdb-proxy.cubos-academy.workers.dev/3/movie/?language=pt-BR) passando um parametro de rota com o valor do **id** do filme. Ex: Buscando pelo filme com id 436969 https://tmdb-proxy.cubos-academy.workers.dev/3/movie/**436969**?language=pt-BR.


A estrutura HTML deverá ser a seguinte:
![](https://i.imgur.com/quJYytr.png)

Informações do retorno da API necessárias para o preenchimento:
- texto do `<h3 class="modal__title">` === title
- src da `<img class="modal__img">` === backdrop_path
- texto do `<p class="modal__description">` === overview
- texto da `<div class="modal__average">` === vote_average
- **ISSO NÃO É OBRIGATÓRIO**
  - para cada genre, você deverá criar um `<span class="modal__genre">`, colocar como texto o valor de genre.name e adicioná-lo na `<div class="modal__genres">`

O modal poderá ser "fechado" por meio de um clique nele próprio ou na `<img class="modal__close">`, ao clicar em qualquer um dos dois, a classe "hidden" deverá ser adicionada a `<div class="modal">`

### Mudança de tema **NÃO OBRIGATÓRIO**

Ao clicar na `<img class="btn-theme">`, caso o **tema atual** seja "light" ou "claro", o mesmo deverá ser trocado para o tema "dark" ou "escuro", após isso, você deverá modificar o tema (imagens e cores) do seu website de acordo com o Figma. Essa troca de tema, poderá ser facilitada caso seja feita por meio da troca de variáveis CSS.

