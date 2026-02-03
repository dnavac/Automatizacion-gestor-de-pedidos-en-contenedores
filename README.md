# 📦 Automatización de Gestión de Contenedores (n8n)

Este flujo de trabajo de **n8n** permite automatizar la organización de documentos en Google Drive y la comunicación por correo electrónico basada en entradas de Google Sheets.

## 📋 Descripción del Flujo
El sistema monitorea una hoja de cálculo y realiza las siguientes acciones:
* **Sincronización:** Detecta nuevas filas en Google Sheets cada minuto. [cite: 1.1]
* **Organización:** Crea o localiza carpetas en Google Drive basadas en el número de contenedor y de pedido. [cite: 1.1]
* **Procesamiento de Imágenes:** Extrae IDs de archivos de Drive desde una lista de URLs y los organiza en las nuevas carpetas. [cite: 1.1]
* **Notificaciones:**
    * Envía correos electrónicos al supervisor con opciones de Aceptar/Rechazar mediante enlaces de Webhook. [cite: 1.1]
    * Envía confirmaciones personalizadas a los clientes finales con acceso a sus carpetas de pedidos. [cite: 1.1]

## 🛠️ Requisitos
* Una instancia de **n8n** activa. [cite: 1.1]
* Credenciales configuradas para:
    * **Google Sheets API** [cite: 1.1]
    * **Google Drive API** [cite: 1.1]
    * **Gmail API** [cite: 1.1]

## 🚀 Instalación y Configuración

1. **Importar:** Importa el archivo `.json` en tu instancia de n8n.
2. **Personalización de IDs:** Debes actualizar los siguientes valores dentro de los nodos (marcados como placeholders en la versión limpia):
    * **documentId:** Cambia `ID_DE_TU_HOJA_DE_CALCULO` por el ID real de tu Google Sheet. [cite: 1.1]
    * **folderId:** Cambia `ID_CARPETA_CONTENEDORES` por el ID de tu carpeta raíz en Google Drive. [cite: 1.1]
    * **Emails:** Actualiza `correo_destinatario@ejemplo.com` por la dirección real del supervisor. [cite: 1.1]
3. **Webhooks:** Asegúrate de actualizar las URLs de los botones en el nodo `Send a message` para que apunten a tu propia instancia de n8n. [cite: 1.1]

## 📁 Estructura del Archivo
* **Nombre del Workflow:** mariano [cite: 1.1]
* **Nodos principales:** `Google Sheets Trigger`, `Google Drive` (Búsqueda/Creación/Upload), `Code` (JavaScript para limpieza de datos), `Gmail` (Notificaciones HTML). [cite: 1.1]

---
**Nota de Seguridad:** Asegúrate de no compartir públicamente versiones de este flujo que contengan IDs de documentos privados o credenciales de acceso.
