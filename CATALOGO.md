# 📦 Catálogo de Automatizaciones n8n para Minoristas

Este documento reúne **todas las automatizaciones disponibles**, los **ejemplos de entregas ficticias**, las **demos visuales** y el **checklist completo de instalación**.  
Sirve como **índice maestro del proyecto**.

---

## 🚀 Automatizaciones disponibles

### 1. Genérico → WhatsApp
- **Archivo:** `/automatizaciones/generico/Notificador_Ventas_WhatsApp.json`
- **Funcionalidad:** Flujo básico de Webhook → WhatsApp (demo universal).  
- **Precio sugerido:** USD 75 instalación + USD 25/mes mantenimiento.  
- **Uso típico:** mostrar concepto, enganchar sistemas con webhooks.

---

### 2. MercadoLibre → WhatsApp
- **Archivo:** `/automatizaciones/mercadolibre/Notificador_Ventas_ML_WhatsApp.json`
- **Funcionalidad:** Consulta órdenes pagadas en la API de MercadoLibre → WhatsApp (producto, monto, cliente).  
- **Precio sugerido:** USD 100 instalación + USD 25/mes mantenimiento.  
- **Uso típico:** vendedores de ML que no quieren depender de mails fallidos.

---

### 3. Shopify / WooCommerce / Tiendanube → WhatsApp
- **Archivo:** `/automatizaciones/shopify/Notificador_Ventas_Shopify_WhatsApp.json` (pendiente).  
- **Funcionalidad:** Recibe webhook de "Order Created" → WhatsApp inmediato.  
- **Precio sugerido:** USD 80 instalación + USD 25/mes mantenimiento.  

---

### 4. Email → WhatsApp
- **Archivo:** `/automatizaciones/email/Notificador_Ventas_Email_WhatsApp.json` (pendiente).  
- **Funcionalidad:** Detecta correos con asunto de venta ("Has vendido", "Order confirmed") y dispara WhatsApp.  
- **Precio sugerido:** USD 60 instalación + USD 20/mes mantenimiento.  

---

### 5. Google Sheets / Excel → WhatsApp
- **Archivo:** `/automatizaciones/sheets/Notificador_Ventas_Sheets_WhatsApp.json` (pendiente).  
- **Funcionalidad:** Cada fila nueva en una planilla con venta → alerta en WhatsApp.  
- **Precio sugerido:** USD 70 instalación + USD 25/mes mantenimiento.  

---

## 📒 Ejemplos de entregas ficticias

La carpeta [/entregas/](entregas/README.md) contiene registros de entregas a clientes con formato uniforme.

Ejemplos incluidos:

- [Panadería San José – MercadoLibre API](entregas/PanaderiaSanJose-ejemploML-WA.md)  
- [Tienda Ropa Juana – Shopify/Tiendanube](entregas/TiendaRopaJuana-ejemploShopifyTiendNube-WA.md)  
- [Dietética Vida Sana – Email](entregas/DieteticaVidaSana-ejemploEmail-WA.md)  
- [Ferretería Pérez – Sheets](entregas/FerreteriaPerez-ejemplo-Sheets-WA.md)  

Cada archivo incluye fecha, configuración, número de WhatsApp/API key, estado de prueba, precio y notas.

---

## 🎥 Demos disponibles

En la carpeta [/demo/](demo/README.md) hay presentaciones visuales para clientes, con solo 2 capturas: **Venta → WhatsApp recibido**.

- [Demo MercadoLibre](demo/Demo_MercadoLibre.md)  
- [Demo Shopify/Tiendanube/WooCommerce](demo/Demo_Shopify.md)  
- [Demo Email](demo/Demo_Email.md)  
- [Demo Google Sheets](demo/Demo_Sheets.md)  

💡 Mostrar esto en reuniones transmite el valor en segundos:  
**"Cuando vendo → me suena el WhatsApp al instante."**

---

## 💼 Modelo Comercial Referencial

- **Instalación inicial:** USD 60–100  
- **Mantenimiento mensual:** USD 20–25  
- **Regla legal:** 1 instancia de n8n dedicada por cliente (cumple licencia).  
- **Se vende como servicio:** instalación + soporte + monitoreo, no como “software”.  

---

## ✅ Checklist resumido para instalación en clientes

1. **Preparar entorno**  
   - Importar workflow .json correcto desde `/automatizaciones/`.  
   - Renombrar con nombre del cliente.

2. **Configurar origen de ventas**  
   - MercadoLibre → pegar `access_token`.  
   - Shopify/Tiendanube/Woo → conectar webhook a URL de n8n.  
   - Email → casilla IMAP/Gmail + App Password.  
   - Sheets → conectar Google + definir rango.

3. **Configurar destino WhatsApp (CallMeBot)**  
   - Cliente manda desde su WhatsApp: `I allow callmebot to send me messages`.  
   - Copiar su número (+54…) y API key.  
   - Pegarlos en el nodo de WhatsApp.

4. **Probar en vivo**  
   - Simular orden / enviar mail / fila en Sheets.  
   - Confirmar WhatsApp recibido.

5. **Documentar + cobrar**  
   - Crear `entregas/NOMBRECLIENTE.md`.  
   - Anotar configuración, fecha, precio, estado de prueba.  
   - Cobrar instalación y agendar mantenimiento.  

---
