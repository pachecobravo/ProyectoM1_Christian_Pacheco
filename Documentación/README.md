# InsightReach: Segmentación de clientes de restaurantes (EDA)

Proyecto Integrador M1 | Data Science | SoyHenry
Autor: Christian Pacheco

## 1. Contexto y objetivo

InsightReach es una empresa de marketing digital que crea campañas personalizadas para negocios locales. El proyecto analiza su base de clientes de restaurantes, la enriquece con datos de la API de Yelp y propone recomendaciones de segmentación.

## 2. Avance 1: Exploración, limpieza y tablas (`Avance_1_EDA.ipynb`)

**Datos:** 30.000 clientes y 17 columnas. Se detectaron nulos en `edad`, `promedio_gasto_comida`, `preferencias_alimenticias`, `telefono_contacto` y `correo_electronico`, y valores imposibles en `edad` (-5 y 300) y `frecuencia_visita` (-3).

**Limpieza (sobre la base completa, antes de filtrar):**

| Problema | Decisión |
|---|---|
| Edades -5 (97) y 300 (110) | Pasar a nulo e imputar con la mediana por género |
| Frecuencia -3 (1.547) | Reemplazar por 4 (mediana por género) |
| Gasto nulo (145) | Imputar con la mediana por género |
| Preferencias nulas (1.403) | Reemplazar por "No especificado" |
| Duplicados | Ninguno |
| Teléfono y correo (~50% nulos) | Se dejan sin tratar: son datos de contacto y no entran al análisis de comportamiento |

Se usó la mediana porque no se distorsiona con valores extremos. Los 1.463 registros con gasto 0 se conservaron: coinciden con los clientes de frecuencia 0, es decir, no son errores.

**Filtro:** se eligió **Chicago** por tener más clientes (5.384).

**Hallazgos principales en Chicago:**
- Género equilibrado (50,4% masculino y 49,6% femenino).
- Preferencias: carnes (29,5%) y vegetariano (20,9%).
- El 62,7% consume licor y el 41,1% tiene membresía premium.
- Pago: efectivo (39,4%), tarjeta (33,2%) y app (25,5%).
- Frecuencia de visita: mediana de 4 al mes.
- Gasto: mediana de 19,18; el 61% está en el rango bajo (hasta 25).
- Ingresos: mediana de 3.244; el 60% está en el rango bajo (hasta 4.500).

## 3. Avance 2

## 4. Avance 3

## 5. Cómo reproducir
Instalar `pandas`, `numpy`, `matplotlib`, `seaborn` y `requests`, y ejecutar los notebooks en orden. La API key de Yelp debe ir como variable de entorno, nunca en el repositorio.