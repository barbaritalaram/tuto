# 🚀 TUTO - Plataforma de Aprendizaje con Quarto

Una plataforma web educativa moderna construida con **Quarto** que ofrece tutoriales interactivos en dos formatos: **Tuto Corto** (contenido conciso) y **Tuto Entero** (cursos completos).

## 📖 Descripción del Proyecto

TUTO es un sitio web de aprendizaje que permite a los usuarios acceder a contenido educativo organizado de manera intuitiva. La plataforma está diseñada para maximizar el tiempo de aprendizaje ofreciendo tanto tutoriales rápidos como cursos detallados.

### Características Principales

- 🎯 **Dos tipos de contenido**: Tutos cortos y Tutos enteros
- 🎨 **Diseño responsivo** con tema "sketchy" personalizado
- 📱 **Interfaz moderna** con navegación intuitiva
- 🔍 **Búsqueda integrada** en la barra de navegación
- 📊 **Soporte para visualizaciones** (Python, Plotly, etc.)
- 🌐 **Multiidioma** (configurado en español)
- 📝 **Blog integrado** para publicaciones adicionales

## 🏗️ Estructura del Proyecto

```
tutto/
├── _quarto.yml              # Configuración principal de Quarto
├── index.qmd                # Página de inicio
├── blog.qmd                 # Página principal del blog
├── tutos.qmd                # Lista de todos los tutoriales
├── about.qmd                # Página "Acerca de"
├── requirements.txt         # Dependencias de Python
├── custom-light.scss        # Estilos SCSS personalizados
├── styles.css              # Estilos CSS adicionales
├── images/                  # Recursos gráficos
│   ├── logo.png
│   ├── favicon.ico
│   ├── docker.png
│   ├── tuto_corto.png
│   └── tuto_entero.png
├── tuto_entero/            # Tutoriales completos
│   └── docker/             # Ejemplo: Tutorial de Docker
│       ├── index.qmd
│       ├── 01-virtualizacion.qmd
│       ├── 02-contenedores.qmd
│       └── ...
├── tuto_corto/             # Tutoriales concisos (vacío actualmente)
├── blog/                   # Entradas del blog (vacío actualmente)
├── docs/                   # Sitio web generado
└── _site/                  # Sitio de desarrollo
```

## 🚀 Instalación y Configuración

### Prerrequisitos

