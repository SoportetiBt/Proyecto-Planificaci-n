# Guía paso a paso: subir a GitHub y desplegar en Vercel

Esta guía te lleva desde cero hasta tener el portal publicado en una URL pública (o privada para tu equipo), usando solo el **navegador web**. No necesitas instalar Git ni saber programar.

**Tiempo estimado:** 15–20 minutos.

---

## Parte 1 — Crear cuenta de GitHub (si aún no tienes)

1. Entra a https://github.com/signup
2. Regístrate con tu correo (puedes usar el corporativo `pablo.millon@bigticket.cl` o uno personal).
3. Verifica el correo desde tu bandeja de entrada.
4. Elige el plan **Free** (gratis y suficiente para este caso).

---

## Parte 2 — Crear el repositorio en GitHub

1. Entra a https://github.com/new
2. Completa el formulario:
   - **Repository name:** `portal-planificacion` (en minúsculas, sin espacios)
   - **Description:** `Portal de planificación operativa Canon y Rosen`
   - **Visibility:** elige **Private** si solo tu equipo debe verlo. Elige **Public** si te da igual que sea público (la URL de Vercel es la misma en ambos casos).
   - **NO marques** ninguna de las casillas "Add a README", "Add .gitignore", "Choose a license". Los crearemos arrastrando los archivos.
3. Haz click en **Create repository** (botón verde abajo).

Verás una pantalla que dice *"Quick setup — if you've done this kind of thing before"*. Esa es la página vacía del repo.

---

## Parte 3 — Subir los archivos arrastrándolos al navegador

1. En la página del repositorio recién creado, busca el enlace **uploading an existing file** dentro del bloque *"Quick setup"*. (Si no lo ves, haz click en el botón **Add file** → **Upload files**.)

2. Abre en otra ventana de tu computador la carpeta:

   `C:\Users\millo\OneDrive\Documentos\Claude\Projects\Planifiacion`

3. **Selecciona los 4 archivos** que están en esa carpeta (manteniendo Ctrl):
   - `index.html`
   - `vercel.json`
   - `.gitignore`
   - `README.md`
   - `GUIA_DEPLOY.md` (este mismo archivo, opcional)

4. **Arrástralos** sobre la zona punteada de la página de GitHub que dice *"Drag files here to add them to your repository"*.

5. Espera a que se carguen (verás una barra de progreso por cada archivo). `index.html` es el más pesado (~370 KB), tarda unos segundos.

6. Bajo la zona de carga verás el bloque **Commit changes**:
   - **Commit message:** escribe `Versión inicial del portal`
   - Deja seleccionada la opción **Commit directly to the `main` branch**.

7. Haz click en el botón verde **Commit changes**.

Listo: tu código ya está en GitHub. La página del repo ahora muestra tus archivos.

---

## Parte 4 — Crear cuenta en Vercel y conectar GitHub

1. Entra a https://vercel.com/signup
2. Haz click en **Continue with GitHub**.
3. Autoriza a Vercel para acceder a tu cuenta de GitHub (verás una pantalla de permisos en github.com → botón verde **Authorize Vercel**).
4. En la pantalla de bienvenida de Vercel, elige el plan **Hobby** (gratis). Te pedirá un nombre de equipo: pon algo como `pablo-millon` o `bigticket`.

---

## Parte 5 — Importar el repositorio en Vercel

1. Una vez dentro de Vercel, busca el botón **Add New...** → **Project** (arriba a la derecha). O entra directo a https://vercel.com/new
2. Verás una lista de tus repositorios de GitHub. Si **no aparece** `portal-planificacion`:
   - Haz click en **Adjust GitHub App Permissions** (link debajo de la lista).
   - En la página de GitHub que se abre, elige **Only select repositories** → marca `portal-planificacion` → **Save**.
   - Vuelve a Vercel y refresca.
3. Junto a `portal-planificacion` haz click en **Import**.
4. En la pantalla **Configure Project**:
   - **Project Name:** déjalo como `portal-planificacion` (o cambia si quieres).
   - **Framework Preset:** Vercel debe detectar **Other** automáticamente. Está bien.
   - **Root Directory:** déjalo en `.` (raíz).
   - **Build Command, Output Directory, Install Command:** déjalos **vacíos** (no son necesarios, es un sitio estático).
