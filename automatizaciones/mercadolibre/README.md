🔗 [← Volver al Catálogo General](../../CATALOGO.md)
---

# 🚀 Notificador de Ventas Mercado Libre → WhatsApp

**Archivo asociado:** `Notificador_Ventas_ML_WhatsApp.json`

---

## 🎯 ¿Qué hace?
- Consulta periódicamente las órdenes pagadas en Mercado Libre mediante la API oficial.
- Cada vez que detecta una venta nueva, envía un aviso inmediato al WhatsApp del comerciante usando CallMeBot.
- Incluye: producto vendido, monto total y nombre/nickname del comprador.

---

## 📋 Requisitos
- **Access Token de Mercado Libre válido** (obtenido al autorizar la app del cliente).
- **Refresh Token de Mercado Libre** (para renovar el access token cada vez que expire).
- **Número de WhatsApp del cliente** (formato internacional, por ej. +54911XXXXXXX).
- **API Key de CallMeBot** (el cliente la obtiene enviando el mensaje `I allow callmebot to send me messages` al bot de CallMeBot).

---

## ⏱️ Tiempo de configuración
- Autorizar app Mercado Libre del cliente: 10 minutos.
- Pegado de tokens y datos en el workflow: 20 minutos.
- Prueba de envío por WhatsApp: 5 minutos.  
**Total estimado:** 30–40 minutos en primera instalación.

---

## 💰 Modelo comercial sugerido
- **Instalación inicial:** USD 100 (supone trabajo de vinculación, configuración y prueba).
- **Mantenimiento mensual:** USD 25 (cubre costo de hosting + seguimiento y renovación de tokens en su servidor dedicado).

---

## 📌 Notas
- Este flujo requiere que cada cliente tenga **su propia instancia n8n** (cumpliendo con la licencia de n8n).
- El archivo JSON aquí guardado se importa en la instancia n8n del cliente (`Workflows → Import from File`).
- Solo deben actualizarse: tokens, número de WhatsApp y apikey.
