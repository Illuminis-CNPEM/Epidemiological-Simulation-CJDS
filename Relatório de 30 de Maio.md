$${\text{\huge{\color{orange}Relatório do Dia 30 de Maio Com a Primeira Versão do README.md}}}$$
$$\\ $$
   Este documento é referente ao que foi entregue no dia 30 de maio de 2023, tratando-se de uma análise do que foi entregue em tal data. Neste dia, foi entregue a primeira versão do README.md, assim como era previsto no cronograma de aulas, havendo no documento, uma explicação geral sobre o trabalho, os dois primeiros protótipos do projeto feitos em Python, elementos-chave utilizadas em tais protótipos e ideias para os próximos protótipos. Sob essa ótica, um dos protótipos se tratava de uma simulação em forma matricial com pessoas representadas por 1 quando infectado ou 0 quando não infectado; enquanto o outro, em um gráfico de dispersão com pontos azuis representando pessoas infectadas e pontos vermelhos para não infectadas. É relevante citar que tais protótipos entregues em tal data foram descontinuados a partir da segunda versão do README.md entregue no dia 6 de junho, sendo úteis para a aprendizagem dos integrantes do grupo. Abaixo, neste documento, encontra-se a primeira versão do README.md referente ao dia citado anteriormente:

“Para este projeto, foi definido o título ‘Simulação de evolução epidemiológica’, cujo objetivo é simular a evolução temporal de um vírus dentro de uma população. Esse tipo de projeto se baseia no uso inicial da linguagem Python para representar probabilidades de infecção por meio de determinação de variáveis necessárias para ser possível visualizar o comportamento desse vírus na população. Serão estudados várias possibilidades e casos, infimamente com o intuito de compreender possíveis situações reais aplicados a estudos estatísticos na área de doenças virais.
  
  Essa simulação busca realizar uma reprodução de como um possível vírus, a partir de uma única pessoa contaminada, seria capaz de se disseminar em diferentes níveis de propagação a depender de, principalmente, cinco variáveis: definição dos indivíduos, seja por matriz ou por plano cartesiano; distância relativa entre cada pessoa; definição da probabilidade de infecção; definição do raio de contaminação a partir da área indicada; e nível de imunidade relativa para cada indivíduo dessa população. Essa simulação busca se aproximar da realidade levando em conta várias variáveis para serem consideradas, uma vez que, de fato, uma infecção que possivelmente se transformaria em epidemia iria depender diretamente de inúmeros contextos diferentes a serem analisados. Esse tipo de análise estatística depende diretamente da aplicação de valores previamente fixos, para que uma base central de dados possa iniciar e a simulação possa ser rodada. Para cada variável, podemos realizar a análise a seguir.
  
  Inicialmente, é necessário que haja a plotagem do gráfico que simulem os indivíduos em uma determinada região delimitada pelo espaço. Esse tipo de simulação pode ser realizado por matrizes ou por definição de plano cartesiano. Embora sejam muito úteis para delimitar espaços simétricos, as matrizes, nesse caso em específico, chegou a ser uma das opções para simular cada termo como uma pessoa, mas acabou sendo substituída pela preferência em utilizar o plano cartesiano. Isso se deve pelo motivo de que a matriz realiza a plotagem de distância entre as pessoas de forma totalmente simétrica e valores equivalentes entre eles, o que difere, por exemplo, da realidade de uma simulação. Contudo, ainda utilizamos como base a plotagem em matriz para analisarmos como seria seu comportamento. O gráfico é extremamente importante para servir como base do projeto pois se referencia justamente à população a qual está sendo infectada. Essa quantidade de pessoas seria delimitada por nós, no entanto, as coordenadas representando cada ponto seriam voltadas para a aleatoriedade definida principalmente pela classe Random. 
  
  A distância relativa entre cada pessoa também é uma variável importante para a simulação. Após termos o gráfico em questão, é necessário calcular a distância entre um ponto e todos os demais outros. Isso é necessário para que seja estimado o raio de infecção aplicado em um ponto, sendo capaz de dizer qual a probabilidade de determinada pessoa em sua posição (x,y) consegue contaminar as pessoas que estão dentro do seu raio que foi predefinido, também, por nós. Para exemplificar, podemos pegar um exemplo a qual uma pessoa no ponto1 (3,4) está infectada e está próxima da pessoa2 (3,5), mas está longe de outra pessoa no ponto3 (20,2). Se predefinirmos o raio como 2 metros (utilizando metro como parâmetro de unidade de medida), podemos observar que a pessoa2 está dentro do raio de infecção, enquanto a pessoa3 não está. Sendo assim, o indivíduo que estará dentro desse raio terá suas chances de infecção muito aumentadas em relação à pessoa1, diferentemente da relação pessoa1 – pessoa3, uma vez que temos uma distância muito maior. No Python, essa distância passa a ser calculada automaticamente através da definição de uma função que recebe as coordenadas de cada ponto e realiza o cálculo euclidiano para o seu resultado. 
  
  Além disso, pensamos também em referenciar cada pessoa com uma cor diferente para cada nível de estágio que ela se encontra. Isso servirá para facilitar a interpretação da sequência de eventos ocorridos na simulação. O número de estágios possíveis ainda não foi definido, no entanto, temos até o momento os parâmetros da cor azul, representando uma pessoa não infectada, e a cor vermelha, representando uma pessoa infectada. No entanto, serão representados em cores, também, pessoas curadas da doença, pessoas que acabaram de ser infectadas, pessoas que possuem chance alta de transmissão, e pessoas que possuem baixa imunidade, por exemplo. 

   Foram feitos dois códigos teste para analisarmos cada parâmetro separadamente e, ao fim, podermos reuní-los. Para o primeiro, temos um código voltado ao estudo de um algoritmo de infecção feito em forma matricial. Os indivíduos infectados são representados com o número 1, enquanto saudáveis são números 0. Com o uso da biblioteca numpy é gerado uma matriz 10x10 que será alterada a cada loop com nossa taxa de infecção pré-definida. Tanto o paciente inicial quanto a infecção são geradas aleatoriamente a partir dos comandos da biblioteca random. Isso faz com que o nosso algoritmo tenha um aspecto mais realista no contexto de uma epidemia. O código está sendo explificado abaixo:
