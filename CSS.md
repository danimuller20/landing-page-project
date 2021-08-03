# Flex-box

Ao ativar o `display: flex` em um container no css, as seguintes configurações vem por padrão:
```css
.flex-container {
  display: flex;
  /* configurações padrão */
  flex-direction: row; /* eixo horizontal*/
  justify-content: flex-start; /*move os itens em relação ao eixo principal, nesse caso horizontal*/
  align-items: stretch;/*move os itens em relação ao eixo perpendicular, nesse caso vertical*/
  align-content: initial; /*Alinha todo o conteúdo em relação ao eixo perpendicular*/

/* Possíveis configurações */
  flex-direction: column; /* eixo vertical*/
  flex-wrap: wrap; /*quebra a linha*/
  flex-flow: column wrap; /*Atalho paar definir a direção e a quebra ou não de linhas.*/
}

.flex-item {
  width: 33.33%; /*mesmo espaço para cada item.*/
  flex-grow: 1; /*Permite a distribuição de espaço igualmente dividido entre os elementos, se o valor for 0 ele não permite a distribuição do espaço.*/
  flex-basis: 320px; /*É o espaço fornecido para cada elemento antes do flex-grow dividir o espaço em branco.*/
  flex-shrink: 1; /*Para permitir que o elemento diminua o tamanho em relação ao flex-basis que foi definido, o valor 0 não permite que o item diminua.*/

  flex: 1 1 320px; /*Atalho para definir o grow, shrink e o basis, nessa ordem*/
}
.flex-item:nth-child(2) {
  flex: 2 1 320px; /*A primeira opção define a proporção de espaços sobrando que o elemento vai receber a mais que os outros*/

  flex: 1 2 320px; /*A segunda opção define a proporção que o elemento deve diminuir em relação aos outros*/
}
.flex-item:nth-child(3) {
  align-self: flex-end; /*Alinha o item no eixo perpendicular*/
}
.flex-item:nth-child(1) {
  order: 1; /*Ordena o item, valores positivos colocam para o final, e valores negativos colocam para o inicio, o valor padrão é 0*/
}
```

# Grid

```html
<body>
  <div class="container">
    <div class="grid">
      <div>1</div>
      <div>2</div>
      <div>3</div>
      <div>4</div>
      <div>5</div>
    </div>
  </div>
</body>
```

```css
.container {
  max-width: 1200px;
  margin: 0 auto;
  overflow-x: hidden;
/* Correção de gap */
}

.grid {
  margin-right: -30px; /* Correção de gap */
  display: grid;
  grid-template-columns: 1fr 2fr; /*Define o tamanho de cada coluna e quantas colunas queremos, cada fragmento é uma coluna*/
  grid-template-columns: repeat(10, 1fr); /*Nesse caso teremos 10 colunas com um fragmento cada uma*/
  grid-template-columns: repeat(3, 1fr 2fr); /*Agora teremos 3 colunas com 1 fragmento e 3 colunas com 2 fragmentos por linha*/
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr)); /*Grid responsivo, a quantidade de colunas é automatizada e ela quebra as colunas conforme necessário dependendo do tamanho da tela*/
  grid-template-rows: 2fr 1fr; /*Configuração de fragmentos para as linhas*/
  grid-template-rows: repeat(3, 1fr 2fr); /*3 linhas com 1 fragmento e 3 linhas com 2 fragmentos por linha*/
  /* Podemos usar as mesmas configurações do " grid-template-columns" para " grid-template-rows" */

  grid-template-columns: [um] 1fr [dois] 1fr [tres] 1fr [quatro];
  /* Dando nome aos bois, podemos nomear o número de colunas */

  row-gap: 30px; /*Espaço entre as linhas da grid*/
  column-gap: 30px; /*Espaço entre as colunas da grid*/
  gap: 30px 80px; /*Espaço de 30px entre as linhas e 80px entre as colunas*/
}

.grid div:nth-child(5) {
  grid-column-start: 2;
  grid-column-end: 4;
  grid-row-start: 6;
  grid-row-end: 2;
  /*Faz com que o item selecionado ocupe o espaço especificado*/
  grid-row: span 2; /*Faz o span de 2 linhas, o item ocupa duas linhas da grid*/
  grid-column: span 2; /*Faz o span de 2 colunas, o item ocupa duas colunas da grid*/

  grid-column-start: um;
  grid-column-end: quatro;
  /* Utilização das variáveis criadas acima */
  grid-column: um / quatro; /*Uso com atalho*/
  /* Ou */
  grid-column: 1 / 4;
  grid-column: span 2 / 3; /*Span de duas colunas que termina na coluna 3*/
  grid-row: 1 / 4; /*Span inicia na linha 1 e vai até a linha 4*/

  grid-area: 1 / 1 / 4 / 4; /* Atalho para usar o grid-column e grid-row, nesse caso inicia na linha 1 e na coluna 1 e termina na linha 4 e na coluna 4 */
}
```

# redux slices
Redux rtk
