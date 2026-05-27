# Reportes Ejecutivos UUPZ 2026

## Estructura de cada reporte de plataforma

Todos los reportes siguen la misma estructura (referencia: tiktok_2026_ejecutivo.html):

### Secciones en orden
1. **Header** — nombre plataforma, periodo, 4 KPI pills (pedidos, vasos, neto, $/vaso)
2. **Volumen semanal** — gráfica de barras canvas (SEM10–SEM21), pills de pedidos encima de cada barra
3. **Día de la semana** — tabla DOW con ganador destacado
4. **Volumen mensual** — barras Marzo/Abril/Mayo con etiqueta K
5. **Top 5 modelos mayo** — cards con barra de progreso
6. **Comparativa YoY** — barras dobles 2025 vs 2026 por mes
7. **Desglose Modelo × Capacidad** — stacked bar canvas
8. **Tabla resumen mensual** — pedidos, ticket, vasos, neto, $/vaso con variaciones MoM

### Clases CSS clave
- `.g2` → grid 2 columnas (1.55fr + 1fr)
- `.g2b` → grid 2 columnas (2fr + 1fr)
- `.top5-grid` → grid (1fr + 1.4fr)
- `.badge`, `.badge-g` → chips KPI (rojo/verde)
- `.dow-row`, `.dow-bf`, `.dow-win` → filas día semana
- `.st` → tabla summary mensual
- `.top5-card`, `.top5-hdr`, `.top5-row` → cards Top 5

### Funciones JS compartidas
- `initCanvas(id, h)` → inicializa canvas responsive
- `drawBar(ctx, data, cfg)` → barras simples
- `drawStackedBar(ctx, labels, datasets, cfg)` → barras apiladas
- `roundRect(ctx, x, y, w, h, r)` → helper ML (inline IIFE)
- IIFE `drawYoy()` → gráfica comparativa YoY

---

## Datos por plataforma (Mayo 2026 acumulado Marzo–Mayo)

### SHEIN
- Pedidos: 8,260 | Vasos: 212,240 | Neto: $2,699,352 | $/vaso: $12.72
- YoY: +175% | MoM mayo: +2.0%
- Archivo: `VENTAS SHEIN 2026.xlsx`

### Amazon
- Pedidos: 1,210 | Vasos: 33,740 | Neto: $442,069 | $/vaso: $13.10
- YoY: −21.5% | MoM mayo: −18.5%
- Archivo: `VENTAS AMAZON 2026.xlsx`

### Mercado Libre
- Pedidos: 4,734 | Vasos: 241,322 | Neto: $2,297,893 | $/vaso: $9.52
- YoY: +36.9% | MoM mayo: −15.9%
- Archivo: `VENTAS ML 2026.xlsx` (sheet VENTAS, rows 53–85)
- Weekly pedidos en sheet VENTAS, rows 73–85 (pivot Semana × Paquetes)

### TikTok
- Pedidos: 2,152 | Vasos: 32,656 | Neto: $598,101 | $/vaso: $18.32
- YoY: +1,650% | MoM mayo: −24.5%
- Archivo: `VENTAS WEB + TT 2026.xlsx`
- Sin comisión de plataforma → neto = bruto / 1.16

### WEB / Shopify
- Pedidos: 1,003 | Vasos: 97,348 | Neto: $1,256,840 | $/vaso: $12.91
- YoY: −35.1% | MoM mayo: −0.7%
- Archivo: `VENTAS WEB + TT 2026.xlsx`
- Comisión Shopify 15.21% → neto = bruto × 0.8479 / 1.16
- Canal B2B/mayoreo → ticket promedio ~$1,714/pedido, ~97 vasos/orden

---

## Global (global_2026_ejecutivo.html)

Array PLAT (última versión completa):
```javascript
const PLAT = [
  { id:'shein',  label:'SHEIN',         color:'#e11d48', active:true,
    pedidos:8260,  vasos:212240, neto:2699352, pvNeto:12.72, yoy:175,   momMayo:2.0,
    vasos2025:[4610,22030,50440],   vasos2026:[68740,71060,72440] },
  { id:'amazon', label:'Amazon',         color:'#f97316', active:true,
    pedidos:1210,  vasos:33740,  neto:442069,  pvNeto:13.10, yoy:-21.5, momMayo:-18.5,
    vasos2025:[11765,14840,16380], vasos2026:[12500,11700,9540] },
  { id:'ml',     label:'Mercado Libre',  color:'#3483fa', active:true,
    pedidos:4734,  vasos:241322, neto:2297893, pvNeto:9.52,  yoy:36.9,  momMayo:-15.9,
    vasos2025:[34645,66344,75229], vasos2026:[76620,89470,75232] },
  { id:'tiktok', label:'TikTok',         color:'#2d2d2d', active:true,
    pedidos:2152,  vasos:32656,  neto:598101,  pvNeto:18.32, yoy:1650,  momMayo:-24.5,
    vasos2025:[15,604,1247],       vasos2026:[9116,13411,10129] },
  { id:'web',    label:'WEB',            color:'#6366f1', active:true,
    pedidos:1003,  vasos:97348,  neto:1256840, pvNeto:12.91, yoy:-35.1, momMayo:-0.7,
    vasos2025:[38653,62567,48735], vasos2026:[33798,31884,31666] },
];
```

KPIs globales: Pedidos=17,359 · Vasos=617,306 · Neto=$7.29M · $/Vaso=$11.82
Bubble chart: `maxX=280000, minY=8.5, maxY=20`

---

## Notas técnicas

- Los Excel (~58–60 MB) requieren `openpyxl.load_workbook(..., read_only=True)` para no crashear
- ML weekly pedidos: sheet VENTAS, pivot en rows 73–85 (col A=Semana, col B=Paquetes, col C=Vasos)
- TikTok y WEB están en el mismo archivo `VENTAS WEB + TT 2026.xlsx`
- Colores de mes: Marzo=`#94a3b8` (gris), Abril=color plataforma, Mayo=`#9333ea` (morado)
