# Rutina Lunes — Actualización Reportes Ejecutivos

**Frecuencia:** Cada lunes  
**Duración estimada:** 20–30 min  
**Carpeta:** `/Users/jacky/Documents/REPORTES JOCELYN/`

---

## Paso 1 — Confirmar archivos actualizados

Verificar que los Excel en la carpeta ya tienen los datos de la semana nueva:
- `VENTAS SHEIN 2026.xlsx`
- `VENTAS AMAZON 2026.xlsx`
- `VENTAS ML 2026.xlsx`
- `VENTAS WEB + TT 2026.xlsx`

Si no están actualizados, el usuario los carga antes de continuar.

---

## Paso 2 — Extraer datos de cada Excel

Usar siempre `openpyxl.load_workbook(..., read_only=True, data_only=True)`.

### Lo que extraer por plataforma

**Todos los reportes necesitan:**
- Vasos y pedidos por semana (SEM10 en adelante)
- Vasos y pedidos por mes (Marzo, Abril, Mayo + nueva semana/mes si aplica)
- Top 5 modelos del mes más reciente
- Comparativa YoY por mes
- DOW (día de la semana con más pedidos)
- Tabla resumen: pedidos, ticket promedio, vasos, neto, $/vaso con variación MoM

**ML específico:**
- Sheet: `VENTAS`
- Weekly pedidos: pivot en rows ~73–85 (Semana × Paquetes × Vasos)
- Monthly por modelo: pivot rows 5–22

**TikTok + WEB:**
- Mismo archivo `VENTAS WEB + TT 2026.xlsx`
- Separar datos por canal/cuenta

---

## Paso 3 — Actualizar constantes JS en cada reporte HTML

Archivos a editar y sus constantes principales:

### shein_2026_ejecutivo.html
```
SEM_VASOS, SEM_PEDIDOS, SEM_LABELS
MES_VASOS, MES_PEDIDOS
TOP5_MAYO
YOY.v2025, YOY.v2026
Tabla resumen (HTML estático)
KPI pills en header
```

### amazon_2026_ejecutivo.html
_(mismas constantes que SHEIN)_

### ml_2026_ejecutivo.html
```
SEM_VASOS, SEM_PEDIDOS, SEM_LABELS
MES_VASOS
TOP5_MAYO
COLOR_CAP.datasets (desglose modelo×capacidad)
YOY.v2025, YOY.v2026
DOW array
Tabla resumen
KPI pills en header
```

### tiktok_2026_ejecutivo.html
```
SEMS, SEM_V, SEM_P, SEM_C
MES_V, MES_C
v2025, v2026
ALL_MOD (Top 5)
MAY_TOTAL
KPI pills
```

### web_2026_ejecutivo.html
_(mismas constantes que tiktok)_

### global_2026_ejecutivo.html
```
Array PLAT — actualizar pedidos, vasos, neto, pvNeto, yoy, momMayo,
             vasos2025[], vasos2026[] para cada plataforma
KPI pills del header
```

---

## Paso 4 — Verificar consistencia

- Suma de vasos de todas las plataformas = total en global
- Suma de neto de todas las plataformas = total en global
- Que el mes nuevo aparezca en las gráficas con color correcto
  - Mes más reciente → `#9333ea` (morado)
  - Mes anterior → color plataforma
  - Meses más antiguos → `#94a3b8` (gris)

---

## Paso 5 — Presentar archivos al usuario

Compartir links de los 6 archivos actualizados:
1. shein_2026_ejecutivo.html
2. amazon_2026_ejecutivo.html
3. ml_2026_ejecutivo.html
4. tiktok_2026_ejecutivo.html
5. web_2026_ejecutivo.html
6. global_2026_ejecutivo.html

---

## Notas importantes

- Si se agrega un mes nuevo (ej. Junio), hay que:
  - Rotar colores: el mes que era morado pasa a color plataforma, el nuevo mes es morado
  - Agregar columna a la tabla resumen
  - Ampliar SEM_LABELS si hay semanas nuevas
- Si hay una nueva semana dentro del mes actual, solo agregar el valor al array SEM_VASOS/SEM_PEDIDOS
