# README - Base de Datos Campeonato Relámpago de Fútbol

Este proyecto contiene la estructura de una base de datos para gestionar un torneo de fútbol de eliminación directa (knock-out) con 8 equipos.

## Estructura General de la Base de Datos

Las tablas principales son:

- **Equipos**: Información sobre los equipos.
- **Jugadores**: Detalles de los jugadores y su relación con los equipos.
- **Árbitros**: Información sobre los árbitros.
- **Partidos**: Detalles de los partidos jugados.

## Crear una Tabla (Ejemplo: Equipos)

```sql
CREATE TABLE Teams (
    idTeam INT PRIMARY KEY AUTO_INCREMENT,
    nameTeam VARCHAR(50) NOT NULL,
    cityOrigin VARCHAR(50) NOT NULL,
    foundationYear INT NOT NULL
);
Ejemplo de Inserción de Datos
sql
Copiar
Editar
-- Insertar un equipo
INSERT INTO Teams (nameTeam, cityOrigin, foundationYear)
VALUES ('Equipo 1', 'Ciudad 1', 2000);
Ejemplo de Consulta
sql
Copiar
Editar
-- Obtener todos los equipos ordenados por nombre
SELECT nameTeam, cityOrigin
FROM Teams
ORDER BY nameTeam ASC;
Consultas Adicionales
Mostrar todos los jugadores de un equipo específico (elige uno): Incluyendo su número y posición.

sql
Copiar
Editar
SELECT nameComplete, numberTShirt, position
FROM Players
WHERE idTeam = 1;  -- Reemplazar con el ID de equipo deseado
Listar los partidos de cuartos de final con los nombres de los equipos y el resultado:

sql
Copiar
Editar
SELECT t1.nameTeam AS LocalTeam, t2.nameTeam AS VisitingTeam, m.localTeamGoals, m.visitingTeamGoals
FROM Matches m
JOIN Teams t1 ON m.idLocalTeam = t1.idTeam
JOIN Teams t2 ON m.idVisitingTeam = t2.idTeam
WHERE m.phase = 'Cuartos';
Mostrar árbitros principales con más de 5 años de experiencia:

sql
Copiar
Editar
SELECT nameComplete
FROM Referees
WHERE category = 'Principal' AND experienceYears > 5;
Encontrar todos los porteros del torneo, mostrando a qué equipo pertenecen:

sql
Copiar
Editar
SELECT p.nameComplete, t.nameTeam
FROM Players p
JOIN Teams t ON p.idTeam = t.idTeam
WHERE p.position = 'Goalkeeper';
Consideraciones
Asegúrate de crear las demás tablas (Jugadores, Árbitros, Partidos) siguiendo la misma estructura.
Las consultas deben usar JOINs para unir las tablas relacionadas, y las claves primarias/foráneas deben estar correctamente definidas.
Este README cubre la creación de una tabla básica, inserciones, consultas simples y ejemplos de cómo manejar los datos del torneo. Puedes extenderlo según los requerimientos específicos del proyecto.
