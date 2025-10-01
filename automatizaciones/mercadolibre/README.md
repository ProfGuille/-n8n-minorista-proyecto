🔗 [← Volver al Catálogo General](../../CATALOGO.md)
---

# 🚀 Notificador de Ventas Mercado Libre → WhatsApp

**Archivo asociado:** `Notificador_Ventas_ML_WhatsApp.json`

---

## 🎯 ¿Qué hace?
Este es un workflow **autocontenido** que se ejecuta cada 5 minutos y realiza el ciclo completo:
1.  **Renueva el access_token** de Mercado Libre automáticamente usando el `refresh_token`.
2.  **Consulta las órdenes pagadas** más recientes.
3.  Si encuentra órdenes nuevas, **envía un aviso inmediato a WhatsApp** con los detalles.

---

## 📋 Requisitos (por cliente)
-   **Refresh Token de Mercado Libre:** Se obtiene una única vez al autorizar tu aplicación en la cuenta del cliente.
-   **Seller ID del cliente:** El ID de vendedor de su cuenta de Mercado Libre.
-   **Número de WhatsApp del cliente.**
-   **API Key de CallMeBot** del cliente.

---

## 💰 Modelo comercial sugerido
-   **Instalación inicial:** USD 100.
-   **Mantenimiento mensual:** USD 25.

---

## 📌 Notas
-   Este flujo es **estable y 100% automático**. No requiere intervención manual para renovar tokens.
-   Se instala importando el `.json` en la instancia n8n del cliente y personalizando los 4 campos clave.
