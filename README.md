# Camoufox + CapSolver: Solución de Automatización Web Imparable

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Status: Active](https://img.shields.io/badge/Status-Active-brightgreen.svg)]()

> **Resumen (TL;DR)**: Utilice **Camoufox** para evadir la huella digital del navegador y **CapSolver** para resolver automáticamente CAPTCHAs como Cloudflare Turnstile y reCAPTCHA v2/v3. Juntos, permiten una automatización web estable y similar a la humana a escala, con una detección mínima y altas tasas de éxito.

---

## 🚀 Visión General

La automatización web moderna se enfrenta a dos obstáculos principales: la sofisticada **huella digital anti-bot** y los persistentes **desafíos de CAPTCHA**. Este repositorio proporciona una solución robusta y lista para producción al integrar dos potentes herramientas:

1.  **Camoufox**: Un navegador anti-detección de código abierto basado en Firefox que falsifica las huellas digitales del navegador a nivel nativo de C++.
2.  **CapSolver**: Un servicio de resolución de CAPTCHA impulsado por IA que maneja prácticamente todos los desafíos modernos, incluidos Turnstile y reCAPTCHA.

Esta integración garantiza que sus scripts de automatización parezcan usuarios humanos legítimos, tanto en términos de identidad del navegador como de comportamiento de interacción.

![Diagrama de Integración](https://assets.capsolver.com/prod/posts/camoufox-capsolver/BHTvecwsomf8-10fb15c77258a991b0028080a64fb42d.png)

## ✨ Características Clave

| Característica | Contribución de Camoufox | Contribución de CapSolver |
| :--- | :--- | :--- |
| **Anti-Detección** | Falsificación de huella digital nativa C++ (WebGL, Canvas, Fuentes, etc.) | N/A |
| **Omisión de CAPTCHA** | N/A | Resuelve Turnstile, reCAPTCHA v2/v3
, etc. |
| **Comportamiento Humano** | Algoritmo de humanización de movimiento del ratón incorporado | Resolución rápida, confiable y consistente |
| **Geo-Localización** | Cálculo automático de zona horaria/localidad basado en la IP del proxy | N/A |

## 🛠️ Configuración e Instalación

### 1. Requisitos Previos

Necesitará una clave API de CapSolver. Puede registrarse y obtener su clave aquí:
👉 **[Obtenga Su Clave API de CapSolver](https://dashboard.capsolver.com/dashboard/overview/?utm_source=github&utm_medium=repo&utm_campaign=camoufox-capsolver-integration)**

> **Bono**: ¡Use el código **`CAMOUFOX`** al registrarse para recibir créditos de bonificación!

### 2. Instalación

Instale el paquete Python Camoufox y la biblioteca `httpx` para llamadas a la API asíncronas.

```bash
# Instale Camoufox con soporte GeoIP
pip install -U camoufox[geoip]

# Instale el cliente HTTP necesario
pip install httpx

# Descargue el binario del navegador Camoufox
camoufox fetch
```

## 💻 Lógica Central de Integración (Método API)

El enfoque recomendado es utilizar la API de CapSolver directamente para un control y flexibilidad máximos.

### `capsolver_api.py`

Este módulo contiene las funciones asíncronas para interactuar con la API de CapSolver.

## 💡 Ejemplos de Uso

### Ejemplo 1: Resolución de Cloudflare Turnstile

Este ejemplo demuestra cómo usar la función `solve_captcha` para obtener un token Turnstile e inyectarlo en la página controlada por Camoufox.

```python
# El código de ejemplo está en el archivo main.py
# Consulte el archivo main.py para la implementación completa.
```

## 🔗 Alternativa: Método de Extensión del Navegador

Para casos de uso más simples, puede cargar la extensión del navegador CapSolver directamente en Camoufox.

```python
from camoufox.sync_api import Camoufox

with Camoufox(
    addons=["/ruta/a/extension-capsolver"],
    headless=False  # Las extensiones generalmente requieren el modo con interfaz
) as browser:
    page = browser.new_page()
    # La extensión detectará y resolverá automáticamente los CAPTCHAs
```

## 🤝 Contribución

¡Las contribuciones son bienvenidas! Si tiene sugerencias para mejorar la integración, abra un problema (issue) o envíe una solicitud de extracción (pull request).

## 📄 Licencia

Este proyecto está bajo la Licencia MIT - consulte el archivo [LICENSE](LICENSE) para obtener más detalles.
