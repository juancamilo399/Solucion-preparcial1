Dados los siguientes hechos

    % heroe(Nombre, Nivel, Clase).
    heroe(eldric, 15, guerrero).

    % mision(Nombre, NivelMinimo, ClaseRecomendada).
    mision(derrotar_al_dragon, 20, guerrero).
    mision(rescatar_al_mercader, 10, picaro).
    mision(escoltar_la_caravana, 12, guerrero).
    mision(infiltrarse_en_la_fortaleza, 18, picaro).
    mision(recuperar_el_amuleto, 14, guerrero).

Define una regla heroe_es_apto_para(NombreHeroe, NombreMision) que determine si un héroe es apto para una misión

    heroe_es_apto_para(NombreHeroe, NombreMision) :-
    % 1. Obtener los datos del héroe
    heroe(NombreHeroe, NivelHeroe, ClaseHeroe),

    % 2. Obtener los datos de la misión
    mision(NombreMision, NivelMin, ClaseHeroe),

    % 3. Verificar la condición del nivel
    NivelHeroe >= NivelMin.

Y ahora encuentra todas las misiones aptas para eldric, esto usando un predicado predefinido, escribe cómo quedaría dicha consulta.

    findall(Misiones, heroe_es_apto_para(eldric, Misiones), ListaMisiones)