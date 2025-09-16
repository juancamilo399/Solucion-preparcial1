¿Qué consulta utilizarías para obtener una lista con todos los números mayores a 5 de la lista `[3, 8, 2, 9, 5]`? y porque?

a. ?- findall(X, (member(X, [3, 8, 2, 9, 5]), X > 5), Lista).

b. ?- include(>(5), [3, 8, 2, 9, 5], Lista).

c: ?- member(X, [3, 8, 2, 9, 5]), X > 5.

d. ?- bagof(X, X > 5, Lista).

Es la a, ya que findall encuentra todas las soluciones que cumplen la condicion dada por el segundo argumento, y agrupa dichas X´s en Lista
