# 📦 Catálogo de Automatizaciones n8n para Minoristas

Este documento reúne todas las automatizaciones disponibles, los ejemplos de entregas ficticias y las demos visuales.  
Sirve como **índice maestro del proyecto**.

---

## 🚀 Automatizaciones disponibles

### 1. Genérico → WhatsApp
- **Archivo:** `/automatizaciones/generico/Notificador_Ventas_WhatsApp.json`
- **Funcionalidad:** Flujo básico de Webhook → WhatsApp (demo universal).  
- **Precio sugerido:** USD 75 instalación + USD 25/mes mantenimiento.  
- **Uso típico:** presentaciones iniciales o conectar sistemas que ya exponen webhooks.

---

### 2. MercadoLibre → WhatsApp
- **Archivo:** `/automatizaciones/mercadolibre/Notificador_Ventas_ML_WhatsApp.json`
- **Funcionalidad:** Consulta órdenes pagadas en la API de MercadoLibre → WhatsApp con producto, monto y cliente.  
- **Precio sugerido:** USD 100 instalación + USD 25/mes mantenimiento.  
- **Uso típico:** vendedores de ML que no quieren depender de mails fallidos.

---

### 3. Shopify / WooCommerce / Tiendanube → WhatsApp
- **Archivo:** `/automatizaciones/shopify/Notificador_Ventas_Shopify_WhatsApp.json` (pendiente).  
- **Funcionalidad:** Conecta webhook de “Order Created” de la tienda → WhatsApp instantáneo.  
- **Precio sugerido:** USD 80 instalación + USD 25/mes mantenimiento.  

---

### 4. Email → WhatsApp
- **Archivo:** `/automatizaciones/email/Notificador_Ventas_Email_WhatsApp.json` (pendiente).  
- **Funcionalidad:** Detecta correos de “Has vendido” o “New Order” y dispara WhatsApp.  
- **Precio sugerido:** USD 60 instalación + USD 20/mes mantenimiento.  

---

### 5. Google Sheets / Excel → WhatsApp
- **Archivo:** `/automatizaciones/sheets/Notificador_Ventas_Sheets_WhatsApp.json` (pendiente).  
- **Funcionalidad:** Una fila nueva en una planilla (producto + monto) → genera WhatsApp automático.  
- **Precio sugerido:** USD 70 instalación + USD 25/mes mantenimiento.  

---

## 📒 Ejemplos de entregas ficticias

La carpeta [/entregas/](entregas/README.md) contiene entregas documentadas con formato estandarizado.  
Ejemplos ya cargados:

- [Panadería San José – ML API](entregas/PanaderiaSanJose-ejemploML-WA.md)  
- [Tienda Ropa Juana – Shopify/Tiendanube](entregas/TiendaRopaJuana-ejemploShopifyTiendNube-WA.md)  
- [Dietética Vida Sana – Email](entregas/DieteticaVidaSana-ejemploEmail-WA.md)  
- [Ferretería Pérez – Sheets](entregas/FerreteriaPerez-ejemplo-Sheets-WA.md)  

Cada archivo incluye:  
- Fecha, cliente y sistema configurado.  
- Número de WhatsApp + API key usados.  
- Estado de pruebas.  
- Modelo comercial y notas.

---

## 🎥 Demos disponibles

En la carpeta [/demo/](demo/README.md) están listas presentaciones visuales con capturas, pensadas para **mostrar el valor al cliente en segundos**.

- [Demo MercadoLibre](demo/Demo_MercadoLibre.md)  
- [Demo Shopify / Tiendanube / WooCommerce](demo/Demo_Shopify.md)  
- [Demo Email](demo/Demo_Email.md)  
- [Demo Google Sheets / Excel](demo/Demo_Sheets.md)

💡 Todas siguen el mismo esquema:  
**1. Captura de la venta** → **2. Captura del WhatsApp recibido** → explicación en texto breve.

---

## 💼 Modelo Comercial Referencial

- **Instalación inicial:** USD 60–100 según el origen.  
- **Mantenimiento mensual:** USD 20–25.  
- **Cumplimiento legal:** Una instancia de n8n por cliente.  
- **Entregables:**  
  - Importación del workflow en instancia propia.  
  - Configuración con datos del cliente.  
  - Prueba en vivo.  
  - Documentación en `/entregas/`.

---
