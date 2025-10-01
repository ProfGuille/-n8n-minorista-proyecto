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
*   Abre tu terminal y pega el siguiente comando, **reemplazando `[AQUÍ_PEGAS_TU_CLIENT_SECRET]` y `[AQUÍ_PEGAS_EL_CODE]`** por los valores correctos.

    ```bash
    curl -X POST "https://api.mercadolibre.com/oauth/token" \
    -H "Content-Type: application/x-www-form-urlencoded" \
    -d "grant_type=authorization_code&client_id=1423485043615619&client_secret=[AQUÍ_PEGAS_TU_CLIENT_SECRET]&code=[AQUÍ_PEGAS_EL_CODE]&redirect_uri=https://www.google.com"
    ```
*   La terminal te devolverá una respuesta en formato JSON. De ahí, **copia y guarda estos dos valores**:
    *   `"refresh_token": "TG-xxxxxxxx..."` ← **Este es el que usarás en el workflow.**
    *   `"user_id": 123456789` ← **Este es el Seller ID del cliente.**

---
#### **C. Cliente con Email (Gmail)**

**1. Qué necesitas pedirle:** Su dirección de correo y una "Contraseña de Aplicación".

**2. Instrucciones para darle al cliente (copia y pega):**

> Para que el robot pueda leer los correos de venta de forma segura, Google requiere una "Contraseña de Aplicación". Es una clave especial de 16 letras que solo sirve para esta automatización y **no expone tu contraseña principal**.
>
> Sigue estos pasos para generarla:
>
> 1.  Ve a este enlace oficial de Google: **https://myaccount.google.com/apppasswords**
> 2.  Inicia sesión con tu cuenta de Gmail si te lo pide.
> 3.  En "Seleccionar app", elige **"Otra (nombre personalizado)"**.
> 4.  Escribe un nombre para identificarla, por ejemplo: `Robot N8N Ventas`.
> 5.  Haz clic en **"Generar"**.
> 6.  Google te mostrará una **contraseña de 16 letras** en un recuadro amarillo. **Cópiala y pégamela aquí**.
>
> **Importante:** Esta clave solo se muestra una vez. Cópiala antes de cerrar la ventana.

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
2.  El workflow se ejecutará. Si el cliente tiene ventas pagadas recientes, recibirá un WhatsApp.
3.  **Para una prueba inmediata:** Modifica temporalmente el nodo **`4. Enviar WhatsApp`**. En el campo `text`, escribe un mensaje fijo como: `Prueba de conexión con Mercado Libre exitosa.`. Ejecuta el workflow. El cliente recibirá este mensaje. **No olvides volver a poner la expresión original después.**

#### **Prueba para Shopify / WooCommerce / Tiendanube**
1.  Ve al panel de la tienda del cliente, a la sección "Webhooks".
2.  Busca un botón que diga **"Enviar notificación de prueba"**.
3.  **Si no hay botón de prueba:** Crea un **pedido de prueba** en la tienda usando un método de pago manual.
4.  El cliente debe recibir un WhatsApp.

#### **Prueba para Email**
1.  Abre tu propia cuenta de correo.
2.  Redacta un nuevo email. **Para:** La dirección de correo del cliente. **Asunto:** `Has vendido`.
3.  Envía el correo. El cliente debe recibir el WhatsApp.

#### **Prueba para Google Sheets**
1.  Abre la hoja de cálculo de Google Sheets del cliente.
2.  Añade una fila con datos de prueba. El cliente debe recibir el WhatsApp.

---

### **Paso 5: Documentar y Cobrar (Tu Tarea Interna)**
-   [ ] Activa el workflow para que corra automáticamente.
-   [ ] En la carpeta `/entregas/`, crea un archivo `NOMBRE-CLIENTE.md` y completa la plantilla que está en `/entregas/README.md`.
-   [ ] Envía la confirmación y el link de pago por la instalación.
-   [ ] Registra la fecha para el próximo cobro del mantenimiento.
