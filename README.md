$${\text{\Huge{\color{orange}Epidemological Simulation - Ilum 2023}}}$$
$$\\ $$


$${\text{\Huge{\color{purple}READ ME FINAL:}}}$$
$$\\ $$


Nesta parte, será apresentado em tópicos a operação da simulação em questão e, abaixo, serão apresentados os relatórios atualizados em cada aula, juntamente aos textos explicativos detalhadamente.


<li> O objetivo desse código é realizar a simulação de evolução epidemiológica em uma determinada cidade em que o próprio usuário irá definir. </li>
<li> O código é programado de maneira a relacionar um vírus em que, dependendo dos parâmetros decididos por quem irá executá-lo, consiga apresentar o comportamento das pessoas em relação à infecção. O código encontra-se abaixo: </li>
<li> Existem vários inputs a serem comentados: </li>
<li> 1. Tamanho da cidade mxn: indica a escala da cidade. O usuário pode inserir quaisquer valores que desejar, ressaltando que a letra "x" (em minúsculo) deve estar entre os números para as dimensões da escala. Por exemplo: 40x40, 20x60. </li>
<li> 2. Máximo de passos por dia em porcentagem decimal da própria cidade (0.0 - 1.0): representa o quanto os habitantes irão se movimentar. Por exemplo, em uma escala 100x100, se o usuário inserir o valor máximo (1.0), ele poderá se movimentar no máximo até um décimo da escala, ou seja, o seu limite será um quadrado de 10x10. </li>
<li> 3. Quantos humanos você deseja colocar: indica a quantidade de habitantes que deseja simular</li>
<li> 4. Quantas pessoas infectadas você quer ter inicialmente (%): deve ser inserido um número inteiro, sendo esse número uma porcentagem referente ao número total de habitantes que foi escolhido anteriormente.Por exemplo, se foi escolhido uma cidade com</li>
<li> 5. Qual o raio de infecção: representa o tamanho do raio em que a pessoa infectada pode transmitir para outras pessoas dentro da escala definida</li>
<li> 6. Taxa de infecção (0.1 - 1.0): indica a probabilidade de infecção (por exemplo, 0,8 representa 80% de probabilidade)</li>
<li> 7. Tempo médio de morte: tempo que leva o indivíduo a morrer a partir do dia da infecção</li>
<li> 8. Desvio padrão da distribuição da probabilidade de morte: taxa de erro (para mais ou para menos) da probabilidade de morte das pessoas</li>
<li> 9. Dias padrão de infecção: quanto tempo os habitantes ficarão infectados até se recuperarem totalmente</li>
<li> 10. Quantos dias você quer simular: decide quanto tempo essa simulação será executada.</li>

A partir disso, o gráfico é gerado dia por dia, indicando a movimentação entre as pessoas (as quais estão representadas por bolinhas) e como o vírus irá se espalhar.
Cada pessoa é representado por uma cor:

<li> Azul: indivíduo saudável </li>
<li> Vermelho: recém-infectado</li>
<li> Magneta: infectado intermediário</li>
<li> Roxo: infectado em recuperação</li>
<li> Verde: imune </li>
<li> Preto: morto </li>

Além disso, é possível gerar um gráfico do comportamento populacional (situação de saúde) em função do tempo decorrido. Esse gráfico é gerado logo após toda a simulação acabar, desde que o código seja executado completamente. Uma simulação em gif pode ser visualizada abaixo: 
** INSIRA O GIF AQUI **

