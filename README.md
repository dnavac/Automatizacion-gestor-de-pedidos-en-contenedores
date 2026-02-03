# 📦 Automatización de Gestión de Contenedores (n8n)

Este flujo de trabajo de **n8n** permite automatizar la organización de documentos en Google Drive y la comunicación por correo electrónico basada en entradas de Google Sheets.

## 📋 Descripción del Flujo
El sistema monitorea una hoja de cálculo y realiza las siguientes acciones:
* **Sincronización:** Detecta nuevas filas en Google Sheets cada minuto.
* **Organización:** Crea o localiza carpetas en Google Drive basadas en el número de contenedor y de pedido.
* **Procesamiento de Imágenes:** Extrae IDs de archivos de Drive desde una lista de URLs y los organiza en las nuevas carpetas.
* **Notificaciones:**
    * Envía correos electrónicos al supervisor con opciones de Aceptar/Rechazar mediante enlaces de Webhook.
    * Envía confirmaciones personalizadas a los clientes finales con acceso a sus carpetas de pedidos.

## 🛠️ Requisitos
* Una instancia de **n8n** activa.
* Credenciales configuradas para:
    * **Google Sheets API**
    * **Google Drive API**
    * **Gmail API**

## 🚀 Instalación y Configuración

1. **Importar:** Importa el archivo `.json` en tu instancia de n8n.
2. **Personalización de IDs:** Debes actualizar los siguientes valores dentro de los nodos (marcados como placeholders en la versión limpia):
    * **documentId:** Cambia `ID_DE_TU_HOJA_DE_CALCULO` por el ID real de tu Google Sheet.
    * **folderId:** Cambia `ID_CARPETA_CONTENEDORES` por el ID de tu carpeta raíz en Google Drive.
    * **Emails:** Actualiza `correo_destinatario@ejemplo.com` por la dirección real del supervisor.
3. **Webhooks:** Asegúrate de actualizar las URLs de los botones en el nodo `Send a message` para que apunten a tu propia instancia de n8n.

## 📁 Estructura del Archivo
* **Nombre del Workflow:** contenedores-pedido
* **Nodos principales:** `Google Sheets Trigger`, `Google Drive` (Búsqueda/Creación/Upload), `Code` (JavaScript para limpieza de datos), `Gmail` (Notificaciones HTML).

---
**Nota de Seguridad:** Asegúrate de no compartir públicamente versiones de este flujo que contengan IDs de documentos privados o credenciales de acceso.
