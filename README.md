# Lytics - Landing Page

Landing page corporativa responsive para **Lytics**, una plataforma de desarrollo organizacional.

## Características

✅ **Diseño Responsive** - Se adapta perfectamente a dispositivos de cualquier tamaño
✅ **Framework Vue.js** - Componentes modernos y reutilizables
✅ **Sistema de Diseño Completo** - Variables CSS estandarizadas para colores, tipografía y espaciado
✅ **Tipografía Premium** - Fuente Inria Sans en múltiples variantes
✅ **Video integrado** - Demostración de la plataforma en loop
✅ **Paleta Blanco + Azul** - Diseño corporativo limpio y profesional

## Estructura del Proyecto

```
lytics landing/
├── src/
│   ├── assets/
│   │   ├── Logo LYTICS.png
│   │   ├── mixkit-corporate-and-business-buildings-in-the-city-4170-hd-ready.mp4
│   │   └── Inria_Sans/
│   ├── components/
│   │   ├── Header.vue
│   │   ├── Hero.vue
│   │   ├── Features.vue
│   │   ├── Video.vue
│   │   ├── CTA.vue
│   │   └── Footer.vue
│   ├── styles/
│   │   └── design-system.css
│   ├── App.vue
│   └── main.js
├── index.html
├── vite.config.js
└── package.json
```

## Secciones de la Landing Page

### 1. Header
- Logo de Lytics
- Navegación principal
- Botón CTA "Comenzar Ahora"
- Sticky en scroll

### 2. Hero
- Título principal impactante
- Subtítulo descriptivo
- Botones de acción
- Animación de elemento flotante

### 3. Features (Características)
- 6 características principales en grid responsive
- Iconos emoji
- Tarjetas con efecto hover
- Fondo gris claro

### 4. Video
- Sección con video corporativo
- Proporciones 16:9 (responsive)
- Loop automático sin sonido
- Overlay degradado suave

### 5. CTA (Call To Action)
- Fondo con degradado azul
- Mensajes motivadores
- Dos opciones de botón
- Nota de beneficios

### 6. Footer
- Información de empresa
- Links a producto
- Links legales
- Social media

## Sistema de Diseño

### Colores
- **Primario**: `#0066CC` (Azul corporativo)
- **Fondo**: `#FFFFFF` (Blanco)
- **Texto**: `#333333` (Gris oscuro)
- **Acentos**: Grises neutrales

### Tipografía
- **Familia**: Inria Sans (300, 400, 700)
- **H1**: 64px
- **H2**: 48px
- **Cuerpo**: 16px

### Espaciado (Escala 8px)
- `--spacing-xs`: 4px
- `--spacing-sm`: 8px
- `--spacing-md`: 16px
- `--spacing-lg`: 24px
- `--spacing-xl`: 32px
- `--spacing-2xl`: 48px
- `--spacing-3xl`: 64px

### Breakpoints Responsivos
- Mobile: < 640px
- Tablet: 768px
- Desktop: 1024px
- Large: 1280px

## Instalación y Uso

### 1. Instalar dependencias
```bash
npm install
```

### 2. Desarrollo local
```bash
npm run dev
```
Abre [http://localhost:3000](http://localhost:3000)

### 3. Build para producción
```bash
npm run build
```

### 4. Preview de producción
```bash
npm run preview
```

## Características Responsivas

- ✅ Header adaptable a mobile
- ✅ Grid de características fluido
- ✅ Video con proporciones correctas en todos los tamaños
- ✅ Botones full-width en mobile
- ✅ Tipografía escalable
- ✅ Navegación mobile-friendly

## Personalización

### Cambiar Colores
Edita `src/styles/design-system.css`:
```css
:root {
  --color-primary: #0066CC; /* Cambiar azul */
  --color-white: #FFFFFF;   /* Cambiar blanco */
}
```

### Cambiar Contenido
Edita los componentes en `src/components/`:
- Textos en las secciones
- URLs de links y botones
- Características principales

### Agregar Fuentes
La fuente Inria Sans está optimizada. Para otras fuentes, edita `design-system.css`.

## Performance

- ✅ Video optimizado (HD pero comprimido)
- ✅ CSS variables para reutilización
- ✅ Componentes Vue pequeños y rápidos
- ✅ Animations GPU-aceleradas
- ✅ Loading progresivo

## Compatibilidad

- Chrome/Edge: ✅ Completo
- Firefox: ✅ Completo
- Safari: ✅ Completo
- iOS Safari: ✅ Completo
- Android Chrome: ✅ Completo

## Licencia

Inria Sans - Open Font License (OFL)

---

**Hecho con ❤️ para Lytics**
