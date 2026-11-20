# Voz natural en Windows (EN PRUEBA)

> Esta versión todavía no se ha probado en un Windows real. Úsala solo en una sesión de prueba acompañada. La guía
> principal (Mac, probada) está en el [README](README.md).

En Windows, tu mano derecha habla con las **voces de Windows** (por ejemplo **Sabina**, de México). Suenan más
robóticas que Siri: las «voces naturales» de Windows (Jorge, Dalia) son solo del Narrador y Microsoft no deja que otros
programas las usen. Todo lo demás funciona igual que en Mac: «usa el modo voz», Esc para callarla, «velocidad 1.2x»,
«usa la voz de Helena», y lo que elijas se queda guardado.

**Requisito:** Git para Windows. Claude Code lo usa para descargar el plugin y para correr la voz (por Git Bash).

## Instalar: copia y pega esto en tu mano derecha (Claude Code en Windows)

```text
Instálame el plugin «Voz natural» de la clase Mano Derecha (versión de Windows, en prueba), paso a paso, y cuéntame
cada paso en una frase:

0. Revisa que este Windows tenga Git: corre `git --version`. Si no existe, dime que lo instale desde
   https://git-scm.com/download/win con las opciones de fábrica (o con `winget install --id Git.Git -e`), que cierre y
   vuelva a abrir Claude, y espera a que te diga «listo».
1. Busca la orden de Claude Code: usa `command -v claude` o `where.exe claude`. Si no aparece, búscala en la carpeta de
   la app de Claude:
   find "$APPDATA/Claude" "$LOCALAPPDATA" -maxdepth 6 -iname "claude.exe" 2>/dev/null | head -5
2. Con esa orden, instala el plugin:
   "<orden de claude>" plugin install voz-natural --marketplace danielsantacolomavalencia-lang/voz-natural
3. Dale permiso a la voz para que no me pregunte cada vez: con tu herramienta de editar archivos, agrega
   "Bash(voz-natural-decir *)" a la lista "allow" dentro de "permissions" en ~/.claude/settings.json
   (C:\Users\<mi usuario>\.claude\settings.json). Crea esas llaves si no existen y no borres nada de lo que ya hay.
4. Revisa qué voces en español tengo con:
   powershell.exe -NoProfile -Command 'Add-Type -AssemblyName System.Speech; (New-Object System.Speech.Synthesis.SpeechSynthesizer).GetInstalledVoices() | ForEach-Object { $_.VoiceInfo.Name + " " + $_.VoiceInfo.Culture }'
   Si no aparece ninguna «es-», explícame paso a paso: Configuración › Hora e idioma › Voz › Administrar voces ›
   Agregar voces › Español (México). Si después sigue sin aparecer, Configuración › Hora e idioma › Idioma y región ›
   Agregar un idioma › Español (México), con «Texto a voz» marcado. Espera a que te diga «listo» y vuelve a revisar.
5. Al terminar, dime que abra una conversación nueva y escriba «usa el modo voz».
```

## Qué revisar en la prueba

| Revisa | Cómo | Si falla |
|---|---|---|
| Se instaló | Escribe `/voz-natural:probar` en una conversación nueva | Que la mano derecha revise el paso 2 |
| Suena | `/voz-natural:probar` dice una frase | Paso 4 (voces en español) y el volumen |
| No pide permiso | «usa el modo voz» y dos o tres preguntas seguidas | Paso 3 (el permiso) |
| Esc la calla | Presiona Esc mientras habla | Anotar qué pasó para revisarlo |
| Un mensaje nuevo la calla | Escríbele mientras habla | Anotar qué pasó |
| Velocidad | «velocidad 1.2x» | Anotar qué pasó |

El registro de lo que dijo está en `C:\Users\<usuario>\.claude\voz-natural\voz.log`.
