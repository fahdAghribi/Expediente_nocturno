# Expediente Nocturno

Juego de detectives para móvil. Son las tres de la madrugada, la comisaría está vacía y en tu mesa solo hay una lámpara, un café frío y las pruebas de un crimen. Examinas los objetos, cruzas pistas en la libreta y, antes del amanecer, acusas a un culpable desde la máquina de escribir.

Tres casos:

1. **El anticuario de Via Laietana** · Barcelona, 1984
2. **El incendio de la calle Muntaner** · Barcelona, 1985
3. **La llamada del club de ajedrez** · Bilbao, 1986

Funciona sin conexión, en Android y en iPhone.

## Estructura

| Ruta | Qué es |
|---|---|
| `app/` | La app nativa (Capacitor 8). El juego está en `app/www/index.html`. Instrucciones de compilación y publicación en [`app/LEEME.md`](app/LEEME.md) |
| `app/www/models/` | Modelos 3D del despacho y de las pruebas (glTF, optimizados para móvil) |
| `app/tienda/` | Textos de las fichas de App Store y Google Play, iconos, capturas y política de privacidad |
| `expo-go/` | Envoltorio para probar el juego en el móvil con Expo Go. Es un submódulo: vive en su propio repositorio, [`expo-go`](https://github.com/fahdAghribi/expo-go) |
| `videos/expediente-nocturno-promo/` | Tráiler vertical (1080×1920) hecho con HyperFrames |
| `expediente-movil.html` | Versión antigua del juego en un solo archivo, sin modelos 3D |

## Probar el juego en el ordenador

El juego carga los modelos 3D y la música como archivos aparte, así que hay que servirlo por HTTP (abrir el HTML con doble clic no carga los modelos):

```sh
cd app/www
python3 -m http.server 8080
```

Y abre <http://localhost:8080>.

## Compilar las apps

```sh
cd app
npm install
npx cap sync          # copia www/ a los proyectos de Android e iPhone
npm run android:apk   # o android:aab para Google Play
npx cap open ios      # luego Archive en Xcode
```

Los detalles (Java, SDK de Android, firma, números de versión, publicación en las tiendas) están en [`app/LEEME.md`](app/LEEME.md).

**La clave de firma de Android no está en el repositorio** (`app/signing/` está en `.gitignore`). Sin ella no se pueden publicar actualizaciones en Google Play: guárdala aparte en un sitio seguro.

## Clonar con el submódulo

```sh
git clone --recurse-submodules https://github.com/fahdAghribi/Expediente_nocturno.git
```

Si ya lo has clonado sin él: `git submodule update --init`.

## Tecnología

- **three.js r128** para la escena 3D, con objetos hechos por código y modelos glTF cargados con `GLTFLoader`. Si un modelo no carga, el juego usa el objeto dibujado por código.
- **HTML y CSS** para la interfaz: fichas, libreta, informes.
- **Capacitor 8** para empaquetarlo como app de Android e iPhone.

## Créditos y licencias

- Three.js (MIT). Fuentes Anton, Courier Prime y Reenie Beanie (SIL Open Font License) y Special Elite (Apache 2.0).
- Modelos 3D de Sketchfab con licencia **Free Standard**: «Pedestal desk» de shuvalov.di, «Antique Desk Lamp - Game model» de LorenzoDrago y «Cyberpunk Room Flooring» de riach.
- Modelos 3D de Sketchfab con licencia **CC Attribution 4.0**, que obliga a citar al autor en algún sitio visible para los jugadores: «1930s style typewriter - w/o branding» de KWojcik, «Western Electric 500 Vintage Rotary Telephone» de vicky12218, «Coffee Mug (School Project)» de FrenchBaguette, «Old Wrist Watch DH» de twilightfox, «Glass Ashtray» de RED2000, «Key» de eucocker y «Knight Figurine 3D print model» de SakoSculpt.
- Música del tráiler y del juego: «Suspense» de Bardify.