1. **Quarto CLI** - [Descargar e instalar](https://quarto.org/docs/get-started/)
2. **Python 3.7+** (para notebooks de Python)
3. **Git** para control de versiones

### Instalación

1. **Clonar el repositorio**:
```bash
git clone <url-del-repositorio>
cd tutto
```

2. **Crear y activar entorno virtual de Python**:
```bash
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate
```

3. **Instalar dependencias de Python**:
```bash
pip install -r requirements.txt
```

4. **Vista previa del sitio**:
```bash
quarto preview
```

5. **Generar el sitio**:
```bash
quarto render
```

## 📝 Cómo Agregar Contenido

### 1. Agregar un Nuevo Tuto Entero

1. **Crear directorio para el nuevo tutorial**:
```bash
mkdir tuto_entero/nombre-del-tutorial
```

2. **Crear archivo índice**:
```qmd
---
title: "Título del Tutorial"
subtitle: "Descripción breve"
author: "Tu Nombre"
date: "2025-01-20"
categories: ["Categoría", "Tuto Entero"]
lang: es
format: 
  html:
    page-navigation:
    prev: 
        href: index.qmd
        text: "Página Anterior"
    next: 
        href: 01-primera-leccion.qmd
        text: "Página Siguiente"
---

## Descripción del Curso
Tu descripción aquí...

<a href="01-primera-leccion.qmd" class="btn btn-primary">Siguiente</a>
```

3. **Crear lecciones numeradas**:
   - `01-introduccion.qmd`
   - `02-conceptos-basicos.qmd`
   - `03-ejemplos-practicos.qmd`
   - etc.

4. **Actualizar la navegación en `_quarto.yml`**:
```yaml
navbar:
  right:
    - text: "Tuto Entero"
      menu:
        - text: "Docker"
          file: tuto_entero/docker/index.qmd
        - text: "Tu Nuevo Tutorial"
          file: tuto_entero/nombre-del-tutorial/index.qmd
```

### 2. Agregar un Tuto Corto

1. **Crear archivo en el directorio `tuto_corto/`**:
```qmd
---
title: "Título del Tuto Corto"
author: "Tu Nombre"
date: "2025-01-20"
categories: ["Tuto Corto"]
lang: es
---

# Tu contenido conciso aquí

Contenido directo al grano...
```

2. **Actualizar la navegación** si es necesario.

### 3. Agregar Entrada de Blog

1. **Crear archivo en el directorio `blog/`**:
```qmd
---
title: "Título del Post"
author: "Tu Nombre"
date: "2025-01-20"
categories: ["Blog", "Categoría"]
lang: es
---

Tu contenido del blog...
```

### 4. Agregar Imágenes y Recursos

1. **Subir imágenes al directorio `images/`**
2. **Referenciar en archivos `.qmd`**:
```markdown
![Descripción](./images/tu-imagen.png)
```

## 🎨 Personalización del Diseño

### Colores y Estilos

- **Archivo principal**: `custom-light.scss`
- **Estilos adicionales**: `styles.css`
- **Tema base**: "sketchy" (se puede cambiar en `_quarto.yml`)

### Modificar Colores de la Navbar

Edita las variables en `custom-light.scss`:
```scss
$color-navbar-bg: #ffffff;       // Fondo de la navbar
$color-navbar-fg: #18181b;       // Color del texto
$color-navbar-hover: #4f46e5;    // Color al hacer hover
```

### Personalizar Hero Banner

Modifica los estilos en `styles.css`:
```css
.hero-banner {
  background: linear-gradient(135deg, #tu-color 0%, #otro-color 100%);
}
```

## 📋 Configuración Avanzada

### Archivo `_quarto.yml`

El archivo de configuración principal controla:

- **Información del sitio** (título, idioma, favicon)
- **Estructura de navegación**
- **Tema y estilos**
- **Formato de salida**
- **Herramientas de código**

### Opciones Importantes

```yaml
format:
  html:
    theme: sketchy              # Tema visual
    fontsize: 1.2em            # Tamaño de fuente
    linestretch: 1.7           # Espaciado de líneas
    code-fold: true            # Código plegable
    code-summary: "Mostrar código"  # Texto del botón
```

## 🚀 Despliegue

### GitHub Pages

1. **Configurar en `_quarto.yml`**:
```yaml
project:
  output-dir: docs
```

2. **Generar el sitio**:
```bash
quarto render
```

3. **Configurar GitHub Pages** para usar la carpeta `/docs`

### Otros Servicios

- **Netlify**: Conectar directamente con el repositorio
- **Vercel**: Similar a Netlify
- **GitHub Actions**: Para automatizar el despliegue

## 📚 Recursos y Referencias

- [Documentación oficial de Quarto](https://quarto.org/)
- [Guía de sitios web con Quarto](https://quarto.org/docs/websites/)
- [Temas de Bootstrap para Quarto](https://quarto.org/docs/output-formats/html-themes.html)
- [Sintaxis de Markdown en Quarto](https://quarto.org/docs/authoring/markdown-basics.html)

## 🤝 Contribuir

1. **Fork el repositorio**
2. **Crear una rama para tu característica**: `git checkout -b nueva-caracteristica`
3. **Agregar tu contenido** siguiendo la estructura establecida
4. **Commit tus cambios**: `git commit -m 'Agregar nueva característica'`
5. **Push a la rama**: `git push origin nueva-caracteristica`
6. **Crear un Pull Request**

## 📄 Licencia

Este proyecto está bajo la licencia especificada por Barbarita Lara.

## 👤 Créditos

- **Creado por**: Barbarita Lara
- **GitHub**: [@barbaritalaram](https://github.com/barbaritalaram)
- **Instagram**: [@barbaritalaram](https://www.instagram.com/barbaritalaram/)
- **Web**: [barbaritalara.com](https://barbaritalara.com/)

---

