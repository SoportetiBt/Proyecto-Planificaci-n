# Portal de Planificación

Portal web autocontenido para visualizar los datos de planificación operativa de **Canon** (RM y V Región) y **Rosen** (V Región y IV Coquimbo).

## Demo

Una vez desplegado en Vercel, el portal estará disponible en una URL del tipo:

`https://portal-planificacion.vercel.app`

## Estructura del repositorio

```
.
├── index.html        # Portal completo (autocontenido, sin dependencias)
├── vercel.json       # Configuración de despliegue en Vercel
├── .gitignore        # Archivos excluidos del repositorio
└── README.md         # Este archivo
```

## Uso local

Abre `index.html` con doble click en tu navegador. No requiere servidor.

## Cómo cargar datos

El portal acepta los siguientes archivos Excel desde la pestaña **Cargar Archivos**:

- `Planificacion RM <DD.MM.YYYY>.xlsx` → Canon RM
- `Planificacion Rosen V <DD.MM.YYYY>.xlsx` → Rosen V Región
- `Planificacion Rosen IV <DD.MM.YYYY>.xlsx` → Rosen IV (Coquimbo)
- `Maestro de Planificacion.xlsx` → Catálogo de vehículos y capacidades
- `Malla de Rotacion Planificacon.xlsx` → (opcional) Rotación semanal

Los datos cargados quedan guardados en el navegador del usuario (localStorage).

## Despliegue

Este repositorio está pensado para desplegarse como **sitio estático en Vercel** conectado directamente al repositorio de GitHub. Cada vez que hagas un commit a la rama `main`, Vercel reconstruye y publica automáticamente.

Ver `GUIA_DEPLOY.md` para instrucciones paso a paso.

## Privacidad

- El portal es **solo lectura de visualización**. No envía datos a ningún backend.
- Los archivos Excel se procesan **localmente en el navegador** del usuario.
- No se incluyen Excel con datos reales en este repositorio (ver `.gitignore`).

## Licencia

Uso interno.
