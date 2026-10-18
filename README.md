# 🦑 Rabapark — Índice de Sufrimiento Aparcacionista de Santander

Mapa ciudadano que estima lo difícil que es aparcar por zonas de Santander, hecho un finde con **datos abiertos** del Ayuntamiento de Santander.

👉 **Demo:** https://rabapark.github.io/

## ¿Qué es?
Un mapa de calor de **presión de aparcamiento** (el "Índice de Sufrimiento Aparcacionista", de 😇 Bendición a 💀 Abandona toda esperanza) combinando zona azul (OLA), cercanía a playas y al centro, densidad de vados y los parkings subterráneos como "válvulas de escape".

Antes del mapa, **Rabuca** (la mascota: una raba de calamar) te lo explica en un intro de 5 pasos.

Incluye geolocalización ("¿Dónde estoy?"), buscador de destinos, ranking de barrios y tarjeta para compartir.

> ⚠️ Es **presión estimada estructural**, NO plazas libres en tiempo real (ese dato no está publicado en abierto).

## 😤 Quejas ciudadanas (datos abiertos)
Cualquiera puede marcar en el mapa dónde no ha podido aparcar (motivo + comentario opcional, **anónimo**). Las quejas se publican en vivo como **datos abiertos CC BY 4.0**, descargables en CSV y GeoJSON desde la web, o vía API (PostgREST de Supabase, solo lectura e inserción; la clave es pública por diseño):

```
GET https://axydjqbwnrrvhtksceco.supabase.co/rest/v1/quejas?select=*
apikey: sb_publishable_DgQxCjK25RV6KHlLp7PsYQ_w_Qazrue
```
Campos: `id`, `created_at` (UTC), `lat`, `lng`, `motivo` (`sin_sitio`, `zona_azul`, `carga_descarga`, `parking_lleno`, `mal_aparcados`, `otro`), `comentario` (≤280), `zona`. Resumen agregado: `/rest/v1/quejas_resumen`. Sin nombres, correos ni IPs; sin enlaces en comentarios; límite de ritmo (20 quejas/minuto en total y sin duplicados en el mismo punto durante 5 minutos). Ayuntamiento, prensa, asociaciones de vecinos: son vuestros, usadlos.

## Datos
- [Portal de Datos Abiertos de Santander](http://datos.santander.es/) — © Ayuntamiento de Santander, CC BY 4.0
- Mapa base © OpenStreetMap contributors

## Stack
HTML + [Leaflet](https://leafletjs.com/) en un único archivo autónomo. Datos procesados y embebidos como GeoJSON.

## Autor
Un proyecto de fin de semana de [Carlos Pérez del Molino](https://www.linkedin.com/in/carlosperezdelmolino/).
