# Hide & Shrink · Historial de diseño

Proyecto de Wild Hex anteriormente identificado como **Búsqueda y escondite en la Facultad de Psicología**. **Hide & Shrink** es el nombre provisional aceptado el 19/11/2026; el repositorio es `WildHex/hide-shrink`.

Juego cooperativo de búsqueda y escondite contra la Presencia, con estudiantes y fantasmas. Freud y Lacan son los dos fantasmas de referencia, sin habilidades diferenciadas confirmadas. La Presencia administra el objetivo secreto y sus efectos. No hay combate.

## Alcance y estado de la documentación

Este historial reúne decisiones recuperadas del 17–20/11/2026, el documento de diseño v0.4.1 y un resumen de prueba v0.3.0. Las fechas narrativas son de Uruguay; la exportación conserva su fecha UTC.

- **Decisión del diseñador:** instrucción explícita; no implica balance validado.
- **Referencia de iteración:** regla descrita en el GD, con valores o adjudicaciones que pueden seguir a prueba.
- **Resultado registrado:** dato de la exportación; no prueba por sí solo que se hayan seguido todas las reglas.
- **Pendiente:** alternativa o problema sin cierre confirmado.

Esta incorporación es documental. No modifica ni verifica ejecutando la aplicación. Las funciones atribuidas a v0.4.1 son las descritas por su GD; no se presentan como comprobaciones independientes del código.

## 17/11 · Base y tablero

Se definieron dos fantasmas de referencia y se distinguieron los marcadores de ruido del marcador de investigación. La investigación directa de la Presencia no necesita un ruido previo. El diseñador decide cuándo cerrar la prueba.

El tablero v0.1 toma como referencia el plano de la Facultad de Psicología. El GD posterior conserva esa geometría: 28 recintos nombrados, 51 casillas de circulación y 37 interiores incluidos patios, para un total de 88; 35 aberturas incluida la entrada. Es una adaptación funcional, no un relevamiento arquitectónico verificado. Los patios son transitables y la red ofrece circuitos; cada recinto conserva tantas casillas interiores como puertas.

La carta determina qué se busca; la ubicación se establece aparte y en secreto. En la iteración documentada, se gana al recuperar el objetivo y escapar al menos un estudiante por el acceso principal. Coincidir con un fantasma estando expuesto causa captura inmediata, incluso durante el recorrido. La captura de todos los estudiantes termina en derrota.

**Pendiente:** transporte y transferencia del objeto tras capturar a su portador. No se ha cerrado que quede en el piso ni quién deba llevarlo hasta la salida. La regla de victoria descrita por la mesa no resuelve ese vacío.

## 18/11 · v0.3.0 y correcciones de movimiento

Se corrigió la duplicación entre tirada de acciones y tirada de movimiento: **una única tirada de 1–3 por turno**, con caras físicas 1, 1, 2, 2, 3, 3. Mover una casilla, buscar, esconderse o abrir consume una acción según corresponda. No se vuelve a tirar al agotarlas. En v0.3.0 también la persecución usaba ese presupuesto; el 20/11 se documenta una excepción nueva.

Los fantasmas comienzan en habitaciones aleatorias distintas, con orientación y destino de patrulla sorteados. La persecución se activa al ver a un estudiante expuesto, sigue su posición mientras exista visión y, al perderla, retoma investigación o patrulla. La prioridad es persecución → investigación → patrulla.

Las correcciones de interfaz pedidas incluyen retratos de Freud y Lacan, destinos translúcidos, tablero completo sin desplazamiento de página, movimiento asistido, avance por participante y deshacer movimiento. Siguiente jugador solo cierra la ronda tras completar el ciclo, no en cada pulsación. Las versiones deben actualizarse junto con sus documentos.

## 19/11 · Nombre e identidad

Se aceptó tentativamente **Hide & Shrink** para este proyecto. Es uno de los tres proyectos nuevos en desarrollo mencionados junto con Craft the Wild (Minecardft) y Chop & Shop (Crawler-shop). Son proyectos distintos: sus reglas e historiales no se mezclan.

## 20/11 · Prueba exportada de v0.3.0

Fuente: `Facultad_v0.3.0_Resumen_R32.md`, exportado el **2026-11-20T22:34:17.036Z**. Dos estudiantes y dos fantasmas. La cabecera indica ronda 32 y victoria; el registro de rondas cerradas llega a la 31.

| Métrica | Registro |
| --- | ---: |
| Movimientos asistidos / pasos | 117 / 162 |
| Colocaciones libres / ajustes manuales | 0 / 52 |
| Ruido generado registrado | 7 |
| Investigaciones | 2 |
| Búsquedas / objetivos encontrados | 9 / 1 |
| Escondites | 2 |
| Intentos de puertas / fallidos | 3 / 0 |
| Capturas / escapes | 0 / 1 |
| Tensión final / ruido residual presente | 0 / 6 |

El estudiante 1 escapó; el estudiante 2 seguía en juego. Pasos acumulados: estudiante 1, 55; estudiante 2, 39; Freud, 25; Lacan, 43.

**Límites del resultado:** hay numerosos turnos omitidos y cierres manuales. El usuario aclaró que dejó llegar al estudiante para comprobar la salida. Por tanto, la victoria registrada es una comprobación funcional parcial, no evidencia suficiente de dificultad ni de balance. Tampoco valida carrera, persecución fija o ruido de las versiones posteriores.

