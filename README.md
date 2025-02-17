# Guía de Preparación del Entorno de Desarrollo Full-Stack

## Índice
- [Introducción](#introducción)
- [Requisitos Previos](#requisitos-previos)
- [Herramientas de Desarrollo](#herramientas-de-desarrollo)
- [Visual Studio Code en Detalle](#visual-studio-code-en-detalle)
- [Configuración del Entorno](#configuración-del-entorno)
- [Verificación de la Instalación](#verificación-de-la-instalación)
- [Solución de Problemas Comunes](#solución-de-problemas-comunes)

## Introducción

Esta guía te ayudará a preparar tu entorno de desarrollo para el curso de Full-Stack Development. Seguiremos un proceso paso a paso para instalar y configurar todas las herramientas necesarias.

## Requisitos Previos

Antes de comenzar, asegúrate de tener:

- Un ordenador con Windows 10/11, macOS (10.15 o superior) o Linux
- Mínimo 8GB de RAM (recomendado 16GB)
- Al menos 20GB de espacio libre en disco
- Conexión a Internet estable

## Herramientas de Desarrollo

### 1. Editor de Código
Instalaremos Visual Studio Code:
1. Descarga VS Code desde [https://code.visualstudio.com/](https://code.visualstudio.com/)
2. Ejecuta el instalador y sigue las instrucciones

#### Visual Studio Code en Detalle

##### Elementos Principales de la Interfaz

1. **Barra de Actividad (izquierda)**
   - Explorador de archivos (primer icono)
   - Búsqueda (lupa)
   - Control de versiones (branch)
   - Extensiones (cuatro cuadrados)
   - Run and Debug (play con bug)

2. **Barra Lateral**
   - Se expande al seleccionar un icono de la barra de actividad
   - Muestra el contenido específico de cada sección

3. **Editor**
   - Área principal donde se edita el código
   - Soporta múltiples pestañas y división de pantalla
   - Sistema de pestañas para navegar entre archivos

4. **Barra de Estado (inferior)**
   - Información del archivo actual
   - Codificación
   - Tipo de archivo
   - Posición del cursor

##### Indicadores de Estado de Archivos

- **Punto blanco en la pestaña**: Indica que el archivo tiene cambios sin guardar
- **Cruz (x)**: Cierra la pestaña
- **Letra M**: Indica que el archivo está modificado (en Git)
- **Letra U**: Indica que el archivo es nuevo y no está trackeado (en Git)

##### Búsqueda en Ficheros

1. **Búsqueda rápida en archivo actual**
   - `Ctrl + F` (Windows/Linux) o `Cmd + F` (macOS)
   - Búsqueda instantánea con resaltado
   - Opciones de coincidencia exacta y expresiones regulares

2. **Búsqueda en todos los archivos**
   - `Ctrl + Shift + F` (Windows/Linux) o `Cmd + Shift + F` (macOS)
   - Permite buscar en todo el proyecto
   - Filtros por tipo de archivo o carpeta
   - Soporte para expresiones regulares

3. **Búsqueda de archivos**
   - `Ctrl + P` (Windows/Linux) o `Cmd + P` (macOS)
   - Navegación rápida entre archivos
   - Búsqueda difusa (fuzzy search)

##### Extensiones Recomendadas

1. **Desarrollo Web**
   - Live Server: Servidor de desarrollo local con recarga automática
   - Prettier: Formateador de código
   - Console Ninja: Mejora la experiencia de debugging con console.log

2. **Control de Versiones**
   - Git Graph: Visualización gráfica del historial de Git
   - GitLens: Información detallada sobre el historial de código
   - Git Blame: Muestra quién modificó cada línea de código

3. **Productividad**
   - Codeium: Autocompletado de código con IA
   - Auto Rename Tag: Renombra automáticamente etiquetas HTML/XML

##### Configuración de Extensiones

###### Prettier
```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "prettier.singleQuote": true,
  "prettier.semi": true
}
```

###### Live Server
1. Click derecho en archivo HTML
2. Seleccionar "Open with Live Server"
3. El navegador se abrirá automáticamente

###### GitLens
- Habilitar la visualización de blame en el editor
- Configurar la información mostrada en los tooltips

### 2. Control de Versiones
Instala Git:
1. Windows: Descarga desde [https://git-scm.com/](https://git-scm.com/)
2. macOS: Instala mediante Homebrew: `brew install git`
3. Linux: `sudo apt install git` (Ubuntu/Debian) o `sudo dnf install git` (Fedora)

Configura Git:
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

### 3. Node.js y npm
1. Descarga Node.js LTS desde [https://nodejs.org/](https://nodejs.org/)
2. Instala siguiendo las instrucciones del asistente
3. Verifica la instalación:
```bash
node --version
npm --version
```

### 4. PNPM (Alternativa a npm)
Instala PNPM globalmente:
```bash
npm install -g pnpm
```

### 5. MongoDB
Para la base de datos utilziaremos el servicio en la nube Atlas de MongoDB

## Configuración del Entorno

### Configuración de VS Code

1. Abre VS Code
2. Configura el formateo automático:
   - Presiona `Ctrl+,` (Windows/Linux) o `Cmd+,` (macOS)
   - Busca "format on save"
   - Activa la opción

### Configuración de un Proyecto Base

1. Crea un nuevo directorio para tu proyecto:
```bash
mkdir mi-proyecto-fullstack
cd mi-proyecto-fullstack
```

2. Inicializa un proyecto con npm:
```bash
npm init -y
```

3. Instala las dependencias básicas:
```bash
npm install express mongoose
npm install -D nodemon
```

4. Configura los scripts en package.json:
```json
{
  "scripts": {
    "start": "node index.js",
    "dev": "nodemon index.js"
  }
}
```

## Verificación de la Instalación

Ejecuta estos comandos para verificar que todo está correctamente instalado:

```bash
node --version
npm --version
pnpm --version
git --version
```

## Solución de Problemas Comunes

### Error: EACCES al instalar paquetes globales con npm
Solución:
```bash
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.profile
source ~/.profile
```

### Error: La ejecución de scripts está deshabilitada en este sistema

Presiona Win + S, escribe PowerShell, haz clic derecho y selecciona "Ejecutar como administrador".

Ejecutar:
```bash
Set-ExecutionPolicy Unrestricted -Scope CurrentUser
```

### Error: Puerto 3000 en uso
Cuando un puerto se encuentra en uso, nos está indicando que otra aplicación ya está usando este puerto. Comprobad que no tengamos ninguna aplicación corriendo en este puerto, o intentad hacer un cambio del puerto de la aplicación.

## Recursos Adicionales

- [Documentación oficial de Node.js](https://nodejs.org/docs)
- [Documentación de React](https://react.dev)
- [Documentación de Express](https://expressjs.com)
- [Documentación de MongoDB](https://docs.mongodb.com)
- [Guía de Git](https://git-scm.com/doc)

## Soporte

Si encuentras algún problema durante la instalación:
1. Revisa la sección de solución de problemas
2. Consulta los recursos adicionales
3. Pregunta en el foro del curso
4. Contacta con el equipo docente

---
¡Buena suerte con el curso!
