---
name: probar
description: Prueba la voz de tu mano derecha, muestra las voces en español de esta Mac y ayuda a elegir otra o a cambiar la velocidad.
disable-model-invocation: true
argument-hint: "[nombre de una voz | velocidad <número>]"
allowed-tools: Bash(voz-natural-decir *)
---

1. Corre este comando: dice una frase de prueba y muestra la voz, la velocidad y si está encendida.

   ```bash
   voz-natural-decir probar
   ```

2. Corre este otro para ver las voces en español que tiene la Mac:

   ```bash
   voz-natural-decir voces
   ```

3. Si el usuario escribió algo después de la orden ($ARGUMENTS):
   - Un nombre de voz (como `Paulina (Mejorada)`): `voz-natural-decir elegir "<nombre exacto de la lista>"`
   - `velocidad <número>` (entre 150 y 230; 185 es lo normal): `voz-natural-decir velocidad <número>`

4. Si la lista no tiene ninguna voz «mejorada», «Enhanced» o «Premium», explícale cómo bajar una gratis (suena mucho
   más natural): Ajustes del Sistema › Accesibilidad › Lectura y voz (en versiones anteriores, «Contenido leído») ›
   botón ⓘ junto a «Voz del sistema» › Voz › buscar «Paulina» › la nube junto a «Paulina (mejorada)». Al terminar la
   descarga, el plugin la elige solo (si no eligió otra a mano).
