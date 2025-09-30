🔗 [← Volver a Entregas](README.md)
---

# Cliente: Dietética Vida Sana

**Fecha de instalación:** 20/02/2024  
**Automatización instalada:** Email → WhatsApp  
**Archivo JSON usado:** Notificador_Ventas_Email_WhatsApp.json

---

## 📋 Configuración realizada
- **Origen de ventas:** Casilla de correo del cliente (Gmail).  
- **Trigger configurado en n8n:** Nodo IMAP Gmail con filtro de asunto `"Has vendido"`  
- **Credenciales:**  
  - Usuario: ventas@vidasana.com.ar  
  - App Password: generado en Google (NO expuesto en este repo).  
- **Número de WhatsApp configurado:** +54 9 351 654 7890  
- **API Key CallMeBot:** entregada tras activación del cliente.  

---

## ✅ Estado
- Instalación probada: **Sí** (simulación reenvío de correo de venta).  
- WhatsApp recibido con asunto extraído: **Sí**  
- Cliente confirmó que funciona con sus mails reales: **Sí**

---

## 💸 Comercial
- Instalación cobrada: **USD 60**  
- Mantenimiento mensual: **USD 20**  
- Fecha de próximo cobro: 20/03/2024  

---

## 📝 Notas adicionales
- Cliente pidió que además del asunto del mail, se extraiga el monto (contenido del cuerpo).  
- Se dejó pendiente ajuste en parsing del correo con nodo `Function` para detectar líneas como: `"Total: $XXXX"`.  
