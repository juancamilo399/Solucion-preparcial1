Dado el predicado:


    max(X, Y, X) :- X >= Y, !.
    max(_, Y, Y).

¿Cuál es el resultado de la consulta ?- max(3, 5, M). y porque?

* 5, dado que al evaluar la primera regla es falso, se havce corte, y luego M, toma el valor de Y, es decir 5, esto mediante la segunda regla.