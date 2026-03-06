# 📈 **Simulador Bursátil en Tiempo Real**

### _Una Aplicación Full-Stack con Vue.js, Firebase y la API de Yahoo Finance_

<div align="center">

[![Vue.js](https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D)](https://vuejs.org/)
[![Firebase](https://img.shields.io/badge/firebase-ffca28?style=for-the-badge&logo=firebase&logoColor=black)](https://firebase.google.com/)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white)](https://getbootstrap.com/)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

<br>

</div>

---

## 📋 **Tabla de Contenidos**

1. [🎯 Objetivo del Proyecto](#-objetivo-del-proyecto)
2. [✨ Características Principales](#-características-principales)
3. [🏗️ Arquitectura del Proyecto](#️-arquitectura-del-proyecto)
4. [🛠️ Stack Tecnológico](#️-stack-tecnológico)
5. [⚙️ Configuración Inicial (Paso a Paso)](#️-configuración-inicial-paso-a-paso)
6. [🔐 Seguridad: Variables de Entorno](#-seguridad-variables-de-entorno)
7. [🛡️ Buenas Prácticas de Ciberseguridad](#️-buenas-prácticas-de-ciberseguridad)
8. [📊 Obtención de Datos Reales (Yahoo Finance)](#-obtención-de-datos-reales-yahoo-finance)
9. [🚀 Despliegue en Producción](#-despliegue-en-producción)
10. [👨‍🏫 Autor y Contacto](#-autor-y-contacto)
11. [📄 Licencia](#-licencia)

---

## 🎯 **Objetivo del Proyecto**

Este proyecto es un **producto digital educativo** diseñado para demostrar el desarrollo de una aplicación web profesional y segura. Su objetivo es permitir a los usuarios:

- Registrarse e iniciar sesión de forma segura utilizando **Firebase Authentication**.
- Visualizar una lista de activos financieros (acciones) con **datos en tiempo real** obtenidos de la API pública de Yahoo Finance.
- Realizar operaciones simuladas de **compra y venta** para gestionar un portafolio de inversión personal.
- Todo ello implementado con **estrictas medidas de seguridad** (sanitización de entradas, protección de rutas, variables de entorno) y un **código limpio y modular**.

---

## ✨ **Características Principales**

- **🧑‍🤝‍🧑 Autenticación de Usuarios:** Sistema completo de registro e inicio de sesión con email/contraseña, gestionado por Firebase.
- **📡 Datos de Mercado en Tiempo Real:** Conexión a la API de Yahoo Finance para mostrar precios y variaciones actualizados de acciones como Apple, Microsoft, Tesla, etc.
- **📱 Diseño Totalmente Responsive:** Interfaz de usuario moderna y adaptable a cualquier dispositivo gracias a **Bootstrap 5**.
- **💰 Simulador de Portafolio:** Los usuarios pueden comprar y vender acciones de forma simulada para ver cómo evoluciona su cartera de inversión.
- **🛡️ Seguridad Reforzada:** Implementación de sanitización de inputs con DOMPurify, protección de rutas con Vue Router y uso de variables de entorno para credenciales sensibles.
- **🏗️ Código Modular y Escalable:** Estructura de carpetas organizada por funcionalidad (stores, servicios, vistas, utilidades) para facilitar el mantenimiento y la colaboración.

---

## 🏗️ **Arquitectura del Proyecto**

La aplicación sigue una arquitectura limpia y por capas, separando claramente las responsabilidades.

```mermaid
graph TD
    A[Usuario] --> B{Vue Router<br/>Protección de Rutas}
    B -- Ruta Pública --> C[Vistas<br/>Home, Login, Register]
    B -- Ruta Privada --> D[Vista Dashboard]

    C --> E[Stores (Pinia)<br/>auth.js]
    D --> E

    E --> F[Servicios (Services)]
    F --> G[Firebase Auth]
    F --> H[Yahoo Finance API]

    E --> I[Utilidades (Utils)<br/>sanitize.js]
    I --> J[(DOMPurify)]

    style B fill:#f9f,stroke:#333,stroke-width:2px
    style E fill:#ccf,stroke:#333,stroke-width:2px
    style F fill:#cfc,stroke:#333,stroke-width:2px
    style I fill:#fcf,stroke:#333,stroke-width:2px
```

### **Estructura de Carpetas**

```
simulador-bursatil/
├── 📁 .vscode/                  # Configuración del editor
├── 📁 node_modules/              # Dependencias (ignorado por git)
├── 📁 public/                    # Archivos públicos estáticos
├── 📁 src/                       # Código fuente de la aplicación
│   ├── 📁 assets/                # Recursos estáticos (imágenes, estilos globales)
│   ├── 📁 components/            # Componentes reutilizables (opcional)
│   ├── 📁 config/                # Archivos de configuración (constantes, etc.)
│   │   └── constants.js
│   ├── 📁 router/                # Configuración de las rutas
│   │   └── index.js
│   ├── 📁 services/              # Lógica de negocio y comunicación con APIs externas
│   │   ├── firebase.js
│   │   └── stockApi.js
│   ├── 📁 stores/                # Estado global de la aplicación con Pinia
│   │   └── auth.js
│   ├── 📁 utils/                 # Funciones de utilidad y helpers
│   │   └── sanitize.js
│   ├── 📁 views/                 # Componentes de las páginas (vistas del router)
│   │   ├── HomePage.vue
│   │   ├── LoginPage.vue
│   │   ├── RegisterPage.vue
│   │   └── Dashboard.vue
│   ├── App.vue                   # Componente raíz de la aplicación
│   └── main.js                   # Punto de entrada de la aplicación
├── 📁 tests/                      # Archivos de prueba (opcional)
├── .env                           # 🔴 NO SUBIR: Variables de entorno locales (reales)
├── .env.example                   # ✅ SUBIR: Ejemplo de variables de entorno
├── .gitignore                     # Archivos y carpetas ignorados por git
├── eslint.config.js               # Configuración de ESLint
├── index.html                     # Archivo HTML principal
├── jsconfig.json                  # Configuración para el autocompletado de rutas
├── package.json                   # Dependencias y scripts del proyecto
├── package-lock.json              # Versiones exactas de las dependencias
├── README.md                      # 📄 Este archivo
├── vite.config.js                 # Configuración de Vite
└── vitest.config.js               # Configuración de Vitest (pruebas)
```

---

## 🛠️ **Stack Tecnológico**

### **Dependencias de Producción**

| Paquete          | Versión | Función Principal                                                                              |
| :--------------- | :-----: | :--------------------------------------------------------------------------------------------- |
| `vue`            | ^3.3.8  | Framework progresivo para construir la interfaz de usuario.                                    |
| `vue-router`     | ^4.2.5  | Enrutamiento oficial para Vue.js, permite la navegación entre vistas y la protección de rutas. |
| `pinia`          | ^2.1.7  | Store de estado intuitivo y type-safe, sucesor de Vuex.                                        |
| `firebase`       | ^10.7.0 | SDK de Firebase para utilizar servicios como Authentication y Firestore.                       |
| `bootstrap`      | ^5.3.2  | Framework CSS para crear interfaces responsivas y atractivas.                                  |
| `@popperjs/core` | ^2.11.8 | Necesario para los componentes interactivos de Bootstrap.                                      |
| `dompurify`      | ^3.0.6  | Biblioteca para sanitizar HTML y prevenir ataques XSS.                                         |

### **Dependencias de Desarrollo**

| Paquete              | Versión | Función Principal                                                  |
| :------------------- | :-----: | :----------------------------------------------------------------- |
| `@vitejs/plugin-vue` | ^4.5.0  | Plugin oficial para integrar Vue 3 con Vite.                       |
| `vite`               | ^5.0.0  | Herramienta de construcción y servidor de desarrollo ultrarrápida. |
| `eslint`             | ^9.39.2 | Herramienta para mantener la calidad y consistencia del código.    |

---

## ⚙️ **Configuración Inicial (Paso a Paso)**

Siga estos pasos para poner el proyecto en marcha en su máquina local.

### **Requisitos Previos**

- **Node.js** (versión 18 o superior)
- **npm** (generalmente incluido con Node.js)
- Una **cuenta gratuita en Google** para Firebase.

### **1. Clonar el Repositorio**

```bash
git clone https://github.com/nuevacumbre/simulador-bursatil.git
cd simulador-bursatil
```

### **2. Instalar Dependencias**

```bash
npm install
```

_Este comando instalará todas las dependencias listadas en `package.json`._

### **3. Configurar Firebase**

1.  Ve a la [Consola de Firebase](https://console.firebase.google.com/) e inicia sesión con tu cuenta de Google.
2.  Haz clic en **"Crear un proyecto"** (o "Agregar proyecto").
    - Asígnale un nombre, por ejemplo, `simulador-bursatil-clase`.
    - Puedes deshabilitar Google Analytics por ahora si lo deseas.
3.  Una vez creado el proyecto, haz clic en el icono de la web **`</>`** para registrar tu aplicación.
    - Ponle un nombre (ej. "simulador-web") y **no marques** la casilla de "Firebase Hosting" por ahora. Haz clic en "Registrar app".
4.  Firebase te mostrará un bloque de código con la configuración de tu proyecto (las claves `apiKey`, `authDomain`, etc.). **Guarda estos valores**.
5.  En el menú lateral izquierdo, ve a **"Authentication"** > **"Sign-in method"** (Método de acceso).
6.  Haz clic en **"Email/Password"** (Correo electrónico/contraseña), habilita el método y guárdalo.

### **4. Configurar Variables de Entorno**

Para proteger tus credenciales de Firebase, usaremos un archivo `.env`.

1.  En la raíz del proyecto, localiza el archivo `.env.example`.
2.  **Crea una copia** de este archivo y renómbralo como **`.env`**.
3.  Abre el archivo **`.env`** y pega los valores de configuración que obtuviste de Firebase en el paso anterior.

    ```env
    # .env
    VITE_FIREBASE_API_KEY=AIzaSy...tu_clave_real
    VITE_FIREBASE_AUTH_DOMAIN=tu-proyecto.firebaseapp.com
    VITE_FIREBASE_PROJECT_ID=tu-proyecto-id
    VITE_FIREBASE_STORAGE_BUCKET=tu-proyecto.appspot.com
    VITE_FIREBASE_MESSAGING_SENDER_ID=123456789
    VITE_FIREBASE_APP_ID=1:123456789:web:abcdef
    # VITE_FIREBASE_MEASUREMENT_ID=G-XXXXX (opcional)
    ```

### **5. Ejecutar la Aplicación**

```bash
npm run dev
```

¡Eso es todo! La aplicación estará disponible en `http://localhost:5173` (o un puerto similar indicado en la terminal).

---

## 🔐 **Seguridad: Variables de Entorno**

Proteger las credenciales es un pilar fundamental. Así es como lo gestionamos:

- **Archivo `.gitignore`:** El archivo `.gitignore` ya incluye `.env` para evitar que se suba accidentalmente al repositorio público.
- **Archivo `.env.example`:** Se proporciona un archivo de ejemplo (`.env.example`) para que otros desarrolladores sepan qué variables necesitan configurar, sin incluir los valores reales.
- **Uso en Código:** En `src/services/firebase.js`, las credenciales se leen desde las variables de entorno usando `import.meta.env`.

  ```javascript
  // src/services/firebase.js (fragmento)
  const firebaseConfig = {
    apiKey: import.meta.env.VITE_FIREBASE_API_KEY,
    authDomain: import.meta.env.VITE_FIREBASE_AUTH_DOMAIN,
    // ... resto de las variables
  }
  ```

---

## 🛡️ **Buenas Prácticas de Ciberseguridad**

Este proyecto no solo funciona, sino que lo hace de forma segura.

### **1. Sanitización de Inputs (XSS Prevention)**

Se utiliza **DOMPurify** para limpiar cualquier dato introducido por el usuario, eliminando código malicioso.

- **Helper `sanitize.js`:** Contiene funciones como `sanitizeInput()` que usan DOMPurify para limpiar strings.
- **Uso en Stores:** Antes de enviar un email a Firebase para autenticación, se sanitiza.

  ```javascript
  // Fragmento de src/stores/auth.js
  import { sanitizeInput } from '@/utils/sanitize'
  // ...
  const sanitizedEmail = sanitizeInput(email)
  ```

### **2. Protección de Rutas (Route Guards)**

Vue Router se encarga de que los usuarios no autenticados no puedan acceder al Dashboard.

- **Meta Campos:** Se definen `requiresAuth: true` y `requiresGuest: true` en las rutas.
- **Guardia Global:** Un `router.beforeEach` redirige a los usuarios basándose en su estado de autenticación.

  ```javascript
  // Fragmento de src/router/index.js
  router.beforeEach((to, from, next) => {
    const authStore = useAuthStore()
    if (to.meta.requiresAuth && !authStore.isAuthenticated) {
      next({ name: 'login' })
    } else {
      next()
    }
  })
  ```

### **3. Escapado Automático de Vue**

Vue, por defecto, escapa todo el contenido de las plantillas, lo que añade una capa extra de protección contra XSS.

### **4. Buenas Prácticas en Firebase**

- **Habilitar solo Email/Password:** Se utiliza el método de autenticación más básico y controlado.
- **No exponer credenciales:** Gracias a las variables de entorno, las claves de API de Firebase nunca se suben al repositorio.

---

## 📊 **Obtención de Datos Reales (Yahoo Finance)**

Para proporcionar datos de mercado auténticos, la aplicación se conecta a la API pública de Yahoo Finance.

### **El Servicio `stockApi.js`**

Este archivo centraliza toda la lógica de obtención de datos.

- **Lista de Símbolos:** Define un array con los tickers de las acciones a consultar (`AAPL`, `MSFT`, `GOOGL`, etc.).
- **Función `obtenerAccionesReales`:** Es una función asíncrona que itera sobre la lista de símbolos y realiza peticiones `fetch` a la API.
- **Proxy CORS:** Para evitar el error de CORS al hacer peticiones desde un navegador local, se utiliza un proxy público gratuito.

  ```javascript
  // Fragmento de src/services/stockApi.js
  const CORS_PROXY = 'https://api.allorigins.win/raw?url='
  const yahooUrl = `https://query1.finance.yahoo.com/v8/finance/chart/${symbol}`
  const proxyUrl = `${CORS_PROXY}${encodeURIComponent(yahooUrl)}`
  const response = await fetch(proxyUrl)
  ```

- **Datos de Respaldo:** Si la API falla o hay un error de red, la función devuelve datos de respaldo para que la interfaz de usuario no se rompa.

### **Estructura de Datos**

La API devuelve un objeto JSON complejo. El servicio extrae los datos relevantes:

```javascript
// Ejemplo de datos procesados para el Dashboard
{
  id: 'AAPL',
  nombre: 'Apple Inc.',
  simbolo: 'AAPL',
  precio: 175.50,
  variacion: 2.34,
  sector: 'Tecnología'
}
```

---

## 🚀 **Despliegue en Producción**

Una vez que el proyecto está listo, puedes desplegarlo fácilmente en plataformas como **Firebase Hosting** o **Vercel**.

### **Construir la Aplicación para Producción**

```bash
npm run build
```

Este comando genera una carpeta `dist/` con todos los archivos estáticos optimizados y listos para servir.

### **Desplegar en Firebase Hosting**

1.  Instala las herramientas de Firebase CLI si no las tienes: `npm install -g firebase-tools`
2.  Inicia sesión: `firebase login`
3.  Inicializa Firebase Hosting en tu proyecto: `firebase init hosting`
    - Selecciona tu proyecto de Firebase.
    - Especifica `dist` como directorio público.
    - Configúralo como una aplicación de una sola página (SPA) respondiendo "Sí".
4.  Despliega: `firebase deploy`

¡Tu aplicación estará en línea en una URL como `https://tu-proyecto.web.app`!

---

## 🛠️ **Configuración del Proyecto (Recordatorio para Desarrollo)**

### **Configuración del IDE Recomendada**

[VS Code](https://code.visualstudio.com/) + [Vue (Official)](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (y deshabilitar Vetur).

### **Navegador Recomendado**

- Navegadores basados en Chromium (Chrome, Edge, Brave, etc.):
  - [Vue.js devtools](https://chromewebstore.google.com/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
  - [Activar "Custom Object Formatter" en Chrome DevTools](http://bit.ly/object-formatters)
- Firefox:
  - [Vue.js devtools](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
  - [Activar "Custom Object Formatter" en Firefox DevTools](https://fxdx.dev/firefox-devtools-custom-object-formatters/)

### **Comandos Útiles**

| Comando             | Descripción                                                             |
| :------------------ | :---------------------------------------------------------------------- |
| `npm install`       | Instala todas las dependencias del proyecto.                            |
| `npm run dev`       | Inicia el servidor de desarrollo con recarga en caliente.               |
| `npm run build`     | Compila y minifica la aplicación para producción en la carpeta `dist/`. |
| `npm run test:unit` | Ejecuta las pruebas unitarias con Vitest.                               |
| `npm run lint`      | Ejecuta el linter para corregir problemas de estilo de código.          |

---
