# ✅ Checklist y Manual de Implementación para Clientes

Esta es tu guía **única y detallada** para instalar cualquier automatización. Contiene las instrucciones que debes seguir y las que debes **copiar y pegar para tu cliente**.

---

### **Paso 1: Preparar el Entorno (Tu Tarea Interna)**
-   [ ] Abre la **instancia n8n del cliente** en tu servidor (VPS).
-   [ ] Importa el workflow `.json` correcto desde tu repositorio en `/automatizaciones/`.
-   [ ] Renombra el workflow con un nombre claro (ej: `Ventas_ML_PanaderiaSanJose`).

---

### **Paso 2: Obtener la Información del Cliente**

Esta es la parte donde interactúas con el cliente. A continuación, tienes las guías para cada caso.

---
#### **A. Para CUALQUIER Cliente (Activación de WhatsApp)**

**1. Qué necesitas pedirle:** El número de WhatsApp y una clave (API Key) que él mismo debe generar.

**2. Instrucciones para darle al cliente (copia y pega):**

> Hola [Nombre del Cliente], para activar las notificaciones en tu WhatsApp, por favor sigue estos 2 simples pasos:
>
> 1.  Desde tu celular, envía este mensaje exacto:
>     `I allow callmebot to send me messages`
>     al siguiente número de WhatsApp: **+34 684 783 708**
>
> 2.  El bot te responderá con un mensaje que contiene tu "API Key" (es un número largo). Por favor, reenvíame ese mensaje o copia y pega la clave aquí.
>
> ¡Con eso ya podremos conectar todo!

---
#### **B. Cliente con Mercado Libre**

**1. Qué necesitas pedirle:** Un `Refresh Token` y su `Seller ID`. Sigue las instrucciones para obtenerlos sin usar esas palabras técnicas.

**2. Instrucciones para darle al cliente (copia y pega):**

> Para conectar tu cuenta de Mercado Libre de forma 100% segura, necesito que autorices mi aplicación. Es un proceso de 1 minuto y yo **nunca veré tu contraseña**.
>
> 1.  Haz clic en este enlace:
>     **https://auth.mercadolibre.com.ar/authorization?response_type=code&client_id=1423485043615619&redirect_uri=https://www.google.com**
>
> 2.  Inicia sesión con tu cuenta de Mercado Libre si te lo pide.
>
> 3.  Haz clic en el botón azul que dice **"Permitir"** o **"Autorizar"**.
>
> Después de autorizar, la página te llevará a Google. Eso es todo. Por favor, **cópia y pégala aquí la dirección web completa** que te aparece en el navegador. ¡Avísame cuando lo hayas hecho!

**3. Tu Tarea (después de que el cliente te pasa la URL):**
*   De la URL que te pasó el cliente (ej: `https://www.google.com/?code=TG-xxxxxxxx`), **copia solo el código** que empieza con `TG-`. Ese es el `code`.
*   Abre tu terminal y pega el siguiente comando, **reemplazando `[AQUÍ_PEGAS_EL_CODE]`** por el código que acabas de copiar.

    ```bash
    curl -X POST "https://api.mercadolibre.com/oauth/token" \
    -H "Content-Type: application/x-www-form-urlencoded" \
    -d "grant_type=authorization_code&client_id=1423485043615619&client_secret=kU3rHWl5UebbqNhm0W9cXUAwynpZum6P&code=[AQUÍ_PEGAS_EL_CODE]&redirect_uri=https://www.google.com"
    ```
*   La terminal te devolverá una respuesta en formato JSON. De ahí, **copia y guarda estos dos valores**:
    *   `"refresh_token": "TG-xxxxxxxx..."` ← **Este es el que usarás en el workflow.**
    *   `"user_id": 123456789` ← **Este es el Seller ID del cliente.**

---

### **Paso 3: Configurar el Workflow en n8n (Tu Tarea Interna)**
-   [ ] Abre el workflow importado.
-   [ ] **Nodo de Origen:** Pega las credenciales que obtuviste del cliente (el `refresh_token` y `seller_id` de ML, la `App Password` de Gmail, etc.).
-   [ ] **Nodo de Destino (WhatsApp):** Pega el `phone` y `apikey` del cliente.
-   [ ] Guarda el workflow.

---

### **Paso 4: Probar en Vivo (Instrucciones Detalladas)**

Aquí eliges la prueba según el sistema del cliente:

#### **Prueba para Mercado Libre**
1.  Abre el workflow en n8n y haz clic en el botón **"Execute Workflow"**.
2.  El workflow se ejecutará. Revisa el nodo **`2. Consultar Órdenes`**.
    -   Si el cliente tiene ventas pagadas recientes, el nodo mostrará datos en la sección "Output" y el cliente recibirá un WhatsApp.
    -   Si el `results` sale vacío (`[]`), significa que la conexión funcionó pero no hay nuevas ventas que reportar.
3.  **Para una prueba inmediata y visible para el cliente (incluso si no hay ventas):**
    -   Modifica temporalmente el nodo **`4. Enviar WhatsApp`**.
    -   En el campo `text`, borra la expresión y escribe un mensaje fijo como: `Prueba de conexión con Mercado Libre exitosa. ¡Ya estás listo para recibir notificaciones!`.
    -   Ejecuta el workflow. El cliente recibirá este mensaje y confirmará que la conexión funciona.
    -   **No olvides volver a poner la expresión original en el campo `text` después de la prueba.**

#### **Prueba para Shopify / WooCommerce / Tiendanube**
1.  Ve al panel de administrador de la tienda del cliente.
2.  Ve a la sección donde creaste el webhook (`Configuración > Notificaciones > Webhooks` o similar).
3.  Busca un botón o enlace que diga **"Enviar notificación de prueba"** (o "Send test notification"). Haz clic ahí.
4.  **Si no hay botón de prueba:** Crea un **pedido de prueba** en la tienda. Puedes usar un código de descuento del 100% o un método de pago manual ("contra reembolso") para que no implique dinero real. Luego, puedes cancelar el pedido.
5.  El cliente debe recibir un WhatsApp con los datos de la venta de prueba.

#### **Prueba para Email**
1.  Abre tu propia cuenta de correo (Gmail, Outlook, la que sea).
2.  Redacta un nuevo email.
    -   **Para:** La dirección de correo del cliente (la que configuraste en el nodo IMAP).
    -   **Asunto:** Escribe el texto exacto que pusiste en el filtro (ej: `Has vendido`).
3.  Envía el correo.
4.  En unos instantes (n8n revisa periódicamente), el cliente debe recibir el WhatsApp con el asunto del correo que enviaste.

#### **Prueba para Google Sheets**
1.  Abre la hoja de cálculo de Google Sheets del cliente.
2.  Ve a la primera fila vacía y **añade datos de prueba** en las columnas correspondientes (ej: Columna A: `Producto de Prueba`, Columna B: `100`).
3.  Dependiendo de la configuración del trigger, n8n lo detectará en el siguiente ciclo (puede tardar unos minutos) y el cliente recibirá el WhatsApp con los datos de esa fila.

---

### **Paso 5: Documentar y Cobrar (Tu Tarea Interna)**
-   [ ] Activa el workflow para que corra automáticamente.
-   [ ] En la carpeta `/entregas/`, crea un archivo `NOMBRE-CLIENTE.md` y completa la plantilla que está en `/entregas/README.md`.
-   [ ] Envía la confirmación y el link de pago por la instalación.
-   [ ] Registra la fecha para el próximo cobro del mantenimiento.
