---
format: 1080x1920
duration: 37.5s
message: "Tres crímenes sin resolver te esperan esta noche. ¿Eres capaz de encontrar al culpable antes del amanecer?"
arc: Gancho nocturno → Ambiente (lámpara, lluvia) → Jugabilidad (prueba, sospechosos, pistas, acusación) → 3 casos → Reto
audience: jugadores de móvil a los que les gustan los misterios, el noir y los juegos de detectives
mode: autonomous
music: none
assembly: hand-authored index.html (gameplay video lives inside each frame sub-composition so overlays sit on top of it; the workflow assembler hoists videos above frames, which would hide the type)
---

## Video direction

- **Palette (frame.md):** night `#07060a` ground; lamp gold `#f0c26a` = the one accent (hero words, clock, title); cream `#e9dfc6` = secondary text; police-stamp red `#a8261d` only for "culpable / crimen / queda libre". Type over footage always sits on a dark gradient band.
- **Type:** Anton for hero lines (sentence case, huge, tight); Special Elite uppercase tracked for kickers/labels (typewriter voice); no body copy.
- **Footage:** real gameplay recorded from the game (1080×1920, silent) is the hero of frames 2–8; every clip gets a slow push-in on its wrapper so nothing sits dead; grade slightly darker/cooler at the edges (vignette at root).
- **Motion grammar:** reveals land on music hits; words punch in with a short scale-down slam (power3/expo out) or type on letter by letter (typewriter); no idle breathing; hard cuts on the beat, thunder flashes as the only "transition" (white→blue flash then decay).
- **Rhythm:** frames 1–3 build the mood (slower), 4–7 accelerate (gameplay beats every ~4 s), 8 is a fast triptych (three cuts in 4 s), 9 is the climax then a held read on the challenge line.
- **Root layers:** film grain + vignette over everything; music bed (Alec Koff "Mysterious Dark Music", from 26.02 s: tension build under frames 1–8, a silent breath at 29.7 s under the Bilbao cut, riser into the final flash, full drop exactly on the title slam at 31.6 s) + synthesized thunder / stamp / typewriter / clock SFX.
- **Never:** spoilers (no verdict, no deduction text naming a culprit), store-availability claims, generic stock shapes, floating bokeh, front-loaded slides.

## Frame 1 — Gancho: las tres de la madrugada

- scene: Negro absoluto, relámpago; "03:00" en dorado y "La comisaría está vacía." a máquina
- duration: 3.3s
- transition_in: cut
- status: animated
- src: compositions/frames/f01-hook.html
- blueprint: compose
- focal: type
- sfx: thunder @0.1 · typewriter keys 0.4–1.2 and 2.0–3.1
- asset_candidates: none (type + rain streaks)

Scene 1 (0.0–0.4s): black; a white→blue thunder flash fills the frame and decays; diagonal rain streaks fade in over the whole frame.
Scene 2 (0.4–1.7s): kicker "BRIGADA DE HOMICIDIOS · TURNO DE NOCHE" types on letter by letter, upper third, centered.
Scene 3 (1.7–2.1s): on the music hit "03:00" slams in huge in lamp gold, centered at ~0.38 height, with a soft gold glow.
Scene 4 (2.1–3.3s): "La comisaría está vacía." types on under the clock in cream; hold.

## Frame 2 — Una lámpara, un café, un crimen

- scene: La pantalla de título se funde y la lámpara ilumina la mesa del caso 1
- duration: 3.5s
- transition_in: cut
- status: animated
- src: compositions/frames/f02-lampara.html
- blueprint: compose
- focal: capture/assets/t01-encendido.mp4 (media 3.0 s →)
- roles: t01-encendido = background (full-bleed, slow push-in)

Scene 1 (0.0–0.9s): footage: title screen dissolving into the lit desk; "Una lámpara." punches in, upper third, cream on dark band.
Scene 2 (0.9–2.0s): "Un café frío." stacks under it.
Scene 3 (2.0–3.5s): "Y un crimen." lands in Anton with "crimen" in stamp red; hold.

## Frame 3 — Fuera llueve. Dentro, alguien miente.

