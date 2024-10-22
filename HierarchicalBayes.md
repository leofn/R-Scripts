HierarchicalBayes
========================================================
author: Manoel Galdino
date: 24/07/2014

Modelo Hierárquicos Bayesianos e Topic Models
========================================================
Um exemplo simples de modelo hierárquico
- 8 schools example - adaptado de Gelman et. al.
- Qual o efeito de aulas direcionadas para aumentar desempenho
no Scholastic Aptitude Test?
- Aulas dadas em 8 escolas.
-Efeito (e incerteza) estimado do tratamento em cada escola


Modelo Hierárquicos Bayesianos - 8 schools
========================================================


School        | estimated treatment effect | standard error of the estimate  
------------- | -------------              |  ------------
A             | 28                         |  15
B             | 8                          |  10
C             | -3                         |  16
D             | 7                          |  11
E             | -1                         |  9
F             | 1                          |  11
G             | 18                         |  10
H             | 12                         |  18
Modelo Hierárquicos Bayesianos e Topic Models
========================================================
Qual o verdadeiro efeito do tratamento na escola A?

- 28, pois é ATE e não-viesado
- 8 (efeito médio em todas as escolas). Efeito n é significativamente
diferente de 8 (p > 0.05)
- Primeiro considera cada escola isoladamente
- Ignora evidencia de que cursos similares tem efeito menor que 20 pontos
- Segundo considera que tratamento em todas as escolas são iguais
- Apesar de que cursos são ensinados por diferentes profs. para diferentes estudantes.

Modelo Hierárquicos Bayesianos e Topic Models
========================================================
Solução de modelos hierárquicos

- (1) Assuma que o "verdadeiro efeito" em cada escola vem de uma distribuição normal com média mu e desvio padrão sigma  desconhecidos 
- (2) Assuma que o efeito observado em cada escola é derivado de uma distribuição normal com média igual ao verdadeiro efeito e desvio padrão igual ao da tabela

Modelo Hierárquicos Bayesianos e Topic Models
========================================================
Solução de modelos hierárquicos

- Modelo ou Verossimilhança
- y[i] ~ N(mu[i], sigma[i]^2) # cada y tem sua própria média e dp
- mu[i] ~ N(mu.grande, sigma.grande^2) # as médias tem uma média geral das escolas. Isso que gera o partial pooling ou shrinkage
- Prioris: mu.grande ~ N(0, 100 ) e sigma.grande ~ U(0, 1000)
- se sigma.grande -> 0, então todas escolas têm mesma média
- se sigma.grande -> inf, então grande média é não-informativa e cada escola tem sua própria média
- caso intermediário equivale a partial pooling ou shrinkage


Modelo Hierárquicos Bayesianos e Topic Models
========================================================
Solução de modelos hierárquicos

- Em Topic Models, simplificadamente, temos
 - cada doc têm palavras que seguem distrib de um tópico
 - w[i,d] ~ Distrib do Tópico k
 - MAs, prob. de um doc A vir de tópico K não é (a priori) a mesma de vir de um tópico J. Docs de um mesmo autor têm maior prob. de virem do mesmo tópico.
- O exemplo aqui é mais complicado, pois se trata de priori sobre distribuições mais complexas que a Normal. Ex. Dirichelet.

Slide With Code
========================================================


```r
summary(cars)
```

```
     speed           dist    
 Min.   : 4.0   Min.   :  2  
 1st Qu.:12.0   1st Qu.: 26  
 Median :15.0   Median : 36  
 Mean   :15.4   Mean   : 43  
 3rd Qu.:19.0   3rd Qu.: 56  
 Max.   :25.0   Max.   :120  
```

Slide With Plot
========================================================

![plot of chunk unnamed-chunk-2](HierarchicalBayes-figure/unnamed-chunk-2.png) 

