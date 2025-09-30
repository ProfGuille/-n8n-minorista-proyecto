🔗 [← Volver a Entregas](README.md)
---

# Cliente: Ferretería Pérez

**Fecha de instalación:** 25/02/2024  
**Automatización instalada:** Google Sheets → WhatsApp  
**Archivo JSON usado:** Notificador_Ventas_Sheets_WhatsApp.json

---

## 📋 Configuración realizada
- **Origen de ventas:** Google Sheets compartido por el cliente.  
- **Trigger configurado en n8n:** Nodo Google Sheets.  
  - Evento: Nueva fila añadida.  
  - Hoja: `Ventas_2024`  
  - Columnas usadas:  
    - Columna A → Producto  
    - Columna B → Monto  
    - Columna C → Cliente (nombre o teléfono).  
- **Credenciales:** OAuth Google (cuenta del cliente, autorizada en n8n).  
- **Número de WhatsApp configurado:** +54 9 260 456 7890  
- **API Key CallMeBot:** generada y entregada por el cliente.  

---

## ✅ Estado
- Instalación probada: **Sí** (fila dummy con producto: `Martillo`, monto: `$2500`).  
- WhatsApp recibido correctamente con datos de la fila: **Sí**  
- Cliente validó que cada fila real dispara el mensaje: **Sí**

---

## 💸 Comercial
- Instalación cobrada: **USD 70**  
- Mantenimiento mensual: **USD 25**  
- Fecha de próximo cobro: 25/03/2024  

---

## 📝 Notas adicionales
- Cliente quiere que además de notificarse él, se envíe copia de alerta al celular del encargado de stock.  
- Se dejó preparado nodo duplicado de WhatsApp para futuro agregar múltiples números.
