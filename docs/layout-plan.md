# Plan de layout - Dashboard de influencer

Planificación previa a la maquetación. Stack: **HTML + Tailwind CSS v4** (CDN `@tailwindcss/browser@4`), sin CSS propio.

Referencia visual: [reference/influencer-dashboard-reference.png](reference/influencer-dashboard-reference.png)

## Estructura

```
<body>
  <aside>            sidebar: logo, <nav>, perfil
  <div>
    <header>         h1, subtítulo, acciones
    <main>
      <section>      1. KPIs
      <section>      2. Drivers
      <section>      3. Detalle operacional
```

### Escritorio (`lg` en adelante)

```
+-----------+---------------------------------------------+
|  Logo     |  Título + subtítulo          [Botones]      |
|           +---------------------------------------------+
|  Nav      |  [KPI] [KPI] [KPI] [KPI]                    |
|           +----------------------+----------------------+
|           |  Plataformas         |  Productos           |
|           +----------------------+----------------------+
|  Perfil   |  Engagement por plataforma (3 columnas)     |
|           +---------------------------------------------+
|           |  Tabla de campañas                          |
|           +----------------------+----------------------+
|           |  Tabla de plataformas|  Alertas             |
+-----------+----------------------+----------------------+
```

### Tablet (`md`)

- Sidebar convertido en barra superior con la navegación en horizontal.
- KPIs en 2 columnas; drivers en 1-2 columnas.

### Móvil (base)

- Barra superior con logo y navegación con scroll propio si no cabe.
- Todo en 1 columna. Las tablas hacen scroll horizontal **dentro de su card**, nunca la página.

## Bloques

### 1. KPIs (bloque superior)

| KPI | Valor | Responde a |
|-----|-------|------------|
| Comisiones totales | 6.270 € | ¿Cuánto dinero genero en comisiones? |
| Ingresos por ventas | 41.800 € | Volumen de negocio generado |
| Tasa de conversión | 0,07% | ¿Qué tan bien convierten mis anuncios? |
| Engagement medio | 7,8% | Engagement global |

### 2. Drivers (bloque intermedio)

1. **Rendimiento por plataforma:** comisión y % del total con barras de progreso.
2. **Rendimiento por producto:** precio, ingresos, comisión y conversión.
3. **Engagement por plataforma:** likes, comentarios, compartidos, guardados.

### 3. Detalle operacional (bloque inferior)

- **Tabla de campañas:** marca, producto, fechas, estado, ventas, comisión, ROI.
- **Tabla de plataformas:** alcance, engagement, conversiones, coste, ROI.
- **Alertas:** caídas o picos de conversión y anomalías.

## Componentes reutilizables

| Componente | Uso |
|------------|-----|
| Card KPI | etiqueta + icono + valor + variación |
| Card widget | contenedor con título para drivers y tablas |
| Barra de progreso | % por plataforma |
| Tabla | campañas, productos, plataformas |
| Badge | estado (Activa / Pausada / Finalizada) y tasas |
| Alerta | icono + mensaje + severidad |

## Estilo

- Fondo `slate-50`, cards blancas con `rounded-2xl`, borde `slate-200` y sombra suave.
- Sidebar `slate-900`; acento `indigo-600`.
- Colores por plataforma: Instagram `pink-500`, TikTok `slate-900`, YouTube `red-600`.
- Variación positiva `emerald-600`; negativa `red-600`.

## Datos de ejemplo

Comisión: 15% de cada venta.

| Producto | Precio | Clics | Ventas | Conversión | Ingresos | Comisión |
|----------|--------|-------|--------|------------|----------|----------|
| A | 50 € | 5.770 | 300 | 5,2% | 15.000 € | 2.250 € |
| B | 120 € | 3.660 | 150 | 4,1% | 18.000 € | 2.700 € |
| C | 80 € | 2.900 | 110 | 3,8% | 8.800 € | 1.320 € |
| **Total** | | **12.330** | **560** | **4,5%** | **41.800 €** | **6.270 €** |

Conversión por producto = ventas / clics.

| Plataforma | Me gusta | Comentarios | Compartidos | Guardados | Total |
|------------|----------|-------------|-------------|-----------|-------|
| Instagram | 14.200 | 1.600 | 1.200 | 1.000 | 18.000 |
| TikTok | 29.500 | 2.900 | 2.600 | 1.000 | 36.000 |
| YouTube | 4.900 | 650 | 300 | 150 | 6.000 |

| Plataforma | Alcance | Interacciones | Engagement | Conversiones | Coste | Comisión | ROI |
|------------|---------|---------------|-----------|--------------|-------|----------|-----|
| Instagram | 250.000 | 18.000 | 7,2% | 280 | 900 € | 3.135 € | 3,5x |
| TikTok | 400.000 | 36.000 | 9,0% | 190 | 600 € | 2.127 € | 3,5x |
| YouTube | 120.000 | 6.000 | 5,0% | 90 | 500 € | 1.008 € | 2,0x |

Fórmulas: engagement = interacciones / alcance; conversión = conversiones / alcance; ROI = comisión / coste.
