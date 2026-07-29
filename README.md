# plannet-web

Páginas estáticas de Plannet: información legal y ayuda. Se sirven con
**GitHub Pages** y se abren desde la app dentro de un WebView.

## Páginas

| Fichero | Contenido | Obligatoria |
|---|---|---|
| `privacyPolicy.html` | Política de privacidad **+ términos de uso** (un solo documento) | Sí (Google Play y App Store) |
| `childSafetyPolicy.html` | Política de seguridad infantil / normas CSAE | Sí (Google Play, apps sociales) |
| `delete-account.html` | Eliminación de cuenta (formulario) | Sí (Google Play y App Store) |
| `frequentQuestions.html` | Preguntas frecuentes | No |
| `index.html` | Portada con enlaces | No |
| `styles.css` | Estilos comunes | — |

## Idiomas

Cada página contiene sus traducciones en un objeto JS (`es`, `en`, `de`, `zh`)
y renderiza según el parámetro `?lang=xx`. Si no se indica o no está soportado,
usa español. La app añade el idioma del dispositivo automáticamente.

Ejemplo: `privacyPolicy.html?lang=en`

## Publicar en GitHub Pages

1. En el repositorio: **Settings → Pages**.
2. **Source**: `Deploy from a branch`.
3. **Branch**: `main` y carpeta `/ (root)`. Guardar.

Las páginas quedan en:

```
https://jona234.github.io/plannet-web/privacyPolicy.html
https://jona234.github.io/plannet-web/childSafetyPolicy.html
https://jona234.github.io/plannet-web/frequentQuestions.html
https://jona234.github.io/plannet-web/delete-account.html
```

Esas URLs son las que consume la app en `lib/core/constants.dart`.

## Eliminación de cuenta

`delete-account.html` pide email/nick y contraseña, hace login contra la API
para obtener el token y llama a `DELETE /api/users/me`. El backend borra el
usuario y todos sus datos asociados (eventos, asistencias, amistades,
conversaciones, comentarios y notificaciones).

⚠️ **La constante `API` al principio del fichero apunta a una URL de Railway
que todavía no existe.** Hay que actualizarla con la URL pública real de la API
cuando se despliegue, o el formulario no funcionará.

Los usuarios registrados con Google o Apple no tienen contraseña; para ellos la
página indica que soliciten el borrado por correo.
