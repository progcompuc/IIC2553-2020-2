
---
title: contest 12 - hints y códigos de ejemplo
---

[Index](../index) > [Contests](../contests) > [Contest 12](../contests#contest-12) > ```{{page.title}}```

### A - Find a Number
<details> 
  <summary>Hint 1</summary>
  Notemos que podemos recorrer los números de mayor a menor con una especie de bfs, donde a partir de un número x agregamos a la cola todos aquellos números de la forma 10 x + i, con i dígito. Esto es útil pues si llegamos a descartar un número y no proseguir su bfs nos ahorramos pasar por todos los números que representan sucesores del número eliminado, reduciendo considerablemente el espacio de búsqueda.
</details>
<details> 
  <summary>Hint 2</summary>
  Notemos además que para cada número podemos obtener su resto resto respecto a d y la suma de sus dígitos, sin embargo como sólo nos interesan números con suma de dígitos de a lo más s, pues un número con suma mayor no puede generar el número que buscamos, entonces hay una cantidad finita de configuraciones (resto, suma) en los números que buscaremos, de hecho podemos concluir que dada una configuración (resto, suma), el óptimo de números a agregar será el mismo para todos los números con la misma configuración. Considerando lo anterior, no vale la pena volver a revisar configuraciones que ya han sido exploradas antes en el bfs.
</details>
<details> 
  <summary>Solución + código</summary>
  La solución juntando todo lo anterior consiste en realizar un bfs en el árbol implícito descrito en el hint1, registrando como nodos las configuraciones finitas de (resto, suma). Además necesitamos llevar cuenta de qué configuraciones ya han sido visitadas. La primera vez que lleguemos a la configuración (0, s), es decir resto 0 (o divisible por d) y suma s, habremos tomado el camino óptimo, para reconstruir el camino basta haber registrado el parent de cada configuración generada, es decir qué configuración la agregó a la queue del bfs. Si nunca pasamos por la configuración (0, s), sabremos que no hay solución.
  <a href="https://github.com/BenjaminRubio/CompetitiveProgramming/blob/master/Problems/Codeforces/FindANumber.cpp">Código de ejemplo</a>
</details>

### B - Yet Another Multiple Problem
<details> 
  <summary>Hint</summary>
  Revisen los hints del problema A, en este problema podemos usar una idea parecida pero adaptada a lo que piden.
</details>
<details> 
  <summary>Solución + código</summary>
  La solución consiste en realizar el mismo bfs del problema A pero sólo considerando restos y los dígitos que estén permitidos, la primera vez que lleguemos a la configuración (0) habremos tomado el camino óptimo. De lo contrario no habrá solución.
  <a href="https://github.com/BenjaminRubio/CompetitiveProgramming/blob/master/Problems/SPOJ/YetAnotherMultipleProblem.cpp">Código de ejemplo</a>
</details>

### E - Forest for the Trees
<details> 
  <summary>Hint</summary>
  Para que exista un lattice point entre (0, 0) y (xb, yb) se necesita un punto cuya pendiente desde (0, 0) sea la misma que (xb, yb). Es decir, necesitamos que la fracción yb / xb, no sea irreducible. En caso de no ser una fracción irreducile, podemo reducirla al máximo dividiendo tanto el numerador como el denominador por el gcd(xb, yb) y definir x' = xb / g, y' = yb / g. De esta forma todos los lattice entre (0, 0) y (xb, yb) serán multiplos de (x', y').
</details>
<details> 
  <summary>Solución + código</summary>
  Para obtener el árbol más cercano a (0, 0) en caso de existir sólo hay 2 opciones, o es precisamente (x', y') descrito en el hint, o este punto estaa dentro del rectángulo talado. En el segundo caso necesitamos encontrar el primer múltiplo de (x', y') que esté fuera del rectángulo talado, esto se puede hacer de 2 formas, realizando búsqueda binaria sobre el factor o con una fórmula cerrada. La fórmula cerrada sale de obtener el factor como f = min(x2 / x', y2 / y') + 1, esto pues el el mínimo múltiplo de x' o y' que supera al rectángulo talado.
  <a href="https://github.com/BenjaminRubio/CompetitiveProgramming/blob/master/Problems/Kattis/ForestForTheTrees.cpp">Código de ejemplo</a>
</details>

<!-- <details> 
  <summary>Hint</summary>   
</details>
<details> 
  <summary>Solución + código</summary>
  <a href="">Código de ejemplo</a>
</details> -->

[Index](../index) > [Contests](../contests) > [Contest 12](../contests#contest-12) > ```{{page.title}}```