# 🥏 RED · Desde La Línea

**La red social de los clubes de disco volador en Latinoamérica.**

> 🔗 Demo en vivo: **[desdelalinea.github.io/APP4DV](https://desdelalinea.github.io/APP4DV/)**

Comunidad de disco volador · LATAM — una app web (PWA) para que los clubes de Ultimate, Freestyle y Disc Golf de la región se organicen, se conecten entre sí y hagan crecer el deporte, todo desde el navegador y sin depender de WhatsApp disperso ni Excel.

---

## ¿Qué resuelve?

Los clubes de disco volador en LATAM crecen a punta de voluntad y grupos de WhatsApp. RED le da a cada club una casa digital propia — y los conecta a todos entre sí a través de una red regional — para:

- Publicar y encontrar oportunidades (becas, cupos, patrocinios, equipo, vacantes, intercambios) dentro de su club **o** en toda la Red LATAM.
- Administrar miembros, roles y reglas internas sin depender de un grupo de chat.
- Asignar rutinas de entrenamiento y verificar el cumplimiento con evidencia real.
- Organizar eventos y torneos con confirmación de asistencia.
- Construir un perfil deportivo persistente, recuperable incluso si cambias de celular.

---

## Funcionalidades

### 📋 Directorio
Feed de oportunidades filtrable por categoría y fecha, con alcance **Mi club** o **Red LATAM**. Cada publicación indica autor, club, vigencia y contacto directo; los posts se pueden compartir y destacar.

### 🏟️ Mi club
Perfil del club con logo, disciplinas, reglas internas editables, código de invitación regenerable, listado de miembros con su rol, envío de anuncios masivos por WhatsApp y gestión de eventos/torneos con asistencia.

### 💪 Rutinas
Admins y capitanes publican rutinas de entrenamiento con fecha límite; cada jugador sube evidencia (foto o video) y el club la aprueba o rechaza, con reintento si fue rechazada.

### 👤 Perfil
Datos personales, club, disciplina, rol y alcance dentro de la red. Incluye aseguramiento de cuenta: se puede vincular la identidad anónima del dispositivo a un correo y contraseña para recuperar el acceso desde otro celular.

### 🔐 Roles y alcance
- **Admin** — control total del club: código de invitación, roles, reglas, eventos.
- **Capitán** — modera publicaciones, crea rutinas y eventos, habilita alcance de red a otros miembros.
- **Miembro** — participa y publica según el alcance que le fue asignado (club o Red LATAM).

---

## Stack técnico

- **Frontend:** HTML/CSS/JS vanilla en un solo archivo, sin build ni frameworks — pensado para deploy directo en GitHub Pages.
- **Backend:** 100% Firebase — sin servidor propio.
  - **Firestore** como base de datos.
  - **Authentication** anónima por dispositivo, con vinculación opcional a correo/contraseña para recuperación de cuenta.
  - **Storage** para logos de club y evidencias de rutinas.
- **Tipografías:** Anton (títulos), Inter (texto), JetBrains Mono (datos y elementos técnicos).
- **PWA-ready:** metaetiquetas de instalación en iOS/Android.

---

## Modelo de datos (Firestore)

| Colección | Contenido |
|---|---|
| `red_dll_clubes` | Perfil público de cada club |
| `red_dll_codigos` | Código de invitación por club (solo lo lee el admin) |
| `red_dll_miembros` | Membresía: rol y alcance de cada persona en cada club |
| `red_dll_oportunidades` | Publicaciones del directorio |
| `red_dll_rutinas` | Rutinas de entrenamiento asignadas por el club |
| `red_dll_entregas` | Evidencia de cumplimiento de rutinas |
| `red_dll_eventos` | Eventos y torneos del club, con asistencia |
| `red_dll_perfiles` | Respaldo del perfil por usuario, para recuperación de cuenta |
| `red_dll_superadmins` | Super-administradores de toda la red (se otorga manualmente desde consola) |

Todos los permisos —quién puede leer, publicar, moderar o borrar— quedan definidos en [`firestore.rules`](./firestore.rules).

---

## Puesta en marcha

1. Clona este repositorio.
2. Crea un proyecto en [Firebase Console](https://console.firebase.google.com).
3. Activa **Firestore Database**.
4. Ve a **Authentication → Sign-in method** y activa el proveedor **Anónimo**.
5. En **Configuración del proyecto → General → Tus apps**, crea una app web y copia el objeto `firebaseConfig`.
6. Pega ese objeto en `index.html`, reemplazando los campos `PEGA_AQUI_TU_...`.
7. Copia el contenido de `firestore.rules` en **Firestore Database → Reglas** en la consola de Firebase.
8. (Opcional) Activa **Storage** si quieres soportar logos de club y evidencias en foto/video.
9. Sirve `index.html` como sitio estático — por ejemplo con GitHub Pages, tal como está desplegado actualmente.

Si falta algún campo de configuración, la propia app lo detecta y muestra una pantalla de ayuda con los pasos pendientes.

---

## Sobre Desde La Línea

RED es un proyecto de **Desde La Línea**, plataforma de organización de eventos, transmisión (UltiStats) y herramientas digitales para la comunidad de disco volador en Latinoamérica — con base en Medellín, Colombia.

---

## Contacto

¿Preguntas, ideas o quieres sumar a tu club a la red? Escríbenos a **desdelalinea@gmail.com**.
