Se tiene el siguiente programa

	asignar_categoria(P, bronce) :- P =< 50.
	asignar_categoria(P, plata)  :- P =< 80.
	asignar_categoria(P, oro)    :- P =< 100.

Cual es resultado de la consulta ?-asignar_categoria(40, N)., Si hay que corregir algo como lo harías sin agregar más comparadores lógicos?

* Es bronce, plata, oro, se arregla agregando cortes.