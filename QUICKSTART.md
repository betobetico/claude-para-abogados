# Inicio Rápido

**60 segundos.** Esto te lleva a usar los plugins.

## Instalar en Claude Cowork

1. [Instala Claude Desktop](https://claude.com/download)
2. Obtén acceso a Claude Cowork
3. Sigue las instrucciones del vídeo:

https://github.com/user-attachments/assets/51394f0a-5277-4fe2-b81c-5c5e9ac876b5

## Instalar en Claude Code

1. **Abre Claude Code** (en tu terminal) o **Claude Cowork** (la app de escritorio). ¿No sabes cuál tienes? Si tienes una ventana de terminal con Claude, eso es Claude Code.

2. **Añade el marketplace.** En Claude Code, escribe:
   ```
   /plugin marketplace add betobetico/claude-para-abogados
   ```
   Claude Code lo descarga directamente de GitHub; no hace falta descargar nada antes. Para recibir las novedades más adelante: `/plugin marketplace update claude-para-abogados`.

   **Desde una copia local** (si has descargado y descomprimido el repositorio): escribe `/plugin marketplace add ` (con un espacio al final), luego **arrastra la carpeta `claude-para-abogados` a la ventana del terminal** — rellenará la ruta. Pulsa Enter. O escribe la ruta completa: `/plugin marketplace add /Users/tu/Desktop/claude-para-abogados`

3. **Instala tu plugin.** Elige el que encaje con tu trabajo de la tabla de abajo:
   ```
   /plugin install mercantil@claude-para-abogados
   ```

4. **⚠️ Reinicia Claude Code.** Cierra y vuelve a abrir. Este paso no es opcional — el plugin no estará activo hasta que reinicies.

5. **Ejecuta la configuración.** 2 minutos (rápida) o 10-15 minutos (completa).
   ```
   /mercantil:entrevista-inicial
   ```

6. **Conecta una herramienta de investigación.** Las citas se marcan como no verificadas sin ella. En Cowork: Ajustes → Conectores. En Claude Code: el plugin ya lista el MCP de investigación en su configuración; se te pedirá autorización la primera vez que un skill lo necesite.

## Instalar con alcance de usuario, no de proyecto

Cuando ejecutes `/plugin install`, se te puede preguntar si instalar solo para este proyecto o para todos (alcance de usuario). **Elige alcance de usuario.**

Es contraintuitivo: el alcance de proyecto parece más seguro. Pero el alcance de proyecto bloquea al plugin para leer archivos fuera de la carpeta del proyecto — tus documentos en Descargas, tu contrato en Documentos, tu expediente en Dropbox. La mayoría de skills necesitan leer tus archivos. El alcance de usuario no da al plugin acceso extra — solo puede leer archivos que tú le señales explícitamente o que estén en el directorio actual. Simplemente significa que el plugin funciona desde cualquier carpeta.

Si ya instalaste con alcance de proyecto y quieres cambiar: `/plugin uninstall <plugin>`, luego `/plugin install <plugin>@claude-para-abogados` desde tu directorio home.

## ¿Qué plugin es para mí?

| Eres... | Instala... | Primer comando |
|---|---|---|
| Abogado mercantilista / contratos | `mercantil` | `/mercantil:revision` |
| Abogado societario / M&A | `societario` | `/societario:revision-tabular` |
| Abogado laboralista / RRHH | `laboral` | `/laboral:consulta` |
| Abogado de PI / marcas | `propiedad-intelectual` | `/pi:busqueda-marca` |
| Abogado procesalista / litigios | `procesal` | `/procesal:intake` |
| Abogado de privacidad / DPD | `privacidad` | `/privacidad:triaje` |
| Abogado de consumo / producto | `consumo` | `/consumo:consulta` |
| Compliance / regulatorio | `regulatorio` | `/regulatorio:alertas` |
| Gobernanza de IA | `gobernanza-ia` | `/gobernanza-ia:triaje` |
| Abogado fiscalista | `fiscal` | `/fiscal:consulta` |
| Abogado administrativista | `administrativo` | `/administrativo:procedimiento` |
| Abogado inmobiliario | `inmobiliario` | `/inmobiliario:arrendamiento` |
| Abogado concursalista | `concursal` | `/concursal:diagnostico` |
| Abogado de familia | `familia` | `/familia:convenio` |
| DPD / protección de datos | `proteccion-datos` | `/proteccion-datos:rat` |
| Abogado de startups / fundador | `startups` | `/startups:constitucion` |
| Supervisor de clínica jurídica | `clinica-juridica` | `/clinica:intake` |
| Estudiante de Derecho | `estudiante-derecho` | `/estudiante:socratico` |
| Legal ops / buscando skills | `hub-constructor` | `/hub-constructor:entrevista-inicial` |

## Qué estás instalando

Cada plugin aprende tu playbook a través de una entrevista de configuración, lo escribe en un archivo de perfil de práctica (`~/.claude/plugins/config/claude-para-abogados/<plugin>/CLAUDE.md`), y cada skill lee de él. El perfil es tuyo — edítalo, repite la configuración, o dile a un skill que lo actualice.

**Todo resultado es un borrador para revisión profesional.** Los plugins señalan lo que no están seguros, marcan las citas por fuente y bloquean cualquier acción irreversible. Un abogado revisa, verifica y asume la responsabilidad. Hacen esa revisión más rápida; no la sustituyen.

## Qué incluye

20 plugins por área de práctica, recetas de agentes programados y conectores. La referencia completa está en [README.md](README.md).

## ¿Problemas?

- **"Comando no encontrado"** tras instalar → olvidaste el paso 4. Reinicia Claude Code.
- **"Ejecuta la configuración primero"** → ejecuta `/<plugin>:entrevista-inicial` antes de cualquier otro comando.
- **Citas marcadas `[verificar]`** → conecta una herramienta de investigación (paso 6). Sin ella, cada cita viene de datos de entrenamiento, no de una base de datos actualizada.
- **"No puedo leer [archivo]"** → normalmente significa que el plugin tiene alcance de proyecto y el archivo está fuera de la carpeta. Ver "Instalar con alcance de usuario" arriba — reinstala con alcance de usuario o mueve el archivo a la carpeta del proyecto.
- **El plugin no hace X** → ejecuta `/hub-constructor:entrevista-inicial` para encontrar algo mejor, o consulta el README del plugin para "Lo que este plugin no hace".
