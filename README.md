# RetoCajamar

Oficinas:
  Código de oficina con 4 dígitos (con 0 a la izquierda)
  Completé horario por Default (según el docuemnto de Glosario) a los que no tenían horario.
  En la dirección saqué los 0 a la izquierda del número.
  Cambié el formato de provincia, población y Municipio.
  Traje el nombre de la Provincia desde una base del INE, ya que sólo tenia el código.
  Quise corregir los Municipios, pero por código postal no podía hacerlo ya que el mismo código postal puede pertenecer a más de un Municipio.
  
Ocupación:
    Traje el día de la semana (Ahora que lo pienso debería haberlo cambiado a Castellano!)
    Generé columnas de Ocupación Alta, Media y Baja (al final no las usé).
    Generé una puntuación: 0: Alta, 0.5 Medio, 1 Baja.
    Hice una Pivot por oficina y día de la semana y hora, con el promedio de la ocupación en ese día hora. 
      0 es más ocupada (menos recomendable), 1 es menos ocupada (más recomendable)
    Si es NA e porque la oficina esta cerrada en ese día y hora.
    
Uní la Ocupación a las Oficinas (oficinas_ocupacion)

Cajeros:
    Código de oficina con 4 dígitos (con 0 a la izquierda)
    Si el número de la calle es 0 lo puse vacío.
    Generé el campo dirección como calle + Número.
    Agregué el número de la provincia y corregí los nombres de provincias mas escritos (Base INE)
    
Estados:
    Agregué día de la semana.
    Estado 1: Operativo, 0: Fuera de Linea.
    Calcule el promedio de actividad por Cajero, día de la semana y hora (1 estuvo siempre activo, 0, estuvo siempre fuera de línea).
  
Uní los cajeros con el Estado, le agregué info de la Entidad.
Intenté agregarle Info de la Oficina, pero la clave de Oficina es Oficina+Corresp, y Corresp no está en el fichero de Cajeros.
Traté de hacerlo por Oficina+COD_POSTAL, pero hay una oficina (la 0787) que tiene las dos Corresp en el mismo código Postal y me las duplicaba.

Le puse TIPO=CAJERO a la base de CAJEROS y TIPO=OFICINA a las OFICINAS y junté las dos bases.
Quedaron entonces el tipo, la ubicación, los datos de dirección, horario, operaciones que se puede hacer, y una columa por día de la 
semana y hora con un valor entre 0 y 1, donde 0 es más ocupada o más probabilidad de estar fuera de línea, y 1 es menos ocupada
o más probabilidad de estar Operativo.

