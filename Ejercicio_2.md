Se tiene el siguiente predicado para calcular la suma de los enteros desde 1 hasta `N`. Analiza el código:

    % Caso base
    suma_hasta(0, 0).
    % Caso recursivo
    suma_hasta(N, Suma) :-
	    N > 0,
        N1 is N - 1,
	    Suma is N + SumaAnterior,
	    suma_hasta(N1, SumaAnterior).


¿Qué sucede al ejecutar la consulta `?- suma_hasta(3, S)`?

* Error, dado que SumaAnterior, se define en la ultima linea, por lo que en la penultima no es un valor al que se pueda acceder.