```py
import numpy as np
import random
import time
import os

infection_rate = 0.2

# Confere se todos foram infectados ou não
def all_infected(matrix):
    return np.count_nonzero(matrix) == matrix.size

# Cria matriz 10x10
matrix = np.zeros((10, 10)) 

# Paciente inicial
row = random.randint(0, 10)
column = random.randint(0, 10)
matrix[row][column] = 1

# Infectar as pessoas
while not all_infected(matrix):
    next_matrix = np.copy(matrix)

    # Verifica os vizinhos das células infectadas para propagação da infecção
    for i in range(10):
        for j in range(10):
            if matrix[i][j] == 1:
                # Propagação da infecção para os vizinhos dentro de um bloco de distância
                for k in range(i - 1, i + 2):
                    for l in range(j - 1, j + 2):
                        if k >= 0 and k < 10 and l >= 0 and l < 10 and (k != i or l != j):
                            if matrix[k][l] == 0 and random.random() < infection_rate:
                                next_matrix[k][l] = 1
                        
    # Atualiza a matriz
    matrix = next_matrix
    os.system('cls' if os.name == 'nt' else 'clear')
    print(matrix)
    
    # Aguarda um tempo antes de infectar a próxima pessoa
    time.sleep(1)

print("Todas as pessoas foram infectadas.")
  
 ```
 
   Para o segundo código, é notório um dos primeiros protótipos funcionais e simples de uma simulação de evolução epidemiológica deste trabalho. Tal simulação se baseia em uma representação de uma evolução epidemiológica a partir de um gráfico de dispersão, sendo o código escrito inteiramente na linguagem Python no Jupyter Lab pelo Kernel ilumpy a partir da biblioteca NumPy para cálculos numéricos e da biblioteca Matplotlib para plotar o gráfico. Nesse sentido, tal simulação possui quatro parâmetros: o número total de pessoal, representado por N; o número inicial de pessoas contaminadas, representado por i; o raio de contágio, representado por R; e a taxa de contágio, representado por T. A partir desses parâmetros, são geradas coordenadas aleatórias para todos os N indivíduos a partir da função np.random.rand(N) em duas listas, uma para a coordenada x e outra para a y. 

   Dessa forma, é criado uma lista denominada states com um número de elementos N, em que se define se o indivíduo está ou não infectado, a partir do valor 0 para não infectado ou 1 para infectado, sendo estabelecido inicialmente que todos os indivíduos não estão, com exceção dos primeiros I indivíduos da lista com coordenadas aleatórias. Posteriormente, é definido uma função para calcular a distância entre duas pessoas. Assim, o gráfico de dispersão da semana zero é plotado, havendo N indivíduos no total, dos quais I estão inicialmente infectados, estando esses representados por pontos vermelhos, enquanto os não infectados são representados por pontos azuis. Já os gráficos das semanas 1 a 10, são plotados a partir de uma série de loop e condicionais, que são responsáveis por executar a simulação, iterar cada indivíduo, verificar se cada um está ou não infectado e, caso esteja, iterar cada indivíduo além do infectado em análise e verificar se está ou não infectado e, caso não esteja, verificar se a distância entre os dois indivíduos é menor que R e, caso seja, o indivíduo poderá ser infectado ou não a partir da taxa de infeção T.

