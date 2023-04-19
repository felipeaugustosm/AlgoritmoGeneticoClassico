ALGORITMO GENÉTICO CLÁSSICO EM JAVA – HELLO WORLD
Introdução
Algorítimos Genéticos, AGs, são métodos de busca inspirados na evolução dos seres vivos, introduzidos por John Holland (1975) e popularizados por um de seus alunos, David Goldberg (1989), seguem o princípio da seleção natural e sobrevivência dos mais aptos, segundo Charles Darwin (1859). Ele propôs que quanto mais apto um indivíduo for de sobreviver em um meio ambiente, mais chances ele terá de se reproduzir e passar sua carga genética para seus descendentes.

É nisto que se baseia os Algoritmos Genéticos, buscar boas soluções em um espaço de busca grande, em que uma busca pontual seria muito cara.

Se quiser saber mais sobre AGs, leia este ótimo material:  INTRODUÇÃO AOS ALGORITMOS GENÉTICOS (Estéfane G. M. de Lacerda e André Carlos P. L. F. de Carvalho)

Algoritmo Genético Clássico
É um modelo de AG simples, para soluções simples. Pode ser exemplificado no pseudo-código abaixo:

Seja S(t) a população de cromossomos na geração t.
t ← 0
inicializar S(t)
avaliar S(t)
enquanto o critério de parada não for satisfeito faça
t ← t+ 1
selecionar S(t) a partir de S(t- 1)
aplicar crossover sobre S(t)
aplicar mutação sobre S(t)
avaliar S(t)
fim enquanto
Detalhes da Aplicação
Neste exemplo uso como função objetivo, encontrar um gene pré definido por uma frase em uma String, por exemplo:

Olá Mundo
A população inicial será criada com 50 indivíduos aleatórios, com genes de mesmo comprimento que a solução, a aptidão será calculada pelo número de letras iguais a solução, por exemplo se a solução fosse ‘ola’, o gene ‘olq’ teria aptidão 2 e o gene ‘qlw’ teria aptidão 1.

O critério de parada será a solução encontrada, ou até chegar um número máximo de gerações definida na aplicação.

Implementei a seleção por torneio, onde são sorteados 3 indivíduos, destes os 2 com maior aptidão são selecionados para o crossover.

Utilizei uma taxa de corssover de 60%, que pode ser alterada, e um crossover de 1 ponto, exemplo:

| = ponto de corte aleatório

p1: shw|jakw

p2: wjd|jwke

f1: shw|jwke

f2: wjd|jakw
Defini uma taxa de mutação de 3%, também podendo ser alterada, que substitui um gene por outro aleatório, por exemplo:

oaa muwdp -> oaa mpwdp
Mesmo não fazendo parte de um AG clássico, utilizo o elitismo, que copia o melhor indivíduo para a próxima geração.

Código
Há quatro classes neste exemplo:
HelloWorldAG.java (Classe Main com a execução do algorítimo);
Algoritimo.java (Métodos e variáveis estáticas para controle do AG, crossover, seleção…);
Populacao.java (Classe de domínio que define uma população, contém uma lista de indivíduos);
Individuo.java (Classe de domínio que representa um indivíduo, contém seus genes e valor de aptidão).