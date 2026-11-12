# Intercambio de regalos (familia)

Página de una sola hoja, sin cuentas, para que cada quien escriba su nombre y sus opciones de regalo
y vea a quién le toca regalarle y lo que quiere toda la familia. Presupuesto: $1,000 pesos por regalo.

- `index.html`: toda la página (HTML, CSS y JS). Se publica con GitHub Pages.
- Almacén: Firebase Realtime Database por su API REST, sin SDK. La constante `DB_URL` dentro de
  `index.html` apunta a la base. Cada celular guarda un id aleatorio en `localStorage` y escribe
  solo su propia llave en `/intercambio/listas/<id>`.
- Modo admin: abrir la página con `#admin` al final del enlace muestra un botón "Quitar" en cada tarjeta.

## Activar el almacén (una sola vez)

1. Entrar a https://console.firebase.google.com con tu cuenta de Google y crear un proyecto
   (por ejemplo `intercambio-familia`). Google Analytics se puede desactivar.
2. En el menú de la izquierda: Build → Realtime Database → Create database. Ubicación: United States.
   Modo: "Start in locked mode" (las reglas se cambian en el paso 3).
3. Pestaña Rules: pegar esto y publicar.

```json
{
  "rules": {
    "intercambio": { ".read": true, ".write": true },
    ".read": false,
    ".write": false
  }
}
```

4. En la pestaña Data aparece la URL de la base, con la forma
   `https://NOMBRE-default-rtdb.firebaseio.com`. Copiarla sin diagonal al final en `index.html`:
   `var DB_URL = 'https://NOMBRE-default-rtdb.firebaseio.com';`

## Publicar

Repositorio `aneyranazarrett/intercambio`, rama `main`, GitHub Pages desde la raíz.
Enlace: https://aneyranazarrett.github.io/intercambio/
