Define un Predicado encontrar_y_duplicar(Lista, Limite, Resultado)
 que encuentra el primer número en una lista que es mayor que un límite N y lo duplica, el resultado estaría en una variable R. Usa recursión.

Recuerda las diferentes formas de representar una lista.


    % Predicado que encuentra el primer número en una lista que es mayor que un Límite y lo duplica.

    % Caso 1: La cabeza de la lista (H) es menor que el Límite.
    % Unifica Resultado con H*2 y el corte (!) detiene la búsqueda.

    encontrar_y_duplicar([H|_], Limite, Resultado) :-
        H > Limite,
        Resultado is H * 2.

    % Caso 2: La cabeza no cumple. Se sigue buscando en la cola (T).

    encontrar_y_duplicar([_|T], Limite, Resultado) :-
        encontrar_y_duplicar(T, Limite, Resultado).