$${\text{\Huge{\color{orange}Início do relatório - 30/05/2023}}}$$
$$\\ $$
Para este projeto, foi definido o título “Simulação de evolução epidemiológica”, cujo objetivo é simular a evolução temporal de um vírus dentro de uma população. Esse tipo de projeto se baseia no uso inicial da linguagem Python para representar probabilidades de infecção por meio de determinação de variáveis necessárias para ser possível visualizar o comportamento desse vírus na população. Serão estudadas várias possibilidades e casos, infimamente com o intuito de compreender possíveis situações reais aplicados a estudos estatísticos na área de doenças virais.
  
  Essa simulação busca realizar uma reprodução de como um possível vírus, a partir de uma única pessoa contaminada, seria capaz de se disseminar em diferentes níveis de propagação a depender de, principalmente, cinco variáveis: definição dos indivíduos, seja por matriz ou por plano cartesiano; distância relativa entre cada pessoa; definição da probabilidade de infecção; definição do raio de contaminação a partir da área indicada; e nível de imunidade relativa para cada indivíduo dessa população. Essa simulação busca se aproximar da realidade levando em conta várias variáveis para serem consideradas, uma vez que, de fato, uma infecção que possivelmente se transformaria em epidemia iria depender diretamente de inúmeros contextos diferentes a serem analisados. Esse tipo de análise estatística depende diretamente da aplicação de valores previamente fixos, para que uma base central de dados possa iniciar e a simulação possa ser rodada. Para cada variável, podemos realizar a análise a seguir.
  
  Inicialmente, é necessário que haja a plotagem do gráfico que simulem os indivíduos em uma determinada região delimitada pelo espaço. Esse tipo de simulação pode ser realizado por matrizes ou por definição de plano cartesiano. Embora sejam muito úteis para delimitar espaços simétricos, as matrizes, nesse caso em específico, chegou a ser uma das opções para simular cada termo como uma pessoa, mas acabou sendo substituída pela preferência em utilizar o plano cartesiano. Isso se deve pelo motivo de que a matriz realiza a plotagem de distância entre as pessoas de forma totalmente simétrica e valores equivalentes entre eles, o que difere, por exemplo, da realidade de uma simulação. Contudo, ainda utilizamos como base a plotagem em matriz para analisarmos como seria seu comportamento. O gráfico é extremamente importante para servir como base do projeto pois se referencia justamente à população a qual está sendo infectada. Essa quantidade de pessoas seria delimitada por nós, no entanto, as coordenadas representando cada ponto seriam voltadas para a aleatoriedade definida principalmente pela classe Random. 
  
  A distância relativa entre cada pessoa também é uma variável importante para a simulação. Após termos o gráfico em questão, é necessário calcular a distância entre um ponto e todos os demais. Isso é necessário para que seja estimado o raio de infecção aplicado em um ponto, sendo capaz de dizer qual a probabilidade de determinada pessoa em sua posição (x,y) consegue contaminar as pessoas que estão dentro do seu raio que foi predefinido, também, por nós. Para exemplificar, podemos pegar um exemplo no qual uma pessoa no ponto1 (3,4) está infectada e está próxima da pessoa2 (3,5), mas está longe de 

outra pessoa no ponto3 (20,2). Se predefinirmos o raio como 2 metros (utilizando metro como parâmetro de unidade de medida), podemos observar que a pessoa2 está dentro do raio de infecção, enquanto a pessoa3 não está. Sendo assim, o indivíduo que estará dentro desse raio terá suas chances de infecção muito aumentadas em relação à pessoa1, diferentemente da relação pessoa1 – pessoa3, uma vez que temos uma distância muito maior. No Python, essa distância passa a ser calculada automaticamente através da definição de uma função que recebe as coordenadas de cada ponto e realiza o cálculo euclidiano para o seu resultado. 
  
  Além disso, pensamos também em referenciar cada pessoa com uma cor diferente para cada nível de estágio que ela se encontra. Isso servirá para facilitar a interpretação da sequência de eventos ocorridos na simulação. O número de estágios possíveis ainda não foi definido, no entanto, temos até o momento os parâmetros da cor azul, representando uma pessoa não infectada, e a cor vermelha, representando uma pessoa infectada. No entanto, serão representados em cores, também, pessoas curadas da doença, pessoas que acabaram de ser infectadas, pessoas que possuem chance alta de transmissão, e pessoas que possuem baixa imunidade, por exemplo. 
  

  Portanto, ainda serão testados as demais variáveis e demais códigos para que a simulação realmente possa ser efetiva em sua demonstração.

$${\text{\Huge{\color{orange}Atualização - Relatório (06/06/2023)}}}$$
$$\\ $$

