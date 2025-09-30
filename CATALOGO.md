# 📦 Catálogo de Automatizaciones n8n para Minoristas

Este archivo organiza **todas las automatizaciones disponibles**, listas para importar en n8n y adaptar a cada cliente según el sistema que use para registrar sus ventas.  

---

## 🚀 Automatizaciones Disponibles

### 1. Genérico → WhatsApp
- **Archivo:** `/automatizaciones/generico/Notificador_Ventas_WhatsApp.json`
- **Funcionalidad:** Flujo simple de Webhook → WhatsApp (demo base).  
- **Precio sugerido:** USD 75 instalación + USD 25/mes mantenimiento.  
- **Ideal para:** mostrar rápido el concepto o enganchar cualquier sistema que exponga un webhook.  

---

### 2. MercadoLibre → WhatsApp
- **Archivo:** `/automatizaciones/mercadolibre/Notificador_Ventas_ML_WhatsApp.json`
- **Funcionalidad:** Consulta órdenes pagadas vía API de MercadoLibre y envía WhatsApp con datos (producto, cliente, monto).  
- **Precio sugerido:** USD 100 instalación + USD 25/mes mantenimiento.  
- **Ideal para:** vendedores de MercadoLibre que no quieren depender de mails inestables.  

---

### 3. Shopify / WooCommerce / Tiendanube → WhatsApp
- **Archivo:** `/automatizaciones/shopify/Notificador_Ventas_Shopify_WhatsApp.json` (pendiente generar).  
- **Funcionalidad:** Recibe notificaciones de ventas mediante webhook → gatilla mensaje inmediato por WhatsApp.  
- **Precio sugerido:** USD 80 instalación + USD 25/mes mantenimiento.  

---

### 4. Email → WhatsApp
- **Archivo:** `/automatizaciones/email/Notificador_Ventas_Email_WhatsApp.json` (pendiente generar).  
- **Funcionalidad:** Detecta correos entrantes con asunto de “nueva venta” (ej. MercadoLibre, Tiendanube) y dispara WhatsApp.  
- **Precio sugerido:** USD 60 instalación + USD 20/mes mantenimiento.  

---

### 5. Sheets / Excel → WhatsApp
- **Archivo:** `/automatizaciones/sheets/Notificador_Ventas_Sheets_WhatsApp.json` (pendiente generar).  
- **Funcionalidad:** Cada fila nueva en hoja de cálculo (Google Sheets) = venta → notificación de WhatsApp.  
- **Precio sugerido:** USD 70 instalación + USD 25/mes mantenimiento.  

---

## 📒 Ejemplos de Entregas (ficticias)

La carpeta `/entregas/` incluye ejemplos documentados de cómo queda cada instalación entregada a clientes:  

- `PanaderiaSanJose-ejemploML-WA.md` → Caso MercadoLibre (API).  
- `TiendaRopaJuana-ejemploShopifyTiendNube-WA.md` → Caso Shopify/Tiendanube (Webhook).  
- `DieteticaVidaSana-ejemploEmail-WA.md` → Caso Email.  
- `FerreteriaPerez-ejemplo-Sheets-WA.md` → Caso Sheets.  

Cada archivo incluye: fecha, configuración, números/API key, estado de prueba, notas y modelo comercial aplicado.

---

## 💼 Modelo Comercial General

- **Instalación inicial:** USD 60–100 (según origen).  
- **Mantenimiento mensual:** USD 20–25.  
- **Cumplimiento legal:** Una instancia n8n separada por cliente (cumple licencia).  
- **Valor principal:** el cliente no necesita abrir n8n, solo recibe sus ventas directo al WhatsApp (que es lo que realmente quiere).

---

## ✅ Cómo usar este catálogo

1. Elegí el flujo según el sistema del cliente.  
2. Importá el JSON en la instancia n8n del cliente.  
3. Configurá:
   - Credenciales de origen (API Token ML, webhook shopify, usuario Gmail, conexión Sheets, etc.)
   - Número de WhatsApp y apikey de CallMeBot.  
4. Probá un evento de venta → el WhatsApp llega.  
5. Documentá en `/entregas/` usando la plantilla estándar.  

---
