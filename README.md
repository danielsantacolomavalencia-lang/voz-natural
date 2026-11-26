# Voz natural · tu mano derecha te habla

Plugin de Claude Code para Mac. Le dices **«usa el modo voz»** y, desde ahí, tu mano derecha te **cuenta en voz** el
resumen de lo que te responde, como un colega que trabajó contigo: qué hizo, qué te entrega y dónde quedó, lo
importante y qué necesita de ti. Lo escrito no cambia: queda igual, para cuando quieras ver una tabla o un detalle.

- Usa la voz que ya trae tu Mac (la mejor: **Siri**). **No instala nada más**, no manda nada a internet y no gasta
  saldo en ningún servicio de voz.
- Tú le hablas con el **micrófono** de Claude Code; ella te responde en voz.
- **¿Windows?** Hay una versión en prueba: [WINDOWS.md](WINDOWS.md). Esta guía es la de Mac.

## Instalar: copia y pega esto en tu mano derecha (Claude Code)

```text
Instálame el plugin «Voz natural» de la clase Mano Derecha, paso a paso, y cuéntame cada paso en una frase:

0. Revisa que la Mac tenga git (Claude Code lo usa para descargar el plugin de GitHub): corre `xcode-select -p`.
   Si falla, corre `xcode-select --install`, dime que acepte la ventana de «herramientas de línea de comandos»
   (gratis, unos minutos) y espera a que te diga «listo».
1. Busca la orden de Claude Code: usa `command -v claude`; si no existe, usa la que trae la app de escritorio:
   ls -t "$HOME/Library/Application Support/Claude/claude-code"/*/*/claude.app/Contents/MacOS/claude | head -1
2. Con esa orden, instala el plugin:
   "<orden de claude>" plugin install voz-natural --marketplace danielsantacolomavalencia-lang/voz-natural
3. Dale permiso a la voz para que no me pregunte cada vez: con tu herramienta de editar archivos, agrega
   "Bash(voz-natural-decir *)" a la lista "allow" dentro de "permissions" en ~/.claude/settings.json.
   Crea esas llaves si no existen y no borres nada de lo que ya hay en el archivo.
4. Revisa si mi voz del sistema ya es Siri con:
   defaults read com.apple.Accessibility SpokenContentDefaultVoiceSelectionsByLanguage
   Si no aparece «com.apple.siri», explícame paso a paso cómo ponerla: Ajustes del Sistema › Accesibilidad ›
   Lectura y voz › Voz del sistema › Siri › Voz 2 (si pide descargarla, que acepte; son unos 200 MB). Pregúntame
   de qué país soy: la voz de Siri debe ser del español de mi país (por ejemplo, «Español (España)» si vivo en España).
   Espera a que te diga «listo».
5. Pregúntame de qué país soy y corre `voz-natural-decir pais <dos letras>` (ES, MX, CO…) para que la voz tenga mi
   acento aunque la región de mi computadora diga otra cosa.
6. Al terminar, dime que abra una conversación nueva y escriba «usa el modo voz».
```

¿Prefieres hacerlo a mano? En la app de escritorio, pestaña **Code**: botón **+** › **Add plugins** (agrega primero el
catálogo `danielsantacolomavalencia-lang/voz-natural`), o en la terminal:

```bash
claude plugin install voz-natural --marketplace danielsantacolomavalencia-lang/voz-natural
```

## Usarlo

| Le dices | Qué pasa |
|---|---|
| «Usa el modo voz» | Desde ahí te cuenta en voz cada respuesta, hasta que lo apagues |
| «Léeme el resumen» | Solo esa respuesta, en voz |
| «Apaga el modo voz» | Deja de hablar. Lo escrito sigue igual |

**Para callarla:** presiona **Esc**, o escríbele o díctale otro mensaje: la voz se calla al instante.

## La mejor voz: Siri (gratis, 3 minutos)

Las voces de fábrica suenan robóticas. Las de **Siri** son las más naturales de la Mac:

1. **Ajustes del Sistema › Accesibilidad › Lectura y voz** (en versiones anteriores, «Contenido leído»).
2. En **Voz del sistema**, elige **Siri** y una de sus voces (por ejemplo, **Voz 2**), del español de tu país
   (si vives en España, **Español (España)**). Si te pide descargarla, acepta.
3. Listo: el plugin la usa sola. (Siri solo funciona así, como voz del sistema; no se puede elegir por nombre.)

¿Prefieres otra? Junto a **Voz del sistema**, el botón **ⓘ** › **Voz** › busca por ejemplo **Paulina** y toca la
**nube** junto a **Paulina (mejorada)**.

## Cambiar la voz o la velocidad

**El acento sale de tu país.** Sin que hagas nada, el plugin mira la región de tu computadora (Mac: Ajustes del Sistema ›
General › Idioma y región; Windows: Configuración › Hora e idioma › Región) y prefiere una voz de ese país: en España,
Mónica o Marisol; en México, Paulina. Si no hay voz de tu país, usa la del español más cercano.

Pídeselo en el chat, con tus palabras:

| Le dices | Qué pasa |
|---|---|
| «¿Qué voces tengo?» | Te cuenta las voces en español que tiene tu Mac |
| «Usa la voz de Siri» | Usa Siri (si es la voz del sistema) |
| «Usa la voz de Mónica» | Cambia a esa voz (basta el nombre; si hay versión mejorada, usa esa) y se presenta |
| «Elige tú la mejor» | Vuelve a la elección automática |
| «Soy de España» / «usa acento de Colombia» | Prefiere las voces de ese país (si no hay, una del español más cercano) |
| «Habla más rápido» / «más despacio» | Cambia la velocidad poco a poco |
| «Velocidad 1.2x» | Esa velocidad exacta (1x es lo normal) |

**Lo que elijas se queda guardado** en todas tus conversaciones, aunque cierres Claude o se actualice el plugin, hasta
que pidas otra cosa. También sirve `/voz-natural:probar`, que dice una frase de prueba y te muestra la voz elegida.

## Hablarle con tu voz

- **App de escritorio:** el botón del **micrófono** en la caja de mensaje.
- **Terminal:** escribe `/voice` (el idioma se pone en `/config` › Language › Spanish). La transcripción no gasta tokens.

## Cómo funciona

- La skill `modo-voz` le enseña a Claude a contarte su respuesta como un colega (nunca lee tablas, código ni rutas) y a
  decirla con la orden `voz-natural-decir`, que usa `say`, la voz de tu Mac, justo antes de mostrarte lo escrito.
- Mientras el modo voz está encendido, cada mensaje tuyo le llega con un recordatorio invisible para que no se le
  olvide hablarte. No ves ningún ícono ni texto extra.
- Tu voz, tu velocidad y si el modo voz está encendido se guardan en `~/.claude/voz-natural/`.
- El resumen hablado agrega unas pocas líneas a cada respuesta: es todo lo que suma al uso de tu plan.

## Si algo falla

- **Error al descargar de GitHub («git not found»):** falta git; corre `xcode-select --install` y acepta la ventana.
- **Te pide permiso cada vez que habla:** falta el paso 3 de la instalación (el permiso `Bash(voz-natural-decir *)`).
- **No suena:** sube el volumen y escribe `/voz-natural:probar`. El registro de lo que dijo está en
  `~/.claude/voz-natural/voz.log`.
- **Suena robótica:** pon Siri como voz del sistema (arriba).

Hecho para la clase Mano Derecha. Mac probado; Windows en prueba ([WINDOWS.md](WINDOWS.md)).
