Dados los siguientes hechos

    % interes(Persona, Interes).
    interes(ana, lectura).
    interes(ana, senderismo).
    interes(ana, cine).
    interes(juan, senderismo).
    interes(juan, musica).
    interes(juan, cine).
    interes(elena, lectura).
    interes(elena, musica).
    interes(pedro, senderismo).

Define una regla comparte_interes_con(Persona1, Persona2) que sea cierta si la   dos personas comparten interés.

    comparte_interes_con(Persona1, Persona2) :-
        % Encuentra un interés para la Persona1
        interes(Persona1, UnInteres),

        % Encuentra una Persona2 que también tenga ese interés
        interes(Persona2, UnInteres),
        
        % Asegúrate de que no es la misma persona
        Persona1 \= Persona2.
        
Ahora define una consulta que encuentre las personas con las que ana comparte intereses, sin repetir, esto usando un predicado predefinido, escribe como quedaría dicha consulta

    setof(Persona, comparte_interes_con(ana, Persona), ListaPersonas)