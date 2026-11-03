# Mi Bodeguita con Firebase

## Publicar
Sube esta carpeta a Netlify (app.netlify.com/drop). Necesita HTTPS; no abras index.html con doble clic.

## Conectar
1. Firebase Console > Configuración del proyecto > Tus apps > app web: copia `apiKey` y `appId`.
2. En la app: Ajustes > Sincronizar con Firebase. Pega ambos, escribe tu correo y contraseña de Firebase Authentication y toca Conectar.
3. La sesión queda guardada: la próxima vez conecta sola.

## Reglas de la base de datos (obligatorio)
Firebase Console > Realtime Database > Reglas. Pega esto y toca Publicar:

```json
{
  "rules": {
    "businesses": {
      "$uid": {
        ".read": "auth != null && auth.uid === $uid",
        ".write": "auth != null && auth.uid === $uid"
      }
    }
  }
}
```

## Limitaciones
- Se sincroniza una copia completa de los datos por cuenta. No vendas desde varios dispositivos sin internet a la vez: puede haber sobrescritura.
- Descarga respaldos JSON con regularidad.
- No calcula impuestos ni emite facturas fiscales.
