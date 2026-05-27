# Memoria — UUPZ Reportes Ejecutivos

## Contexto
Jacky, área de reportes y análisis UUPZ. Trabajamos en la carpeta **REPORTES JOCELYN**.
Cada lunes se actualizan los reportes ejecutivos con datos de la semana anterior.

## Reportes activos
| Archivo | Plataforma | Fuente de datos |
|---------|------------|-----------------|
| `shein_2026_ejecutivo.html` | SHEIN | `VENTAS SHEIN 2026.xlsx` |
| `amazon_2026_ejecutivo.html` | Amazon | `VENTAS AMAZON 2026.xlsx` |
| `ml_2026_ejecutivo.html` | Mercado Libre | `VENTAS ML 2026.xlsx` |
| `tiktok_2026_ejecutivo.html` | TikTok | `VENTAS WEB + TT 2026.xlsx` |
| `web_2026_ejecutivo.html` | WEB/Shopify | `VENTAS WEB + TT 2026.xlsx` |
| `global_2026_ejecutivo.html` | Global (5 plataformas) | Todos los anteriores |

→ Detalle completo: memory/projects/reportes-ejecutivos.md

## Términos rápidos
| Término | Significado |
|---------|-------------|
| **vasos** | Unidades de producto vendidas |
| **pedidos / paquetes** | Número de órdenes/envíos |
| **neto** | Ingreso neto después de comisión + IVA |
| **bruto** | Ingreso bruto antes de deducciones |
| **SEM** | Semana del año (SEM10 = semana 10) |
| **YoY** | Year-over-Year, comparativa vs año anterior |
| **MoM** | Month-over-Month, comparativa vs mes anterior |
| **DOW** | Day of Week — día de la semana |
| **PLAT** | Array JS con configuración de plataformas en global |
| **PV neto** | Precio promedio por vaso (neto ÷ vasos) |

→ Glosario completo: memory/context/glosario.md

## Fórmulas clave
- **Neto general:** `bruto × (1 − comisión) / 1.16`
- **TikTok** (sin comisión): `bruto / 1.16`
- **WEB/Shopify** (15.21% comisión): `bruto × 0.8479 / 1.16`
- **ML** (~27.5% comisión): `bruto × 0.725 / 1.16`
- **SHEIN** (~30% comisión): `bruto × 0.70 / 1.16`
- **Amazon** (~25% comisión): `bruto × 0.75 / 1.16`

## Colores de plataforma
| Plataforma | Color |
|------------|-------|
| SHEIN | `#e11d48` |
| Amazon | `#f97316` |
| Mercado Libre | `#3483fa` |
| TikTok | `#2d2d2d` |
| WEB | `#6366f1` |
| Marzo (neutro) | `#94a3b8` |
| Mayo (acento) | `#9333ea` |

## Rutina lunes — actualización semanal
1. El usuario comparte los archivos Excel actualizados (o confirma que ya están en la carpeta)
2. Leo cada Excel con `openpyxl read_only=True` (archivos ~58-60 MB)
3. Extraigo: vasos/pedidos por semana, por mes, por modelo, YoY, DOW
4. Actualizo las constantes JS en cada reporte HTML
5. Actualizo el array `PLAT` en `global_2026_ejecutivo.html`
6. Verifico que los totales cuadren entre plataformas y el global

→ Procedimiento detallado: memory/projects/rutina-lunes.md
