# Reportes Ejecutivos UUPZ 2026

## Última actualización
Semana 22 · Junio 2026

## Datos por plataforma (Mayo 2026 acumulado Marzo–Mayo, incluye SEM22)

### SHEIN
- Pedidos: 16,675 | Vasos: 236,760 | Neto: $3,014,071 | $/vaso: $12.73
- YoY: +207% | MoM mayo: +36.4%
- SEM_V = [17280,15390,14150,15000,15090,15820,18330,16330,22180,20060,18450,19940,25060]
- SEM_P = [1158,1039,929,1054,1105,1147,1327,1174,1580,1399,1343,1434,1738]
- DOW winner: Domingo (2,636 ped)

### Amazon
- Pedidos: 1,765 | Vasos: 36,350 | Neto: $476,185 | $/vaso: $13.10
- YoY: −15.4% | MoM mayo: +3.8%
- SEM_V = [2875,3020,2320,1755,2860,2360,3670,3330,2010,3560,2820,3160,2610]
- SEM_P = [132,143,109,101,117,119,174,160,96,164,144,169,137]
- DOW winner: Martes (451 ped)

### Mercado Libre
- Pedidos: 5,118 | Vasos: 261,421 | Neto: $2,488,728 | $/vaso: $9.52
- YoY: +48.4% | MoM mayo: +6.5%
- SEM_V = [21261,16622,15461,16036,13403,18113,24032,25198,29278,23804,19214,17079,19389]
- SEM_P = [394,339,307,272,274,330,459,489,592,627,570,474,474]
- DOW winner: Martes (955 ped)

### TikTok
- Pedidos: 2,284 | Vasos: 33,966 | Neto: $640,130 | $/vaso: $18.84
- YoY: +1,720% | MoM mayo: −29.5%
- SEM_V = [1566,1372,2266,2476,2939,3458,4006,2962,2056,4666,1416,2719,2064]
- SEM_P = [95,89,144,163,186,236,251,203,144,310,148,183,132]

### WEB / Shopify
- Pedidos: 1,126 | Vasos: 109,688 | Neto: $1,402,905 | $/vaso: $12.79
- YoY: −9.7% | MoM mayo: +38.0%
- SEM_V = [10106,7805,5614,6822,6309,6867,8224,7399,5670,11110,11796,9900,12200]
- SEM_P = [111,83,67,59,61,78,87,80,51,121,99,99,122]

---

## Global (global_2026_ejecutivo.html)

```javascript
const PLAT = [
  { id:'shein',  label:'SHEIN',         color:'#e11d48', active:true,
    pedidos:16675, vasos:236760, neto:3014071, pvNeto:12.73, yoy:207,   momMayo:36.4,
    vasos2025:[4610,22030,50440],   vasos2026:[68740,71060,96960] },
  { id:'amazon', label:'Amazon',        color:'#f97316', active:true,
    pedidos:1765,  vasos:36350,  neto:476185,  pvNeto:13.10, yoy:-15.4, momMayo:3.8,
    vasos2025:[11765,14840,16380], vasos2026:[12500,11700,12150] },
  { id:'ml',     label:'Mercado Libre', color:'#3483fa', active:true,
    pedidos:5118,  vasos:261421, neto:2488728, pvNeto:9.52,  yoy:48.4,  momMayo:6.5,
    vasos2025:[34645,66344,75229], vasos2026:[76620,89470,95331] },
  { id:'tiktok', label:'TikTok',        color:'#2d2d2d', active:true,
    pedidos:2284,  vasos:33966,  neto:640130,  pvNeto:18.84, yoy:1720,  momMayo:-29.5,
    vasos2025:[15,604,1247],       vasos2026:[7680,15421,10865] },
  { id:'web',    label:'WEB',           color:'#6366f1', active:true,
    pedidos:1126,  vasos:109688, neto:1402905, pvNeto:12.79, yoy:-9.7,  momMayo:38.0,
    vasos2025:[38653,62567,48735], vasos2026:[33798,31884,44006] },
];
```

KPIs globales: Pedidos=26,968 · Vasos=678,185 · Neto=$8.02M · $/Vaso=$11.83
Vol %: ML 38.5% · SHEIN 34.9% · WEB 16.2% · Amazon 5.4% · TikTok 5.0%
Neto %: SHEIN 37.6% · ML 31.0% · WEB 17.5% · TikTok 8.0% · Amazon 5.9%
Bubble chart: `const maxX = 300000, minY = 8.5, maxY = 20;`
