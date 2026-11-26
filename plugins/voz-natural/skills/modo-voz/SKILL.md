---
name: modo-voz
description: Tu mano derecha te habla. Cuenta en voz alta, con la voz de tu computadora (Mac o Windows), el resumen de lo que te responde por escrito, como un colega, para que casi no tengas que leer. Úsala SIEMPRE que el usuario pida voz con cualquier palabra («usa el modo voz», «modo voz», «háblame», «léeme el resumen», «dímelo en voz», «resumen en voz») y para apagarla («apaga el modo voz», «ya no me hables», «sin voz»).
allowed-tools: Bash(voz-natural-decir *)
---

# Modo voz: te cuento en voz lo que te escribo

Tu computadora dice en voz alta lo que le mandas con el script de abajo. **Lo escrito no cambia nada:** mismo razonamiento,
mismo detalle, mismas tablas. La voz es un complemento encima: el resumen narrado de tu respuesta, para que el usuario
entienda todo casi sin leer y vaya a lo escrito solo por el detalle.

## Cómo suena

Cada frase se dice así, por la terminal (la frase entre comillas simples, para que la terminal no toque los signos):

```bash
voz-natural-decir 'Tu frase aquí.'
```

La orden **espera a que termine de decirla** antes de devolver el control: lo que el usuario oye y lo que ve van
juntos. Si responde «SIN VOZ», dilo por escrito en una línea y sigue.

## Si el usuario te interrumpe

- **Esc** corta la orden y la voz se calla al instante. No vuelvas a decir lo que estabas diciendo: lo escrito ya está en
  pantalla.
- **Si escribe o dicta otro mensaje** mientras hablas, la voz también se calla sola: atiende el mensaje nuevo.

## Encender y apagar

- **«Usa el modo voz»** (o «modo voz», «háblame»): enciéndelo y cuéntalo en voz en una frase («Listo, ya te hablo…»).
  Desde ahí, haz lo de «En cada respuesta» en todas tus respuestas de esta conversación hasta que lo apague.

  ```bash
  voz-natural-decir encender
  ```

- **«Léeme el resumen»** o «dímelo en voz» (una sola vez): haz lo de «En cada respuesta» solo en esta respuesta, sin
  encender nada.
- **«Apaga el modo voz»** (o «ya no me hables», «sin voz»): apágalo, confírmalo por escrito en una frase y deja de hablar.

  ```bash
  voz-natural-decir apagar
  ```

Mientras está encendido, cada mensaje del usuario te llega con un recordatorio invisible «[Modo voz encendido]».

## Cambiar la voz o la velocidad

- **«¿Qué voces tengo?»**: `voz-natural-decir voces`
  y cuéntale cuáles hay, sin leer la lista entera.
- **«Usa la voz de Siri»**: `voz-natural-decir elegir siri`. Las voces de Siri son las más naturales, pero solo funcionan si
  son la «voz del sistema»; si no lo son, el script dice cómo ponerla y tú se lo explicas.
- **«Usa la voz de Mónica»** (o «cambia a Paulina mejorada»): `voz-natural-decir elegir 'Mónica'`. Acepta el nombre a medias
  y se queda con la mejor versión que haya; la nueva voz se presenta sola. «Elige tú la mejor» → `voz-natural-decir elegir auto`.
- **«Soy de España»** (o «usa acento de Colombia», «pon la voz de México»): `voz-natural-decir pais ES` (dos letras: ES,
  MX, CO, AR, CL…; «auto» vuelve a la región de la computadora). Sin pedirlo, el script ya prefiere las voces del país de
  la región de su computadora; si esa región no es su país, esto lo arregla. Si eligió una voz por nombre, esa manda.
- **«Habla más rápido / más despacio»**: `voz-natural-decir velocidad 1.1x` (o `0.9x`), un paso a la vez. **«Velocidad 1.2x»**
  (o «a 1.5»): `voz-natural-decir velocidad 1.2x`. También acepta palabras por minuto (185 es lo normal = 1x).
- **Lo que elige se queda guardado para siempre** (en todas sus conversaciones, aunque cierre Claude o se actualice
  el plugin), hasta que pida otra cosa. No hace falta volver a configurarlo: díselo la primera vez que cambie algo.
- Al encender el modo voz, el script dice qué voz y velocidad quedaron. Si la voz es «elegida automáticamente», cuéntale
  en tu frase que puede pedir otra cuando quiera («si te gusta otra voz o más velocidad, dímelo y la dejo fija»).
- Si pide una voz que no tiene, explícale cómo bajarla. **Mac:** Ajustes del Sistema › Accesibilidad › Lectura y voz ›
  botón ⓘ junto a «Voz del sistema» › Voz › buscar el nombre › la nube junto a la versión «(mejorada)». **Windows:**
  Configuración › Hora e idioma › Voz › Administrar voces › Agregar voces › Español de su país. Siri solo existe en Mac.

## En cada respuesta

Haz tu trabajo y escribe tu respuesta como siempre. **Justo antes de tu mensaje final**, una sola llamada al script con
el resumen hablado. Empieza por el nombre del usuario si lo sabes.

## Qué se cuenta: como un colega que te cuenta su trabajo

La voz no lee la respuesta: la cuenta ya digerida, como una persona que trabajó contigo.

1. **Qué hice y qué te entrego, y dónde quedó.** «Te dejé una tabla con los pagos de octubre», sin leerla.
2. **Lo importante, sin omitir:** decisiones que tomé, lo que cambió, riesgos, errores y lo que no pude verificar. Si
   algo salió mal o quedó a medias, se dice en voz, nunca solo por escrito.
3. **Lo que necesito de ti:** cada pregunta clara, una por una, y qué recomiendo. Si no necesito nada, se dice.
4. **Nunca se leen** tablas, código, listas largas, rutas, enlaces ni comandos: se nombran y se resumen («son cinco
   pendientes; los dos urgentes son…»).
5. **El largo sigue a la importancia:** corto si fue algo chico; más completo si hubo mucho trabajo o una decisión. Si
   el usuario quiere el detalle de algo, lo pide en el siguiente turno.

## Cómo se habla

- Para oírse, no para leerse: de tú, en español natural, tono de conversación. Sin código, rutas, comandos, siglas
  técnicas, tablas ni enlaces. Números solo si importan, dichos como se hablan.
- **Respaldo escrito, siempre:** la voz nunca reemplaza el texto. Todo lo que dices en voz queda también en tu
  respuesta escrita. Si la computadora falla o el usuario no estaba escuchando, no se pierde nada.
- Sin relleno («¡Excelente pregunta!») y sin anunciar lo que vas a decir.
