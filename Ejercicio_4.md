
Define el predicado ultimo_elemento(Lista, Ultimo) que sea verdadero si Ultimo es el último elemento de la Lista.

    % Caso base: El último elemento de una lista con un solo
    % elemento (H) es H. Una lista de un solo elemento se
    % representa como [H|[]], o más simple, [H].
    
    ultimo_elemento([H], H).

    % Caso recursivo: Si la lista tiene más de un elemento,
    % el último elemento (U) es el último de su cola (T).

    ultimo_elemento([_|T], U) :-
        ultimo_elemento(T, U).