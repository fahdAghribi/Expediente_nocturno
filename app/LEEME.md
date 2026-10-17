# Expediente Nocturno · app para Android e iPhone

El juego va empaquetado dentro de una app nativa con [Capacitor](https://capacitorjs.com) 8. Todo funciona sin conexión: Three.js r128 y las cuatro fuentes (Anton, Courier Prime, Reenie Beanie y Special Elite) van incluidos en la app.

## Qué hay en cada carpeta

| Ruta | Contenido |
|---|---|
| `www/index.html` | El juego. **Es el archivo que se edita.** |
| `www/vendor/three.min.js`, `www/fonts/`, `www/fonts.css` | Three.js y fuentes en local |
| `www/vendor/GLTFLoader.js`, `www/models/` | Cargador de modelos 3D y los modelos del despacho (escritorio, lámpara, suelo, máquina de escribir, teléfono, taza, reloj, cenicero, llave y figura), ya optimizados para móvil |
| `www/audio/suspense.m4a` | Música de suspense: un ciclo de 97,4 s recortado de la pista de 1 hora, que suena en bucle sin cortes |
| `www/fotos/` | Fotos de los sospechosos de los tres casos (`<id>.webp`, recortadas con fondo transparente; `<id>` es el del sospechoso en el código) y de cada víctima (`victima-c1.jpg`, `victima-c2.jpg`, `victima-c3.jpg`). El juego les pone la pared, la regla de estatura, el cartel y el filtro de época. Si falta alguna, usa la cara dibujada. `FOTOS=false` en `www/index.html` vuelve a las caras dibujadas |
| `backups/` | Copias de `www/index.html` antes de cambios grandes |
| `capacitor.config.json` | Nombre, identificador, colores, pantalla de carga |
| `android/` | Proyecto nativo de Android (Gradle) |
| `ios/` | Proyecto nativo de iPhone (Xcode, Swift Package Manager) |
| `assets/` | Originales del icono y la pantalla de carga (generados desde `design/art.html`) |
| `signing/` | **Clave de firma de Android y sus contraseñas. No la pierdas ni la compartas.** |
| `tienda/` | Textos para las tiendas, política de privacidad, iconos, gráfico y capturas |
| `../entregables/` | `.aab` para Google Play y `.apk` para instalar directamente |

## La clave de firma (importante)

`signing/expediente-nocturno-release.jks` firma todas las versiones de Android, y su contraseña está en `signing/keystore.properties`.

- Haz **ya** una copia de la carpeta `signing/` en un sitio seguro fuera de este Mac (un gestor de contraseñas o un disco cifrado).
- Google Play solo acepta actualizaciones firmadas con la misma clave. Si activas *Firma de apps de Play* (viene activada por defecto), esta clave pasa a ser tu «clave de subida», y si la pierdes Google puede cambiarla tras una solicitud. Aun así, guárdala.

## Probar en un Android

Pasa `entregables/ExpedienteNocturno-1.2.apk` al teléfono y ábrelo. Android te pedirá permitir la instalación desde esa fuente.

## Publicar en Google Play

1. Crea una cuenta en [Play Console](https://play.google.com/console) (pago único de 25 $). Las cuentas personales nuevas deben pasar una prueba cerrada con al menos 12 testers durante 14 días antes de poder publicar en producción.
2. **Crear app** → nombre «Expediente Nocturno», idioma Español (España), Juego, Gratis.
3. **Ficha de Play Store:** copia los textos de `tienda/ficha-tienda.md` y sube el icono de 512, el gráfico destacado y las capturas de `tienda/capturas-google-play/`.
4. **Contenido de la app:** política de privacidad (ver más abajo), clasificación de contenido (respuestas orientativas en la ficha), seguridad de los datos (no se recoge ningún dato), público objetivo (13 años o más) y anuncios (no).
5. **Pruebas → Prueba cerrada** (o *Producción* si tu cuenta ya puede): crea una versión y sube `entregables/ExpedienteNocturno-1.2-google-play.aab`.

## Publicar en la App Store (iPhone)

Necesitas un Mac con **Xcode** (gratis en la Mac App Store, unos 15 GB; ahora mismo no está instalado) y una cuenta del [Apple Developer Program](https://developer.apple.com/programs/) (99 $ al año).

1. Instala Xcode, ábrelo una vez para que termine de configurarse y ejecuta:
   ```sh
   sudo xcode-select -s /Applications/Xcode.app
   cd "Expediente nocturno/app"
   npx cap sync ios
   npx cap open ios
   ```
2. En Xcode: selecciona el proyecto **App** → pestaña *Signing & Capabilities* → elige tu **Team**. El identificador ya es `es.expedientenocturno.juego`.
3. Para probarlo, conecta tu iPhone y pulsa ▶. Con una cuenta de Apple gratuita también funciona, pero la app caduca a los 7 días.
4. En [App Store Connect](https://appstoreconnect.apple.com) crea la app con el mismo identificador, copia los textos de la ficha y sube las capturas de `tienda/capturas-iphone-6.9/` y el icono de 1024.
5. En Xcode: destino *Any iOS Device* → **Product › Archive** → **Distribute App** → *App Store Connect*. Cuando aparezca la compilación en App Store Connect, añádela a la versión y envíala a revisión.

La declaración de cifrado ya está puesta en `Info.plist` (no usa cifrado propio), así que no te la preguntarán en cada subida.

## Política de privacidad

Las dos tiendas exigen una URL pública. El texto está en `tienda/privacidad.html`. Antes de subirlo:

1. Sustituye `CORREO_DE_CONTACTO` (aparece dos veces) por el correo que quieras mostrar.
2. Publícalo en cualquier web pública, por ejemplo GitHub Pages o tu propio dominio, y pega esa URL en las dos consolas.

## Hacer cambios y sacar una versión nueva

1. Edita `www/index.html`.
2. Sube el número de versión:
   - Android: `android/app/build.gradle` → `versionCode` (+1 cada vez) y `versionName`.
   - iPhone: en Xcode, *General* → *Version* y *Build*.
3. Compila:
   ```sh
   export JAVA_HOME=/opt/homebrew/opt/openjdk@21/libexec/openjdk.jdk/Contents/Home
   export ANDROID_HOME=/opt/homebrew/share/android-commandlinetools
   npm run android:aab    # .aab para Google Play → android/app/build/outputs/bundle/release/
   npm run android:apk    # .apk instalable     → android/app/build/outputs/apk/release/
   npx cap sync ios       # y luego Archive en Xcode
   ```
4. Si cambias el icono o la pantalla de carga: edita `design/art.html`, vuelve a generar los PNG de `assets/` y ejecuta `npm run assets`.

## Notas técnicas

- **Botón Atrás de Android:** cierra la lupa, el documento abierto o el cajón, y si no hay nada abierto minimiza la app.
- **Vibración:** usa el plugin Haptics, que funciona también en iPhone.
- El sonido se pausa al salir de la app.
- **Lienzos en modo CPU:** todas las texturas generadas (fichas, fotos, documentos) se dibujan en lienzos con `willReadFrequently`, en la función `mk()`. En Android, Chrome pierde o mezcla el contenido de los lienzos acelerados por GPU cuando se leen sus píxeles: salían fichas en blanco o un sospechoso con la cara de otro. No lo quites.
- **Música y mezcla:** la música empieza en cuanto se abre el juego (en un navegador normal, con el primer toque) y baja de volumen al encender la lámpara para dejar sitio a la lluvia y los efectos. Los volúmenes están en `MIX`, al principio de la sección `SOUND` de `www/index.html`. Si cambias la pista, el bucle depende de `MUSIC.loopStart` y `MUSIC.loopEnd`.
- **Expo Go:** después de cambiar `www/`, ejecuta `python3 expo-go/scripts/build-game.py` desde la carpeta del proyecto (incrusta el juego, los modelos y la música en `expo-go/src/gameHtml.js`).
- **Identificador de la app:** `es.expedientenocturno.juego`. Si prefieres otro (por ejemplo, con un dominio tuyo), cámbialo **antes** de la primera publicación: después ya no se puede. Hay que cambiarlo en `capacitor.config.json`, en `android/app/build.gradle` (`namespace` y `applicationId`) y en Xcode, y mover `MainActivity.java` a la nueva ruta de paquete.
- **Licencias de terceros:** Three.js (MIT); Anton, Courier Prime y Reenie Beanie (SIL Open Font License); Special Elite (Apache 2.0). Todas permiten incluirlas en una app comercial.
- **Modelos 3D** (Sketchfab, licencia *Free Standard*, uso comercial permitido): «Pedestal desk» de shuvalov.di, «Antique Desk Lamp - Game model» de LorenzoDrago y «Cyberpunk Room Flooring» de riach.
- **Modelos 3D** (Sketchfab, licencia *CC Attribution 4.0*: uso comercial permitido **dando crédito al autor**, por ejemplo en la ficha de la tienda o en unos créditos del juego): «1930s style typewriter - w/o branding» de KWojcik, «Western Electric 500 Vintage Rotary Telephone» de vicky12218, «Coffee Mug (School Project)» de FrenchBaguette, «Old Wrist Watch DH» de twilightfox, «Glass Ashtray» de RED2000, «Key» de eucocker y «Knight Figurine 3D print model» de SakoSculpt.
- Si un modelo no carga, el juego usa el objeto dibujado por código. La esfera del reloj (parada a las 23:12), las colillas con carmín, la etiqueta de la llave, la sangre y la bolsa de la figura y la hoja de la máquina se dibujan siempre por código encima del modelo. La versión de un solo archivo (`expediente-movil.html`) no los usa.
- **Fotos de los personajes:** caras sintéticas de personas que no existen, generadas por StyleGAN2 y descargadas de thispersondoesnotexist.com. **Antes de publicar en las tiendas, conviene sustituirlas por imágenes con una licencia comercial clara** (generadas por ti con una IA de imagen, o de un banco de imágenes): basta con reemplazar los archivos de `www/fotos/` por otros con el mismo nombre y formato. Los pañuelos de Rosa y Begoña se dibujan encima de la foto (el de Rosa es una pista del caso 1).
- **Música:** «Suspense · D&D/TTRPG Music» de Bardify. **Antes de publicar en las tiendas, confirma que su licencia permite incluirla en una app comercial** (y si pide atribución, añádela a la ficha).
