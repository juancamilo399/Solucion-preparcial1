Dada la siguiente base de conocimientos en Prolog:

	% progenitor(X,Y) X es progenitor de Y
    progenitor(juan, pedro).
    progenitor(pedro, ana).
    progenitor(juan, maria).
    progenitor(maria, carlos).
    abuelo(A, N) :- progenitor(A, P), progenitor(P, N).


* ¿Cuál es el resultado de la consulta ?- abuelo(juan, ana). y explicar

    True, ya que prolog unifica progenitor(juan, pedro) y progenitor(pedro, ana)

* ¿Cual es el resultado de la consulta ?- abuelo(juan,N). y explicar

    ana y carlos, ya que mediante el backtracking encuentra estas soluciones