```py
# V1
import numpy as np
import matplotlib.pyplot as plt

# Parâmetros da simulação
N = 100   # Número total de pessoas
I = 1     # Número inicial de infectados
R = 0.1 * 200   # Raio do contágio
T = 20    # Taxa de contágio em %

# Gerar posições aleatórias das pessoas no plano
x = np.random.rand(N) * 200
y = np.random.rand(N) * 200

# Definir o estado inicial de cada pessoa (0 = não infectado, 1 = infectado)
states = np.zeros(N)
states[:I] = 1

# Função para calcular a distância entre duas pessoas
def calculate_distance(pos1, pos2):
    return np.sqrt((pos1[0] - pos2[0]) ** 2 + (pos1[1] - pos2[1]) * 2)

# Plotar o gráfico de pontos inicial
plt.figure(figsize=(6, 6))
colors = ['blue' if state == 0 else 'red' for state in states]
plt.scatter(x, y, color=colors)
plt.xlabel('Eixo X')
plt.ylabel('Eixo Y')
plt.title('Simulação de Evolução Epidemiológica - Semana 0')

# Executar a simulação
for t in range(1, 11):
    # Iterar sobre cada pessoa
    for i in range(N):
        if states[i] == 1:  # Se a pessoa estiver infectada
            # Verificar a contaminação de pessoas próximas
            for j in range(N):
                if states[j] == 0:  # Se a pessoa não estiver infectada
                    distance = calculate_distance((x[i], y[i]), (x[j], y[j]))
                    if distance < R:
                        if T <= np.random.rand() * 100: # Probabilidade de contaminar a partir de P
                            states[j] = 1  # Contaminação

    # Plotar o gráfico de pontos atualizado
    plt.figure(figsize=(6, 6))
    colors = ['blue' if state == 0 else 'red' for state in states]
    plt.scatter(x, y, color=colors)
    plt.xlabel('Eixo X')
    plt.ylabel('Eixo Y')
    plt.title(f'Simulação de Evolução Epidemiológica - Semana {t}')
    plt.show()
```
  Portanto, ainda serão testados as demais variáveis e demais códigos para que a simulação realmente possa ser efetiva em sua demonstração.“
