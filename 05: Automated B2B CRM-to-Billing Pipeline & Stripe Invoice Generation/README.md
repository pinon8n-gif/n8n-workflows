# 💳 Automated B2B CRM-to-Billing Pipeline & Stripe Invoice Generation

Un pipeline avanzado construido en n8n diseñado para sincronizar el cierre de tratos comerciales en HubSpot con la plataforma de pagos Stripe, automatizando la validación fiscal, la normalización de direcciones mediante Regex y la creación de facturas.

## ⚙️ Arquitectura del Sistema

El proyecto automatiza todo el ciclo financiero posterior a una venta cerrada:

1. 🎯 CRM Trigger & Validation Engine

**Archivo:** `5-workflow.json` Un motor de validación que se ejecuta en tiempo real tras ganar un trato.

* **Captura de Eventos:** Recibe peticiones vía Webhook desde HubSpot al momento de cambiar el estado de un trato a "Closed Won".
* **Control de Integridad:** Evalúa si existen los datos fiscales obligatorios (RUT/NIF, Dirección y Email).
* **Control de Excepciones:** Si faltan datos clave, frena el flujo de cobro y crea automáticamente un Ticket de Soporte en HubSpot para alertar al equipo comercial.

2. 🧹 Data Normalization & Billing Engine

**Archivo:** `5-workflow.json` Un procesador de datos y emisor de facturas en Stripe.

* **Normalización (ETL):** Utiliza **JavaScript** y expresiones regulares (**Regex**) para limpiar y desglosar la dirección del cliente en calle (`line1`), ciudad (`city`) y código postal (`postal_code`).
* **Creación de Cliente:** Da de alta o actualiza al cliente corporativo en la API de Stripe con la información sanitizada.
* **Emisión de Factura:** Agrega el concepto de cobro (`Invoice Item`) con el monto del trato y finaliza la factura oficial.
* **Sincronización Bidireccional:** Actualiza el trato en HubSpot adjuntando la URL pública de la factura (`hosted_invoice_url`) para agilizar la cobranza.

## 🛠️ Stack Tecnológico

* **Orquestación:** n8n, Webhooks, Error Handling (Ticket Creation).
* **CRM & Ventas:** HubSpot API (Deals & Tickets Management).
* **Pasarela de Pagos:** Stripe API (Customers, Invoice Items, Invoices via HTTP REST).
* **Procesamiento:** JavaScript, Regex, manipulación avanzada de JSON.

## 🚀 Cómo importar este flujo

1. Descarga el archivo `.json` de este directorio.
2. En tu instancia de n8n, ve a *Workflows > Import from File...*
3. Configura tus propias credenciales para HubSpot y la API de Stripe.
4. Ajusta los parámetros de los encabezados HTTP según tu entorno.