## 20/11 · Iteración v0.4.0, conservada en el GD v0.4.1

La secuencia de entregas identifica v0.4.0 antes de v0.4.1 el mismo día. El GD vigente describe estas reglas para la nueva prueba:

- **Acciones normales:** una tirada de 1–3; mover una casilla cuesta una acción. Buscar y esconderse cuestan una acción dentro de una habitación. Moverse vuelve a exponer al estudiante.
- **Correr:** alternativa previa a tirar. Hasta cuatro pasos, elegidos uno a uno. Hasta dos pasos generan cero ruido; tres generan uno; cuatro generan dos. Se cuentan pasos reales, incluidos rodeos y retornos. El ruido se resuelve en la casilla final al terminar la carrera, pasar turno o ser capturado. La carrera dedica el turno al movimiento: no habilita buscar, abrir ni esconderse. Tras el primer paso no puede sustituirse por una tirada ni iniciarse otra carrera.
- **Persecución:** tres movimientos fijos sin dado. Si comienza durante el turno, los pasos ya gastados cuentan dentro de los tres. Perder y recuperar visión no renueva el presupuesto. Patrulla e investigación vuelven al dado de 1–3 en la siguiente activación que corresponda.
- **Ayuda visual solicitada:** primeras tres casillas de alcance en un color y cuarta en otro; elegir cada paso. El GD usa amarillo y naranja. El alcance no decide automáticamente el recorrido.
- **Control de turnos documentado:** advertencia antes de omitir una tirada o efecto pendiente de Presencia; una omisión confirmada conserva motivo y participante. Carrera y persecución fija no exigen tirada.

Estas referencias requieren nueva prueba; no se recalculan los movimientos del registro v0.3.0 con ellas.

## 20/11 · Corrección prioritaria de ruido, v0.4.1

El diseñador identificó el ruido como el problema crítico y rechazó conservar marcadores que ya no aportaban función.

**Decisión explícita:** el ruido desaparece tras resolver su comprobación, tanto si falla como si activa investigación. En caso de éxito queda el marcador de investigación. Se elimina la reducción automática por silencio; la Tensión solo se reduce cuando el ruido activa investigación.

La parametrización actual del GD es:

1. Cada ruido suma uno a Tensión, hasta seis. Dos ruidos se añaden juntos antes de comprobar.
2. Tirar 1d6: resultado menor o igual a Tensión activa investigación en esa casilla.
3. El éxito resta dos de Tensión, con mínimo cero; la magnitud sigue como parámetro de prueba. El fallo conserva el aumento.
4. Retirar el ruido en ambos casos. Existe un único marcador de investigación, que se traslada al nuevo objetivo.
5. Asignar al fantasma libre más cercano por recorrido abierto; la Presencia resuelve empates. Un perseguidor no se distrae. Si todos persiguen, la investigación queda pendiente.
6. Llegar a investigación retira su marcador sin otra reducción. La investigación directa de Presencia no crea ruido ni modifica Tensión.
7. Cerrar rondas silenciosas no baja Tensión.

El GD describe una migración que retira ruido residual y el antiguo parámetro de silencio, conservando Tensión, investigación y registros históricos. No se verificó aquí su ejecución.

## Otras referencias vigentes y asuntos abiertos

- **Puertas:** abrir una cerrada cuesta una acción y un ruido. Destrabar consume una acción aun fallando: 4–6 abre y genera dos ruidos; 1–3 falla sin ruido. Cerrar por una acción es provisional. Por defecto una cerrada bloquea movimiento y visión; probar que los fantasmas la atraviesen sigue como alternativa.
- **Visión:** frontal de 90° y sin límite de distancia como valores de prueba. Muros y puertas cerradas la bloquean. Ángulo, alcance y desempate entre estudiantes visibles siguen pendientes de balance.
- **Descubrimiento:** buscar al estudiante oculto cuesta una acción; 1d6 estrictamente menor que Tensión lo descubre y captura. Igualdad y seis lo salvan. No se ejecuta gratis al entrar.
- **Presencia:** caras 1–2 ruido; 3–4 puerta; 5 investigación directa; 6 nuevo destino sorteado para un fantasma elegido. Una tirada y una aplicación por turno.
- **Objetivo:** resolver captura del portador y transferencia; evitar inferir una decisión del mero registro de victoria.
- **Próxima prueba:** carrera de 2/3/4 pasos, persecución sin renovar presupuesto, ruido retirado en éxito y fallo, Tensión persistente en silencio, investigación pendiente y empates, puertas, deshacer sin nueva tirada y omisiones de turno. Registrar duración y adjudicaciones manuales.

## Fuentes y trazabilidad

- Conversaciones de diseño y tablero del 17/11; correcciones del 18/11.
- Aceptación provisional del nombre del 19/11.
- Conversación Hide & Shrink del 20/11: correr, prueba de salida, pregunta sobre captura del portador y corrección explícita de ruido/Tensión.
- `Facultad_v0.3.0_Resumen_R32.md`, exportación citada arriba.
- `GD_Busqueda_y_escondite_v041.pdf`, revisión v0.4.1, 20/11/2026, siete páginas; sustituye las reglas anteriores donde se indica.

No se incorporan código de la app, imágenes ni datos secretos de la partida. Un documento de versión y una prueba parcial no equivalen a validación del balance.