A partir da criação dos códigos de plotagem gráfica inicial, um novo código foi ordenado com o objetivo de realizar uma base de simulação para o nosso projeto. O resultado final desse código plota um gráfico composto por um plano cartesiano contendo um número de pessoas - isto que pode ser modificado no código - definido em random, ou seja, de modo aleatório em uma matriz, e que apresenta uma quantidade inicial de pessoas infectadas. Essa quantidade de infectados também pode ser modificada para que diferentes análises possam ser feitas para esta simulação. As pessoas saudáveis são aquelas representadas por bolinhas de cor azul; as infectadas, são aquelas que estão com a cor vermelha, magenta e roxa; já as com imunidade, por sua vez, são representadas pela cor verde.

No início, com o uso do input, o próprio usuário poderá definir alguns parâmetros da simulação, tratando-se do número total de habitantes, do número de pessoas inicialmente infectadas, do “tamanho” da cidade (por meio da definição de um tamanho da matriz), do número de dias que as pessoas contaminadas continuam infectando, do número de dias que essas pessoas apresentam de imunidade após pararem de infectar, do raio de infecção e, a partir disso, da probabilidade de infecção a partir desse raio predefinido, além do número de dias de simulação. Para que o gráfico possa ser rodado como desejado, será necessário que todos esses dados sejam inseridos. Logo, basta adicionar esssas informações logo após o código ser baixado e poderá ser rodado normalmente.

A partir da inserção desses valores, o código será rodado várias vezes com um “delay” de 1 segundo para cada dia que foi passado. A cada dia, é plotado o gráfico representando o dia atual e oculto o gráfico do dia anterior. A partir da probabilidade dada inicialmente, a infecção poderá ser disseminada (ou não) à medida que os dias forem passando. Esse tipo de comportamento irá induzir a um espalhamento do número de infectados pelo mapa e a tendência de aglomeração em determinadas regiões específicas da cidade. Assim, é possível analisar se serão todos os habitantes infectados, se o vírus possui alta taxa de transmissão e infecção, se haverá uma disseminação rápida ou lenta, se existirão pessoas que mesmo infectadas não são capazes de transmitir, entre outros fatores. 
As cores de cada bolinha indica o estado em que o habitante está no referente dia. Se está em sua cor azul, significa que ele está saudável e passível de ser contaminado. Se está com a cor vermelha, representa um indivíduo que acabou de ser infectado e possui alta probabilidade de infecção no raio em que está inserido. Em rosa claro, representa um terceiro dia intermediário em que sua taxa de transmissão é reduzida, mas que ainda possui chance de contaminar o grupo ao redor da área referida. Quando se apresenta em magenta/roxo escuro, sua taxa de transmissão é diminuída ainda mais, chegando próximo ao dia em que o paciente se torna imune. Depois, a bolinha fica verde, o que indica um estado de imunidade presente e que retira a possibilidade de infecção a partir do tempo de imunidade, o qual também foi definido pelo usuário. Uma vez que o habitante está nessa situação de imune, presume-se que seu sistema imunológico está fortalecido a partir do desenvolvimento de anticorpos, ou seja, mesmo que tenha um outro indivíduo contaminado dentro do raio de infecção, a sua probabilidade de ser também contaminado será diminuída. Logo, nessa simulação, indivíduos imunes não podem ser diretamente transformados em infectados novamente. É necessário que ele retorne para sua condição de “saudável” para que, enfim, tenha a possibilidade de contrair o vírus novamente. 

O código do protótipo descrito se encontra no documento “main.ipynb”, sendo necessário apenas baixá-lo e rodá-lo no Jupyter Lab para a sua utilização.

Para as próximas semanas, planeja-se elaborar outro(s) protótipo(s) a partir do aprimoramento do descrito em tal documento, adicionando elementos que tornem a simulação mais fidedigna de uma evolução epidemiológica. Nessa perspectiva, é pensável a criação de um parâmetro de probabilidade de morte pelo patógeno pelos infectados, o que poderia ser representado visualmente a partir de uma outra cor de bolinha. Ademais, planeja-se adicionar ao código a movimentação das pessoas no plano cartesiano a partir de uma baixa mudança aleatória de coordenada das bolinhas a cada dia, tornando tal simulação mais dinâmica. 

Portanto, planeja-se criar melhores protótipos de simulação de evolução epidemiológica a partir da adição de novos elementos e do refinamento do atual código.

$${\text{\Huge{\color{orange}Atualização - Relatório (13/06/2023)}}}$$
$$\\ $$

