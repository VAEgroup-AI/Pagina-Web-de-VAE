# Plan de Mejoras - Web Versión Productiva

Este plan detalla los cambios propuestos para corregir los problemas visuales y de contenido en el sitio web de **VAE AI Consulting**.

---

## 1. Ajustes según "Brochure Vae - Sesión Andreas"

### A. Frase en el Navbar de la sección PyMEs
* **Problema**: La frase *"...nos apasiona ayudarte a hacer crecer tu negocio..."* se ve muy grande (`text-base`) y se divide/corta en dos líneas ("cajas cortadas") en ciertas resoluciones de pantalla debido a la falta de espacio.
* **Solución**:
  * Reducir el tamaño de la fuente a `text-xs md:text-sm` para darle un toque más delicado y profesional.
  * Agregar la clase `whitespace-nowrap` para evitar que el texto se divida en múltiples renglones.
  * Cambiar el breakpoint de visualización a `xl:flex` (o ajustar márgenes) para evitar solapamientos con los enlaces del menú en pantallas medianas.
* **Archivo a modificar**: [pymes/index.html](file:///C:/Users/Alfredo/Desktop/Alfredo/Trabajo/Grupo%20Proyecto%20AI/Web%20Version%20Productiva/pymes/index.html) (Línea 48-50)

### B. Sección "Sobre Nosotros" en PyMEs (Alineación con versión Corporativa)
* **Problema**: El texto y el enfoque de la sección de PyMEs difiere del corporativo y se requiere unificar el mensaje.
* **Solución**:
  * Modificar el título secundario a: `Ingeniería, Estrategia y Humanidad`.
  * Reemplazar los dos párrafos de descripción por el texto oficial de la versión corporativa (Corpo):
    1. *"Somos un equipo multidisciplinario con más de 20 años de trayectoria en ingeniería, tecnología y desarrollo humano. No solo aplicamos tecnología: la conectamos con las personas y los objetivos de negocio."*
    2. *"Diseñamos soluciones inteligentes con una mirada práctica, acompañando a cada cliente en la selección y sostenimiento de herramientas que fortalecen su operación real."*
* **Archivo a modificar**: [pymes/index.html](file:///C:/Users/Alfredo/Desktop/Alfredo/Trabajo/Grupo%20Proyecto%20AI/Web%20Version%20Productiva/pymes/index.html) (Líneas 101-105)

---

## 2. Corrección de la "I" recortada en "Bienvenidos a VAE AI Consulting"

* **Problema**: Al renderizar el título principal en cursiva (`italic`) con un fondo con clip de gradiente (`text-transparent bg-clip-text`), la última letra del renglón superior (la **I** de **AI**) queda recortada por el borde del contenedor.
* **Solución**:
  * Ampliar el contenedor del título aumentando su ancho máximo de `max-w-2xl` a `max-w-3xl` o `max-w-4xl`. Esto le da más espacio para que quepa todo en una sola línea en pantallas grandes.
  * Convertir el elemento `span` que contiene el gradiente en `inline-block` y añadir un padding derecho (`pr-4`). Esto evita que el texto se rompa a mitad de la frase de forma extraña y añade un margen de seguridad a la derecha para que el slant (inclinación) del texto itálico no sea recortado por el clip de fondo.
* **Archivo a modificar**: [index.html](file:///C:/Users/Alfredo/Desktop/Alfredo/Trabajo/Grupo%20Proyecto%20AI/Web%20Version%20Productiva/index.html) (Líneas 84-87)

---

## Detalle de Cambios en Código (Propuesta de Modificación)

### En [index.html](file:///C:/Users/Alfredo/Desktop/Alfredo/Trabajo/Grupo%20Proyecto%20AI/Web%20Version%20Productiva/index.html):
```diff
-        <div class="text-center max-w-2xl mb-12">
+        <div class="text-center max-w-3xl mb-12">
             <h1 class="text-3xl md:text-5xl font-extrabold tracking-tight mb-4 italic text-white uppercase">
-                Bienvenidos a <span class="text-transparent bg-clip-text bg-gradient-to-r from-[var(--verde-lima)] to-[var(--azul-electrico)] pr-2">VAE AI Consulting</span>
+                Bienvenidos a <span class="inline-block text-transparent bg-clip-text bg-gradient-to-r from-[var(--verde-lima)] to-[var(--azul-electrico)] pr-4">VAE AI Consulting</span>
             </h1>
```

### En [pymes/index.html](file:///C:/Users/Alfredo/Desktop/Alfredo/Trabajo/Grupo%20Proyecto%20AI/Web%20Version%20Productiva/pymes/index.html):
```diff
-            <div class="hidden lg:flex flex-1 justify-start pl-12 text-base tracking-wide text-white/60 font-medium italic">
-                ...nos apasiona ayudarte a <span class="text-[var(--verde-lima)] font-semibold not-italic px-1.5">hacer crecer tu negocio</span>...
-            </div>
+            <div class="hidden xl:flex flex-1 justify-start pl-12 text-xs md:text-sm tracking-wide text-white/50 font-normal italic whitespace-nowrap">
+                ...nos apasiona ayudarte a <span class="text-[var(--verde-lima)] font-medium not-italic px-1">hacer crecer tu negocio</span>...
+            </div>
```
```diff
-                <h3 class="text-4xl font-bold mb-8 italic text-white">Trabajo en Equipo, Planificación y Acompañamiento Humano</h3>
-                <div class="space-y-6 text-gray-400 text-lg leading-relaxed">
-                    <p>Somos un equipo con más de 20 años de experiencia ayudando a empresas a crecer mediante tecnología práctica y el desarrollo de los equipos de trabajo. Desde VAE, venimos a hacer que la tecnología trabaje para las personas y para las metas de tu negocio.</p>
-                    <p>Diseñamos soluciones sencillas y lógicas con una mirada práctica, acompañándote a elegir y mantener las herramientas que realmente sirven para el día a día de tu negocio.</p>
-                </div>
+                <h3 class="text-4xl font-bold mb-8 italic text-white">Ingeniería, Estrategia y Humanidad</h3>
+                <div class="space-y-6 text-gray-400 text-lg leading-relaxed">
+                    <p>Somos un equipo multidisciplinario con más de 20 años de trayectoria en ingeniería, tecnología y desarrollo humano. No solo aplicamos tecnología: la conectamos con las personas y los objetivos de negocio.</p>
+                    <p>Diseñamos soluciones inteligentes con una mirada práctica, acompañando a cada cliente en la selección y sostenimiento de herramientas que fortalecen su operación real.</p>
+                </div>
```