- scene: Lluvia sobre Via Laietana; un trueno ilumina el despacho
- duration: 3.7s
- transition_in: cut
- status: animated
- src: compositions/frames/f03-lluvia.html
- blueprint: compose
- focal: capture/assets/t02-lluvia.mp4 (media 1.15 s →; the game's own thunder flash lands at ~1.3 s)
- roles: t02-lluvia = background (full-bleed, push-in)
- sfx: thunder @1.25

Scene 1 (0.0–1.25s): rainy desk; "Fuera, llueve." in cream, upper third.
Scene 2 (1.25–1.6s): white flash pulse over the footage synced with the game's lightning.
Scene 3 (1.6–3.7s): "Dentro, alguien miente." slams in, gold on "miente"; hold.

## Frame 4 — Examina cada prueba

- scene: La cámara entra en la prueba nº 2; la lupa recorre la colilla con carmín
- duration: 4.3s
- transition_in: cut
- status: animated
- src: compositions/frames/f04-prueba.html
- blueprint: compose
- focal: capture/assets/t04-prueba.mp4 (media 2.9 s →)
- roles: t04-prueba = background (full-bleed, push-in toward the photo)
- sfx: stamp @0.3

Scene 1 (0.0–0.3s): evidence sheet with the magnifier sweeping.
Scene 2 (0.3–1.9s): red rubber-stamp label "PRUEBA Nº 2" thumps in, rotated, lower-middle on a dark band; "Mira de cerca." in cream beside.
Scene 3 (1.9–4.3s): "Nada es casual." lands in gold Anton; hold.

## Frame 5 — Cuatro sospechosos, un culpable

- scene: Ficha policial de Andrés Ruiz, 61 años, portero nocturno
- duration: 4.2s
- transition_in: cut
- status: animated
- src: compositions/frames/f05-sospechosos.html
- blueprint: compose
- focal: capture/assets/t05-ficha.mp4 (media 0.6 s →)
- roles: t05-ficha = background (full-bleed, push-in on the mugshot)
- sfx: stamp @1.8

Scene 1 (0.0–1.8s): the mugshot fills the frame; "4 sospechosos." in cream Anton, lower-middle band.
Scene 2 (1.8–4.2s): "1 culpable." stamps in red (rotated stamp frame) under it; hold.

## Frame 6 — Cruza las pistas antes del amanecer

- scene: La libreta del inspector con nueve deducciones sin resolver; luego el teléfono con la pista del comisario
- duration: 4.3s
- transition_in: cut
- status: animated
- src: compositions/frames/f06-pistas.html
- blueprint: compose
- focal: capture/assets/t06-libreta.mp4 (media 0.2 s, 0–2.1 s) → capture/assets/t07-telefono.mp4 (media 2.0 s, 2.1–4.3 s)
- roles: t06-libreta = background · t07-telefono = background
- sfx: clock ticks 2.2–4.0

Scene 1 (0.0–2.1s): notebook; "Cruza las pistas." gold Anton, lower-middle band.
Scene 2 (2.1–2.4s): hard cut to the phone call; a clock "03:00" appears in gold.
Scene 3 (2.4–4.3s): the clock races 03:00 → 05:59 with ticks; "Antes del amanecer." in cream under it; hold.

## Frame 7 — Señala al culpable

- scene: Informe final para el juez: "¿Quién mató a Ernesto Valls?"; el jugador duda entre sospechosos
- duration: 3.7s
- transition_in: cut
- status: animated
- src: compositions/frames/f07-acusar.html
- blueprint: compose
- focal: capture/assets/t08-acusar.mp4 (media 1.6 s →; selections at ~1.0 s and ~2.1 s)
- roles: t08-acusar = background (push-in on the suspect row)
- sfx: stamp @2.2

Scene 1 (0.0–2.2s): accusation screen; the player taps one suspect, then another; "Señala al culpable." cream, lower-middle band.
Scene 2 (2.2–3.7s): "Si fallas, queda libre." stamps in red; hold.

## Frame 8 — Tres casos

- scene: Tríptico rápido: Barcelona 1984, Barcelona 1985, Bilbao 1986
- duration: 4.1s
- transition_in: cut
- status: animated
- src: compositions/frames/f08-casos.html
- blueprint: compose
- focal: capture/assets/t03-mirar.mp4 (media 2.0, 0–1.35 s) → capture/assets/t11-muntaner.mp4 (media 5.0, 1.35–2.7 s) → capture/assets/t10-bilbao-lluvia.mp4 (media 1.0, 2.7–4.1 s)
- roles: all three = background (full-bleed, each with its own push-in)
- sfx: thunder @2.7 (soft)

Scene 1 (0.0–1.35s): case 1 desk; label "CASO 1 · BARCELONA 1984" + "El anticuario de Via Laietana".
Scene 2 (1.35–2.7s): flash cut to case 2 desk; "CASO 2 · BARCELONA 1985" + "El incendio de la calle Muntaner".
Scene 3 (2.7–4.1s): flash cut to case 3 desk with rain; "CASO 3 · BILBAO 1986" + "La llamada del club de ajedrez". A big gold "3" counter ticks 1→2→3 at the top across the three cuts.

## Frame 9 — El reto

- scene: Relámpago, título "Expediente Nocturno" en dorado y el reto "¿Te atreves a resolverlos?"
- duration: 6.4s
- transition_in: cut
- status: animated
- src: compositions/frames/f09-reto.html
- blueprint: compose
- focal: type over capture/assets/t09-bilbao.mp4 (media 3.2 →, dimmed)
- roles: t01-encendido = background (dimmed, blurred lightly)
- sfx: thunder @0.05

Scene 1 (0.0–0.5s): thunder flash; the lit desk appears very dim behind; rain streaks.
Scene 2 (0.5–1.6s): on the music climax "EXPEDIENTE / NOCTURNO" slams in, huge gold Anton, centered at ~0.36 height, lamp-glow bloom behind.
Scene 3 (1.6–2.6s): kicker "3 CASOS · 1 NOCHE" types on in cream Special Elite under the title.
Scene 4 (2.6–4.8s): "¿Te atreves a resolverlos?" lands in cream Anton under the title; hold.
Scene 5 (3.35–5.8s): a thin gold rule draws in and "MUY PRONTO EN APP STORE" slams in below the challenge, gold Anton; hold.
Scene 6 (5.8–6.4s): final fade to black (last frame only).
