# 🎓 tutor-guiado

Una **Agent Skill** que convierte a tu asistente de IA (GitHub Copilot en VS Code, Claude Code y otros agentes compatibles) en un **tutor de programación paciente**: no te da la solución, te ayuda a llegar a ella.

> Si la IA te da la respuesta, haces el ejercicio. Si te guía, **aprendes**.

## ¿Qué hace?

Cuando pides ayuda con un ejercicio de programación, el asistente:

- ❌ **No** escribe la solución ni edita tus archivos.
- ✅ Te hace preguntas para que expliques el problema con tus palabras.
- ✅ Te da **pistas graduales** (de pregunta orientadora a ejemplo análogo), nunca de golpe.
- ✅ Revisa tu código empezando por lo que está bien y señalando **un solo** punto de mejora cada vez.
- ✅ Te ayuda a leer mensajes de error y a proponer casos de prueba.
- ✅ Usa ejemplos de **otro dominio** para que no puedas copiar y pegar la respuesta.

Está pensada para estudiantes, autodidactas y docentes que quieren usar IA sin perder el aprendizaje por el camino.

## Ejemplo

**Tú:** Mi función `suma_pares(lista)` siempre devuelve `None` y no entiendo por qué. 😩

**Tutor:** Tranquilo, es un error muy común y tiene arreglo sencillo. Vamos a investigarlo juntos. Cuando llamas a la función con `[1, 2, 3, 4]`, ¿qué resultado esperas obtener? Y, mirando tu código, ¿en qué línea crees que la función "entrega" ese resultado a quien la llamó?

**Tú:** Esperaba 6. Creo que lo entrega en la línea donde hago `total += n`.

**Tutor:** Bien pensado: ahí es donde **calculas** el total, y lo haces correctamente. Ahora una pregunta: ¿calcular un valor y devolverlo son lo mismo? Piensa en una calculadora que hace la cuenta pero no te enseña la pantalla. ¿Qué palabra de Python sirve para "enseñar" el resultado a quien llamó a la función?

## Instalación

Copia la carpeta de la skill dentro de tu proyecto:

```
tu-proyecto/
└── .github/
    └── skills/
        └── tutor-guiado/
            └── SKILL.md
```

- **VS Code + GitHub Copilot:** `.github/skills/` (algunas versiones usan `.agents/skills/`; consulta la [documentación de VS Code](https://code.visualstudio.com/docs/copilot/customization/agent-skills)).
- **Claude Code:** `.claude/skills/tutor-guiado/SKILL.md`.

Importante: el nombre de la carpeta debe coincidir con el campo `name` del `SKILL.md`.

Después reinicia la ventana de VS Code (`Ctrl+Shift+P` → *Developer: Reload Window*) y abre un chat nuevo, porque las skills se detectan al iniciar la sesión.

## Uso

- **Automático:** pide ayuda con un ejercicio ("estoy atascado con esta función", "revísame este código") y el agente debería activarla por la descripción.
- **Manual:** escribe `/tutor-guiado` en el chat.
- **Salir del modo tutor:** dile explícitamente "sal del modo tutor" o "ya terminé, dame la solución para comparar".

## Limitaciones (importante)

- Una skill es una **instrucción**, no un bloqueo técnico. El modelo la sigue casi siempre, pero no está garantizado, sobre todo si insistes mucho en que te dé la respuesta.
- En **modo agente**, el asistente tiene herramientas para editar archivos. Para mayor fiabilidad usa el modo **Ask** (chat normal).
- El resultado varía según el modelo elegido; los más capaces respetan mejor las restricciones.
- Si no se activa sola, invócala con `/tutor-guiado`.

## Cómo está diseñada

La skill se apoya en tres ideas pedagógicas:

1. **Escalera de pistas:** pregunta orientadora → pista conceptual → pista localizada → ejemplo análogo → pseudocódigo general. No se saltan niveles.
2. **Feedback acotado:** un punto de mejora cada vez, empezando por lo positivo.
3. **El error como información:** nunca se corrige directamente; se pregunta qué se esperaba y qué ocurrió.

## Personalízala

Es un archivo Markdown: edita `SKILL.md` para adaptarla a tu asignatura, tu lenguaje o tu nivel (más estricta con las pistas, más flexible, otro idioma…). Las contribuciones y sugerencias son bienvenidas mediante *issues* o *pull requests*.

## Licencia

MIT. Haz lo que quieras con ella, citando la autoría.

---

*Autor: Daniel Mateos-García*
