Se tiene la siguiente base de hechos que representa la ubicación de una serie de puntos en una cuadrícula. El objetivo es encontrar el camino a seguir un robot desde la posición inicial hasta la final, recogiendo todas las partes.

    % El almacén es una cuadrícula de 4x4 (coordenadas de 1 a 4).
    dimensiones(4, 4).

    % Posición inicial del robot.
    posicion_inicial(pos(1, 1)).

    % Ubicación de las partes a recolectar.
    parte(engranaje, pos(4, 1)).
    parte(chip, pos(1, 4)).
    parte(bateria, pos(4, 4)).

    % Hay un obstáculo en el centro.
    obstaculo(pos(2, 2)).
    obstaculo(pos(2, 3)).
    obstaculo(pos(3, 2)).

    % El destino final una vez recolectado todo.
    punto_ensamblaje(pos(3, 3)).


Teniendo en cuenta el algoritmo DFS visto en clase donde un estado se define como estado(Posicion, Partes), siendo Posicion representado por pos(X,Y). Además asume que ya están definidas las reglas.


* movimiento(PosicionActual, PosicionSiguiente)
* es_valida(Posicion)

La regla de búsqueda de solución se define como

    solucion(Camino) :- 
        posicion_inicial(Inicio),
        dfs(estado(Inicio, []), [estado(Inicio, [])], Camino).

Escribe cómo deberían definirse las reglas meta(estado(Pos, Partes) y siguiente_estado(estado(PosActual, PartesActuales), estado(PosSiguiente, NuevasPartes)).

Se tiene el predicado predefinido msort(Lista, ListaSort), que evalúa si al ordenar Lista es igual que ListaSort, además [H|Lista] representa el agregar un elemento a Lista en la cabeza, siendo esta una forma de append.

    % Caso base: El estado actual es la meta. El camino es este estado.
    dfs(Estado, _, [Estado]) :-
        meta(Estado).

    % Caso recursivo:
    dfs(EstadoActual, Visitados, [EstadoActual | CaminoRestante]) :-
        siguiente_estado(EstadoActual, SiguienteEstado),
        \+ member(SiguienteEstado, Visitados),
        dfs(SiguienteEstado, [SiguienteEstado | Visitados], CaminoRestante).


---

    % --- Definición de la meta ---
    % La meta se alcanza si el robot está en el punto de ensamblaje Y
    % tiene exactamente las tres partes requeridas.
    meta(estado(Pos, Partes)) :-
        punto_ensamblaje(Pos),
        msort(Partes, [bateria, chip, engranaje]). % msort para orden canónico.

---

    % --- Regla de transición de estados (Definición por Casos) ---

    % CASO 1: El robot se mueve a una nueva posición Y recoge una parte que no tenía.
    siguiente_estado(estado(PosActual, PartesActuales), estado(PosSiguiente, NuevasPartes)) :-
        movimiento(PosActual, PosSiguiente),
        es_valida(PosSiguiente),
        parte(P, PosSiguiente),
        not(member(P, PartesActuales)),
        msort([P | PartesActuales], NuevasPartes).
        % NuevasPartes es la lista ordenada al añadir la parte P como cabeza y cola PartesActuales

    % CASO 2: El robot se mueve a una nueva posición que está vacía o
    % que tiene una parte que ya posee. El inventario no cambia.
    siguiente_estado(estado(PosActual, PartesActuales), estado(PosSiguiente, PartesActuales)) :-
        movimiento(PosActual, PosSiguiente),
        es_valida(PosSiguiente).

---

    % --- Predicados auxiliares ---

    % Define los 4 posibles movimientos desde una posición.
    movimiento(pos(X, Y), pos(X, Y1)) :- Y1 is Y + 1. % Arriba
    movimiento(pos(X, Y), pos(X, Y1)) :- Y1 is Y - 1. % Abajo
    movimiento(pos(X, Y), pos(X1, Y)) :- X1 is X + 1. % Derecha
    movimiento(pos(X, Y), pos(X1, Y)) :- X1 is X - 1. % Izquierda

    % Verifica si una posición es válida (dentro de los límites y no es un obstáculo).
    es_valida(pos(X, Y)) :-
        dimensiones(MaxX, MaxY),
        X > 0, X =< MaxX,
        Y > 0, Y =< MaxY,
        \+ obstaculo(pos(X, Y)).

