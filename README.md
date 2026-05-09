# CENS 451 · La Matanza — Sitio Web Institucional

Sitio web oficial del **Centro Educativo de Nivel Secundario N° 451** de La Matanza, Provincia de Buenos Aires.  
Incluye una app pública con asistente virtual y un panel administrativo para el equipo directivo, preceptores y docentes.

---

## Estructura del proyecto

```
/
├── index.html      → App pública (Valeria, sedes, analíticos, preinscripción)
├── admin.html      → Panel administrativo (directivo, preceptores, docentes)
└── README.md
```

---

## `index.html` — App pública

Página de acceso libre para aspirantes, alumnos/as y egresados/as.

### Funcionalidades

- **Asistente virtual Valeria** — responde consultas sobre inscripción, modalidad, materias y horarios. Adapta sus respuestas según el perfil del/la usuario/a (futuro/a alumno/a, egresado/a o docente).
- **Orientación por barrio** — al indicar dónde vivís, Valeria sugiere la sede más cercana con dirección real.
- **5 sedes operativas** — información de cada sede con su localidad asignada.
- **Búsqueda de analíticos** — por DNI y/o apellido.
- **Preinscripción en línea** — formulario integrado en la misma página.
- **Contacto** — teléfono `11 5312-6676` e Instagram `@cens.451` presentes en toda la interfaz.

---

## `admin.html` — Panel Administrativo

Acceso restringido para el equipo del CENS. Requiere usuario y contraseña.

### Roles y credenciales

| Rol | Usuario | Contraseña |
|---|---|---|
| Director/a | `admin` | `cens451` |
| Preceptor/a | `preceptor` | `prece451` |
| Docente | `docente` | `doc451` |

> ⚠️ **Importante:** cambiá las contraseñas antes de publicar en producción, o migrá la autenticación a Firebase Auth.

### Permisos por rol

| Módulo | Director/a | Preceptor/a | Docente |
|---|:---:|:---:|:---:|
| Información institucional | ✅ editar | — | — |
| Horarios | ✅ editar | — | — |
| Documentos / FAQ | ✅ | — | — |
| Links y recursos docentes | ✅ | — | ✅ ver |
| Analíticos (3 zonas de carga) | ✅ | ✅ | — |
| Preinscripciones | ✅ | ✅ ver | — |
| Export a Excel | ✅ | ✅ | — |

### Sincronización con app pública

Los cambios realizados desde el panel (horarios, información, FAQ) se reflejan automáticamente en lo que Valeria responde en `index.html`.

---

## Despliegue en Vercel

### 1. Crear el repositorio en GitHub

```bash
git init
git add index.html admin.html README.md
git commit -m "Initial commit — CENS 451 sitio web"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/cens451.git
git push -u origin main
```

### 2. Conectar con Vercel

1. Ir a [vercel.com](https://vercel.com) e iniciar sesión con GitHub.
2. Clic en **Add New → Project**.
3. Seleccionar el repositorio `cens451`.
4. Dejar la configuración por defecto (Vercel detecta automáticamente que es un sitio estático).
5. Clic en **Deploy**.

En menos de 2 minutos tenés dos URLs:

| Archivo | URL |
|---|---|
| App pública | `https://cens451.vercel.app/` |
| Panel admin | `https://cens451.vercel.app/admin.html` |

### Actualizaciones

Cualquier `git push` al branch `main` despliega automáticamente.

```bash
git add .
git commit -m "Descripción del cambio"
git push
```

---

## Tecnologías utilizadas

- HTML5 / CSS3 vanilla — sin frameworks, carga instantánea
- JavaScript ES6+ — lógica del asistente y panel
- [SheetJS (xlsx)](https://sheetjs.com/) — exportación de preinscripciones a Excel
- Google Fonts — DM Serif Display, DM Sans, Space Mono

---

## Contacto institucional

- 📞 `11 5312-6676`
- 📸 Instagram: [@cens.451](https://instagram.com/cens.451)