5. Haz click en **Deploy** (botón negro).

Vercel construye el sitio. En 30–60 segundos verás una animación de confeti y la URL pública del portal:

`https://portal-planificacion-xxxx.vercel.app`

Haz click en el preview o en **Visit** para abrir tu portal en producción.

---

## Parte 6 — Actualizar el portal en el futuro

Cada vez que quieras cambiar el portal (por ejemplo, regenerar `index.html` con datos nuevos):

**Opción rápida (web):**

1. Entra al repositorio en GitHub: `https://github.com/<tu-usuario>/portal-planificacion`
2. Haz click sobre `index.html` → botón con ícono de lápiz **Edit** (o el botón **...** → **Upload files** para reemplazarlo arrastrando).
3. Sube/edita el archivo → escribe un commit message tipo `Actualización 18.05.2026` → **Commit changes**.
4. Vercel detecta el cambio automáticamente y vuelve a publicar en menos de 1 minuto. No tienes que tocar nada en Vercel.

**Opción más cómoda** si vas a actualizar seguido: instala **GitHub Desktop** (https://desktop.github.com) que es un programa gráfico que sincroniza una carpeta local con GitHub sin escribir comandos.

---

## Parte 7 — Compartir con tu equipo

Una vez desplegado, comparte con tu equipo:

- **URL pública de Vercel:** la del paso 5 (`https://portal-planificacion-xxxx.vercel.app`).
- Si quieres una URL personalizada (`portal.bigticket.cl`):
  1. En Vercel → entra a tu proyecto → **Settings** → **Domains**.
  2. Click en **Add** → escribe `portal.bigticket.cl` (o el dominio que tengas).
  3. Vercel te dará un registro CNAME o A para configurar en el DNS de tu dominio. Tu equipo de TI lo agrega en el panel del dominio (GoDaddy, Cloudflare, etc.).
  4. En minutos, tu portal queda accesible en el dominio propio.

### Restringir acceso (opcional, plan pago)

Si quieres que **solo personas autorizadas** puedan entrar al portal, Vercel ofrece **Password Protection** o **Vercel Authentication** (plan Pro, USD 20/mes). Como el portal es solo visualización y los datos sensibles se cargan localmente en el navegador, normalmente no es necesario.

---

## Solución de problemas

**"El archivo `index.html` es demasiado grande para subir por la web."**
GitHub permite hasta 25 MB por archivo vía web (100 MB vía Git). `index.html` pesa ~370 KB, así que no debería haber problema.

**"Vercel dice 'No Output Directory named "public" found after the Build completed'."**
En **Configure Project** asegúrate que el **Output Directory** quedó **vacío** (no `public`). Si ya desplegaste con error, ve a **Settings → General → Build & Development Settings** del proyecto en Vercel y deja Output Directory en `(default)` o vacío. Después dispara un nuevo deploy desde **Deployments → ... → Redeploy**.

**"Mi repositorio no aparece en la lista de Vercel."**
Probablemente la app de Vercel no tiene permiso. En la pantalla de import → **Adjust GitHub App Permissions** → marca el repo → Save.

**"Hice cambios en GitHub pero Vercel no actualiza."**
Entra al proyecto en Vercel → pestaña **Deployments**. Debería aparecer un deploy nuevo automáticamente. Si no, haz click en **Redeploy** del último deploy exitoso.

---

## Resumen visual

```
[Tu carpeta local]
  C:\Users\millo\OneDrive\Documentos\Claude\Projects\Planifiacion
        │
        │  (1) arrastras archivos al navegador
        ▼
[GitHub]
  https://github.com/<tu-usuario>/portal-planificacion
        │
        │  (2) Vercel se conecta al repo
        ▼
[Vercel]
  https://portal-planificacion-xxxx.vercel.app
        │
        │  (3) tu equipo abre el link
        ▼
[Equipo]
  15-50 personas viendo el portal
```

Cualquier cambio futuro: lo subes a GitHub → Vercel republica solo.