**INSERÇÃO DE DADOS POR INPUT**

Após a criação do código, ao momento em que ele é rodado, foi adicionado um input para que o usuário possa por si mesmo decidir os parâmetros de valores que deseja simular. Isso foi adicionado com o objetivo de permitir com que o indivíduo que irá realizar a testagem do código possa utilizar de vários valores diferentes para diversas e quantas simulações forem necessárias para uma boa análise da simulação. 
 
Para isso, inicialmente, temos um input que pede a quantidade de humanos na simulação. Recomenda-se que seja um valor entre 1 a 1000 humanos, pois valores muito maiores que isso exigirá um tempo maior para que o código possa ser rodado em notebooks normais. Contudo, poderá ser rodado em um número maior dependendo do dispositivo utilizado. 

A escala utilizada é definida em uma medida nxm (em metros), ou seja, é possível escolher qualquer área que desejar para a simulação dessa cidade. O usuário deve inserir dois valores contendo um “x” entre eles, para justamente indicar essa relação entre comprimento e largura da área.
 
O número de infectados iniciais permanece a critério do usuário a partir do número de humanos que foi indicado por ele. Além disso, o raio de infecção também pode ser decidido. No entanto, é válido ressaltar que estamos utilizando um parâmetro em metros, logo, o raio deverá ser um valor dentro da escala definida pelo indivíduo.
 
A probabilidade de infecção se refere à taxa de transmissão. Esse número inserido deve ser entre um valor maior que zero até um valor menor ou igual a 1. Ressalta-se que esse valor deve ser inserido como float, utilizando o ponto para representar as casas decimais. Esse número escolhido entre 0 a 1 indica uma taxa em porcentagem. Por exemplo, se for inserido um valor de 0.4, significa que, considerando toda a população amostral como suscetível à contaminação, existe uma probabilidade de 40% de uma pessoa vizinha ser infectada quando entra em contato com uma pessoa que já possui a doença dentro do raio previamente estabelecido pelo usuário. No entanto, é válido ressaltar que essa probabilidade é diminuída à medida que a distância aumenta.
 
Após isso, tem-se os dias padrão de infecção a ser definido. Esses dias dizem a quanto tempo leva de quando o indivíduo é contaminado até ter sua saúde completamente estabelecida sem o vírus. Nesse caso em específico, considera-se que todos os indivíduos possuem o mesmo tempo de recuperação. 
 
Por fim, a última pergunta do input se refere aos dias de simulação. Este parâmetro também fica a critério do usuário, não tendo necessariamente um limite pré-estabelecido. 

**MOVIMENTO ENTRE OS INDIVÍDUOS**

Foi adicionado um código em que os habitantes se movimentam. Isso foi feito para obter uma simulação mais realística de pessoas que podem ir para outros locais e, consequentemente, contaminar pessoas que já estavam naquele local anteriormente. 

**GIF DE SIMULAÇÃO**

Abaixo está presente um GIF com uma simulação com dados previamente estabelecidos para ser possível identificar o comportamento do gráfico (ainda sem o movimento entre os indivíduos)

![](https://github.com/Illuminis-CNPEM/Epidemiological-Simulation-CJDS/blob/main/simulacao.gif)

**CÓDIGO ATUALIZADO**

O código está atualizado no arquivo com o nome "main.ipynb".

$${\text{\Huge{\color{orange}Atualização - relatório 20/06/2023}}}$$
$$\\ $$

**MORTES**
Foi adicionado o parâmetro de mortes, indicando indivíduos que, a partir da contaminação pela doença, poderá desenvolver probabilidade de morrer, a depender dos dias em que ele permanece com a mesma infecção. Esses indivíduos mortos, a partir do momento em que se transformam na cor "preta", não poderá mais se mover, sendo retirado, portanto, da lista de pessoas saudáveis. 


**GIF DE SIMULAÇÃO**
O novo gif é gerado com legenda para cada cor indicada e com o movimento entre os habitantes. Isso facilita a visualização do usuário para compreender como que a propagação do vírus irá ocorrer a partir da movimentação deles. 


**RESULTADO FINAL**
O código final está no mesmo repositório com o título "main.ipynb". 
