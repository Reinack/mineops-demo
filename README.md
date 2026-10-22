# MineOps — demo

Plataforma de gestión de operaciones mineras: mina, planta, inventario,
mantenimiento, seguridad y planificación sobre una sola base de datos
multi-empresa.

**➡️ Recorrido completo con capturas: https://reinack.github.io/mineops-demo/**

El código fuente es privado. Este repositorio contiene únicamente la vitrina:
capturas de la aplicación real corriendo sobre un dataset de demostración
enteramente ficticio.

---

## Origen

Parte de lo que ves acá viene de un sistema que se usó en producción en
canteras reales, donde reemplazó planillas de Excel y registros en papel:

- **Inventario de explosivos**, que antes no existía.
- **Gestión de combustible**, con seguimiento diario del consumo y de su destino de uso.
- **Embolsado**, con control al momento en lugar de un registro casi inexistente.
- **Ingreso de camiones y cantidad transportada**, con trazabilidad completa
  y la información lista para la documentación que se entrega al Estado.

Cada cantera tenía una producción distinta, de ahí que las líneas de producción
se definan en datos y no en código.

Lo demás (seguridad, control de leyes, reservas, confiabilidad de activos,
reconciliación mina-planta) se agregó después, tomando prácticas estándar de
la industria, y **no formó parte del sistema en producción**.

## Cómo se construyó

Desarrollado con asistencia de IA. Los requisitos, la estructura de módulos y
las decisiones de diseño salen del trabajo con la operación real; el código se
escribió en colaboración con un asistente de IA.

---

## Qué es

Nació de generalizar un sistema real de cantera y molienda de carbonatos, y se
completó con las prácticas estándar de la industria que ese sistema no cubría:
seguridad, control de leyes, reservas, confiabilidad de activos y reconciliación
mina-planta.

Cuatro decisiones lo sostienen:

1. **El stock es un libro mayor, no un saldo.** Una sola tabla de movimientos
   con signo y trazabilidad al documento de origen. No se edita ni se borra un
   asiento: se contra-asienta.
2. **Las líneas de producción se definen en datos.** Agregar un producto o una
   medición es configuración, no una migración.
3. **La planificación baja por recetas recursivas**, con rendimiento del proceso
   y merma del componente como correcciones separadas.
4. **Todo es multi-empresa desde la primera tabla.** Dar de alta una minera
   nueva no toca una línea de código.

## Módulos

`core` · `catalog` · `geology` · `mining` · `processing` · `inventory` ·
`packaging` · `lot` · `maintenance` · `hse` · `sales` · `planning`

## Motores de cálculo

`units` · `ledger` · `recipes` · `repack` · `lots` · `production` · `blasting` ·
`fleet` · `oee` · `safety` · `reconciliation` · `kpi`

## Stack

Python · Flask · SQLAlchemy · SQLite en desarrollo · PostgreSQL en producción.

## Sobre los datos de las capturas

Todo el contenido visible es generado. No hay nombres de personas, documentos,
clientes, proveedores, precios ni volúmenes de ninguna empresa real: las
personas se identifican por rol y número, y las contrapartes son razones
sociales inventadas.
