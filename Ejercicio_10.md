Dados los siguientes hechos

    % habilidad(Empleado, Habilidad).
    habilidad(laura, python).
    habilidad(laura, sql).
    habilidad(carlos, java).
    habilidad(carlos, sql).
    habilidad(sofia, python).
    habilidad(sofia, ia).
    habilidad(sofia, sql).

    % habilidades_requeridas(Proyecto, Habilidad).
    habilidades_requeridas(sistema_login, python).
    habilidades_requeridas(sistema_login, sql).
    habilidades_requeridas(motor_busqueda, python).
    habilidades_requeridas(motor_busqueda, ia).
    habilidades_requeridas(reportes_db, java).
    habilidades_requeridas(reportes_db, sql).

Definir una regla puede_liderar(Empleado, Proyecto) que determine si un Empleado puede liderar un Proyecto, sólo si cuenta con todas las habilidades

    puede_liderar(Empleado, Proyecto) :-
        forall(
            habilidades_requeridas(Proyecto, HabilidadRequerida),
            habilidad(Empleado, HabilidadRequerida)
        ).