# Cliente: Tienda de Ropa Juana

**Fecha de instalación:** 15/02/2024  
**Automatización instalada:** Shopify → WhatsApp  
**Archivo JSON usado:** Notificador_Ventas_Shopify_WhatsApp.json

---

## 📋 Configuración realizada
- **Origen de ventas:** Shopify (Webhook "Order Created").  
- **Webhook configurado en Shopify:**  
  - URL: https://n8n-juana.myvps.com/webhook/venta-shopify  
  - Método: POST  
  - Evento: Order Created.  
- **Número de WhatsApp configurado:** +54 9 294 456 7890  
- **API Key CallMeBot:** proporcionada tras activación del cliente.  

---

## ✅ Estado
- Instalación probada: **Sí** (pedido de test en Shopify).  
- WhatsApp recibido al simular venta: **Sí**  
- Cliente validó que el aviso llega al instante: **Sí**

---

## 💸 Comercial
- Instalación cobrada: **USD 80**  
- Mantenimiento mensual: **USD 25**  
- Fecha de próximo cobro: 15/03/2024  

---

## 📝 Notas adicionales
- Cliente pidió modificar el texto de alerta para que incluya el número de orden de Shopify.  
- Se dejó configurada la variable `{{$json["id"]}}` en el mensaje de WhatsApp.  
