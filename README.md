# ⚡ CYBER_PARSE // Y2K DATA SUITE PRO

> **Kernel Data Inspector & Transpiler (v2.0)**  
> Una suite web *client-side* para formateo, minificación, inspección interactiva y conversión bidireccional de datos entre estructuras **JSON** y **YAML**.

![License: MIT](https://img.shields.io/badge/License-MIT-00f0ff.svg)
![Build: Pure JS](https://img.shields.io/badge/Stack-HTML5%20%7C%20CSS3%20%7C%20VanillaJS-ff007f.svg)
![Privacy: 100% Offline](https://img.shields.io/badge/Privacy-100%25%20Local-ffe600.svg)

---

## 📸 Vista General

`CYBER_PARSE` está diseñado para ofrecer una experiencia visual **Y2K / Cyberpunk** combinada con utilidades de ingeniería de software de alta productividad. No requiere backend, no realiza peticiones HTTP externas para el procesamiento de datos y garantiza privacidad total (*Zero-Data Retention*).

---

## 🛠️ Características Principales

* ⚡ **Formateado & Minificación JSON:** Sangría configurable (2 o 4 espacios) o compactación a una sola línea.
* 🔄 **Transpilación Bidireccional:** Conversión instantánea de **JSON ↔ YAML** con preservación de tipos de datos.
* 🌳 **Inspector en Árbol (Tree View):** Renderizado jerárquico recursivo de la estructura del documento con nodos colapsables.
* 📊 **Analizador de Métricas (Y2K Stats):**
  * Cálculo de peso en Bytes (Entrada vs. Salida).
  * Porcentaje de reducción de tamaño.
  * Conteo total de claves (*Keys*).
  * Profundidad máxima de anidación (*Max Depth*).
* 📁 **Drag & Drop:** Carga rápida mediante arrastre de archivos `.json`, `.yaml` o `.txt`.
* 💾 **Persistencia Local:** Sincronización automática del último búfer de entrada en `localStorage`.
* 🛡️ **Zero-Network Privacy:** Procesamiento local en el hilo de ejecución de la GPU/CPU del navegador.

---

## 🏗️ Arquitectura Técnica

El proyecto implementa el **Module Pattern (IIFE)** para garantizar el encapsulamiento de métodos, evitando la contaminación del scope global.

---

## 🔰 Manual para Novatos (Guía de Inicio Rápido)

### 1. ¿Cómo ejecutar el proyecto?
1. Descarga el archivo `index.html`.
2. Haz doble clic sobre él para abrirlo en cualquier navegador (Chrome, Firefox, Edge, Safari).
3. **¡Listo!** No necesitas instalar Node.js, compilar ni levantar servidores locales.

### 2. Primeros Pasos
* **Formatear un JSON desordenado:** Pega tu texto en el panel izquierdo (`INPUT_STREAM`) y haz clic en `⚡ [Format JSON]`.
* **Probar datos de muestra:** Si no tienes un JSON a mano, usa la sección inferior **`// INJECT_PAYLOADS:`** y presiona `[1. JSON Valid]`.
* **Ver los datos visualmente:** Haz clic en el botón `🌳 [Tree View]` de la barra superior para explorar tus objetos y arrays mediante desplegables.
* **Descargar el resultado:** Haz clic en `DOWNLOAD` en la esquina superior derecha del panel de salida.

---

## 🚀 Manual para Avanzados (Guía Técnica & DX)

### 1. Inserción de Payloads y Pruebas
Puedes inyectar estructuras JSON complejas mediante la API interna del módulo `TestData`:

```javascript
// Cargar un payload directamente en el Input Stream desde la consola del navegador
TestData.loadDeepJSON();
Toolbox.formatJSON();

//PRUEBAS

1. 🛒 E-Commerce API (Anidación profunda, arrays de objetos y métricas)
Ideal para probar el Tree View, el conteo de Total Keys y el calculador de Profundidad Máxima.

JSON
{
  "status": "success",
  "code": 200,
  "data": {
    "store": {
      "id": "str_9921",
      "name": "CyberTech Store",
      "location": "Sector 7",
      "active": true
    },
    "pagination": {
      "page": 1,
      "limit": 10,
      "total_items": 42
    },
    "products": [
      {
        "id": "prod_101",
        "title": "Teclado Mecánico RGB",
        "price": 129.99,
        "currency": "USD",
        "stock": 15,
        "categories": ["periféricos", "gaming"],
        "specs": {
          "switches": "Cherry MX Red",
          "wireless": true,
          "battery_mah": 4000
        },
        "reviews": [
          {"user": "Alex", "rating": 5, "comment": "Excelente táctica"},
          {"user": "Marta", "rating": 4, "comment": "Buen brillo de LED"}
        ]
      },
      {
        "id": "prod_102",
        "title": "Monitor UltraWide 34\"",
        "price": 499.50,
        "currency": "USD",
        "stock": 0,
        "categories": ["monitores", "workstation"],
        "specs": {
          "refresh_rate_hz": 144,
          "panel": "IPS",
          "hdr": true
        },
        "reviews": []
      }
    ]
  }
}
2. 🔐 Auth Response & JWT User Profile (Excelente para "Sanitización/Masking")
Esta simula la respuesta de un servidor tras iniciar sesión. Contiene datos sensibles como tokens, hashes de contraseñas e IPs.

JSON
{
  "auth": {
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c",
    "token_type": "Bearer",
    "expires_in": 3600,
    "refresh_token": "rfr_8819283912a39b00"
  },
  "user": {
    "uuid": "u_8829-ab12-9901",
    "username": "cyber_ghost",
    "email": "user@network-corp.io",
    "role": "SYSTEM_ADMIN",
    "is_verified": true,
    "security": {
      "mfa_enabled": true,
      "last_login_ip": "192.168.1.104",
      "password_hash": "$2b$12$eA3Z8vD9H2lq1KjJ3uO4.e.rP0A1B2C3D4E5F6G7H8I9J0K1L2M3N4"
    }
  }
}
3. 📊 Server Telemetry & Logs (Probar compresión y "Minify")
Un JSON repleto de métricas e historia de estado de un servidor. Puedes darle a Minify para ver cuánto porcentaje de peso comprimes.

JSON
{
  "cluster_id": "eu-west-1a",
  "timestamp": 1785068000,
  "metrics": {
    "cpu": {
      "usage_percent": 78.4,
      "cores": 16,
      "temperature_celsius": 62.5
    },
    "memory": {
      "total_mb": 32768,
      "used_mb": 24500,
      "free_mb": 8268,
      "swap_used_mb": 120
    },
    "network": {
      "interface": "eth0",
      "bytes_sent": 104857600,
      "bytes_recv": 524288000,
      "packets_dropped": 0
    }
  },
  "active_services": [
    { "name": "nginx", "status": "running", "pid": 1042 },
    { "name": "postgresql", "status": "running", "pid": 1105 },
    { "name": "redis", "status": "degraded", "pid": 1201 },
    { "name": "docker_daemon", "status": "running", "pid": 892 }
  ]
}
4. ⚙️ Archivo de Configuración YAML (Probar conversor YAML ➡️ JSON)
Para probar la conversión en sentido contrario, pega este bloque en el panel de entrada y dale al botón [YAML > JSON]:

YAML
version: '3.8'
services:
  web_app:
    image: node:20-alpine
    container_name: frontend_prod
    ports:
      - "8080:8080"
    environment:
      NODE_ENV: production
      PORT: 8080
      API_URL: "https://api.domain.internal/v1"
    restart: always

  database:
    image: postgres:15
    container_name: postgres_db
    environment:
      POSTGRES_DB: app_data
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: super_secret_password_123
    volumes:
      - db_data:/var/lib/postgresql/data

volumes:
  db_data:
    external: false
