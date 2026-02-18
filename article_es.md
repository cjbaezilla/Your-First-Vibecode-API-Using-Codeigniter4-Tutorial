# Vibe Coding para Tu Primera API: Cómo Construimos LaunchPad API en Días (No Meses)

![Promoción LaunchPad API](docs-graphics/promo_horizontal_es.png)

*Una guía práctica para emprendedores que quieren construir su backend sin contratar a un desarrollador ni ahogarse en complejidad técnica*

---

## Cómo Usar Esta Guía (Sí, Es Larga—Y Eso Es Bueno)

Seamos honestos desde el principio: esta guía es extensa. Si buscas un tutorial rápido del tipo "copia y pega este código y tendrás una API en 10 minutos", te vas a decepcionar. Y sinceramente, eso es algo bueno, porque esos tutoriales rápidos son exactamente por lo que tantos emprendedores terminan con sistemas rotos e inseguros que les cuestan miles de dólares arreglar después.

### Por Qué La Hicimos Así

Cuando comencé a aprender a construir software, me frustraba exactamente lo mismo que tú podrías estar sintiendo ahora. Cada tutorial se saltaba las partes que realmente necesitaba entender. Decían "solo ejecuta este comando" sin explicar por qué. Pasaban por alto consideraciones de seguridad porque "eso es cosa de avanzados." Asumían que ya sabía qué era un "ORM" o por qué importa el "middleware."

Seguía chocando contra paredes donde las cosas no funcionaban y no tenía idea de por qué. Pasaba horas buscando en Google mensajes de error que no tenían sentido para mí. Seguía un tutorial paso a paso solo para descubrir que estaba escrito para una versión antigua del software, y ahora nada funcionaba.

Así que cuando escribimos esta guía, tomamos una decisión deliberada: **vamos a explicar todo.** No porque pensemos que no eres lo suficientemente inteligente para resolverlo, sino porque no deberías tener que hacerlo. Construir software ya es suficientemente difícil sin tener que descifrar lo que la documentación asume que ya sabes.

Esta guía es larga porque:

- **Explicamos el "por qué" detrás de cada decisión**, no solo el "qué" y el "cómo"
- **Compartimos los errores que cometimos** para que tú puedas evitarlos (cometimos muchos)
- **Proporcionamos contexto** sobre cómo encajan las diferentes piezas
- **Documentamos alternativas** que consideramos y por qué elegimos lo que elegimos
- **Incluimos solución de problemas** para los obstáculos que realmente encontrarás

### Tres Formas de Leer Esta Guía

Dependiendo de dónde estés en tu camino, tienes tres opciones:

**Ruta 1: La Inmersión Profunda (Recomendada si tienes tiempo)**

Léela de principio a fin. Sí, es larga, pero terminarás con una comprensión completa no solo de cómo construir una API, sino de cómo funcionan las APIs, por qué están estructuradas como están, y cómo solucionar problemas cuando inevitablemente ocurran. Esta es la ruta que mejor te servirá a largo plazo porque realmente entenderás lo que estás construyendo.

**Ruta 2: El Vistazo Estratégico (Si necesitas avanzar rápido)**

Lee estas secciones primero:
1. **Esta introducción** (estás aquí ahora)
2. **El Problema Que Todos Enfrentamos** – para entender si esta guía realmente es para ti
3. **¿Qué es el "Vibe Coding"?** – para entender la metodología
4. **El Stack Técnico** – para entender con qué estamos construyendo (ojea los detalles técnicos, enfócate en las analogías)
5. **La Visión General Completa de la Arquitectura** – para ver el panorama general
6. **Guía de Inicio Rápido** – para ponerte en marcha rápido

Luego usa el resto como referencia cuando lo necesites. Vuelve a secciones específicas cuando encuentres esos problemas en tu propio proceso de construcción.

**Ruta 3: El Rescate "Estoy Atascado" (Para cuando las cosas salen mal)**

Usa la tabla de contenidos para saltar directamente a la sección que coincida con tu problema actual:
- ¿No puedes hacer funcionar el servidor? → La sección de Instalación Completa
- ¿Confundido sobre autenticación? → Entendiendo la Autenticación y Shield
- ¿Recibes mensajes de error extraños? → Solución de Problemas Comunes
- ¿No estás seguro si tu API es segura? → Inmersión Profunda en Seguridad
- ¿Necesitas entender la estructura de la base de datos? → Arquitectura de Base de Datos
- ¿Listo para desplegar pero no sabes por dónde empezar? → Día 5: Llevando Tu API a Internet
- ¿Recibes "Error 500 del Servidor Interno" en producción? → Día 5: Solución de Problemas de Despliegue
- ¿La conexión a la base de datos falla en el servidor? → Día 5: Configuración de Base de Datos en Producción

### Lo Que Realmente Vas a Construir

Al seguir esta guía, crearás LaunchPad API—un sistema de autenticación y gestión de usuarios listo para producción que incluye:

- Registro de usuarios e inicio de sesión (con verificación de email)
- Manejo seguro de contraseñas (ni siquiera almacenarás las contraseñas tú mismo)
- Tokens de API para autenticación de aplicaciones móviles
- Grupos de usuarios y permisos (administradores, usuarios regulares, etc.)
- Un framework completo de pruebas
- Protecciones de seguridad contra ataques comunes
- **Despliegue completo a hosting en vivo** (hosting compartido, dominio, SSL, base de datos)
- Configuración de monitoreo, respaldos y mantenimiento
- Documentación completa de cada decisión

Este no es un proyecto de juguete. Es la base que usan negocios reales. Cuando termines, tendrás algo **en vivo en internet** que podrías usar para una aplicación real—no solo código ejecutándose en tu laptop.

### El Cambio de Mentalidad Que Hace Que Esto Funcione

Aquí está la cosa sobre aprender a construir software: no se trata de memorizar comandos o sintaxis. Se trata de entender patrones y principios. Una vez que entiendes por qué algo funciona, puedes aplicar ese entendimiento a nuevas situaciones incluso cuando los detalles específicos cambian.

Piensa en esta guía como aprender a cocinar versus seguir una receta. Una receta te dice "agrega 2 tazas de harina y hornea a 350°F por 30 minutos." Aprender a cocinar significa entender por qué usas harina (estructura), por qué 350°F (reacción de Maillard sin quemar), y por qué 30 minutos (cuajar proteínas y almidones).

Te estamos enseñando a cocinar, no solo a seguir recetas. Por eso nos tomamos el tiempo de explicar el razonamiento. Cuando entiendes el razonamiento, puedes adaptarte cuando tu situación es diferente. Cuando solo sigues recetas, estás perdido en el momento en que algo no coincide exactamente.

### Un Mapa de Lo Que Viene

Esto es lo que cubre esta guía, en orden:

**Parte 1: Entendiendo el Panorama** (Estás aquí)
- El problema que estamos resolviendo y por qué las soluciones existentes fallan
- Lo que realmente significa Vibe Coding y por qué funciona
- Por qué elegimos las herramientas específicas que elegimos (PHP, CodeIgniter 4, Shield)
- El caso de negocio para construir tu API primero (antes de tu aplicación móvil)

**Parte 2: Configurando Tu Entorno**
- Instalando todo lo que necesitas (PHP, Composer, base de datos)
- Configurando tu entorno de desarrollo
- Entendiendo la estructura del proyecto
- Configurando control de versiones (Git)

**Parte 3: La Fundación—CodeIgniter 4**
- Cómo funciona realmente el framework (rutas, controladores, modelos)
- El patrón MVC explicado en términos humanos
- Archivos de configuración y qué controlan
- Herramientas de depuración y desarrollo

**Parte 4: Autenticación con Shield**
- Por qué la autenticación es tan compleja (y por qué necesita serlo)
- Entendiendo tokens, sesiones y seguridad
- Configurando registro de usuarios e inicio de sesión
- Configurando permisos y grupos de usuarios
- Probando tu sistema de autenticación

**Parte 5: Construyendo Funcionalidades Reales**
- Creando tus primeros endpoints de API
- Manejando validación de datos y mensajes de error
- Diseño de base de datos y migraciones
- Subida de archivos y manejo de imágenes
- Rate limiting y rendimiento

**Parte 6: Seguridad, CORS y el Puente a Producción**
- Lista de verificación de seguridad y vulnerabilidades comunes
- Configuración de CORS (qué es y por qué lo necesitas)
- HTTPS y certificados SSL
- Configuración de entorno para producción

**Parte 7: Día 5—Llevando Tu API a Internet (Pasos Reales de Despliegue)**
- Elegir hosting compartido vs. VPS (y por qué el compartido gana para startups)
- Paso a paso: Preparando tu app para producción
- Creando y migrando tu base de datos de producción
- Subiendo archivos vía FTP/SFTP o despliegue con Git
- Configurando tu dominio y DNS
- Configurando certificados SSL gratuitos
- Probando todo antes del lanzamiento
- Monitoreo, respaldos y mantenimiento

**Parte 8: Documentación y Mantenimiento**
- Documentando tu API para otros desarrolladores
- Escribiendo pruebas que realmente detecten errores
- Depurando problemas de producción
- Actualizando dependencias de forma segura

### La Decisión de Documentar Todo

Una cosa más antes de sumergirnos: notarás que documentamos cada decisión que tomamos. ¿Por qué PHP y no Node.js? ¿Por qué CodeIgniter y no Laravel? ¿Por qué este enfoque de autenticación y no aquel?

Hacemos esto por tres razones:

1. **Para que entiendas** – Saber por qué ayuda a que el conocimiento se adhiera
2. **Para que puedas decidir diferente** – Tu situación podría ser diferente de la nuestra. Si entiendes nuestro razonamiento, puedes hacer una elección informada de hacer las cosas diferente
3. **Para que puedas explicar a otros** – Cuando inevitablemente trabajes con otros desarrolladores (o inversores, o socios), podrás articular por qué tu sistema está construido como está

No estamos diciendo que nuestras elecciones son las únicas elecciones correctas. Estamos diciendo que estas son las elecciones que hicimos, aquí está por qué las hicimos, y aquí está lo que aprendimos de ellas. Toma lo que funcione para ti, cuestiona lo que no, y construye algo que se ajuste a tus necesidades específicas.

### Discurso de Ánimo Final (Porque Lo Vas a Necesitar)

Construir software es difícil. No hay forma de evitarlo. Pero no es imposible, y no necesitas un título en ciencias de la computación para hacerlo. Necesitas persistencia, curiosidad y la voluntad de sentarte con la confusión hasta que tenga sentido.

Vas a tener momentos donde nada funcione y no tengas idea de por qué. Eso es normal. Eso es parte del proceso. La diferencia entre las personas que construyen software exitosamente y las que se rinden no es la inteligencia—es la voluntad de seguir adelante cuando las cosas se ponen frustrantes.

Esta guía está aquí para reducir esa frustración tanto como sea posible, pero no puede eliminarla por completo. Construir cosas es inherentemente caótico. Abraza el caos. Aprende de él. Y recuerda que cada mensaje de error es solo la computadora intentando decirte algo—podría estar hablando en un idioma extranjero ahora, pero al final de esta guía, serás fluido.

¿Listo? Vamos a construir algo real.

---

## El Problema Que Todos Enfrentamos

Tienes la idea. La has validado con clientes potenciales. Puedes ver exactamente cómo tu aplicación cambiará la vida de las personas. Pero llega la barrera: **la tecnología**.

Quizás te han cotizado entre $10,000-$50,000 para una API "simple". Quizás has intentado aprender a programar pero te perdiste en tutoriales que asumen que ya sabes qué es un "endpoint". Quizás has escuchado que necesitas contratar a un CTO o cofundador técnico, pero encontrar a la persona adecuada parece imposible cuando ni siquiera sabes qué preguntas hacer.

Nos sentimos exactamente igual.

Pero esto es lo que descubrimos: **No necesitas convertirte en un desarrollador senior para construir software listo para producción.** Necesitas las herramientas adecuadas, el enfoque correcto y un socio de IA que realmente entienda lo que estás intentando hacer.

De eso trata esta guía. Te vamos a mostrar exactamente cómo construimos LaunchPad API—una base de backend segura y escalable—usando una metodología que llamamos **"Vibe Coding"**.

## ¿Qué es el "Vibe Coding"?

Vibe Coding es el arte de construir software junto a la IA, no en contra de ella. En lugar de pasar meses aprendiendo sintaxis y frameworks antes de escribir una sola línea de código de producción, tú:

1. **Configuras tu entorno** con la documentación adecuada
2. **Entrenas a tu asistente de IA** en tu stack tecnológico específico
3. **Construyes iterativamente** con la IA como tu compañero de programación en pareja
4. **Documentas todo** para que tu yo futuro (y tu equipo) entienda el "por qué" detrás de cada decisión

Piénsalo así: La programación tradicional es como aprender a construir una casa convirtiéndote primero en maestro carpintero, electricista y plomero. Vibe Coding es como tener un contratista experto parado junto a ti, pasándote las herramientas adecuadas, explicándote por qué las usamos y asegurándose de que la base sea sólida.

Todavía aprendes. Todavía entiendes lo que estás construyendo. Pero no te quedas atrapado en el infierno de los tutoriales durante seis meses antes de lanzar algo.

## Conoce LaunchPad API

**LaunchPad API** es el nombre de nuestro proyecto para una base de API lista para producción. Piensa en ello como la sala de máquinas de una aplicación web—la parte que los usuarios nunca ven pero que hace que todo funcione.

Esto es lo que incluye LaunchPad API:

- **Autenticación de Usuarios**: Registro, inicio de sesión, restablecimiento de contraseña, sesiones seguras
- **Seguridad de API**: Tokens para aplicaciones móviles, permisos para diferentes tipos de usuarios
- **Estructura de Base de Datos**: Almacenamiento de datos organizado y escalable
- **Herramientas de Administración**: Gestión de usuarios, monitoreo de actividad
- **Framework de Pruebas**: Asegurándonos de que todo funciona antes de que los usuarios lo vean
- **Documentación**: Cada decisión explicada, cada comando documentado

Construimos esto en días, no meses. Y te vamos a mostrar exactamente cómo, para que puedas hacer lo mismo para tu proyecto.

## El Stack Técnico: Explicado Simplemente

![Flujo del Stack Técnico](docs-graphics/flow_horizontal_es.png)

Antes de sumergirnos en el proceso, hablemos de con qué estamos construyendo realmente. Si eres completamente nuevo en esto, estos conceptos pueden sonar intimidantes. No lo son. Piensa en ellos como los ingredientes de una receta—no necesitas saber química orgánica para hornear un pastel.

### ¿Qué es una API?

Una API (Interfaz de Programación de Aplicaciones) es como un mesero en un restaurante. Tú (el cliente) no entras a la cocina a preparar tu propia comida. Le dices al mesero lo que quieres, él lleva esa orden a la cocina y te trae tu comida.

En software:
- Tu aplicación móvil o sitio web es el cliente
- La API es el mesero
- La base de datos y la lógica de negocio es la cocina

La API se asegura de que las solicitudes correctas lleguen a los lugares correctos y que las cosas sensibles (como los datos de otras personas) permanezcan protegidas.

### ¿Por Qué Las Aplicaciones Móviles Absolutamente Necesitan una API (Y Por Qué Existe Esta Guía)?

Permíteme pintarte una imagen. Imagina que acabas de descargar una nueva aplicación de fitness en tu teléfono. La abres, creas una cuenta y comienzas a registrar tus entrenamientos. Puedes ver tu progreso con el tiempo, compararte con amigos y obtener recomendaciones personalizadas basadas en tus objetivos. Parece casi mágico cómo todo simplemente funciona.

Pero esto es lo que no ves sucediendo detrás de escenas, y es crucial entender esto si estás construyendo tu propia aplicación:

**Tu teléfono es realmente bastante limitado por sí mismo.**

Piénsalo. Tu teléfono móvil tiene algo de espacio de almacenamiento, claro. Pero si esa aplicación de fitness almacenara todos tus datos de entrenamiento, todos los datos de tus amigos, todas las bibliotecas de ejercicios y todos los cálculos de análisis directamente en tu teléfono, algunas cosas sucederían bastante rápido:

1. **Te quedarías sin espacio** después de un mes de seguimiento
2. **Perderías todo** si dejas caer tu teléfono en una piscina
3. **No podrías ver el progreso de tus amigos** a menos que te pasen físicamente su teléfono
4. **La aplicación sería imposiblemente lenta** intentando calcular estadísticas complejas en un procesador diminuto
5. **No podrías acceder a tus datos desde otro dispositivo** como tu tableta o computadora

Aquí es donde la API se convierte en el héroe anónimo de las aplicaciones móviles modernas.

**El Trabajo Real de una API Móvil**

Cuando tocas ese botón para registrar un entrenamiento, esto es lo que realmente sucede en un abrir y cerrar de ojos:

Tu teléfono (la aplicación) envía un mensaje a la API diciendo algo como: "Oye, este usuario acaba de correr 3 millas en 28 minutos. Por favor guarda esto y dime cómo se compara con sus carreras anteriores."

La API recibe este mensaje, verifica que realmente eres tú (autenticación), valida que los datos tengan sentido (3 millas en 2 minutos sería sospechoso) y luego hace el trabajo pesado:

- Almacena ese entrenamiento en una base de datos segura donde no desaparecerá si pierdes tu teléfono
- Calcula tu ritmo promedio, calorías quemadas y tendencias de progreso usando computadoras de servidor potentes
- Verifica si has alcanzado algún hito o récord personal
- Busca las actividades recientes de tus amigos para ver si alguien superó tu tiempo
- Prepara una respuesta hermosa con toda esta información formateada perfectamente para la pantalla de tu teléfono

Luego la API envía toda esa información procesada de vuelta a tu teléfono, y la aplicación la muestra de una manera que se ve simple e intuitiva para ti.

**¿Pero Por Qué La Aplicación No Puede Hacer Esto Directamente?**

Esta es la pregunta que me confundió cuando comencé a aprender sobre desarrollo de aplicaciones. ¿Por qué toda esta ida y vuelta? ¿Por qué no simplemente conectar la aplicación directamente a la base de datos?

Aquí está la cuestión: **podrías, técnicamente, pero sería una pesadilla de seguridad.**

Si tu aplicación se conectara directamente a la base de datos, eso significaría que cada copia de tu aplicación flotando por ahí en miles de teléfonos necesitaría contener la contraseña de la base de datos y detalles de conexión. Sería como darle a cada cliente en un restaurante las llaves de la cocina, la caja fuerte y la oficina del dueño. Claro, la mayoría de las personas no harían nada malicioso, pero solo se necesita una persona para arruinarlo todo.

La API actúa como un guardia de seguridad con una descripción de trabajo muy específica. Decide:
- Quién tiene permitido solicitar qué datos (autenticación)
- Qué operaciones se permite realizar a cada persona (autorización)
- Si los datos enviados parecen legítimos (validación)
- Cuánta información liberar y en qué formato (transformación de datos)

Sin esta capa intermedia, cualquier persona con un poco de conocimiento técnico podría potencialmente leer la información privada de otros usuarios, eliminar bases de datos completas o manipular datos de maneras que rompan tu aplicación.

**El Caso de Negocio Que Lo Hizo Clic Para Mí**

Cuando comenzamos a planificar nuestra propia aplicación, seguía pensando: "¿No podemos simplemente construir la aplicación móvil y omitir la parte de la API? ¿No sería más rápido y barato?"

Luego un mentor me hizo una serie de preguntas que cambiaron todo:

"¿Qué pasa cuando quieres agregar una versión web de tu aplicación más tarde?"
"¿Qué pasa si quieres dejar que desarrolladores de terceros construyan integraciones?"
"¿Cómo actualizarás la lógica de la aplicación sin obligar a cada usuario a descargar una nueva versión?"
"¿Qué pasa con los paneles de administración para que gestiones usuarios y veas análisis?"

Cada pregunta reveló otra razón por la que la API no es solo un requisito técnico—es una estrategia de negocio.

Sin una API, tu aplicación móvil es una isla. Solo puede hacer lo que se programó en ella cuando la lanzaste por primera vez. ¿Quieres agregar una nueva función? Cada usuario tiene que actualizar su aplicación a través de la App Store, lo que toma días o semanas en aprobarse y depende de que los usuarios realmente hagan clic en "Actualizar".

Con una API, tu aplicación se convierte en una ventana hacia un sistema en constante evolución. Puedes agregar funciones, cambiar la lógica de negocio, actualizar algoritmos y lanzar mejoras al instante. La aplicación en los teléfonos de tus usuarios permanece igual, pero la inteligencia detrás de ella sigue volviéndose más inteligente.

**Por Qué Esta Guía Se Enfoca en Construir la API Primero**

Después de meses de investigación, conversaciones con desarrolladores y, francamente, algunos errores costosos, nos dimos cuenta de algo contraintuitivo: **los proyectos de aplicaciones más exitosos comienzan con la API, no con la aplicación móvil.**

Aquí está nuestro razonamiento, y por qué estructuramos esta guía de la manera que lo hicimos:

**La API es tu base.** Si comienzas diseñando pantallas móviles hermosas (lo cual es tentador porque son visuales y divertidas), estás construyendo una casa sin saber cómo es el terreno debajo. Podrías descubrir que el diseño de tu aplicación requiere estructuras de datos o lógica que son increíblemente difíciles de implementar eficientemente. O peor, podrías construirte en un callejón donde agregar funciones más tarde requiere reconstruir todo.

**La API te obliga a pensar en tu lógica de negocio claramente.** Cuando diseñas un endpoint de API para "crear un nuevo pedido" o "calcular costos de envío", tienes que definir exactamente qué información entra, qué procesos suceden y qué sale. Esta claridad hace que toda tu aplicación sea más robusta. No solo estás haciendo pantallas bonitas—estás definiendo cómo opera tu negocio digitalmente.

**La API funciona para todo.** Una vez que tienes una API sólida, puedes construir:
- Una aplicación móvil (iOS o Android)
- Una aplicación web
- Una aplicación de escritorio
- Integraciones con otros servicios
- Herramientas de administración para tu equipo
- APIs de socios para desarrolladores de terceros

Todo esto puede usar exactamente el mismo backend. Eso es increíblemente poderoso. No estás reconstruyendo tu lógica de negocio cuatro veces diferentes para cuatro plataformas diferentes. La construyes una vez, correctamente, y todo lo demás simplemente se conecta a ella.

**Seguridad desde el día uno.** Cuando construyes la API primero, la seguridad no es una reconsideración que agregas más tarde. Está tejida en la tela de cómo se mueven los datos a través de tu sistema. Te ves obligado a pensar en autenticación, autorización, validación de datos y encriptación desde el principio. Esto es mucho más difícil (y más caro) de añadir más tarde.

**Las pruebas son más fáciles.** Las APIs pueden probarse automáticamente de maneras que las aplicaciones móviles no pueden. Puedes escribir scripts que verifiquen que cada endpoint funcione correctamente, que las reglas de seguridad se apliquen, que los datos se validen apropiadamente. Esto significa que para cuando comiences a construir tu aplicación móvil, tienes confianza de que el backend es sólido. No te estás preguntando si los errores están en la aplicación o en el servidor.

**La Aplicación Móvil Se Vuelve Simple**

Aquí está la cosa hermosa que sucede cuando tienes una API bien diseñada: construir la aplicación móvil se vuelve casi sencillo. La aplicación se transforma de una pieza compleja de software que tiene que manejar la lógica de negocio, el almacenamiento de datos, la gestión de usuarios y la seguridad en algo mucho más simple—una capa de presentación.

El trabajo de la aplicación móvil se convierte en:
1. Mostrar pantallas agradables y recolectar la entrada del usuario
2. Enviar esa entrada a la API
3. Recibir datos procesados de vuelta
4. Mostrarlos hermosamente al usuario

Eso es todo. Todas las cosas difíciles—la seguridad, los cálculos, la gestión de datos, las integraciones—viven en la API donde pueden ser apropiadamente protegidas, probadas y mantenidas.

**Ejemplos Reales de Nuestro Viaje**

Cuando estábamos validando nuestra idea de aplicación, hablamos con varios emprendedores que habían construido aplicaciones móviles sin APIs adecuadas. Sus historias fueron notablemente similares:

Un fundador nos contó sobre gastar $15,000 en una hermosa aplicación iOS que funcionaba genial... hasta que quisieron agregar una versión Android. Descubrieron que toda la lógica de negocio estaba incrustada en el código iOS, lo que significaba que esencialmente tenían que reconstruir todo desde cero para Android. Otros $15,000 perdidos.

Otro compartió cómo su aplicación se volvía más y más lenta a medida que agregaban funciones. Debido a que todo se calculaba en el teléfono, los dispositivos más antiguos no podían manejar la carga de trabajo. Tuvieron que reescribir toda la aplicación para mover el procesamiento a un servidor, esencialmente comenzando de nuevo.

Un tercero tuvo un susto de seguridad cuando se dieron cuenta de que su aplicación estaba almacenando las credenciales de la base de datos directamente en el código. Cualquier adolescente con un teléfono jailbroken podría haber extraído esas credenciales y accedido a toda su base de datos de usuarios.

Estas no son historias de terror para asustarte. Son errores honestos de personas inteligentes que no sabían lo que no sabían. Casi cometimos los mismos errores nosotros mismos. Es exactamente por eso que decidimos escribir esta guía.

**Lo Que Realmente Estás Construyendo Aquí**

Cuando sigues esta guía y construyes LaunchPad API, no solo estás creando un backend técnico. Estás construyendo:

- **Un cerebro central** que puede impulsar cualquier interfaz que crees ahora o en el futuro
- **Una fortaleza de seguridad** que protege los datos de tus usuarios y tu negocio
- **Una base escalable** que crece con tu éxito en lugar de derrumbarse bajo él
- **Un activo de negocio** que hace que tu empresa sea más valiosa (a los inversores les encanta la tecnología bien arquitectada)
- **Tu propia tranquilidad** sabiendo que estás construyendo sobre suelo sólido

La aplicación móvil que construyas más tarde será mejor, más rápida y más segura porque estás tomando el tiempo de construir esta base primero. Y si decides agregar una aplicación web, integraciones de socios o herramientas de administración más adelante, ya tendrás el 80% del trabajo hecho.

Por eso comenzamos con la API. No porque sea la parte más emocionante (seamos honestos, las pantallas de inicio de sesión y las tablas de bases de datos no son tan sexys como las interfaces móviles animadas), sino porque es la parte que determina si tu aplicación tiene éxito o se convierte en otra historia de advertencia sobre deuda técnica y brechas de seguridad.

Al final de esta guía, tendrás una API a la que cualquier desarrollador móvil puede conectarse con confianza. Te agradecerán por la documentación clara, las respuestas consistentes y el manejo robusto de errores. Y te agradecerás a ti mismo cuando tu aplicación escale a miles de usuarios sin sudar.

Ese es el poder de construir la base primero.

### ¿Qué es PHP?

PHP es un lenguaje de programación que existe desde 1995. Alimenta aproximadamente el 77% de todos los sitios web, incluyendo gigantes como Facebook, Wikipedia y WordPress.

Esto es lo que necesitas saber sobre PHP moderno (versión 8.2 y superior):

**Es Rápido**: PHP moderno es increíblemente rápido—generalmente más rápido que Python o Node.js para tareas web típicas.

**Es Estable**: Tener 30 años de existencia significa que ha sido probado en batalla. Los errores se encuentran y se corrigen. La documentación es exhaustiva. La comunidad es masiva.

**Está en Todas Partes**: Casi todas las compañías de hosting web soportan PHP. Casi todos los desarrolladores lo conocen o pueden aprenderlo rápidamente. Nunca estás atrapado en una tecnología de nicho.

**No Es El PHP De Tu Papá**: Si por última vez escuchaste sobre PHP en 2005, olvídate de todo. PHP moderno tiene tipos, clases, sintaxis moderna y todas las características que esperarías de un lenguaje de programación del 2026.

### ¿Qué es CodeIgniter 4?

CodeIgniter es un framework de PHP. Piensa en un framework como una base preconstruida para una casa. En lugar de verter concreto, colocar bloques e instalar plomería desde cero, obtienes una base sólida con la infraestructura ya en su lugar.

CodeIgniter 4 específicamente:

- **Maneja las Cosas Aburridas**: Enrutamiento (mapear URLs a código), conexiones de base de datos, encabezados de seguridad, validación de entrada—lo hace automáticamente
- **Impone Buena Estructura**: Te guía para organizar tu código apropiadamente, lo cual importa cuando tu aplicación crece
- **Es Liviano**: A diferencia de algunos frameworks que se sienten hinchados, CodeIgniter se mantiene fuera de tu camino
- **Tiene Gran Documentación**: El manual es claro, completo y escrito para humanos
- **Es Moderno**: La versión 4 (lanzada en 2020) lo actualizó con las características más recientes de PHP

Elegimos CodeIgniter porque está en el punto óptimo entre "demasiado simple para ser útil" y "tan complejo que necesitas un PhD". Se sale de tu camino cuando quieres construir, pero está ahí para ayudar cuando lo necesitas.

### ¿Qué es Composer?

Composer es el gestor de paquetes de PHP. Si eso no significa nada para ti, piensa en ello así:

Imagina que estás horneando un pastel, pero en lugar de comprar harina, azúcar y huevos por separado, podrías simplemente decir "quiero un pastel de chocolate" y alguien entrega todo lo que necesitas, en las cantidades correctas, con instrucciones.

Eso es Composer.

En el mundo del software, los desarrolladores comparten sus soluciones a problemas comunes. ¿Necesitas autenticación de usuario? Alguien ya lo construyó. ¿Necesitas enviar correos electrónicos? Hay un paquete para eso. ¿Necesitas validar formularios? Hecho.

En lugar de escribir miles de líneas de código (e introducir miles de oportunidades para errores), ejecutas un comando:

```bash
composer require codeigniter4/shield
```

Y así de simple, tienes un sistema de autenticación completo—registro de usuario, inicio de sesión, restablecimiento de contraseña, características de seguridad, tokens de API—instalado y listo para usar.

Composer maneja:
- Descargar el código
- Descargar cualquier código de EL cual dependa
- Instalar todo en los lugares correctos
- Actualizar todo cuando salen nuevas versiones
- Asegurarse de que las versiones no entren en conflicto entre sí

Es como tener un asistente meticuloso que nunca olvida una dependencia y siempre lee las instrucciones.

### Configurando Tu Entorno de Desarrollo Local

Aquí está algo que nos confundió por mucho tiempo: No puedes simplemente hacer doble clic en un archivo PHP y ejecutarlo como un documento de Word o una hoja de cálculo. PHP es un lenguaje del lado del servidor, lo que significa que necesita un servidor para ejecutarse. Tu computadora necesita actuar como un servidor web, al menos mientras estás construyendo y probando tu aplicación localmente.

Ahora, podrías configurar esto manualmente. Podrías instalar PHP en sí, luego instalar un servidor web como Apache o Nginx, luego instalar una base de datos como MySQL, luego configurarlos todos para que se comuniquen entre sí. Pasarías días leyendo documentación, editando archivos de configuración, solucionando problemas de por qué las cosas no se conectan apropiadamente, y generalmente peleando con tu computadora en lugar de construir tu aplicación.

O... podrías usar una herramienta que haga todo esto por ti automáticamente.

**Entran los entornos de desarrollo local como XAMPP y Laragon.**

Estas son aplicaciones especializadas diseñadas para convertir tu computadora en un servidor web completo con una sola instalación. Piensa en ellas como kits pre-empaquetados que contienen todo lo que necesitas para ejecutar aplicaciones PHP localmente.

**Lo Que Realmente Son Estas Herramientas**

Cuando decimos "entorno de desarrollo", nos referimos a un stack completo de software que refleja en qué se ejecutará tu aplicación cuando esté en vivo en internet. Un stack típico de PHP incluye:

1. **El servidor web** (generalmente Apache) — Este es el software que escucha las solicitudes de los navegadores y entrega páginas web
2. **PHP en sí** — El intérprete del lenguaje de programación que ejecuta tu código
3. **Un servidor de base de datos** (generalmente MySQL o MariaDB) — Donde tu aplicación almacena todos sus datos
4. **phpMyAdmin** — Una herramienta visual para gestionar tu base de datos sin escribir comandos SQL
5. **Otras utilidades** — Herramientas de prueba de correo, generadores de certificados SSL, visores de registros

Configurar cada uno de estos componentes individualmente es como comprar piezas de auto y armar el motor tú mismo cuando realmente solo quieres ir a la tienda. Los entornos de desarrollo local te dan el auto completamente ensamblado.

**XAMPP: El Veterano**

XAMPP ha existido desde 2002 y es uno de los entornos de desarrollo local más ampliamente utilizados. El nombre significa Multiplataforma (X), Apache, MySQL, PHP y Perl. Es mantenido por Apache Friends y ha sido descargado millones de veces.

Cuando instalas XAMPP, obtienes:
- Servidor web Apache configurado y listo para usar
- PHP (múltiples versiones disponibles)
- Servidor de base de datos MySQL
- phpMyAdmin para gestión de bases de datos
- ProFTPD para transferencia de archivos
- Mercury Mail para probar el envío de correos

XAMPP es confiable, bien documentado y probado en batalla. Si te encuentras con un problema, lo más probable es que alguien más también lo haya tenido y haya una solución en Stack Overflow.

**Laragon: La Alternativa Moderna**

Laragon es más nuevo—comenzó alrededor de 2016—pero ha ganado una following apasionada entre los desarrolladores de PHP. Elegimos Laragon para este proyecto, y aquí está por qué:

Primero, es rápido. Realmente rápido. Arranca en segundos y usa recursos mínimos del sistema. En una computadora moderna, apenas notas que está ejecutándose.

Segundo, es portátil. Puedes instalar Laragon en una unidad USB y llevar todo tu entorno de desarrollo contigo a cualquier computadora. Esto es increíblemente útil si trabajas en múltiples máquinas o quieres mostrar tu trabajo a alguien sin configurar su computadora.

Tercero, hace que las tareas comunes sean sencillas. Crear un nuevo proyecto en Laragon es tan simple como escribir un nombre y hacer clic en "Crear". Automáticamente configura la estructura de carpetas, configura el host virtual e incluso crea una URL local amigable (como `myproject.test` en lugar de `localhost/myproject`).

Cuarto, incluye comodidades modernas que XAMPP carece:
- Soporte incorporado para HTTPS listo para usar
- Fácil cambio entre versiones de PHP
- Integración de terminal con atajos útiles
- Integración de Git
- Instalación con un clic de aplicaciones populares (WordPress, Laravel, Symfony, etc.)

**Cómo Estas Herramientas Habilitan Tu Proceso de Desarrollo**

Tener un entorno de desarrollo local cambia todo sobre cómo construyes software. Esto es lo que se vuelve posible:

**1. Bucle de Retroalimentación Instantánea**

Escribes algo de código, guardas el archivo, actualizas tu navegador y ves el resultado inmediatamente. Este bucle de retroalimentación ajustado es esencial para el desarrollo productivo. Sin un entorno local, tendrías que subir archivos a un servidor remoto cada vez que quisieras probar un cambio, agregando minutos a cada iteración.

**2. Experimentación Segura**

Tu entorno local es tu caja de arena. Puedes romper cosas, probar ideas locas, estropear la base de datos, eliminar todo y comenzar de nuevo—todo sin afectar a nadie más ni a ningún usuario en vivo. Esta libertad para experimentar es crucial cuando estás aprendiendo y construyendo.

**3. Desarrollo Offline**

Una vez que tu entorno está configurado, no necesitas una conexión a internet para programar. Puedes trabajar en aviones, en cafés con WiFi irregular, o en cualquier lugar. Tu código, tu base de datos, toda tu aplicación vive en tu computadora.

**4. Gestión de Base de Datos**

Tanto XAMPP como Laragon vienen con phpMyAdmin, una interfaz web para gestionar tu base de datos. En lugar de aprender comandos SQL de inmediato, puedes:
- Explorar tablas visualmente
- Agregar o editar registros haciendo clic y escribiendo
- Ejecutar consultas y ver resultados en una tabla formateada
- Importar y exportar datos
- Crear respaldos con unos pocos clics

Este enfoque visual hace que las bases de datos sean mucho menos intimidantes cuando estás comenzando.

**5. Pruebas de Escenarios del Mundo Real**

Un entorno local te permite probar cosas que serían peligrosas o imposibles en un sitio en vivo:
- ¿Qué pasa cuando 10,000 usuarios golpean mi API a la vez? (Usa una herramienta de prueba de carga)
- ¿Cómo se comporta mi aplicación con un millón de registros en la base de datos? (Genera datos de prueba)
- ¿Qué pasa si cambio esta función principal—se romperá todo? (Prueba a fondo antes de desplegar)

**6. Integración de Control de Versiones**

Los entornos de desarrollo modernos se integran con Git, el sistema de control de versiones. Esto significa que puedes:
- Rastrear cada cambio que haces
- Revertir errores al instante
- Crear ramas para experimentar sin afectar tu código principal
- Colaborar con otros sin pisarte los talones

**Por Qué Elegimos Laragon Para Esta Guía**

Realmente probamos tanto XAMPP como Laragon durante este proyecto. Ambos funcionan perfectamente bien con CodeIgniter 4. Pero seguimos volviendo a Laragon por una razón simple: se mantiene fuera de nuestro camino.

Con XAMPP, nos encontramos:
- Cavando en archivos de configuración para cambiar versiones de PHP
- Configurando manualmente hosts virtuales para cada proyecto
- Reiniciando todo el stack cuando hacíamos cambios de configuración
- Lidiando con problemas de permisos en Windows

Con Laragon:
- Hacíamos clic derecho en el icono de la bandeja del sistema y seleccionábamos una versión diferente de PHP
- Creaba automáticamente URLs bonitas para cada proyecto
- Los cambios de configuración tomaban efecto inmediatamente sin reinicios
- Todo simplemente funcionaba en Windows

Para alguien aprendiendo a construir APIs, estas reducciones de fricción importan. Cada minuto no gastado solucionando problemas de tu entorno es un minuto gastado aprendiendo y construyendo.

**El Problema de "Funciona en Mi Máquina"**

Hay una broma recurrente en el desarrollo de software: "Funciona en mi máquina." Esto se refiere a la frustración cuando el código se ejecuta perfectamente en la computadora de un desarrollador pero falla cuando se despliega a un servidor. La causa raíz suele ser diferencias en la configuración—diferentes versiones de PHP, diferentes extensiones habilitadas, diferentes configuraciones de servidor.

Los entornos de desarrollo local ayudan a resolver esto haciendo que tu configuración local sea lo más cercana posible a un servidor de producción. Cuando eventualmente despliegas tu aplicación, hay menos sorpresas porque has estado desarrollando en un entorno que imita lo real.

**Comenzando**

Si estás siguiendo esta guía:

1. Descarga Laragon de laragon.org (es gratis y de código abierto)
2. Instálalo—los valores predeterminados están bien para la mayoría de las personas
3. Crea una nueva carpeta de proyecto en el directorio `www` de Laragon
4. Visita `http://localhost` o `http://tu-proyecto.test` en tu navegador
5. Comienza a programar

Eso es todo. Sin configuración compleja. Sin editar archivos de configuración de Apache. Sin solucionar por qué MySQL no arranca. Solo instalar, crear y construir.

**La Conclusión**

Antes de descubrir herramientas como Laragon, configurar un entorno de desarrollo se sentía como una barrera de entrada. Era este obstáculo técnico que tenías que superar antes de poder siquiera comenzar a aprender. Pasábamos horas siguiendo tutoriales, quedándonos atascados en algún problema de configuración oscuro, y eventualmente renunciando frustrados.

Los entornos de desarrollo local eliminan esa barrera. Te permiten enfocarte en lo que realmente quieres hacer: construir tu aplicación. La infraestructura se vuelve invisible—solo otra herramienta que funciona confiablemente en segundo plano mientras tú creas.

Para LaunchPad API, Laragon nos dio un entorno estable, rápido y fácil de usar donde pudimos construir y probar nuestra API localmente antes de siquiera pensar en el despliegue. Hizo que la base técnica de nuestro proyecto se sintiera accesible en lugar de intimidante.

Si estás comenzando, nuestro consejo es simple: No intentes ser un administrador de sistemas y un desarrollador al mismo tiempo. Deja que herramientas como Laragon manejen la infraestructura para que puedas enfocarte en construir tu producto.

## El Peligro Oculto: Por Qué Tu Archivo `.env` Es Más Importante De Lo Que Piensas

Déjame contarte una historia que me quita el sueño. Un amigo mío—un tipo inteligente, emprendedor exitoso—pasó seis meses construyendo su aplicación. Tenía usuarios, ingresos, todo iba genial. Entonces una mañana, se despertó para descubrir que toda su base de datos había sido borrada. Años de datos de clientes, desaparecidos. Su negocio estaba efectivamente muerto de la noche a la mañana.

¿Qué pasó? Había cometido accidentalmente su contraseña de base de datos a GitHub. Estaba ahí en texto plano para que cualquiera la viera. Alguien la encontró, inició sesión y borró todo.

Este es el tipo de error que parece imposible hasta que te sucede a ti. Y es mucho más común de lo que podrías pensar. He visto esta historia repetirse docenas de veces en foros de desarrolladores, siempre con el mismo desenlace desgarrador: alguien no entendió la importancia de ocultar sus secretos, y pagó el precio.

### El Problema: Código Que Viaja

Aquí hay algo que no era obvio para mí cuando comencé: **tu código va a terminar en lugares que no controlas.**

Piensa en el ciclo de vida de tu aplicación:
1. Escribes código en tu laptop
2. Lo guardas en GitHub (u otro repositorio de código)
3. Quizás compartes acceso con un desarrollador que contrataste
4. Lo despliegas a un servidor web
5. Podrías tener miembros del equipo descargándolo a sus máquinas
6. Eventualmente, podrías hacer partes de él de código abierto

En cada uno de estos pasos, cualquiera con acceso puede leer cada línea de código. Cada. Single. Línea.

Ahora imagina que has escrito algo como esto en tu código:

```php
$databasePassword = "SuperSecretPassword123!";
$apiKey = "sk_live_1234567890abcdef";
```

Esas credenciales están ahora en todas partes donde está tu código. Cualquiera que pueda ver tu código puede iniciar sesión en tu base de datos. Cualquiera que pueda ver tu código puede hacer llamadas a la API usando tu cuenta (y acumular tu factura). Cualquiera que pueda ver tu código puede convertirse en ti.

Esto no es teórico. He visto personalmente repositorios de GitHub con millones de visitas que incluían accidentalmente claves API de Stripe, credenciales de AWS y contraseñas de bases de datos. Los bots escanean GitHub específicamente buscando estos patrones. En el momento en que confirmas un secreto en un repositorio público, está comprometido. Incluso en repositorios privados, estás a un empleado descontento o cuenta hackeada de distancia del desastre.

### La Solución: Variables De Entorno

Entonces, ¿cómo resolvemos esto? Necesitamos una forma de configurar nuestra aplicación sin poner secretos en el código mismo.

Entra el archivo `.env`.

Un archivo de entorno es un archivo especial que se encuentra en la carpeta de tu proyecto pero **nunca se confirma en tu repositorio de código**. Contiene valores de configuración específicos del entorno en el que se ejecuta tu código—tu laptop, tu servidor de pruebas, tu servidor de producción.

Piénsalo así: Tu código es un libro de recetas. El archivo `.env` es la despensa de tu cocina. La receta (código) dice "agrega dos huevos," pero no especifica qué huevos—usas los huevos que estén en tu despensa (entorno) en ese momento. Diferentes cocinas (entornos) tienen diferentes ingredientes, pero la receta se mantiene igual.

Así es como se ve típicamente un archivo `.env`:

```bash
# Configuración de Base de Datos
database.default.hostname = localhost
database.default.database = my_app_db
database.default.username = app_user
database.default.password = SuperSecretPassword123!
database.default.DBDriver = MySQLi

# Claves API
STRIPE_SECRET_KEY = sk_live_1234567890abcdef
STRIPE_PUBLISHABLE_KEY = pk_live_0987654321fedcba

# Configuración de Aplicación
app.baseURL = 'http://localhost:8080'
CI_ENVIRONMENT = development
```

Entonces en tu código, en lugar de escribir la contraseña real, haces referencia a la variable de entorno:

```php
// En lugar de esto (MAL):
$password = "SuperSecretPassword123!";

// Haces esto (BIEN):
$password = getenv('database.default.password');
```

Ahora tu código no contiene secretos. Solo sabe cómo buscarlos cuando se ejecuta.

### Por Qué Esto Importa: Una Analogía Del Mundo Real

Imagina que estás construyendo una casa. No escribirías tu dirección y la combinación de tu caja fuerte directamente en los planos, y luego entregarías copias de esos planos a cada contratista, inspector y repartidor que trabaje en tu casa. Eso es una locura, ¿verdad? Cualquiera con los planos podría encontrar tu casa y abrir tu caja fuerte.

Pero eso es exactamente lo que estás haciendo cuando codificas secretos directamente en tu aplicación.

En cambio, los planos (tu código) describen cómo construir la casa, y cada persona recibe solo la información que necesita para su trabajo específico. El electricista recibe especificaciones eléctricas, no la combinación de la caja fuerte. El plomero recibe diagramas de tuberías, no tu contraseña de WiFi.

El archivo `.env` es como un documento seguro que permanece en la casa después de la construcción. Contiene toda la información sensible que la casa necesita para funcionar—códigos de alarma, contraseñas de WiFi, combinaciones de cajas fuertes—pero nunca se incluye en los planos que se pasan de un lado a otro.

### El Patrón `.env` vs `.env.example`

Aquí está el flujo de trabajo práctico que usan los desarrolladores profesionales:

**1. Crear un archivo `.env.example`**
Este archivo contiene todas las claves de configuración que tu aplicación necesita, pero con valores de marcador de posición en lugar de secretos reales:

```bash
# Copia este archivo a .env y completa tus valores reales
database.default.hostname = localhost
database.default.database = your_database_name
database.default.username = your_username
database.default.password = YOUR_PASSWORD_HERE
```

**2. Agregar `.env` a tu archivo `.gitignore`**
Esto le dice a Git que nunca rastree ni confirme tu archivo `.env`. Permanece solo en tu máquina local.

**3. Copiar `.env.example` a `.env` en cada entorno**
Cuando configuras una nueva laptop de desarrollador, o despliegas a un servidor, copias el archivo de ejemplo y completas los valores reales.

**4. Nunca confirmar el archivo `.env` real**
Nunca. Ni siquiera "solo esta vez." Ni siquiera "solo para probar." Nunca.

### ¿Qué Va En Tu Archivo `.env`?

Con el tiempo, acumularás varios secretos y valores de configuración. Aquí está lo que típicamente pertenece en tu archivo de entorno:

**Credenciales de Base de Datos**
- Nombre del host
- Nombre de la base de datos
- Nombre de usuario
- Contraseña
- Número de puerto

**Claves API**
- Procesadores de pago (Stripe, PayPal)
- Servicios de email (SendGrid, Mailgun)
- Mapas y geolocalización (Google Maps, Mapbox)
- Servicios SMS (Twilio)
- Almacenamiento en la nube (AWS S3, DigitalOcean Spaces)
- Cualquier servicio de terceros con el que te integres

**Secretos de Aplicación**
- Claves de encriptación
- Secretos de sesión
- Claves de firma JWT
- Tokens CSRF

**Configuraciones Específicas Del Entorno**
- URL base (localhost vs dominio de producción)
- Modo de depuración (habilitado en desarrollo, deshabilitado en producción)
- Niveles de log
- Configuración de email (usar emails reales en producción, falsos en desarrollo)

### Los Escenarios De Pesadilla Que Evitamos

Quiero enfatizar lo serio que es esto compartiendo algunas historias más del mundo real:

**La Factura De $50,000 De AWS**
Una startup accidentalmente comprometió sus claves de acceso de AWS en un repositorio público de GitHub. En 24 horas, mineros de criptomonedas habían encontrado las claves, lanzado cientos de máquinas virtuales costosas, y minado Bitcoin a expensas de la startup. La factura fue de $50,000 antes de que la detección de fraude de AWS lo detectara.

**El Rescate De La Base De Datos**
Un desarrollador incluyó credenciales de base de datos en código que luego se hizo de código abierto. Seis meses después, alguien accedió a la base de datos de producción y la mantuvo como rehén por 5 Bitcoin. La empresa tuvo que pagar porque no tenían respaldos adecuados.

**La Violación Del GDPR**
Una empresa con sede en la UE accidentalmente expuso datos de clientes porque sus claves API eran visibles en su código. Se enfrentaron a multas masivas bajo regulaciones GDPR y tuvieron que notificar a miles de clientes sobre la violación.

Estas no son historias de terror para asustarte innecesariamente. Son cuentos cautelares que suceden regularmente porque los desarrolladores subestiman la importancia de mantener los secretos fuera del código.

### Nuestra Estrategia `.env` Para LaunchPad API

En nuestro proyecto, nos tomamos esto en serio desde el día uno. Aquí está nuestro enfoque:

**Paso 1: Crear El Archivo De Ejemplo**
Creamos un archivo `.env.example` que documenta cada opción de configuración que nuestra aplicación necesita. Esto sirve tanto como documentación como plantilla.

**Paso 2: Proteger El Archivo Real**
Agregamos `.env` a nuestro `.gitignore` inmediatamente, antes de escribir cualquier código real. Esto asegura que nunca lo confirmemos accidentalmente.

**Paso 3: Documentar El Proceso De Configuración**
En nuestro README y documentación, le decimos explícitamente a cualquiera que configure el proyecto: "Copia `.env.example` a `.env` y completa tus valores."

**Paso 4: Usar Diferentes Valores Para Diferentes Entornos**
- Desarrollo: Usa base de datos local, modo de depuración habilitado, claves API de prueba
- Pruebas: Usa base de datos de pruebas, modo de depuración habilitado, claves API reales
- Producción: Usa base de datos de producción, modo de depuración deshabilitado, claves API reales, configuraciones de seguridad adicionales

**Paso 5: Nunca Registrar Ni Mostrar Variables De Entorno**
En nuestro código, somos cuidadosos de nunca registrar o mostrar accidentalmente estos valores. Si necesitamos depurar problemas de conexión a la base de datos, registramos que la conexión falló, no qué contraseña intentamos usar.

### Errores Comunes Y Cómo Evitarlos

Incluso los desarrolladores experimentados cometen errores a veces. Aquí están los errores más comunes y cómo prevenirlos:

**Error 1: "Lo Agregaré A Gitignore Después"**
Problema: Creas el archivo `.env`, escribes algo de código, confirmas todo, y luego recuerdas agregarlo a `.gitignore`. Demasiado tarde—ya está en tu historial.

Solución: Agrega `.env` a `.gitignore` inmediatamente cuando creas el proyecto, antes de crear el archivo `.env` real.

**Error 2: "Lo Removí Del Repo, Así Que Estoy Seguro"**
Problema: Confirmaste secretos, te diste cuenta de tu error, y borraste el archivo. Pero Git mantiene el historial. Cualquiera todavía puede ver las confirmaciones antiguas con tus secretos.

Solución: Una vez confirmado, debes rotar (cambiar) todas las credenciales expuestas. Borrar el archivo no es suficiente.

**Error 3: "Solo Estoy Probando, Usaré Valores De Marcador De Posición"**
Problema: Usas credenciales reales en desarrollo "solo para probar," con la intención de limpiarlos más tarde. Lo olvidas.

Solución: Nunca uses credenciales de producción en desarrollo. Crea cuentas de prueba separadas con acceso limitado.

**Error 4: "Mi Repo Es Privado, Así Que Estoy Seguro"**
Problema: Los repositorios privados pueden ser accedidos por cualquiera a quien le des permisos. Los miembros del equipo se van. Las cuentas son hackeadas. "Privado" no significa "seguro."

Solución: Trata los repositorios privados igual que los públicos. Mantén los secretos fuera.

**Error 5: "Encriptaré Los Secretos En El Código"**
Problema: Todavía estás almacenando secretos en código, solo encriptados. Cualquiera con el código puede desencriptarlos.

Solución: No almacenes secretos en código en absoluto, encriptados o no. Usa variables de entorno.

### La Decisión Que Tomamos

Cuando comenzamos LaunchPad API, hicimos una regla innegociable: **Sin secretos en código. Nunca.**

Esto no era solo seguir las mejores prácticas. Era construir una base en la que pudiéramos confiar. Cuando eres un emprendedor, tienes suficiente de qué preocuparte—marketing, ventas, soporte al cliente, financiamiento. Lo último que necesitas es una violación de seguridad que destruya todo lo que has construido.

Al usar variables de entorno desde el día uno, nosotros:
- Podemos compartir nuestro código libremente sin preocuparnos por exponer credenciales
- Podemos desplegar a diferentes entornos sin cambiar código
- Podemos rotar credenciales fácilmente cuando sea necesario
- Podemos incorporar nuevos desarrolladores sin darles acceso a sistemas de producción
- Podemos dormir por la noche sabiendo que nuestros secretos son realmente secretos

**Compromisos a considerar:**
- **Pros**: Seguridad, flexibilidad, despliegue más fácil, mejor colaboración en equipo
- **Contras**: Configuración ligeramente más compleja, necesidad de administrar archivos de entorno en cada servidor

Esta es una decisión que es completamente reversible (siempre puedes cambiar tu enfoque más tarde), pero ¿por qué arriesgarte? Comienza seguro, mantente seguro.

### Comenzando Con Tu Archivo `.env`

Si estás siguiendo esta guía, aquí está exactamente qué hacer:

1. **Crea `.env.example`** en la raíz de tu proyecto
2. **Agrega todas las claves de configuración** que tu app necesita, con valores de marcador de posición
3. **Agrega `.env` a `.gitignore`** antes de crear el archivo real
4. **Copia `.env.example` a `.env`** y completa tus valores reales
5. **Nunca confirmes el archivo `.env`**—revisa dos veces antes de cada confirmación
6. **Respalda tu archivo `.env` de forma segura**—quizás en un administrador de contraseñas

Recuerda: Tu archivo `.env` es la llave de tu reino. Guárdalo en consecuencia.

## Por Qué Las APIs en PHP Tienen Sentido para Emprendedores (La Verdad Real)

Hablemos del elefante en la habitación: Probablemente has escuchado que los desarrolladores "reales" usan Node.js, Python o Ruby. Quizás te estás preguntando si estás cometiendo un error al elegir PHP.

Aquí está nuestra perspectiva como emprendedores, no como teóricos académicos:

### La Ventaja del Hosting Compartido

**PHP se ejecuta en hosting compartido. Node.js, Python y Ruby generalmente no.**

¿Qué es el hosting compartido? Es el hosting de $3-$10 por mes que usa el 90% de los sitios web pequeños. Subes tus archivos vía FTP y se ejecutan. Eso es todo.

Hablemos de números reales:

| Opción | Costo Mensual | Costo Anual | Complejidad de Configuración |
|--------|-------------|-------------|------------------|
| Hosting PHP Compartido | $3-10 | $36-120 | Subir archivos, listo |
| VPS para Node.js/Python | $20-50 | $240-600 | Configuración de servidor, monitoreo, seguridad |
| VPS Administrado | $50-150 | $600-1800 | Más simple, pero caro |

**La diferencia**: $564 a $1,680 por año.

Eso no es solo dinero—es tu presupuesto de marketing, tu presupuesto de diseño, tu pista.

### Por Qué el VPS Cuesta Más (Y En Qué Estás Pagando)

Cuando usas Node.js, Python o Ruby para una aplicación web, generalmente necesitas un VPS (Servidor Privado Virtual). Esto significa:

1. **Obtienes un servidor completo** (virtual, pero aún un servidor)
2. **Instalas el sistema operativo** (Linux, generalmente)
3. **Instalas tu runtime** (Node.js, Python, etc.)
4. **Configuras el servidor web** (Nginx o Apache)
5. **Configuras la gestión de procesos** (PM2 para Node.js, servicios systemd, etc.)
6. **Manejas las actualizaciones de seguridad** (firewall, certificados SSL, parches)
7. **Monitoreas los bloqueos** (y reinicias servicios cuando fallan)
8. **Escalas manualmente** (cuando el tráfico aumenta, actualizas el servidor)

Esto es totalmente factible. Miles de desarrolladores lo hacen todos los días. Pero es una curva de aprendizaje, y es trabajo continuo.

### La Simplicidad de Despliegue de PHP

Con PHP en hosting compartido:

1. **Subes tus archivos** vía FTP o la interfaz web
2. **Eso es todo**

La compañía de hosting maneja:
- El sistema operativo
- El servidor web (Apache)
- La instalación y actualizaciones de PHP
- Los parches de seguridad
- El monitoreo del servidor
- Los certificados SSL (generalmente gratis y automáticos)

Te enfocas en construir tu aplicación, no en cuidar un servidor.

### La Realidad de la Curva de Aprendizaje

Si estás aprendiendo a programar mientras construyes tu negocio, tienes ancho de banda limitado. Cada hora gastada aprendiendo administración de servidores es una hora no gastada en funciones que tus clientes realmente les importan.

El hosting de PHP está diseñado para humanos:
- cPanel o interfaces similares (gestión de archivos con apuntar y hacer clic)
- Instaladores de un clic para aplicaciones comunes
- Herramientas visuales de gestión de bases de datos
- Registros de errores que realmente puedes leer
- Personal de soporte que puede ayudar con preguntas básicas

### Cuándo Node.js (o Python/Ruby) Realmente Gana

No estamos diciendo que PHP siempre sea la elección correcta. La comparación justa importa:

**Elige Node.js/Python/Ruby cuando:**
- Necesitas funciones en tiempo real (chat, actualizaciones en vivo, edición colaborativa)
- Estás haciendo procesamiento computacional pesado
- Ya tienes un cofundador técnico o equipo
- Estás construyendo algo que específicamente necesita esos ecosistemas
- Tu presupuesto de hosting es de $500+/mes de todos modos

**Elige PHP cuando:**
- Estás construyendo una aplicación web estándar (operaciones CRUD, cuentas de usuario, gestión de contenido)
- Quieres minimizar los costos y complejidad de infraestructura
- Necesitas desplegar rápidamente e iterar a menudo
- Quizás necesites transferir esto a otro desarrollador algún día (los desarrolladores de PHP están en todas partes)

Para LaunchPad API—una API REST estándar con autenticación—PHP es la elección pragmática. Podemos enfocarnos en construir funciones en lugar de gestionar servidores.

### La Pregunta de la Escala

"¿Pero PHP escalará?"

Esta pregunta generalmente viene de personas que leen blogs de tecnología pero aún no han escalado nada.

Aquí está la verdad: **Tu elección de lenguaje importa menos que tu arquitectura.**

Facebook se ejecuta en PHP. Wikipedia se ejecuta en PHP. Etsy se ejecuta en PHP. El backend de Slack es en gran parte PHP. Estas compañías sirven miles de millones de solicitudes por día.

Si llegas al punto donde PHP es tu cuello de botella, felicidades—tienes un negocio muy exitoso, y puedes permitirte optimizar o reescribir ese componente específico.

La optimización prematura es el enemigo del progreso. Comienza con lo que funciona, lanza rápido y optimiza cuando tengas usuarios reales y datos reales mostrando dónde están los problemas.

## Nuestra Metodología de "Vibe Coding" en 3 Pasos

![Proceso de Vibe Coding](docs-graphics/vibe_horizontal_es.png)

Ahora entremos en el proceso real. Así es como pasamos de "necesitamos una API" a tener una base lista para producción en días.

### Paso 1: Descargar la Documentación Localmente

Este paso parece simple, pero es absolutamente crucial. Aquí está por qué:

**El Problema con la Ayuda Genérica de IA**

La mayoría de los asistentes de codificación con IA (ChatGPT, Claude, etc.) tienen datos de entrenamiento que tienen meses o años de antigüedad. Saben sobre CodeIgniter, pero podrían no saber sobre las características específicas de CodeIgniter 4. Saben sobre autenticación, pero podrían sugerir enfoques desactualizados.

Cuando pides ayuda genérica a una IA, estás lanzando los dados sobre si el consejo es actual, seguro y sigue las mejores prácticas.

**Nuestra Solución: Documentación Local**

Descargamos la guía completa de usuario de CodeIgniter 4 y la documentación de autenticación de Shield directamente en la carpeta de nuestro proyecto. No enlaces—archivos reales sentados ahí en tu computadora.

Lo que descargamos:
- Toda la guía de usuario de CodeIgniter 4 (documentación HTML)
- La documentación de la biblioteca de autenticación Shield (archivos Markdown)
- Aproximadamente 50MB de material de referencia completo y actualizado

**Por Qué Esto Importa**

Al tener la documentación localmente:
1. **Siempre está disponible**—sin necesidad de conexión a internet
2. **Es la fuente oficial**—sin publicaciones de blog con información desactualizada
3. **Podemos apuntar nuestra IA a ella**—esta es la clave
4. **Podemos buscarla instantáneamente**—encontrar exactamente lo que necesitamos

Piensa en ello como la diferencia entre pedirle consejo a un contratista general versus tener los planos reales y los códigos de construcción justo ahí frente a ti mientras explican.

### Paso 2: Dejar Que La IA Analice Y Cree Skills

Aquí es donde sucede la magia. Usamos un asistente de codificación con IA llamado **OpenCode** (puedes usar herramientas similares como GitHub Copilot, Cursor, o Claude con la configuración correcta).

**¿Qué es OpenCode?**

OpenCode es un asistente de codificación inteligente que vive en tu entorno de desarrollo. A diferencia de los chatbots genéricos, está diseñado para entender tu base de código específica y ayudarte a escribir, depurar y mejorar tu código en contexto.

Piensa en ello como tener un desarrollador senior sentado junto a ti que:
- Nunca se cansa
- Conoce cada línea de tu código
- Puede explicar las cosas pacientemente
- No te juzgará por hacer preguntas "obvias"

**Entrenando La IA En Nuestra Documentación**

Aquí está lo que hicimos:

1. **Apuntamos OpenCode a nuestra documentación local**: Le dijimos que leyera la guía de usuario de CodeIgniter y los docs de Shield que descargamos

2. **Le pedimos crear "Archivos de Skill"**: Estos son archivos de conocimiento especializados que enseñan a la IA sobre áreas específicas de nuestro proyecto

3. **Dejamos que organizara el conocimiento**: La IA analizó miles de páginas de documentación y las destiló en guías prácticas y accionables

**Lo Que Salió De Esto**

OpenCode creó 7 archivos de skill para nosotros:

1. **ci4-api-development** — Cómo construir endpoints de API REST de la manera correcta
2. **ci4-shield-auth** — Autenticación, tokens, permisos y seguridad
3. **ci4-routing-controllers** — Mapeando URLs a código y organizando controladores
4. **ci4-models-database** — Trabajando con bases de datos y modelos de datos
5. **ci4-security** — Validación, limitación de tasa, protección contra ataques
6. **ci4-configuration** — Configuraciones, variables de entorno, servicios
7. **ci4-testing** — Escribiendo pruebas para asegurar que todo funciona

Cada archivo de skill contiene:
- Ejemplos de código prácticos que podemos copiar y modificar
- Mejores prácticas de la documentación oficial
- Patrones comunes y anti-patrones
- Enlaces de vuelta a la documentación completa cuando necesitamos detalles más profundos

**La Diferencia Que Esto Hace**

Ahora cuando pedimos ayuda a OpenCode, no nos da consejos genéricos. Nos da consejos específicos de CodeIgniter 4. Conoce el sistema de autenticación de Shield. Entiende la estructura de nuestro proyecto.

Ejemplo:

**Sin skills:** "¿Cómo protejo una ruta de API?"
→ Respuesta genérica sobre middleware (podría ser incorrecta para nuestro framework)

**Con skills:** "¿Cómo protejo una ruta de API usando la autenticación por token de Shield?"
→ Código específico usando el filtro TokenAuth de Shield con sintaxis apropiada

Esta precisión ahorra horas de depuración y previene errores de seguridad que podrían costarnos más tarde.

### Paso 3: Instalar Bibliotecas Con Composer

Ahora que nuestra IA entiende nuestro stack tecnológico, comenzamos a construir. Lo primero que necesitábamos era autenticación—registro de usuario, inicio de sesión, gestión de contraseñas, tokens de API para aplicaciones móviles.

**La Manera Tradicional**

Sin Composer, necesitaríamos:
1. Escribir lógica de registro de usuario (validación, almacenamiento en base de datos, verificación de correo)
2. Escribir lógica de inicio de sesión (verificación de contraseña, gestión de sesiones)
3. Escribir lógica de restablecimiento de contraseña (tokens seguros, envío de correo)
4. Escribir generación de tokens de API (tokens aleatorios seguros, expiración)
5. Escribir verificación de permisos (quién puede hacer qué)
6. Escribir características de seguridad (limitación de tasa, protección contra fuerza bruta)
7. Probar todo esto a fondo
8. Mantenerlo para siempre

Eso son semanas de trabajo. Y como no somos expertos en seguridad, probablemente introduciríamos vulnerabilidades.

**La Manera De Composer**

Ejecutamos un comando:

```bash
composer require codeigniter4/shield
```

Y obtuvimos todo eso, inmediatamente:

- Registro de usuario con validación de correo
- Inicio de sesión seguro con hash de contraseñas (Argon2id—encriptación de grado militar)
- Restablecimiento de contraseña vía tokens seguros
- Gestión de sesiones
- Tokens de acceso de API con scopes y expiración
- Autenticación HMAC para endpoints de alta seguridad
- Permisos basados en grupos (admin, usuario, etc.)
- Limitación de tasa para prevenir ataques de fuerza bruta
- Comandos CLI para gestionar usuarios
- Migraciones de base de datos completas (crea todas las tablas necesarias)

**La configuración tomó 5 minutos.**

Después de la instalación:
1. Shield creó archivos de configuración para nosotros
2. Ejecutamos las migraciones para configurar las tablas de base de datos
3. Configuramos algunas opciones (como el tiempo de expiración de tokens)
4. La autenticación estaba lista para usar

**Ejemplo Real: Creando Un Endpoint de API Protegido**

Aquí está el código real de nuestro proyecto. No te preocupes si no entiendes cada símbolo—explicaremos:

```php
<?php

namespace App\Controllers\Api;

use CodeIgniter\RESTful\ResourceController;

class UserController extends ResourceController
{
    // Esto se conecta a nuestro UserModel para operaciones de base de datos
    protected $modelName = 'App\Models\UserModel';
    
    // Queremos respuestas JSON por defecto
    protected $format = 'json';

    /**
     * Obtener una lista de todos los usuarios
     * GET /api/users
     */
    public function index()
    {
        // Buscar todos los usuarios de la base de datos
        $users = $this->model->findAll();
        
        // Devolverlos como una respuesta JSON
        return $this->respond([
            'status' => 200,
            'data' => $users
        ]);
    }

    /**
     * Obtener un usuario específico por ID
     * GET /api/users/{id}
     */
    public function show($id = null)
    {
        // Intentar encontrar el usuario
        $user = $this->model->find($id);
        
        // Si no se encuentra el usuario, devolver error 404
        if (!$user) {
            return $this->failNotFound('Usuario no encontrado');
        }
        
        // Devolver los datos del usuario
        return $this->respond([
            'status' => 200,
            'data' => $user
        ]);
    }
}
```

Y para proteger este endpoint para que solo los usuarios conectados puedan acceder a él, agregamos una línea a nuestras rutas:

```php
// routes.php
$routes->group('api', ['filter' => 'tokens'], function($routes) {
    $routes->resource('users');
});
```

Ese `['filter' => 'tokens']` le dice a CodeIgniter: "Oye, antes de dejar que alguien acceda a estas rutas, verifica si tienen un token de API válido."

Shield maneja todo lo demás—verificando el token, asegurándose de que no esté expirado, cargando el usuario, haciéndolos disponibles en nuestro controlador.

**Este es el poder de Vibe Coding con buenas bibliotecas.** Escribimos quizás 20 líneas de código personalizado y obtuvimos un endpoint de API completamente funcional y seguro.

## El Puente Entre Tu API y el Mundo: Entendiendo CORS

Así que has construido tu API. Tienes la autenticación funcionando. Tus endpoints responden perfectamente cuando los pruebas desde tu propia computadora. Todo parece perfecto.

Entonces intentas conectar tu aplicación móvil—o la aplicación web de tu amigo—and de repente nada funciona. El navegador muestra mensajes de error en rojo. Tu app arroja misteriosas excepciones de "Error de Red". Empiezas a cuestionar todo lo que acabas de construir.

Bienvenido a una de las experiencias más frustrantes en el desarrollo de APIs. Nosotros hemos pasado por eso. Déjanos ahorrarte los tres días de confusión por los que pasamos.

### El Escenario Que Rompe El Corazón De Todos

Imagina esto: Acabas de terminar tu API. Estás orgulloso de ella. Abres tu navegador web, navegas a `http://localhost:8080/api/users`, y ves hermosos datos JSON fluyendo de vuelta. "¡Perfecto!" piensas.

Abres el código de tu aplicación móvil—o tal vez tienes un archivo HTML simple con algo de JavaScript—and escribes lo que parece ser el código más sencillo del mundo:

```javascript
fetch('http://localhost:8080/api/users')
  .then(response => response.json())
  .then(data => console.log(data));
```

Debería funcionar, ¿verdad? Estás pidiendo exactamente la misma URL, esperando exactamente los mismos datos. Pero en lugar de tu hermoso JSON, obtienes un error que se ve algo así:

> "El acceso a fetch en 'http://localhost:8080/api/users' desde el origen 'http://localhost:3000' ha sido bloqueado por la política de CORS."

O tal vez tu aplicación móvil simplemente falla silenciosamente, o muestra "Error de Red" sin ningún detalle útil.

¿Qué acaba de pasar? Tu API está funcionando perfectamente. Tu código se ve correcto. Sin embargo, los dos se niegan a hablarse. Es desesperante.

### La Regla de Seguridad Que Nadie Te Contó

Aquí está lo que realmente está pasando—and no es un bug, es una característica de seguridad que se agregó a los navegadores web hace años para protegerte a ti y a tus usuarios.

Imagina que has iniciado sesión en el sitio web de tu banco en una pestaña del navegador. Luego visitas otro sitio web—digamos que es un sitio de noticias aparentemente inocente. Sin ciertas protecciones, ese sitio de noticias podría incluir código JavaScript que haga solicitudes al sitio web de tu banco usando tu sesión de inicio de sesión existente. Podría potencialmente transferir dinero, cambiar tu dirección, o hacer todo tipo de cosas maliciosas usando tu sesión autenticada.

Eso sería catastrófico.

Así que los navegadores web implementaron una regla llamada la **Política del Mismo Origen**. Esta regla dice: "El código ejecutándose en un sitio web solo puede hacer solicitudes a ese mismo sitio web." Si estás en `miapp.com`, puedes hablar con `miapp.com/api/users` todo el día. Pero si intentas hablar con `banco.com` desde `miapp.com`, el navegador interviene y dice "No, no permitido."

Esta regla ha salvado a innumerables personas de ataques de scripting entre sitios y secuestro de sesiones. Es genuinamente importante.

Pero aquí está el problema: tu API y tu frontend son técnicamente diferentes "orígenes" (diferentes puertos, o diferentes dominios), así que el navegador los trata como sitios web diferentes y bloquea la comunicación.

### Entra CORS: El Permiso Para Solicitudes de Origen Cruzado

CORS significa **Cross-Origin Resource Sharing** (Compartición de Recursos de Origen Cruzado). Piénsalo como un sistema de permisos formal. Tu API puede decirle a los navegadores: "Está bien si estos sitios web específicos me hablan. Confío en ellos."

Sin configuración CORS, tu API es como una casa con todas las puertas cerradas. La seguridad es excelente, pero nadie puede visitar. Con CORS, puedes desbloquear puertas específicas para visitantes específicos mientras mantienes el resto de la casa segura.

La forma en que funciona es realmente bastante elegante. Cuando tu código JavaScript intenta hacer una solicitud a un origen diferente, el navegador primero envía lo que se llama una "solicitud preflight". Esto es básicamente el navegador preguntando a tu API: "Oye, este sitio web en el origen X quiere hablarte. ¿Está permitido?"

Tu API responde con encabezados CORS que dicen cosas como:
- "Sí, el origen X está permitido"
- "Pueden usar estos métodos HTTP: GET, POST, PUT, DELETE"
- "Pueden enviar estos encabezados: Content-Type, Authorization"
- "Pueden incluir credenciales como cookies si es necesario"

Solo después de recibir este permiso, el navegador envía realmente la solicitud real con tus datos.

### Por Qué Las Apps Móviles También Enfrentan Esto

Quizás estés pensando: "Pero estoy construyendo una app móvil, no un sitio web. ¿Por qué me importan las reglas de seguridad de los navegadores?"

Excelente pregunta. Las aplicaciones móviles modernas a menudo se construyen usando tecnologías web—React Native, Flutter, Ionic, o incluso solo vistas web embebidas. Estos frameworks usan los mismos motores de navegador subyacentes para hacer solicitudes HTTP. Así que aunque tu app se ejecuta en un teléfono, no en una ventana de navegador, se aplican las mismas reglas CORS porque la capa de red está basada en navegador.

Además, durante el desarrollo, probablemente estás probando tu app móvil en un navegador de todos modos (usando herramientas como simuladores basados en navegador). Y cuando eventualmente construyas un panel web para tus usuarios, definitivamente necesitarás CORS configurado.

La conclusión: CORS es innegociable para el desarrollo moderno de APIs. Necesitas configurarlo correctamente, y necesitas entender lo que estás haciendo para no abrir accidentalmente agujeros de seguridad.

### Cómo Configuramos CORS en CodeIgniter 4

CodeIgniter 4 en realidad hace esto relativamente sencillo una vez que sabes qué hacer. El framework incluye un módulo CORS que viene incorporado pero necesita ser habilitado y configurado.

Aquí está el proceso de decisión por el que pasamos:

**Primera decisión: ¿Qué orígenes debemos permitir?**

En producción, quieres ser muy específico. Si tu frontend se ejecuta en `https://miapp.com`, solo deberías permitir ese origen. No `http://miapp.com` (sin HTTPS), no `https://www.miapp.com` (con www), no comodines que permitirían que cualquier sitio web hable con tu API.

Para desarrollo, necesitábamos permitir múltiples orígenes porque:
- Nuestra app móvil ejecutándose en un simulador podría venir de `http://localhost:8100`
- Nuestro frontend web podría ejecutarse en `http://localhost:3000`
- Nuestras herramientas de prueba de API (como Postman o Insomnia) podrían no enviar un origen en absoluto

**Segunda decisión: ¿Qué métodos HTTP debemos soportar?**

Para una API REST, típicamente necesitas:
- `GET` para leer datos
- `POST` para crear datos
- `PUT` o `PATCH` para actualizar datos
- `DELETE` para eliminar datos
- `OPTIONS` para las solicitudes preflight (los navegadores envían esto automáticamente)

**Tercera decisión: ¿Qué encabezados debemos permitir?**

Como mínimo, necesitas:
- `Content-Type` (para poder enviar JSON)
- `Authorization` (para poder enviar tokens bearer)
- `X-Requested-With` (usado por muchas bibliotecas AJAX)

**Cuarta decisión: ¿Deberíamos permitir credenciales?**

Si estás usando cookies o autenticación basada en sesiones, necesitas permitir credenciales. Para APIs basadas en tokens (que es lo que usa Shield), técnicamente no necesitas cookies, pero permitir credenciales no hace daño y hace tu API más flexible para casos de uso futuros.

### La Configuración Que Realmente Funciona

Después de experimentar (y fallar múltiples veces), aquí está la configuración que funcionó para nosotros. Creamos un archivo de configuración CORS en `app/Config/Cors.php`:

```php
<?php

namespace Config;

use CodeIgniter\Config\BaseConfig;

class Cors extends BaseConfig
{
    // Durante el desarrollo, permitimos múltiples puertos localhost
    // En producción, esto debería ser tu dominio exacto
    public array $allowedOrigins = [
        'http://localhost:3000',     // Servidor de desarrollo React/Vue
        'http://localhost:8100',     // Apps Ionic/Cordova
        'http://localhost:8080',     // Otras pruebas locales
        'http://localhost',          // Desarrollo local general
    ];
    
    // Permitir todos los orígenes con un comodín (¡NO para producción!)
    // Solo usa esto para prototipado rápido, nunca en producción
    public bool $allowAnyOrigin = false;
    
    // Métodos HTTP que nuestra API soporta
    public array $allowedMethods = [
        'GET',
        'POST',
        'PUT',
        'DELETE',
        'OPTIONS',
        'PATCH'
    ];
    
    // Encabezados que el cliente puede enviar
    public array $allowedHeaders = [
        'Content-Type',
        'Authorization',
        'X-Requested-With',
        'Accept',
        'Origin'
    ];
    
    // Encabezados que el cliente puede leer de la respuesta
    public array $exposedHeaders = [];
    
    // Si permitir cookies/credenciales
    public bool $allowCredentials = true;
    
    // Cuánto tiempo los navegadores pueden cachear la respuesta preflight (en segundos)
    // 7200 = 2 horas, reduce las solicitudes preflight
    public int $maxAge = 7200;
}
```

Luego habilitamos el filtro CORS en `app/Config/Filters.php`:

```php
public array $aliases = [
    'csrf'     => CSRF::class,
    'toolbar'  => DebugToolbar::class,
    'honeypot' => Honeypot::class,
    'cors'     => \CodeIgniter\Filters\Cors::class, // Agregar esta línea
];

public array $globals = [
    'before' => [
        'cors', // Aplicar CORS a todas las rutas
        // ... otros filtros
    ],
    'after' => [
        // ...
    ],
];
```

### El Momento De La Verdad: Probando Tu Configuración CORS

Después de configurar CORS, necesitas probarlo correctamente. Aquí está lo que aprendimos:

**Probando desde un navegador:**
Abre la consola de desarrollador de tu navegador e intenta hacer una solicitud fetch a tu API desde un origen diferente. Deberías ver que la solicitud tiene éxito sin errores CORS.

**Probando desde curl:**
```bash
# Probar solicitud preflight
curl -X OPTIONS -H "Origin: http://localhost:3000" \
  -H "Access-Control-Request-Method: POST" \
  -H "Access-Control-Request-Headers: Content-Type" \
  -I http://localhost:8080/api/users

# Deberías ver encabezados como:
# Access-Control-Allow-Origin: http://localhost:3000
# Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS, PATCH
```

**Errores comunes que cometimos:**
1. Olvidar reiniciar el servidor después de cambiar la configuración
2. Usar `*` (comodín) para orígenes en producción (¡riesgo de seguridad!)
3. No incluir el método `OPTIONS` en los métodos permitidos
4. Olvidar permitir el encabezado `Authorization` (rompe la autenticación por token)
5. Probar desde URLs `file://` (los navegadores tratan estos diferente)

### La Lista De Verificación Para Producción

Cuando estés listo para desplegar a producción, actualiza tu configuración CORS:

```php
public array $allowedOrigins = [
    'https://miapp.com',      // Tu dominio de producción
    'https://www.miapp.com',  // Incluir variante www
    'https://admin.miapp.com', // Si tienes un panel de administración separado
];

public bool $allowAnyOrigin = false; // ¡Nunca true en producción!
```

**¿Por qué ser tan restrictivo?**

Imagina que permites cualquier origen (`*`) en producción. Ahora cualquier sitio web en internet puede hacer solicitudes a tu API desde los navegadores de sus usuarios. Podrían:
- Recolectar datos de tus endpoints públicos
- Intentar fuerza bruta en la autenticación usando tu endpoint de login
- Inundar tu API con solicitudes de miles de usuarios

Al restringir a orígenes específicos, te aseguras de que solo tus aplicaciones legítimas puedan comunicarse con tu API.

### Por Qué Esto Importa Más De Lo Que Crees

Los errores CORS a menudo son el primer "muro" real que enfrentan los desarrolladores de APIs principiantes. Has construido algo que funciona perfectamente en aislamiento, pero en el momento en que intentas integrarlo con un frontend real, todo se rompe. Es desmoralizante.

Pero aquí está lo que hemos aprendido: CORS no es solo un obstáculo técnico que superar. Es una parte fundamental de la arquitectura de seguridad web. Entender CORS significa entender cómo funciona la seguridad web. Significa pensar sobre qué aplicaciones deberían tener acceso a tus datos y cuáles no.

Cuando configuras CORS correctamente, no solo estás arreglando un error—estás tomando una decisión de seguridad consciente sobre quién puede hablar con tu API y cómo. Esa es la diferencia entre alguien que "hizo que funcionara" y alguien que entiende lo que está construyendo.

Para LaunchPad API, la configuración CORS fue el puente que conectó nuestro backend con el mundo exterior. Transformó nuestra API de una isla solitaria en un servicio que podía impulsar apps web, apps móviles, e integraciones de terceros. Y una vez que lo entendimos, ya no era aterrador—era solo otra capa de seguridad que controlábamos.

## Día 5: Llevando Tu API a Internet—Pasos Reales de Despliegue Que Realmente Funcionan

Así que has construido tu API. La has probado localmente. Todo funciona perfectamente en tu computadora. Ahora llega el momento de la verdad: ponerla en internet donde la gente real pueda usarla.

Aquí es donde muchas guías te dejan colgando. Dicen "despliega a producción" como si fuera un botón que presionas, y luego pasan al siguiente tema. Pero aquí está la realidad: el despliegue es una serie de decisiones y pasos que pueden hacer o deshacer el lanzamiento de tu proyecto. Hazlo mal, y pasarás tu primera semana peleando con problemas de configuración en lugar de celebrar tu lanzamiento.

Aprendimos esto de la manera difícil. Nuestro primer intento de despliegue fue... llamémoslo "educativo." Rompimos cosas. Tuvimos que revertir. Nos quedamos hasta las 3 de la mañana preguntándonos por qué algo que funcionaba perfectamente en nuestra laptop se negaba a funcionar en el servidor. Pero lo superamos, y ahora te vamos a ahorrar ese dolor.

### El Cambio de Mentalidad: De "Funciona en Mi Máquina" a "Funciona en Todas Partes"

Antes de sumergirnos en los pasos específicos, hablemos del desafío fundamental del despliegue: tu entorno de producción es diferente de tu entorno de desarrollo. Diferente software de servidor, diferentes rutas de archivos, diferentes reglas de seguridad, diferente todo.

Piénsalo así: has estado practicando una canción con tu guitarra acústica en tu habitación. Ahora la estás interpretando en un escenario con una banda completa, sistema de sonido profesional y una audiencia en vivo. La canción es la misma, pero todo lo que la rodea ha cambiado.

Tu trabajo durante el despliegue no es solo mover archivos de un lugar a otro. Es adaptar tu aplicación a su nuevo hogar manteniendo intacta la funcionalidad central. Esto significa entender qué necesita cambiar (configuración) y qué debe permanecer exactamente igual (tu lógica de código).

### Por Qué Elegimos Hosting Compartido (Y Por Qué Tú Probablemente También Deberías)

¿Recuerdas cuando hablamos de las ventajas de PHP? Aquí es donde realmente paga dividendos. Mientras los desarrolladores que usan Node.js o Python están luchando con la configuración de VPS, administración de servidores y pipelines de despliegue, tú vas a subir algunos archivos y listo.

**Pero seamos claros sobre lo que realmente significa el hosting compartido:**

El hosting compartido es como alquilar un departamento en un edificio grande. Obtienes tu propio espacio (espacio en disco, base de datos, cuentas de correo), pero estás compartiendo la infraestructura del edificio (el hardware del servidor, conexión a internet, sistemas de seguridad) con otros inquilinos. La administración del edificio (tu compañía de hosting) se encarga del mantenimiento, actualizaciones de seguridad y mantener todo funcionando.

**Aquí está por qué esto es perfecto para LaunchPad API:**

1. **Costo**: $3-10 por mes versus $20-50+ por un VPS
2. **Simplicidad**: No se requiere administración de servidores
3. **Soporte**: La mayoría de los hosts compartidos tienen soporte 24/7 para problemas básicos
4. **Características**: Usualmente obtienes correo, bases de datos, certificados SSL y más incluidos
5. **Escalabilidad**: Cuando superes el hosting compartido, tendrás ingresos para pagar mejores opciones

**Las compensaciones:**
- No tienes acceso root (no puedes instalar software arbitrario)
- El rendimiento puede variar según lo que otros sitios en el servidor estén haciendo
- Estás limitado a lo que el host proporciona (versiones de PHP, extensiones, etc.)

Para una API nueva con cero usuarios, estas compensaciones son completamente aceptables. No vas a alcanzar los límites de rendimiento con tus primeros cien usuarios. Y para cuando lo hagas, tendrás los ingresos y conocimientos para actualizar.

### Paso 1: Elegir Tu Proveedor de Hosting (La Decisión Que Importa Más De Lo Que Piensas)

Hay cientos de compañías de hosting compartido. Aquí te decimos cómo elegir sin volverte loco:

**Lo que realmente necesitas:**
1. PHP 8.1 o superior (8.2+ preferido)
2. MySQL o MariaDB (ambos funcionan bien)
3. cPanel o panel de control similar (hace la administración más fácil)
4. Certificado SSL gratuito (esencial para HTTPS)
5. Acceso FTP o SFTP (para subir archivos)
6. phpMyAdmin (para administrar tu base de datos visualmente)
7. Soporte razonable (chat 24/7 es ideal)

**Opciones populares que funcionan bien:**
- **Namecheap**: Barato, confiable, bueno para principiantes
- **Hostinger**: Buen rendimiento, asequible, interfaz moderna
- **Bluehost**: Popular, amigable con WordPress (lo que significa amigable con PHP)
- **SiteGround**: Excelente soporte, un poco más caro pero vale la pena por la tranquilidad
- **A2 Hosting**: Amigable con desarrolladores, buen rendimiento

**Lo que elegimos y por qué:**
Elegimos Namecheap para nuestro primer despliegue. No porque sea el mejor en cada categoría, sino porque cumplió todas nuestras casillas a un precio ($3.88/mes) que hizo fácil decir que sí. Su interfaz de cPanel es estándar, su soporte es decente, y no te cobran por cada característica básica.

**El proceso de decisión:**
- Miramos más de 10 hosts
- Eliminamos cualquiera sin soporte para PHP 8.1+
- Eliminamos cualquiera que cobrara extra por certificados SSL
- Elegimos la opción más barata que cumplió nuestros requisitos técnicos
- Planeamos actualizar más tarde si era necesario

**¿Reversible?** Absolutamente. Si tu host decepciona, puedes mover todo tu sitio en unas pocas horas una vez que conoces el proceso. No pienses demasiado en esta decisión.

### Paso 2: Preparando Tu Aplicación para el Mundo Real

Antes de subir nada, necesitas hacer algunos cambios a tu código. Estos no son opcionales—son la diferencia entre una API que funciona y una rota.

**El Baile de la Configuración del Entorno:**

¿Recuerdas tu archivo `.env`? ¿El que tiene todos tus secretos? Ese archivo vive solo en tu máquina local. Nunca lo subas. Pero tu servidor de producción necesita esos mismos valores de configuración—solo con valores diferentes (base de datos de producción, claves API de producción, etc.).

Aquí está el proceso:

1. **Crea un archivo `.env` de producción localmente** (tampoco lo confirmes):
   ```bash
   # .env.production (esto es solo una plantilla, renómbralo a .env en el servidor)
   CI_ENVIRONMENT = production
   app.baseURL = 'https://tudominio.com'
   
   # Base de datos de producción (obtendrás estos de tu panel de control de hosting)
   database.default.hostname = localhost
   database.default.database = tuhosting_usuario_dbname
   database.default.username = tuhosting_usuario
   database.default.password = tu_contraseña_producción
   database.default.DBDriver = MySQLi
   ```

2. **Actualiza tus configuraciones de producción:**
   ```bash
   # En .env.production
   CI_ENVIRONMENT = production
   app.baseURL = 'https://tudominio.com'
   
   # Apaga el debugging en producción
   CI_DEBUG = false
   
   # Configura el logging de errores
   logger.threshold = 4
   ```

3. **Establece los permisos de archivos apropiados localmente** (para que se transfieran correctamente):
   Tu carpeta `writable/` necesita ser escribible por el servidor web. Esto se maneja diferente en diferentes hosts, pero generalmente:
   - Carpetas: 755 (rwxr-xr-x)
   - Archivos: 644 (rw-r--r--)
   - Carpeta `writable/`: 775 (rwxrwxr-x)

**Por qué esto importa:**
- El modo producción deshabilita la salida de depuración (seguridad)
- Las credenciales de base de datos de producción son diferentes (seguridad)
- Los permisos apropiados previenen errores de "permiso denegado"
- Tu URL base afecta cómo funcionan los enlaces y redirecciones

**Error común que evitar:**
No copies simplemente tu archivo `.env` local a producción. Tu base de datos local se llama algo como `ci_api_db`. Tu base de datos de producción se llamará algo como `namecheap_usuario_cidb` con un usuario y contraseña diferentes. Usar credenciales locales en producción fallará.

### Paso 3: Configurando Tu Base de Datos de Producción

Esta es la parte que intimida a la gente, pero en realidad es sencilla una vez que la ves hacerse.

**Creando la Base de Datos:**

1. **Inicia sesión en tu panel de control de hosting** (cPanel, Plesk, o lo que use tu host)
2. **Encuentra "MySQL Databases" o "Asistente de Bases de Datos"**
3. **Crea una nueva base de datos**:
   - Ponle un nombre descriptivo (tuapp_db)
   - El host usualmente le agrega un prefijo con tu usuario (usuario_tuapp_db)
4. **Crea un usuario de base de datos**:
   - Elige una contraseña fuerte (usa un generador)
   - Guarda esta contraseña en algún lugar seguro
5. **Agrega el usuario a la base de datos** con "Todos los Privilegios"

**Moviendo Tus Datos Locales a Producción:**

Tienes dos opciones aquí, y recomendamos la segunda para principiantes:

**Opción 1: Exportar e Importar (Más Control):**
1. Exporta tu base de datos local (usando phpMyAdmin, TablePlus o línea de comandos):
   ```bash
   # Si tienes MySQL localmente
   mysqldump -u root -p ci_api_db > backup.sql
   ```
2. Abre el phpMyAdmin de tu hosting
3. Selecciona tu base de datos de producción
4. Haz clic en "Importar" y sube tu archivo backup.sql

**Opción 2: Ejecutar Migraciones Fresco (Más Limpio):**
1. No exportes datos del desarrollo local
2. Sube tu código (siguiente paso)
3. Conéctate a tu servidor vía SSH o usa la terminal del hosting
4. Ejecuta las migraciones frescas en producción:
   ```bash
   cd /ruta/a/tu/app
   php spark migrate --all
   ```

**Por qué preferimos la Opción 2:**
- Estructura de base de datos más limpia
- Sin datos de prueba contaminando la producción
- Asegura que las migraciones realmente funcionan
- Más fácil de reproducir si necesitas configurar staging más tarde

**Los Únicos Datos Que Quizás Quieras Migrar:**
Si creaste usuarios administradores o datos de configuración esencial localmente, exporta solo esas tablas o filas específicas. No traigas usuarios de prueba, datos dummy o tus sesiones personales de prueba.

### Paso 4: Subiendo Tus Archivos (El Momento de la Verdad)

Ahora estás listo para mover tu código al servidor. Tienes algunas opciones aquí.

**Entendiendo la Estructura de Archivos de Tu Hosting:**

Los hosts compartidos típicamente tienen una estructura como esta:
```
/home/usuario/           <- Tu directorio home (empiezas aquí en FTP)
├── public_html/          <- Raíz web (archivos aquí son públicamente accesibles)
├── mail/                 <- Almacenamiento de correo
├── logs/                 <- Logs del servidor
└── .cpanel/              <- Cosas del panel de control
```

La carpeta `public_html/` es crucial. Los archivos aquí son accesibles para cualquiera en internet. Los archivos fuera de ella (como tu archivo `.env`, si lo pones en el lugar correcto) están protegidos.

**Método de Subida 1: FTP/SFTP (Más Fácil para Principiantes):**

1. **Descarga un cliente FTP** (FileZilla es gratis y funciona genial)
2. **Obtén tus credenciales FTP de tu panel de control de hosting**
3. **Conéctate a tu servidor**
4. **Navega a la carpeta public_html**
5. **Sube tus archivos**

**La Manera de CodeIgniter 4:**
CI4 tiene una estructura específica. Tu carpeta `public/` necesita mapear a la `public_html/` del host. Aquí está cómo:

1. Sube TODO EXCEPTO la carpeta `public/` a `/home/usuario/ci_api/`
2. Sube el CONTENIDO de tu carpeta `public/` a `/home/usuario/public_html/`
3. Edita `/home/usuario/public_html/index.php` para que apunte al lugar correcto:
   ```php
   // Cambia esta línea
   $pathsPath = FCPATH . '../app/Config/Paths.php';
   // A esto (ajusta la ruta según sea necesario)
   $pathsPath = '/home/usuario/ci_api/app/Config/Paths.php';
   ```

**Método de Subida 2: Despliegue con Git (Si Tu Host Lo Soporta):**

Algunos hosts te permiten desplegar vía Git. Esto es más limpio pero requiere acceso SSH:
```bash
# En tu servidor
 git clone https://github.com/tuusuario/turepo.git
 cd turepo
 composer install --no-dev
 php spark migrate
```

**Método de Subida 3: Administrador de Archivos (Sin Software Requerido):**

La mayoría de los paneles de control de hosting tienen un administrador de archivos basado en web. Puedes:
1. Comprimir tu proyecto localmente
2. Subir el zip vía el administrador de archivos
3. Extraerlo en el servidor
4. Mover los archivos a los lugares correctos

**Lo que hicimos:**
Usamos FTP con FileZilla para nuestro primer despliegue. Es visual, puedes ver lo que está pasando, y si algo falla, sabes exactamente dónde. A medida que nos sentimos más cómodos, cambiamos al despliegue con Git para actualizaciones.

**Consejo profesional:** La subida toma un tiempo. Iníciala, toma un café, y vuelve. No te sientes ahí viendo las barras de progreso.

### Paso 5: Configurando Tu Dominio (Haciéndolo Oficial)

Si compraste tu dominio de la misma compañía que tu hosting, esto es automático. Si no, necesitas conectarlos.

**Cómo Funcionan Realmente los Nombres de Dominio (La Versión Simple):**

Cuando alguien escribe `tudominio.com` en su navegador:
1. Su computadora le pregunta a un servidor DNS "¿Cuál es la dirección IP de tudominio.com?"
2. El servidor DNS la busca y devuelve algo como `192.168.1.100`
3. Su navegador se conecta a esa dirección IP
4. Tu servidor de hosting dice "¡Hola! ¿Quieres tudominio.com? Aquí está el sitio web."

**Configurando Tus Nameservers:**

1. **Encuentra los nameservers de tu hosting** (usualmente en tu correo de bienvenida o panel de control)
   - Se ven así: `ns1.tuhost.com` y `ns2.tuhost.com`
2. **Inicia sesión donde compraste tu dominio** (Namecheap, GoDaddy, Google Domains, etc.)
3. **Encuentra la sección "Nameservers" o "DNS"**
4. **Cambia los nameservers a los de tu host**
5. **Espera** (esto puede tomar desde 15 minutos hasta 48 horas en propagarse)

**¿Por qué toma tanto tiempo?**
El DNS es como una gigantesca guía telefónica distribuida. Cuando cambias los nameservers, le estás diciendo a los operadores de la guía telefónica que actualicen sus registros. Algunos verifican actualizaciones frecuentemente (minutos), otros menos frecuentemente (horas o días). Ten paciencia.

**Probando si está funcionando:**
```bash
# Usa dig o nslookup para verificar
 dig tudominio.com
 
# O simplemente visítalo en un navegador
# ¡Si ves tu sitio, está funcionando!
```

**La Lista de Verificación "Han Pasado 2 Horas y Nada Funciona":**
1. Limpia la caché de tu navegador (Ctrl+Shift+R o Cmd+Shift+R)
2. Prueba un navegador diferente
3. Prueba acceder desde tu teléfono (red diferente)
4. Usa una herramienta como https://dnschecker.org/ para ver si se ha propagado globalmente
5. Verifica que no te equivocaste al escribir los nameservers

### Paso 6: Configurando SSL (El Ícono de Candado Que Te Hace Ver Profesional)

HTTPS ya no es opcional. Los navegadores advierten a los usuarios sobre sitios "inseguros". Google posiciona mejor los sitios HTTPS. Necesitas SSL.

**Las Buenas Noticias:**
La mayoría de los hosts compartidos ofrecen certificados SSL gratuitos a través de Let's Encrypt. La configuración usualmente es:

1. **Inicia sesión en tu panel de control de hosting**
2. **Encuentra "SSL/TLS" o "Seguridad" o "Let's Encrypt"**
3. **Haz clic en "Instalar" o "Habilitar"**
4. **Selecciona tu dominio**
5. **Espera 5-10 minutos**

**Lo que pasa detrás de escena:**
La compañía de hosting solicita un certificado de Let's Encrypt (una organización sin fines de lucro que proporciona SSL gratuito). Let's Encrypt verifica que controlas el dominio revisando tus nameservers. Una vez verificado, emiten el certificado. Tu host lo instala automáticamente.

**Después de que SSL está activo:**
1. Actualiza tu archivo `.env`:
   ```bash
   app.baseURL = 'https://tudominio.com'
   ```
2. Prueba visitando `https://tudominio.com` (nota el https://)
3. Deberías ver un ícono de candado en tu navegador

**Problemas Comunes de SSL:**
- **Advertencias de contenido mixto**: Estás cargando recursos HTTP en una página HTTPS. Actualiza todas tus URLs para usar https://
- **Certificado no confiado**: El certificado todavía se está propagando. Espera una hora e intenta de nuevo.
- **Desajuste de dominio**: El certificado es para www.tudominio.com pero estás accediendo a tudominio.com (o viceversa). La mayoría de los hosts arreglan esto automáticamente, pero a veces necesitas especificar ambos.

### Paso 7: Las Pruebas Finales (Antes de Contarle a Nadie)

No anuncies tu lanzamiento todavía. Prueba todo primero.

**La Lista de Verificación de Prueba Básica:**

1. **La página de inicio carga**: Visita `https://tudominio.com`—¿ves algo? ¿Algo?
2. **Los endpoints de API funcionan**: Prueba un endpoint GET simple
   ```bash
   curl https://tudominio.com/api/users
   ```
3. **La autenticación funciona**: Intenta registrar un nuevo usuario
4. **La base de datos está conectada**: ¿Puedes crear/leer datos?
5. **El manejo de errores funciona**: Intenta acceder a un endpoint inexistente. ¿Obtienes un 404 apropiado o un error del servidor?
6. **HTTPS es forzado**: Intenta visitar `http://tudominio.com` (sin la s). ¿Redirige a https?

**Problemas Comunes del Primer Despliegue:**

**"Error 500 del Servidor Interno"**
- Verifica que tu archivo `.env` existe y tiene valores correctos
- Verifica los permisos de archivos (especialmente la carpeta `writable/`)
- Verifica los logs de error de tu host (en cPanel)
- Habilita temporalmente el logging de errores de CI4 para ver el error real:
  ```bash
  CI_DEBUG = true  # ¡Solo temporalmente!
  ```

**"Falló la conexión a la base de datos"**
- Credenciales de base de datos incorrectas en `.env`
- El usuario de la base de datos no tiene privilegios apropiados
- La base de datos no existe (¿la creaste en cPanel?)
- Hostname incorrecto (algunos hosts usan algo diferente de "localhost")

**"404 No Encontrado en todas las rutas"**
- Tu archivo `.htaccess` no está subido o está mal
- mod_rewrite no está habilitado (pregunta a tu host)
- Los archivos de tu carpeta `public/` están en el lugar equivocado

**"Errores de CORS"**
- Actualiza tu configuración de `Cors.php` para permitir tu dominio de producción
- Reinicia tu servidor (algunas configs se cachean)

### Paso 8: Monitoreo y Mantenimiento (Manteniéndolo Vivo)

¡Tu API está en vivo! Pero el trabajo no ha terminado. Necesitas vigilarlo.

**Qué Monitorear:**

1. **Tiempo de actividad**: ¿El servidor está respondiendo? (La mayoría de los hosts proporcionan esto)
2. **Logs de error**: ¿Hay errores que no atrapaste en las pruebas?
3. **Rendimiento**: ¿Es lento? (Usa herramientas como GTmetrix o Pingdom)
4. **Seguridad**: ¿Alguna actividad sospechosa?

**Dónde Encontrar Logs:**

La mayoría de los hosts compartidos proporcionan:
- **Logs de error**: cPanel → Métricas → Errores
- **Logs de acceso**: cPanel → Métricas → Acceso Directo
- **Logs de aplicación**: En tu carpeta `writable/logs/`

**Configurando Monitoreo Básico:**

Herramientas gratuitas que funcionan genial:
- **UptimeRobot**: Verifica si tu sitio está arriba cada 5 minutos. El plan gratuito cubre 50 monitores.
- **Google Search Console**: Te dice sobre problemas de indexación y problemas de seguridad
- **Las estadísticas integradas de tu hosting**: Usualmente encontradas en cPanel

**Estrategia de Respaldos (No Te Lo Saltes):**

La mayoría de los hosts hacen respaldos automatizados, pero tú también deberías:

1. **Respaldos de base de datos**: Exporta tu base de datos semanalmente
2. **Respaldos de archivos**: Descarga tu sitio completo mensualmente
3. **Control de versiones**: Mantén tu código en Git (ya deberías estar haciendo esto)

**Configurando Respaldos Automatizados:**
Muchos hosts ofrecen servicios de respaldo automatizados (a veces pagados). Si quieres hacerlo tú mismo:

```bash
# Agrega esto a tu máquina local como un cron job semanal
 mysqldump -h tuhost.com -u usuario -p'contraseña' nombre_base_datos > backup_$(date +%Y%m%d).sql
```

### El Día del Lanzamiento

Has hecho el trabajo. Ahora es momento de activar el interruptor.

**El Enfoque de Lanzamiento Suave:**
En lugar de anunciar al mundo inmediatamente, prueba esto:

1. **Despliega un día antes**: Date tiempo para arreglar problemas
2. **Prueba con un grupo pequeño**: Pide a 2-3 amigos que lo prueben
3. **Monitorea por 24 horas**: Asegúrate de que sea estable
4. **Luego anuncia**: Comparte con tu audiencia real

**La Lista de Verificación del Día del Lanzamiento:**
- [ ] El sitio carga correctamente
- [ ] El certificado SSL está activo
- [ ] Los endpoints de API responden
- [ ] La autenticación funciona
- [ ] La app móvil (si aplica) se conecta exitosamente
- [ ] El manejo de errores funciona
- [ ] La base de datos está guardando datos
- [ ] Los respaldos están configurados
- [ ] El monitoreo está activo
- [ ] La documentación está actualizada con URLs de producción

**Cuando Las Cosas Salen Mal (Y Podrían):**

Aquí está la verdad: algo se romperá. Quizás no hoy, quizás no esta semana, pero eventualmente. La diferencia entre un lanzamiento estresante y uno tranquilo es la preparación.

**Ten esto listo:**
1. **Plan de rollback**: Saber cómo revertir a la versión anterior rápidamente
2. **Contacto de soporte**: El número de soporte o chat de tu host
3. **Acceso a logs de error**: Saber dónde encontrarlos
4. **Contacto de emergencia**: Alguien técnico que pueda ayudar si estás atascado

### Decisión: Hosting Compartido vs. VPS para Despliegue Inicial

**Fecha**: 17 de febrero de 2026
**Contexto**: Eligiendo infraestructura de despliegue para LaunchPad API

**Opciones Consideradas**:
1. Hosting compartido ($3-10/mes)
2. VPS como DigitalOcean o Linode ($20-50/mes)
3. Plataforma-como-Servicio como Heroku (plan gratuito disponible, pero escala caro)
4. Hosting en la nube como AWS/GCP (excesivo y complejo)

**Decisión**: Hosting compartido para el lanzamiento inicial, con criterios claros para cuándo actualizar

**Razonamiento**:
- **Hosting compartido**: Perfecto para 0-1000 usuarios. Sin administración de servidores. Barato. Fácil.
- **VPS**: Mejor rendimiento y control, pero requiere conocimientos de administración Linux que aún no tenemos
- **PaaS**: Conveniente pero se vuelve caro rápido ($25+/mes para cargas de trabajo de producción)
- **Nube**: Excesivo masivo. Pasaríamos más tiempo aprendiendo AWS que construyendo nuestro producto.

**Disparadores de actualización** (cuándo consideraremos mudarnos a VPS):
- Alcanzando consistentemente los límites de recursos
- Necesidad de software de servidor personalizado
- Ingresos justifican el costo extra
- Tenemos tiempo para aprender administración de servidores

**Compensaciones**:
- **Pros**: Asequible, cero mantenimiento, configuración rápida, perfecto para fase de validación
- **Contras**: Control limitado, recursos compartidos, no puedes instalar software arbitrario

**¿Reversible?** Sí. Moverse de hosting compartido a VPS es un camino de crecimiento común. CI4 lo hace relativamente indoloro ya que el código de la aplicación no cambia—solo la configuración del servidor.

### Tu API Está en Vivo. ¿Y Ahora Qué?

El despliegue no es el final del viaje—es el principio. Tu API es ahora algo vivo que necesita cuidado y alimentación.

Pero aquí está lo hermoso: has construido algo real. Tomaste una idea, aprendiste la tecnología, escribiste el código, y lo pusiste en internet donde cualquiera puede usarlo. Eso no es trivial. Eso es impresionante.

El proceso de despliegue por el que acabamos de caminar es algo que muchos desarrolladores nunca entienden completamente. Usan plataformas automatizadas que ocultan la complejidad, y luego entran en pánico cuando algo sale mal. Tú ahora entiendes cada pieza: los archivos, la base de datos, el dominio, el SSL, todo el stack.

Ese conocimiento es poder. Significa que cuando algo se rompe, sabes dónde buscar. Cuando necesites escalar, sabes qué actualizar. Cuando alguien pregunte "¿cómo funciona tu API?" puedes explicarlo desde los cimientos.

Bienvenido al mundo de producción. Tu API está en vivo. Tus usuarios están esperando. Ve a hacer algo asombroso.

## El Arte de Hablarle a la IA: Una Guía Práctica de Prompt Engineering

![Portada LaunchPad API](docs-graphics/cover_horizontal_es.png)

Aquí hay algo que nos tomó tiempo descubrir: **La forma en que le pides ayuda a la IA importa tanto como tener buena documentación.** Es como la diferencia entre pedirle a un contratista calificado "Constrúyeme una casa" versus "Constrúyeme una casa de tres dormitorios con plano abierto, usando materiales sostenibles, diseñada para una familia con niños pequeños." La misma persona, resultados completamente diferentes.

Cuando comenzamos a usar asistentes de IA, cometimos un error clásico. Escribíamos cosas como:
- "Haz que esto funcione"
- "Arregla este código"
- "¿Cómo hago autenticación?"

Y obteníamos... resultados más o menos. A veces el código funcionaba. A veces estaba desactualizado. A veces era técnicamente correcto pero completamente equivocado para nuestra situación específica. Pasamos horas depurando problemas que podrían haberse evitado si simplemente hubiéramos hecho mejores preguntas.

### Por Qué el Prompt Engineering No Es Solo "Ser Específico"

Quizás pienses que el prompt engineering significa usar términos técnicos elegantes o escribir ensayos a la IA. No lo es. Se trata de darle contexto a la IA para que te pueda dar respuestas relevantes en lugar de genéricas.

Piénsalo así: Si entras a un restaurante y dices "Tengo hambre", el mesero no tiene idea si traerte una ensalada o un bistec. Pero si dices "Tengo hambre, soy vegetariano, me encanta la comida picante y tengo prisa", ahora pueden recomendarte el platillo perfecto.

La IA funciona de la misma manera. Cuantos más contexto proporciones sobre:
- Qué estás intentando lograr (el objetivo)
- Qué restricciones tienes (los límites)
- Qué ya has intentado (la historia)
- Cómo se ve tu proyecto (el contexto)

...mejor podrá ayudarte la IA.

### El Framework Que Usamos para Cada Prompt

Después de semanas de prueba y error, desarrollamos un framework simple que mejoró dramáticamente la calidad de la asistencia de IA. Lo llamamos el **Framework ACTS** (porque todo acrónimo necesita un nombre elegante, aparentemente):

**A - Asignar un Rol**
**C - Clarificar el Contexto**
**T - Especificar la Tarea**
**S - Establecer los Estándares**

Permíteme desglosar qué significa cada uno de estos con ejemplos reales de nuestro proyecto.

#### A - Asignar un Rol

Este es el ingrediente mágico que la mayoría de la gente omite. Cuando le dices a la IA que "actúe como" algo específico, cambia toda su perspectiva y base de conocimientos para servir ese rol.

**En lugar de:** "¿Cómo creo un endpoint de API?"

**Di:** "Actúa como un desarrollador senior de CodeIgniter 4 con 10 años de experiencia construyendo APIs REST seguras. Estoy construyendo un endpoint para registro de usuarios."

¿Ves la diferencia? El primer prompt te da una respuesta genérica que podría funcionar en cualquier framework. El segundo prompt le dice a la IA que use su conocimiento de CodeIgniter específicamente, mejores prácticas de API REST y consideraciones de seguridad—todas las cosas que nos importan profundamente.

**Otros ejemplos de roles que usamos:**
- "Actúa como un experto en seguridad auditando este código de autenticación"
- "Actúa como un ingeniero de DevOps revisando nuestra estrategia de despliegue"
- "Actúa como un escritor técnico documentando esta API para desarrolladores móviles"
- "Actúa como un contribuyente principal de CodeIgniter 4 revisando esta implementación"

Cada rol activa diferentes conocimientos y prioridades. Un "experto en seguridad" señalará vulnerabilidades que un "desarrollador" podría pasar por alto. Un "escritor técnico" sugerirá mensajes de error más claros. El rol da forma a la respuesta.

#### C - Clarificar el Contexto

Aquí es donde le cuentas a la IA sobre tu situación específica. Recuerda, la IA no sabe que estás usando CodeIgniter 4, Shield para autenticación y MySQL para tu base de datos—a menos que se lo digas.

**En lugar de:** "Necesito proteger esta ruta"

**Di:** "Estoy trabajando en un proyecto de CodeIgniter 4 usando Shield para autenticación. La estructura del proyecto sigue las convenciones de CI4 con controladores en app/Controllers/Api/, modelos en app/Models/, y rutas definidas en app/Config/Routes.php. Necesito proteger un endpoint de API para que solo usuarios autenticados con tokens bearer válidos puedan acceder a él."

Ahora la IA sabe:
- El framework (CodeIgniter 4)
- La biblioteca de autenticación (Shield)
- La estructura de directorios
- El mecanismo específico de protección (tokens bearer)

Puede darte código exacto que se ajuste a tu proyecto en lugar de ejemplos genéricos de middleware de Laravel o Express.js.

**Contexto clave para incluir siempre:**
- Tu stack tecnológico (framework, bibliotecas, base de datos)
- La estructura de tu proyecto (dónde viven los archivos)
- Tu método de autenticación (sesión, token, JWT, etc.)
- Qué ya has intentado (si estás depurando)
- El archivo o código específico con el que estás trabajando

#### T - Especificar la Tarea

Sé cristalino sobre qué quieres que haga la IA. Las solicitudes vagas obtienen respuestas vagas.

**En lugar de:** "Haz esto mejor"

**Di:** "Revisa este método del controlador y:
1. Identifica cualquier vulnerabilidad de seguridad
2. Sugiere mejoras en validación de entrada
3. Recomienda mejor manejo de errores
4. Muéstrame el código mejorado con comentarios explicando cada cambio"

Ahora la IA tiene una lista de verificación. Sabe exactamente qué significa "mejor" en este contexto.

**Consejos para especificar tareas:**
- Usa verbos de acción: "Revisa," "Refactoriza," "Explica," "Compara," "Implementa"
- Sé específico sobre los entregables: "código," "explicación," "lista de pros/contras"
- Establece límites: "Manténlo simple" o "Prioriza la seguridad sobre la brevedad"
- Pide múltiples opciones: "Dame dos enfoques y explica cuándo usar cada uno"

#### S - Establecer los Estándares

Aquí es donde defines qué se ve "bueno" para tu proyecto. Diferentes equipos tienen diferentes prioridades—algunos se preocupan por el rendimiento, otros por la legibilidad, otros por la seguridad sobre todo lo demás.

**En lugar de:** "Escribe este código"

**Di:** "Escribe este código siguiendo estos estándares:
- Prioriza la seguridad y validación de entrada sobre la brevedad del código
- Sigue las convenciones y estilo de código de CodeIgniter 4
- Incluye comentarios PHPDoc comprehensivos explicando parámetros y valores de retorno
- Maneja todos los casos de error elegantemente con códigos de estado HTTP apropiados
- Usa type hints donde sea apropiado para PHP 8.2+
- No uses bibliotecas externas a menos que sea absolutamente necesario"

Ahora la IA conoce tus valores. No te dará líneas ingeniosas imposibles de mantener. No omitirá el manejo de errores para hacer el código más corto. Entiende tu definición de calidad.

**Estándares que comúnmente establecemos:**
- "La seguridad es más importante que la conveniencia"
- "Explica tu razonamiento para cada decisión significativa"
- "Escribe código que un desarrollador junior pueda entender"
- "Considera casos límite y validación"
- "Sigue los patrones existentes en nuestra base de código"

### Ejemplos Reales de Nuestro Proyecto

Déjame mostrarte prompts reales que usamos mientras construíamos LaunchPad API. Estos no son teóricos—están copiados directamente de nuestro historial de chat (con información sensible removida).

#### Ejemplo 1: Creando un Nuevo Endpoint

**Nuestro prompt:**
```
Actúa como un desarrollador senior de CodeIgniter 4 especializado en diseño de APIs REST.

Contexto:
- Estamos construyendo LaunchPad API usando CodeIgniter 4.5.x con autenticación Shield
- Nuestros controladores de API están en app/Controllers/Api/ y extienden ResourceController
- Estamos usando MySQL con el Query Builder de CI4
- El proyecto sigue el autoloading PSR-4 y las convenciones de CI4

Tarea:
Crea un método de controlador que maneje solicitudes GET para recuperar una lista paginada de usuarios. El endpoint debe:
1. Requerir autenticación (tokens bearer vía Shield)
2. Soportar parámetros de paginación (page, per_page)
3. Permitir filtrado opcional por estado de usuario (active, inactive)
4. Devolver una respuesta JSON con códigos de estado HTTP apropiados
5. Incluir metadata sobre registros totales y paginación

Estándares:
- Usa los métodos incorporados de ResourceController donde sea apropiado
- Valida todos los parámetros de entrada
- Maneja errores de base de datos elegantemente
- Incluye comentarios PHPDoc
- Sigue los patrones de ResponseTrait de CI4 para consistencia
- La seguridad es la máxima prioridad—asume que toda entrada es maliciosa
```

**Lo que recibimos:**
La IA nos dio un método completo y listo para producción con validación de entrada, manejo de errores, paginación apropiada usando las características incorporadas de CI4, y consideraciones de seguridad. Explicó por qué se hicieron ciertas elecciones (como usar Query Builder para prevenir inyección SQL). Tomó 10 segundos en lugar de los 30 minutos que nos habría tomado escribir y probarlo a nosotros.

#### Ejemplo 2: Depurando un Problema de Autenticación

**Nuestro prompt:**
```
Actúa como un experto en seguridad de CodeIgniter 4 depurando un problema de autenticación.

Contexto:
- Proyecto de CI4 con autenticación Shield
- Estamos usando tokens de API (no sesiones)
- El filtro TokenAuth está aplicado a nuestras rutas de API
- Los usuarios pueden generar tokens vía /api/auth/login exitosamente
- Los tokens se almacenan en la tabla auth_identities

El Problema:
Cuando hacemos solicitudes a endpoints protegidos con un token válido en el encabezado Authorization (Bearer TOKEN), obtenemos una respuesta 401 No Autorizado. El token definitivamente existe en la base de datos y no está expirado.

Lo que hemos verificado:
- El encabezado Authorization se está enviando correctamente (verificado con Postman)
- El token existe en auth_identities con tipo 'access_token'
- El expires_at del token es null (no debería expirar)
- El filtro definitivamente se está aplicando (lo vemos en la configuración de rutas)

Tarea:
1. Lista las causas más probables de este problema en orden de probabilidad
2. Para cada causa, explica cómo verificar si es el problema
3. Proporciona los cambios específicos de código/configuración necesarios para arreglarlo
4. Explica por qué está pasando esto para que podamos prevenirlo en el futuro
```

**Lo que recibimos:**
La IA nos guió a través de un proceso de depuración sistemático. Resultó que habíamos olvidado habilitar el autenticador "token" en la configuración de Shield (solo "session" estaba habilitado). La IA explicó que Shield necesita configuración explícita para qué métodos de auth usar, nos dio el archivo de configuración exacto para editar, y explicó la diferencia entre autenticación por sesión y token para que entendiéramos por qué esto importaba.

Esta respuesta nos ahorró probablemente 2 horas de depuración de prueba y error aleatoria.

#### Ejemplo 3: Revisando Seguridad

**Nuestro prompt:**
```
Actúa como un auditor de seguridad revisando nuestra implementación de autenticación de API.

Contexto:
Estamos construyendo una API de producción que manejará datos sensibles de usuarios. Hemos implementado autenticación Shield con la siguiente configuración:
[pegamos nuestra configuración y métodos clave del controlador aquí]

Tarea:
Realiza una auditoría de seguridad y dinos:
1. Qué estamos haciendo bien (fortalezas de seguridad)
2. Qué vulnerabilidades existen o podrían existir
3. Qué mejores prácticas de la industria nos estamos perdiendo
4. Recomendaciones específicas con ejemplos de código para cualquier arreglo necesario
5. Cómo probar que nuestra seguridad está funcionando correctamente

Estándares:
- Sé exhaustivo—asume que esto será atacado por actores sofisticados
- Prioriza consideraciones del OWASP Top 10
- Considera tanto vulnerabilidades técnicas como fallas de lógica
- Explica el "por qué" detrás de cada recomendación, no solo el "qué"
```

**Lo que recibimos:**
La IA identificó tres problemas que no habíamos considerado:
1. No estábamos limitando la tasa de nuestro endpoint de login (vulnerable a fuerza bruta)
2. Nuestros mensajes de error eran demasiado específicos, potencialmente filtrando información sobre qué usuarios existen
3. No estábamos validando la fortaleza de contraseñas durante el registro

Para cada problema, explicó el vector de ataque, nos mostró exactamente cómo arreglarlo con código, y explicó por qué importaba. Este nivel de revisión de seguridad habría costado cientos de dólares de un consultor. Lo obtuvimos en 60 segundos.

### Los Prompts Que Usamos Una y Otra Vez

Después de construir LaunchPad API, notamos que estábamos usando ciertos patrones de prompt repetidamente. Aquí están nuestras plantillas "de referencia":

**Para generar código nuevo:**
```
Actúa como un [rol] con experiencia en [tecnología específica].

Contexto:
- [Breve descripción del proyecto]
- [Detalles del stack tecnológico]
- [Ubicaciones de archivos relevantes]
- [Cualquier configuración relevante]

Tarea:
[Tarea específica y accionable con requisitos numerados si es compleja]

Estándares:
- [Prioridad 1: usualmente seguridad o rendimiento]
- [Requisitos de estilo de código]
- [Requisitos de documentación]
- [Expectativas de manejo de errores]
```

**Para depurar:**
```
Actúa como un experto depurador especializado en [tecnología].

Contexto:
- [Qué estás construyendo]
- [Qué se supone que debe pasar]
- [Qué está pasando realmente]
- [Mensajes de error o comportamiento inesperado]

Lo que ya he intentado:
1. [Primera cosa que verificaste]
2. [Segunda cosa que verificaste]
3. [Cualquier prueba relevante que ejecutaste]

Tarea:
1. Identifica las causas raíz más probables
2. Explica cómo verificar cada una
3. Proporciona el arreglo con código
4. Explica por qué pasó esto para prevenirlo en el futuro
```

**Para explicar conceptos:**
```
Actúa como un mentor técnico paciente explicando [concepto] a un desarrollador de nivel [nivel de experiencia].

Contexto:
Estoy trabajando en [breve descripción] y tratando de entender [concepto específico]. He leído [lo que ya has leído] pero todavía no tengo claro [confusión específica].

Tarea:
Explica [concepto] en términos simples usando:
- Una analogía de la vida cotidiana
- Un ejemplo de código simple
- La forma específica en que se aplica a mi situación
- Errores comunes a evitar

Estándares:
- Asume que soy inteligente pero nuevo en esta área específica
- No uses jerga sin explicarla
- Conéctalo a beneficios prácticos (¿por qué debería importarme?)
```

**Para comparar opciones:**
```
Actúa como un arquitecto senior ayudando a elegir entre enfoques técnicos.

Contexto:
Estamos decidiendo entre [Opción A] y [Opción B] para [caso de uso específico].

Situación actual:
- [Breve contexto del proyecto]
- [Cualquier restricción o requisito]
- [Nivel de experiencia del equipo]
- [Necesidades de rendimiento/seguridad]

Tarea:
Compara estos enfoques a través de estas dimensiones:
1. Implicaciones de seguridad
2. Características de rendimiento
3. Mantenibilidad y legibilidad
4. Curva de aprendizaje para el equipo
5. Escalabilidad a largo plazo

Para cada opción, proporciona:
- Pros y contras claros
- Cuándo elegir esta opción
- Un breve ejemplo de código mostrando la implementación
- Cualquier truco o error común

Estándares:
- Sé objetivo—no favorezcas uno solo porque es más nuevo o cool
- Considera nuestro contexto (somos [situación del equipo])
- Señala cualquier decisión irreversible
```

### Por Qué Esto Importa Más de Lo Que Piensas

Quizás estés pensando, "Esto parece mucho trabajo solo para hacer una pregunta." Y al principio, así se siente. Escribir un prompt detallado toma 2-3 minutos en lugar de 10 segundos.

Pero aquí está lo que aprendimos: **Un buen prompt ahorra horas.**

Cuando escribes un prompt vago, obtienes una respuesta vaga. Luego pasas 20 minutos tratando de implementarlo, solo para darte cuenta de que no se ajusta a tu situación. Así que vuelves, aclaras, intentas de nuevo. Tres ciclos después, has pasado una hora.

O peor, obtienes código que parece funcionar pero tiene problemas ocultos—agujeros de seguridad, problemas de rendimiento, malas prácticas. No te enteras hasta semanas después cuando algo se rompe o un usuario explota una vulnerabilidad.

Un prompt detallado toma 3 minutos en escribirse pero te da exactamente lo que necesitas la primera vez. Considera tus restricciones, sigue tus estándares, y se ajusta a tu proyecto. Lo implementas una vez y funciona.

**Las matemáticas son simples:** 3 minutos de buen prompting vs. 60+ minutos de ida y vuelta y depuración. Más la tranquilidad de saber que obtuviste una solución segura y de alta calidad.

### Errores Comunes que Cometimos (Para Que Tú No Los Hagas)

Déjame compartir los errores que cometimos mientras aprendíamos esto. Quizás reconoces algunos de estos:

**Error 1: Ser demasiado breve**
- Lo que hicimos: "Arregla esto"
- Lo que pasó: La IA hizo suposiciones, cambió cosas que no queríamos que cambiara, e introdujo nuevos problemas
- La solución: Siempre explica qué significa "arreglar" y proporciona contexto

**Error 2: No especificar el rol**
- Lo que hicimos: Hicimos preguntas generales de programación sin asignar experiencia
- Lo que pasó: Obtuvimos respuestas genéricas que perdieron mejores prácticas específicas del framework
- La solución: Siempre comienza con "Actúa como un [experto específico en tecnología específica]"

**Error 3: No establecer prioridades**
- Lo que hicimos: "Haz este código mejor"
- Lo que pasó: La IA optimizó por brevedad y creó líneas de una sola línea ilegibles
- Lo que queríamos: Seguridad y mantenibilidad sobre astucia
- La solución: Declara explícitamente tus prioridades

**Error 4: Pedir código sin explicación**
- Lo que hicimos: "Dame el código para X"
- Lo que pasó: Obtuvimos código funcional pero no lo entendimos, no pudimos modificarlo, no pudimos depurarlo
- La solución: Pide siempre "explica cómo funciona esto" o "agrega comentarios explicando cada parte"

**Error 5: No proporcionar contexto de archivos**
- Lo que hicimos: Pegamos un fragmento de código sin decir de qué archivo era
- Lo que pasó: La IA sugirió imports y namespaces que no coincidían con nuestra estructura
- La solución: Menciona siempre la ruta del archivo y la estructura del proyecto

**Error 6: Tener miedo de hacer preguntas "tontas"**
- Lo que hicimos: Luchamos con conceptos que no entendíamos en lugar de pedir aclaración
- Lo que pasó: Construimos características sobre cimientos inestables, creamos deuda técnica
- La solución: Usa el rol de "mentor paciente" y pide explicaciones en términos simples. Sin juicio, solo aprendizaje.

### El Cambio de Mentalidad: La IA como Socio Colaborativo

Aquí está el cambio filosófico que hizo toda la diferencia para nosotros:

**Mentalidad antigua:** "La IA es una herramienta que uso para obtener respuestas"
**Nueva mentalidad:** "La IA es un socio colaborativo que necesita contexto para ser útil"

Cuando ves a la IA como un socio, naturalmente proporcionas más contexto. Explicas tus objetivos, restricciones y razonamiento. Tienes un diálogo en lugar de hacer demandas.

Piensa en cómo trabajarías con un desarrollador humano:
- No solo dirías "arregla esto" y te irías
- Explicarías qué está mal, qué has intentado, y qué es el éxito
- Compartirías tu estructura de proyecto y estándares
- Escucharías sus preguntas y proporcionarías aclaración

Trata a la IA de la misma manera. Los prompts que funcionan mejor son los que tratan a la IA como un colega conocedor que acaba de unirse a tu proyecto y necesita ponerse al día.

### Nuestro Checklist de Prompt Engineering

Antes de enviar cualquier prompt a nuestro asistente de IA, ahora pasamos por este checklist mental:

**Asignación de Rol:**
- [ ] ¿Especificé qué experiencia debe usar la IA?
- [ ] ¿Es el rol específico a mi stack tecnológico?
- [ ] ¿Coincide el rol con el tipo de ayuda que necesito (desarrollador vs. experto en seguridad vs. arquitecto)?

**Contexto Proporcionado:**
- [ ] ¿Mencioné el framework y bibliotecas que estoy usando?
- [ ] ¿Describí la estructura de mi proyecto?
- [ ] ¿Incluí código o configuración relevante?
- [ ] Si estoy depurando, ¿dije qué ya he intentado?

**Claridad de Tarea:**
- [ ] ¿Es la tarea específica y accionable?
- [ ] ¿Dividí tareas complejas en pasos numerados?
- [ ] ¿Especificé qué entregables quiero (código, explicación, comparación)?

**Estándares Establecidos:**
- [ ] ¿Declaré mis prioridades (seguridad, rendimiento, legibilidad)?
- [ ] ¿Mencioné cualquier restricción o requisito?
- [ ] ¿Especificé expectativas de estilo de código o documentación?

**Verificación de Tono:**
- [ ] ¿Estoy tratando a la IA como un socio colaborativo?
- [ ] ¿Proporcioné suficiente detalle para que la IA entienda mi situación?
- [ ] ¿Un desarrollador humano entendería lo que estoy pidiendo?

Si podemos marcar todas estas casillas, obtenemos grandes resultados casi siempre.

### Juntándolo Todo: Un Ejemplo Completo

Déjame mostrarte un ejemplo final y comprehensivo que demuestra todo lo que hemos aprendido.

**La Situación:**
Necesitábamos implementar una característica de restablecimiento de contraseña. Esto es crítico para la seguridad, así que queríamos ser extra cuidadosos.

**Nuestro Prompt:**
```
Actúa como un experto senior en seguridad de CodeIgniter 4 con profundo conocimiento de autenticación Shield y mejores prácticas modernas de seguridad.

Contexto:
Estamos construyendo LaunchPad API, una API REST de producción usando:
- CodeIgniter 4.5.x
- Shield para autenticación (actualmente usando tokens)
- Base de datos MySQL
- PHP 8.2+
- Siguiendo convenciones de CI4 y estándares PSR

Nuestra estructura de proyecto:
- Controladores: app/Controllers/Api/
- Modelos: app/Models/
- Config: app/Config/
- Rutas: app/Config/Routes.php

Configuración actual de autenticación:
[Pegamos nuestra configuración de Shield aquí]

La Tarea:
Implementa un flujo seguro de restablecimiento de contraseña para nuestra API que:
1. Permita a usuarios solicitar un restablecimiento de contraseña vía su email
2. Genere un token seguro y limitado en tiempo
3. Envíe un email con un enlace de restablecimiento
4. Valide el token cuando el usuario haga clic en el enlace
5. Permita establecer una nueva contraseña con validación
6. Invalide el token después de usarlo o expirar

Requisitos de Seguridad (en orden de prioridad):
1. Prevenir ataques de tiempo (no revelar si el email existe)
2. Los tokens deben ser criptográficamente seguros y limitados en tiempo
3. Prevenir ataques de repetición (token solo puede usarse una vez)
4. Validar fortaleza de nueva contraseña
5. Registrar todos los intentos de restablecimiento de contraseña para monitoreo de seguridad
6. Limitar la tasa de solicitudes de restablecimiento para prevenir abuso

Estándares de Código:
- Usa las características incorporadas de Shield donde sea posible
- Sigue los patrones de validación y respuesta de CI4
- Incluye comentarios PHPDoc comprehensivos
- Maneja todos los casos de error elegantemente
- Usa type hints para PHP 8.2+
- Asume que toda entrada es maliciosa

Entregables:
1. El(s) método(s) del controlador para manejar solicitudes de restablecimiento
2. Cualquier cambio de modelo necesario
3. Configuración de rutas
4. Actualizaciones de configuración de Shield
5. Una breve explicación de las medidas de seguridad implementadas
6. Sugerencias de pruebas para verificar la seguridad
```

**El Resultado:**
La IA nos dio una implementación completa y lista para producción con:
- Generación segura de tokens usando las características de seguridad de CI4
- Búsqueda de email resistente a ataques de tiempo
- Manejo apropiado de expiración de tokens
- Implementación de limitación de tasa
- Validación comprehensiva
- Mensajes de error claros que no filtran información
- Comentarios detallados explicando cada decisión de seguridad

Nos tomó 5 minutos revisarlo y adaptarlo a nuestras necesidades exactas. Sin un buen prompting, podríamos haber obtenido una implementación básica que "funcionara" pero tuviera agujeros de seguridad que descubriríamos meses después cuando alguien los explotara.

### La Conclusión sobre Prompt Engineering

El prompt engineering no se trata de manipular a la IA o usar palabras clave especiales. Se trata de comunicación clara—la misma habilidad que usas cuando trabajas con colegas humanos.

Los mejores prompts:
- Establecen expectativas claras (asignación de rol)
- Proporcionan contexto necesario (clarificar la situación)
- Definen metas específicas (especificar la tarea)
- Establecen estándares de calidad (fijar el nivel)

Cuando recibes una mala respuesta de la IA, usualmente no es porque la IA sea mala—es porque el prompt estuvo incompleto. La IA te dio exactamente lo que pediste; simplemente no pediste lo correcto.

**Nuestro consejo:** Gasta 3 minutos escribiendo un prompt detallado, ahorra 3 horas de depuración. Trata a la IA como el socio conocedor que es, dale el contexto que necesita, y te sorprenderás de la calidad de ayuda que recibes.

Esta es la pieza final de la metodología de Vibe Coding. Con buena documentación, habilidades de IA entrenadas, bibliotecas apropiadas, y prompting efectivo, tienes todo lo que necesitas para construir software de producción a un ritmo que parecería imposible para desarrolladores tradicionales.

Ahora hablemos de cómo documentamos todo para que nuestros yo futuros (y nuestros asistentes de IA) puedan entender el razonamiento detrás de cada decisión.

## La Filosofía de AGENTS.md: Documentando Todo

Hay un archivo en nuestro proyecto llamado `AGENTS.md` que vale la pena mencionar porque representa un cambio fundamental en cómo pensamos sobre el desarrollo de software.

### Por Qué Documentamos Decisiones

La mayoría del código tiene comentarios explicando QUÉ hace. Raramente explica POR QUÉ lo hace de esa manera. Seis meses después, mirarás tu código y pensarás "¿Por qué lo hice de esta manera? ¿Había una razón?"

O peor, un nuevo desarrollador se une a tu equipo y tiene que hacer ingeniería inversa de tus decisiones leyendo código y adivinando.

**Nuestra regla: Cada decisión técnica se documenta.**

Cuando elegimos CodeIgniter sobre Laravel: documentado.
Cuando elegimos Shield para autenticación: documentado.
Cuando estructuramos nuestras carpetas de cierta manera: documentado.
Cuando configuramos ajustes de seguridad: documentado.

### ¿Qué Hay En AGENTS.md?

Nuestro archivo AGENTS.md se ha convertido en el cerebro vivo de nuestro proyecto:

**1. Descripción General del Proyecto**
- Qué estamos construyendo
- Nuestro stack tecnológico
- Estructura de directorios

**2. Comandos Comunes**
- Cómo iniciar el servidor de desarrollo
- Cómo ejecutar migraciones de base de datos
- Cómo crear nuevos controladores o modelos
- Cómo ejecutar pruebas

**3. Estándares de Desarrollo**
- Cómo estructuramos los controladores
- Cómo estructuramos los modelos
- Lista de verificación de seguridad
- Guías de estilo de código

**4. Referencia de Configuración**
- Qué hace cada archivo de configuración
- Qué ajustes hemos cambiado
- Por qué los cambiamos

**5. Skills Disponibles**
- Enlaces a todos nuestros archivos de skill
- Qué cubre cada uno
- Cuándo referenciar cuál

**6. Documentación Clave**
- Enlaces a nuestra documentación local
- Qué archivos cubren qué temas
- Dónde encontrar información más profunda

**7. Solución de Problemas**
- Problemas comunes que hemos encontrado
- Cómo los resolvimos
- Qué revisar cuando las cosas se rompen

**8. Mejores Prácticas**
- Principios de seguridad que seguimos
- Consejos de rendimiento
- Requisitos de pruebas

### El Formato de Toma de Decisiones

Cuando documentamos una decisión, usamos este formato:

```markdown
## Decision: [Lo que decidimos]

**Fecha**: [Cuándo lo decidimos]
**Contexto**: [Qué situación llevó a esta decisión]
**Opciones Consideradas**:
- Opción A: [descripción]
- Opción B: [descripción]
- Opción C: [descripción]

**Decision**: Elegimos la Opción B porque [razones específicas]

**Trade-offs**:
- Pros: [beneficios]
- Contras: [desventajas]

**¿Reversible?**: [Sí/No] - Si es sí, ¿bajo qué condiciones?
```

**Ejemplo Real de Nuestro Proyecto:**

```markdown
## Decision: Usar Shield para Autenticación

**Fecha**: 17 de febrero de 2026
**Contexto**: Necesitamos autenticación de usuarios para LaunchPad API

**Opciones Consideradas**:
1. Escribir nuestro propio sistema de autenticación
2. Usar Shield (la biblioteca oficial de auth de CodeIgniter)
3. Usar un servicio de terceros (Auth0, Firebase Auth)

**Decision**: Elegimos Shield porque:
- Es la solución de autenticación oficial de CodeIgniter
- Se integra perfectamente con nuestro framework
- Soporta múltiples métodos de auth (sesiones, tokens, HMAC, JWT)
- Tiene permisos basados en roles incorporados
- Es mantenido activamente por el equipo de CodeIgniter
- No nos encierra en un servicio de terceros

**Trade-offs**:
- Pros: Gratis, integrado, control total, sin dependencia de proveedor
- Contras: Lo mantenemos nosotros mismos (pero esto es mínimo con actualizaciones de Composer)

**¿Reversible?**: Parcialmente. Si queremos cambiar a un servicio de terceros más tarde, podemos migrar usuarios. Pero Shield nos da todo lo que necesitamos para el futuro previsible.
```

### Por Qué Esto Importa Para La IA

Aquí está la cosa hermosa: **Nuestro asistente de IA lee AGENTS.md.**

Cuando pedimos ayuda a OpenCode, sabe:
- La estructura de nuestro proyecto
- Nuestros estándares de codificación
- Nuestros requisitos de seguridad
- Dónde encontrar documentación
- Qué decisiones ya hemos tomado

Esto significa que la IA nos da consejos consistentes que coinciden con la filosofía de nuestro proyecto. No sugiere soluciones que entren en conflicto con nuestros patrones establecidos. Entiende las restricciones y metas que hemos establecido.

Es como la diferencia entre pedirle direcciones a un extraño versus preguntarle a alguien que ha leído todo tu plan de proyecto.

## Ejemplos de Código: Lo Que Realmente Construimos

Veamos algo de código real de LaunchPad API. Recuerda, no necesitas memorizar esto—solo necesitas ver que es manejable.

### Ejemplo 1: Un Endpoint Protegido Simple

Esto obtiene el perfil de un usuario, pero solo si ha iniciado sesión:

```php
<?php

namespace App\Controllers\Api;

use CodeIgniter\RESTful\ResourceController;

class ProfileController extends ResourceController
{
    protected $format = 'json';

    /**
     * Obtener el perfil del usuario actual
     * GET /api/profile
     */
    public function index()
    {
        // auth() es una función helper de Shield
        // Nos da acceso al usuario actual
        $user = auth()->user();
        
        // Si de alguna manera no hay usuario conectado, devolver error
        if (!$user) {
            return $this->failUnauthorized('Debes iniciar sesión');
        }
        
        // Devolver los datos del usuario
        return $this->respond([
            'status' => 200,
            'data' => [
                'id' => $user->id,
                'email' => $user->email,
                'username' => $user->username,
                'created_at' => $user->created_at
            ]
        ]);
    }
}
```

**Qué está pasando aquí:**
- Extendemos ResourceController que nos da métodos útiles
- `auth()->user()` obtiene el usuario actualmente conectado desde su token
- Si no hay usuario, devolvemos un error 401 No Autorizado
- Si sí hay, devolvemos sus datos de perfil

**Para proteger esta ruta en routes.php:**

```php
$routes->get('api/profile', 'Api\ProfileController::index', ['filter' => 'tokens']);
```

Eso es todo. Una línea dice "requiere un token válido para acceder a esto."

### Ejemplo 2: Creando Un Nuevo Recurso (con Validación)

Esto crea un nuevo producto en nuestra base de datos:

```php
<?php

namespace App\Controllers\Api;

use CodeIgniter\RESTful\ResourceController;

class ProductController extends ResourceController
{
    protected $modelName = 'App\Models\ProductModel';
    protected $format = 'json';

    /**
     * Crear un nuevo producto
     * POST /api/products
     */
    public function create()
    {
        // Obtener los datos JSON enviados por el cliente
        $data = $this->request->getJSON(true);
        
        // Intentar insertar en la base de datos
        // El modelo valida automáticamente basado en las reglas que definimos
        if (!$this->model->insert($data)) {
            // Falló la validación—devolver los errores
            return $this->failValidationErrors($this->model->errors());
        }
        
        // ¡Éxito! Devolver el ID del nuevo producto
        return $this->respondCreated([
            'id' => $this->model->insertID(),
            'message' => 'Producto creado exitosamente'
        ]);
    }
}
```

**Qué está pasando aquí:**
- `getJSON(true)` analiza el JSON enviado por el cliente en un array PHP
- `$this->model->insert($data)` intenta guardar en la base de datos
- Si falla la validación (tipos de datos incorrectos, campos faltantes), obtenemos errores de vuelta
- `respondCreated()` automáticamente envía el estado HTTP 201 (Creado)

**El modelo con reglas de validación:**

```php
<?php

namespace App\Models;

use CodeIgniter\Model;

class ProductModel extends Model
{
    protected $table = 'products';
    protected $primaryKey = 'id';
    
    // Campos que pueden ser asignados masivamente
    protected $allowedFields = ['name', 'description', 'price', 'stock'];
    
    // Reglas de validación
    protected $validationRules = [
        'name' => 'required|min_length[3]|max_length[255]',
        'description' => 'permit_empty|max_length[1000]',
        'price' => 'required|decimal|greater_than[0]',
        'stock' => 'required|integer|greater_than_equal_to[0]'
    ];
    
    // Mensajes de error personalizados
    protected $validationMessages = [
        'name' => [
            'required' => 'El nombre del producto es requerido',
            'min_length' => 'El nombre del producto debe tener al menos 3 caracteres'
        ],
        'price' => [
            'required' => 'El precio es requerido',
            'greater_than' => 'El precio debe ser mayor que 0'
        ]
    ];
}
```

¿Notas cómo el modelo maneja toda la validación? No escribimos lógica de validación en nuestro controlador—definimos las reglas una vez, y el modelo las aplica automáticamente.

### Ejemplo 3: Verificando Permisos

A veces necesitamos verificar si un usuario tiene permiso específico, no solo si ha iniciado sesión:

```php
<?php

namespace App\Controllers\Api;

use CodeIgniter\RESTful\ResourceController;

class AdminController extends ResourceController
{
    protected $format = 'json';

    /**
     * Obtener todos los usuarios (solo admin)
     * GET /api/admin/users
     */
    public function users()
    {
        $user = auth()->user();
        
        // Verificar si el usuario tiene permiso de admin
        if (!$user->can('admin.access')) {
            return $this->failForbidden('No tienes permiso para acceder a esta área');
        }
        
        // Cargar modelo de usuario
        $userModel = model('UserModel');
        
        // Obtener todos los usuarios
        $users = $userModel->findAll();
        
        return $this->respond([
            'status' => 200,
            'count' => count($users),
            'data' => $users
        ]);
    }
}
```

**Qué está pasando:**
- `auth()->user()` obtiene el usuario actual
- `$user->can('admin.access')` verifica si tienen el permiso de admin
- Si no, devolver 403 Prohibido
- Si sí, mostrar todos los usuarios

**Configurando permisos en AuthGroups.php:**

```php
<?php

namespace Config;

use CodeIgniter\Shield\Config\AuthGroups as ShieldAuthGroups;

class AuthGroups extends ShieldAuthGroups
{
    // Definir grupos de usuarios
    public array $groups = [
        'superadmin' => [
            'title' => 'Super Admin',
            'description' => 'Acceso completo al sistema'
        ],
        'admin' => [
            'title' => 'Administrador', 
            'description' => 'Administradores del día a día'
        ],
        'user' => [
            'title' => 'Usuario',
            'description' => 'Usuarios generales'
        ]
    ];

    // Definir permisos
    public array $permissions = [
        'admin.access' => 'Puede acceder al área de admin',
        'users.create' => 'Puede crear usuarios',
        'users.edit' => 'Puede editar usuarios',
        'users.delete' => 'Puede eliminar usuarios',
        'products.manage' => 'Puede gestionar productos'
    ];

    // Qué grupos tienen qué permisos
    public array $matrix = [
        'superadmin' => ['*'],  // Comodín = todos los permisos
        'admin' => [
            'admin.access',
            'users.*',  // Todos los permisos de usuario
            'products.manage'
        ],
        'user' => [
            'products.read'  // Solo puede ver productos
        ]
    ];
}
```

Esto crea un sistema completo de control de acceso basado en roles. Los usuarios en el grupo "admin" automáticamente obtienen todos los permisos listados, y podemos verificar `$user->can('users.create')` en cualquier lugar de nuestro código.

## Aprovechando OpenCode AI: Nuestro Flujo de Trabajo Diario

Ahora que entiendes lo que construimos, hablemos sobre CÓMO lo construimos. Aquí es donde Vibe Coding realmente brilla.

### Nuestro Flujo de Trabajo Diario

**Configuración Matutina (5 minutos):**
1. Abrir nuestro editor de código con OpenCode integrado
2. Abrir la carpeta del proyecto
3. Preguntarle a OpenCode: "¿Cuál es nuestra meta para hoy?"
4. Revisar el progreso de ayer

**Construyendo Funciones (El Vibe):**

Vamos a recorrer agregar una función real: "Endpoint de actualización de perfil de usuario"

**Paso 1: Pedir el plan**

Nosotros: "Necesitamos agregar un endpoint que permita a los usuarios actualizar su perfil. Deberían poder actualizar su nombre, correo y biografía. ¿Qué archivos necesitamos crear o modificar?"

OpenCode: "Basado en la estructura de nuestro proyecto y el skill de ci4-api-development, necesitaremos:

1. Agregar un método `update()` a `ProfileController`
2. Actualizar las reglas de validación en el modelo User para permitir el campo bio
3. Agregar una ruta en `Routes.php`
4. Considerar: ¿Deberían los usuarios poder cambiar su correo? Eso podría requerir re-verificación.

Déjame mostrarte primero el método del controlador."

**Paso 2: Obtener el código**

OpenCode genera:

```php
public function update()
{
    $user = auth()->user();
    
    if (!$user) {
        return $this->failUnauthorized('Debes iniciar sesión');
    }
    
    $data = $this->request->getJSON(true);
    
    // Solo permitir ciertos campos para actualizar
    $allowedFields = ['username', 'bio'];
    $updateData = array_intersect_key($data, array_flip($allowedFields));
    
    // Manejar el correo por separado (requiere verificación)
    if (isset($data['email']) && $data['email'] !== $user->email) {
        // Activar proceso de cambio de correo
        return $this->failValidationErrors([
            'email' => 'Los cambios de correo requieren verificación. Usa el endpoint de cambio de correo.'
        ]);
    }
    
    if (empty($updateData)) {
        return $this->failValidationErrors(['error' => 'No hay campos válidos para actualizar']);
    }
    
    $userModel = model('UserModel');
    
    if (!$userModel->update($user->id, $updateData)) {
        return $this->failValidationErrors($userModel->errors());
    }
    
    return $this->respondUpdated([
        'message' => 'Perfil actualizado exitosamente',
        'data' => $userModel->find($user->id)
    ]);
}
```

**Paso 3: Hacer preguntas**

Nosotros: "¿Por qué estamos usando `array_intersect_key`?"

OpenCode: "¡Gran pregunta! Esta es una medida de seguridad. Asegura que solo actualicemos campos que explícitamente permitamos. Sin esto, un usuario malicioso podría enviar campos extra en su JSON (como `is_admin: true`) y potencialmente escalar sus privilegios. Hacemos lista blanca de campos permitidos en lugar de lista negra de peligrosos—es más seguro."

Nosotros: "Ah, eso tiene sentido. ¿Qué pasa con la verificación de correo?"

OpenCode: "El correo es especial porque a menudo se usa para recuperación de cuenta y es un identificador único. Si dejamos que los usuarios lo cambien instantáneamente, alguien podría:
1. Tomar el control de una cuenta cambiando a un correo que controlan
2. Bloquear al verdadero dueño
3. Evadir medidas de seguridad

El flujo mejor es:
1. El usuario solicita cambio de correo
2. El sistema envía verificación al NUEVO correo
3. El usuario hace clic en el enlace del nuevo correo
4. El sistema actualiza el correo solo después de la verificación

Shield podría tener manejo incorporado de cambio de correo que podemos usar. Revisa el archivo de skill ci4-shield-auth."

**Paso 4: Implementar y probar**

Agregamos el código, actualizamos la ruta:

```php
$routes->put('api/profile', 'Api\ProfileController::update', ['filter' => 'tokens']);
```

Luego lo probamos:

```bash
# Iniciar el servidor de desarrollo
php spark serve

# En otra terminal, probar con curl
curl -X PUT http://localhost:8080/api/profile \
  -H "Authorization: Bearer TU_TOKEN_AQUI" \
  -H "Content-Type: application/json" \
  -d '{"username": "NuevoNombre", "bio": "Hola mundo"}'
```

**Paso 5: Manejar errores**

Si algo no funciona, le preguntamos a OpenCode:

Nosotros: "Estoy recibiendo un error 500 cuando intento actualizar. Los registros dicen 'Unknown column bio in field list.'"

OpenCode: "Eso significa que la tabla de base de datos no tiene una columna 'bio' todavía. Necesitamos crear una migración para agregarla. Déjame crear eso para ti."

```bash
# Generar migración
php spark make:migration add_bio_to_users_table
```

OpenCode genera el código de migración:

```php
<?php

namespace App\Database\Migrations;

use CodeIgniter\Database\Migration;

class AddBioToUsersTable extends Migration
{
    public function up()
    {
        $this->forge->addColumn('users', [
            'bio' => [
                'type' => 'TEXT',
                'null' => true,
                'after' => 'username'
            ]
        ]);
    }

    public function down()
    {
        $this->forge->dropColumn('users', 'bio');
    }
}
```

Luego:

```bash
# Ejecutar la migración
php spark migrate
```

Problema resuelto.

### La Perspectiva Clave

Nota cómo esto no es solo "La IA escribe código por nosotros." Es una conversación:
- Explicamos lo que queremos
- La IA sugiere un enfoque y explica por qué
- Hacemos preguntas
- La IA nos enseña el razonamiento
- Implementamos
- Probamos
- Resolvemos problemas juntos

Estamos aprendiendo mientras construimos. Para cuando esta función está lista, entendemos:
- Vulnerabilidades de asignación masiva
- Por qué los cambios de correo necesitan verificación
- Cómo funcionan las migraciones
- Cómo probar endpoints de API

Ese es el "Vibe" en Vibe Coding. Es colaborativo, educativo y productivo.

## Decisiones Técnicas: El Por Qué Detrás de Lo Que Construimos

Documentemos algunas decisiones clave que tomamos durante este proyecto, usando nuestro formato de decisión:

### Decision: Almacenar Documentación Localmente vs. Confiar en Documentación Online

**Fecha**: 17 de febrero de 2026
**Contexto**: Necesitamos que la IA nos dé consejos precisos y actuales sobre CodeIgniter y Shield

**Opciones Consideradas**:
1. Apuntar la IA a la documentación online (codeigniter.com)
2. Descargar documentación localmente y apuntar la IA a eso
3. No usar documentación, confiar en los datos de entrenamiento de la IA

**Decision**: Elegimos la opción 2—descargar localmente

**Racional**:
- La documentación online podría estar temporalmente caída
- Los datos de entrenamiento de la IA podrían estar desactualizados (pre-CodeIgniter 4 o versiones más antiguas)
- La documentación local permite desarrollo offline
- Podemos buscar en los documentos localmente al instante
- Asegura que la IA referencie exactamente la misma versión que estamos usando

**Trade-offs**:
- Pros: Confiable, específica de versión, buscable offline
- Contras: Ocupa espacio en disco (~50MB), necesita actualización periódica

**¿Reversible?**: Sí. Si queremos usar documentación online más tarde, solo actualizamos los archivos de skill.

### Decision: Usar CodeIgniter 4 Sobre Laravel u Otros Frameworks

**Fecha**: 17 de febrero de 2026
**Contexto**: Elegir un framework de PHP para nuestra API

**Opciones Consideradas**:
1. Laravel (framework PHP más popular)
2. CodeIgniter 4 (ligero, simple)
3. Symfony (enfocado en empresas)
4. Slim (micro-framework)
5. Sin framework (PHP puro)

**Decision**: CodeIgniter 4

**Racional**:
- **Laravel**: Poderoso pero dogmático y complejo. Tiene una curva de aprendizaje pronunciada. Pesado para una API simple.
- **CodeIgniter**: Simple, documentación clara, se mantiene fuera de tu camino. Perfecto para aprender mientras construyes.
- **Symfony**: Exagerado para nuestras necesidades. Diseñado para aplicaciones empresariales grandes.
- **Slim**: Demasiado mínimo. Terminaríamos reconstruyendo características que CI4 proporciona.
- **PHP puro**: Reinventaríamos la rueda e introduciríamos problemas de seguridad.

CI4 golpea el punto óptimo: lo suficientemente dogmático para guiarnos, lo suficientemente flexible para no pelear con nosotros.

**Trade-offs**:
- Pros: Rápido de aprender, excelente documentación, características de API incorporadas
- Contras: Ecosistema más pequeño que Laravel, menos paquetes de terceros

**¿Reversible?**: Técnicamente sí, pero prácticamente no. Reescribir en otro framework sería una reconstrucción completa.

### Decision: Usar Token Authentication de Shield vs. JWT

**Fecha**: 17 de febrero de 2026
**Contexto**: Elegir método de autenticación para la API

**Opciones Consideradas**:
1. Access Tokens incorporados de Shield
2. JWT (JSON Web Tokens)
3. Auth basado en sesiones (cookies)
4. OAuth2 (Google, GitHub login)

**Decision**: Access Tokens de Shield por ahora, con opción de agregar JWT más tarde

**Racional**:
- **Access Tokens**: Incorporados en Shield, sin dependencias extra, almacenados en base de datos (podemos revocarlos al instante), simple de implementar
- **JWT**: Popular, autocontenido, pero requiere paquete adicional (shield-jwt), más difícil de revocar (necesita lista negra), tamaño de token más grande
- **Sesiones**: No adecuado para API (diseñado para aplicaciones web basadas en navegador)
- **OAuth2**: Bueno para "Iniciar sesión con Google" pero agrega complejidad y dependencia externa

Los access tokens nos dan todo lo que necesitamos para una API básica: autenticación stateless, expiración, scopes, y la capacidad de revocar. Podemos agregar JWT más tarde si necesitamos sus beneficios específicos.

**Trade-offs**:
- Pros: Simple, seguro, revocable al instante, sin dependencias extra
- Contras: Requiere búsqueda en base de datos en cada solicitud (impacto mínimo de rendimiento)

**¿Reversible?**: Sí. Podemos agregar soporte de JWT junto con access tokens si es necesario.

### Decision: Usar MySQL vs. PostgreSQL o SQLite

**Fecha**: 17 de febrero de 2026
**Contexto**: Elegir base de datos para desarrollo y producción

**Opciones Consideradas**:
1. MySQL (más popular, ampliamente soportado)
2. PostgreSQL (características más avanzadas)
3. SQLite (basado en archivos, cero configuración)

**Decision**: MySQL para producción, SQLite para desarrollo/pruebas

**Racional**:
- **MySQL**: Cada host compartido lo soporta. Comunidad masiva. Perfecto para nuestras necesidades.
- **PostgreSQL**: Mejor en algunos aspectos, pero no soportado por la mayoría del hosting compartido. Agrega complejidad de despliegue.
- **SQLite**: Genial para desarrollo (sin servidor que ejecutar), no adecuado para producción (problemas de concurrencia)

Desarrollaremos con SQLite (rápido, fácil) y desplegaremos a MySQL (soporte universal).

**Trade-offs**:
- Pros: Soporte universal de hosting, fácil encontrar ayuda, despliegue simple
- Contras: Menos avanzado que PostgreSQL (pero no necesitamos esas características)

**¿Reversible?**: Parcialmente. CodeIgniter hace relativamente fácil cambiar de base de datos, pero se requeriría migración de datos.

### Decision: Organización Basada en Skills vs. Documentación Monolítica

**Fecha**: 17 de febrero de 2026
**Contexto**: Cómo estructurar el conocimiento de la IA para el proyecto

**Opciones Consideradas**:
1. Un archivo de skill gigante con todo
2. Múltiples archivos de skill enfocados por tema
3. Sin skills, solo confiar en AGENTS.md

**Decision**: Múltiples archivos de skill enfocados

**Racional**:
- **Un archivo gigante**: Difícil de navegar, la IA podría perder contexto relevante
- **Múltiples archivos**: Organización clara, puede referenciar áreas específicas, más fácil de mantener
- **Sin skills**: La IA daría consejos genéricos, no optimizado para nuestro stack

Creamos 7 archivos de skill cubriendo áreas distintas. Cuando necesitamos ayuda con autenticación, nosotros (y la IA) sabemos referenciar ci4-shield-auth.

**Trade-offs**:
- Pros: Organizado, mantenible, contexto enfocado
- Contras: Necesitas saber qué skill referenciar (pero eso es fácil de aprender)

**¿Reversible?**: Sí. Podemos fusionar o dividir archivos de skill en cualquier momento.

## Preocupaciones Comunes Abordadas

### "¡Pero No Soy Lo Suficientemente Técnico!"

Escuchamos esto mucho. Aquí está nuestra perspectiva:

**No necesitas ser un científico de la computación. Necesitas ser persistente.**

Piensa en aprender a manejar:
- No necesitabas entender motores de combustión interna
- No necesitabas ser mecánico
- Aprendiste los controles, practicaste y gradualmente te volviste cómodo
- Ahora manejas sin pensarlo

La programación es similar. Aprendes:
- La sintaxis básica (como aprender los controles)
- Patrones comunes (como aprender las reglas de tránsito)
- Cómo leer errores (como aprender las advertencias del tablero)
- Dónde encontrar ayuda (como saber que puedes buscar en Google o preguntar a un mecánico)

La IA maneja la sintaxis compleja. Tú te enfocas en la lógica: "Cuando un usuario hace X, el sistema debería hacer Y." Esa no es una habilidad técnica—esa es entender tu negocio.

### "¿Qué Pasa Si Rompo Algo?"

**Tres palabras: Control de Versiones (Git).**

Usamos Git para rastrear cada cambio. Piensa en ello como un botón de deshacer infinito que lo recuerda todo.

Antes de hacer cualquier cambio significativo:
1. Guardamos nuestro estado actual (commit)
2. Hacemos el cambio
3. Si funciona: ¡genial!
4. Si se rompe: restauramos el estado anterior (revert)

Es como guardar un videojuego antes de una pelea contra un jefe. Si pierdes, recargas. No se pierde progreso.

Además:
- Romper cosas es cómo aprendes
- El desarrollo local significa que no puedes romper el sitio en producción
- Las pruebas atrapan problemas antes de que los usuarios los vean
- La IA ayuda a arreglar errores

### "¿Esto Realmente Escala?"

Ya abordamos esto antes, pero seamos específicos:

**LaunchPad API puede manejar:**
- Miles de usuarios
- Cientos de solicitudes por segundo (en hardware modesto)
- Millones de registros de base de datos (con indexación apropiada)

**Si creces más allá de eso:**
- Agregar caché (Redis)
- Agregar un CDN para archivos estáticos
- Actualizar a un VPS ($20/mes maneja mucho más tráfico)
- Agregar balanceo de carga
- Optimizar consultas de base de datos

Pero aquí está la clave: **No optimizas para millones de usuarios cuando tienes cero usuarios.**

Construye para tus necesidades actuales. Cuando tengas tracción e ingresos, puedes permitirte optimizar. La optimización prematura es gastar tiempo y dinero en problemas que aún no tienes.

### "¿Qué Pasa Si Necesito Contratar Desarrolladores Más Tarde?"

Esto es realmente una fortaleza de nuestro enfoque:

**Buenas noticias:**
- Los desarrolladores de PHP están en todas partes (es el lenguaje web más popular)
- Los desarrolladores de CodeIgniter son fáciles de encontrar
- Nuestro código sigue las mejores prácticas
- AGENTS.md explica cada decisión
- Los archivos de skill muestran cómo trabajamos

Un nuevo desarrollador puede:
1. Leer AGENTS.md para entender el proyecto
2. Leer los archivos de skill para entender nuestro stack
3. Mirar el código existente para ver nuestros patrones
4. Pedirle ayuda a la IA (está entrenada en nuestros documentos)

Serán productivos en días, no semanas.

### "¿No Es Esto Hacer Trampa?"

**No. Es aprovechar herramientas.**

¿Las calculadoras "hacen trampa" en las matemáticas? No, nos hicieron más productivos.

¿Un carpintero "hace trampa" usando herramientas eléctricas en lugar de sierras manuales? No, trabajan más inteligentemente.

La IA es solo una herramienta. El valor que proporcionas es:
- Entender el problema que estás resolviendo
- Diseñar la solución
- Tomar decisiones sobre arquitectura y trade-offs
- Probar que funciona para usuarios reales
- Iterar basado en retroalimentación

La IA ayuda con sintaxis y código repetitivo. Tú proporcionas la visión y el juicio.

## Los Costos Reales y la Inversión de Tiempo

Seamos honestos sobre lo que esto realmente toma:

### Camino Tradicional (Contratando a un Desarrollador)

**Cronograma:** 4-8 semanas
**Costo:** $5,000-$30,000
**Lo que obtienes:** API funcionando (ojalá)
**Lo que no obtienes:** Comprensión de cómo funciona, capacidad de hacer cambios tú mismo

**Continuación:**
- Cada cambio cuesta más dinero
- Dependencia de su disponibilidad
- Riesgo si desaparecen
- Sobrecarga de comunicación

### Camino de Vibe Coding (Lo Que Hicimos)

**Fase de Aprendizaje:** 1-2 semanas
- Configurando entorno: 1 día
- Entendiendo lo básico: 3-5 días
- Trabajando con IA efectivamente: 3-5 días

**Fase de Construcción:** 1-2 semanas
- Configurando framework: 1 día
- Implementando autenticación: 2-3 días
- Construyendo tus funciones específicas: 5-10 días

**Costo:**
- Asistente de IA: $0-20/mes (OpenCode es gratis, las alternativas varían)
- Hosting: $3-10/mes
- Tu tiempo: Pero estás aprendiendo habilidades valiosas

**Lo que obtienes:**
- API funcionando
- Comprensión profunda de cómo funciona
- Capacidad de hacer cualquier cambio tú mismo
- Habilidades reutilizables para proyectos futuros
- Documentación de cada decisión

**Continuación:**
- Puedes iterar al instante
- Sin dependencia de otros
- Cada cambio te hace mejor
- Nuevas funciones toman horas, no días

### Los Beneficios Ocultos

1. **Velocidad de Iteración**: Cuando un cliente solicita una función, puedes lanzarla el mismo día
2. **Interés Compuesto del Aprendizaje**: Cada proyecto se vuelve más rápido. Tu segunda API tomará la mitad del tiempo
3. **Confianza Técnica**: Puedes evaluar contratistas y entender lo que están haciendo
4. **Capacidad de Pivotar**: Si las necesidades de tu negocio cambian, puedes adaptar tu tecnología al instante
5. **Propiedad**: Posees tu propiedad intelectual completamente

## Lo Que Tenemos Ahora: Funciones de LaunchPad API

Resumamos lo que está realmente construido y funcionando:

### ✅ Sistema de Autenticación
- Registro de usuario con validación de correo
- Inicio de sesión seguro con hash de contraseñas (Argon2id)
- Restablecimiento de contraseña vía tokens seguros
- Gestión de sesiones
- Tokens de acceso de API con expiración
- Scopes de tokens (lectura, escritura, admin)
- Limitación de tasa en endpoints de auth (previene fuerza bruta)

### ✅ Sistema de Autorización
- Grupos de usuarios (admin, usuario, etc.)
- Permisos granulares
- Matriz de permisos basada en grupos
- Verificación fácil de permisos en código

### ✅ Fundamento de API
- Estructura de endpoint RESTful
- Respuestas JSON consistentes
- Códigos de estado HTTP apropiados
- Manejo de errores
- Validación de entrada
- Negociación de contenido (JSON/XML)

### ✅ Sistema de Base de Datos
- Sistema de migración (cambios de esquema versionados)
- Seeders (datos de prueba)
- Query builder (acceso seguro a base de datos)
- Relaciones de modelos

### ✅ Herramientas de Desarrollo
- Servidor de desarrollo local
- Gestión de base de datos vía CLI
- Generación de código (controladores, modelos, migraciones)
- Framework de pruebas (PHPUnit)
- Herramientas de depuración

### ✅ Documentación
- 7 archivos de skill cubriendo todos los aspectos
- AGENTS.md con estándares del proyecto
- Copias de documentación local
- Comentarios de código inline
- Registros de decisiones

### ✅ Características de Seguridad
- Protección CSRF
- Filtrado XSS
- Prevención de inyección SQL (query builder)
- Validadores de seguridad de contraseñas
- Limitación de tasa
- Encabezados seguros

## Comenzando: Tu Turno

Si esto resuena contigo, así es como comenzar tu propio viaje de Vibe Coding:

### Prerrequisitos (Lo Que Realmente Necesitas)

**Hardware:**
- Cualquier computadora de los últimos 5 años
- 4GB RAM mínimo (8GB recomendado)
- Conexión a internet (para descargar, no para trabajar)

**Habilidades:**
- Alfabetización computacional básica (archivos, carpetas, instalar software)
- Capacidad de leer y seguir instrucciones
- Curiosidad y persistencia
- Voluntad de hacer preguntas

**Tiempo:**
- 1-2 horas por día durante 2-3 semanas para sentirse cómodo
- Luego acelera dramáticamente

### Pasos Primeros Paso a Paso

**Semana 1: Configuración del Entorno**

1. **Instalar PHP** (php.net)
   - Windows: Descargar instalador
   - Mac: Incluido o Homebrew
   - Linux: Gestor de paquetes

2. **Instalar Composer** (getcomposer.org)
   - Un comando o instalador
   - Este es tu gestor de paquetes

3. **Instalar un Editor de Código**
   - VS Code (gratis, recomendado)
   - O PHPStorm (pago pero excelente)
   - O OpenCode (con IA incorporada)

4. **Descargar CodeIgniter 4**
   - Vía Composer: `composer create-project codeigniter4/appstarter myproject`
   - O descargar de codeigniter.com

5. **Probarlo**
   - Ejecutar: `php spark serve`
   - Abrir navegador: http://localhost:8080
   - Deberías ver la página de bienvenida

**Semana 2: Aprender Lo Básico**

1. **Leer el tutorial de CodeIgniter**
   - Construir su blog de ejemplo
   - No solo copies—entiende por qué

2. **Jugar con la IA**
   - Configurar OpenCode o similar
   - Pídele que explique el código que estás leyendo
   - Acostúmbrate a la conversación

3. **Construir algo pequeño**
   - Una API de lista de tareas
   - Solo crear, leer, actualizar, eliminar
   - No te preocupes por auth todavía

**Semana 3: Agregar Autenticación**

1. **Instalar Shield**
   - `composer require codeigniter4/shield`
   - `php spark shield:setup`
   - `php spark migrate --all`

2. **Proteger tus endpoints**
   - Agregar el filtro de token a tus rutas
   - Probar con una herramienta como Postman o curl

3. **Documentar tus decisiones**
   - Comienza tu propio AGENTS.md
   - Escribe por qué hiciste las cosas

**Semana 4+: Construir Tu Proyecto Real**

Ahora estás listo para construir tu aplicación real. Tienes:
- Un entorno local funcionando
- Comprensión básica del framework
- Asistencia de IA configurada
- Autenticación lista
- La metodología de Vibe Coding

### Recursos Para Ayudarte

**Documentación Oficial:**
- Guía de Usuario de CodeIgniter 4: https://codeigniter.com/user_guide/
- Documentación de Shield: https://shield.codeigniter.com/
- Documentación de PHP: https://www.php.net/docs.php

**Comunidades:**
- Foro de CodeIgniter: forum.codeigniter.com
- Reddit: r/codeigniter y r/PHPhelp
- Discord: Muchos servidores de PHP y CI4

**Herramientas:**
- OpenCode: Asistente de codificación con IA
- Postman: Pruebas de API
- TablePlus: Gestión de base de datos
- Git: Control de versiones

### Cambios de Mentalidad

**De: "Necesito aprender todo antes de comenzar"**
**A: "Aprenderé lo que necesito mientras construyo"**

No necesitas ser un experto para ser productivo. Aprende el 20% que te da el 80% de los resultados. El resto viene con el tiempo.

**De: "Los errores son malos"**
**A: "Los errores son cómo aprendo"**

Cada mensaje de error te enseña algo. Cada bug te hace mejor. La IA te ayuda a recuperarte rápidamente.

**De: "Necesito permiso para construir"**
**A: "Puedo resolver esto"**

Nadie nos dio permiso. Solo comenzamos. Tú también puedes.

## Conclusión: Tu Idea Merece Existir

Si has leído hasta aquí, tienes algo que quieres construir. Un problema que quieres resolver. Un cambio que quieres hacer en el mundo.

La tecnología no debería detenerte.

Sí, hay una curva de aprendizaje. Sí, a veces te atascarás. Sí, requiere esfuerzo.

Pero no es magia. No está reservado para personas con títulos en ciencias de la computación. Es una habilidad que puedes aprender, y la IA la hace accesible más rápido que nunca.

Construimos LaunchPad API en días, no meses. Documentamos cada decisión para que nosotros (y tú) podamos entender el razonamiento. Creamos una base sobre la que podemos construir por años.

Tú también puedes hacer esto.

Comienza pequeño. Haz preguntas. Rompe cosas y arréglalas. Deja que la IA te guíe. Documenta lo que aprendes.

La barrera de entrada nunca ha sido más baja. Las herramientas nunca han sido mejores. El momento de comenzar es ahora.

**Tu idea merece existir. Ve y constrúyela.**

---

## Acerca de Esta Guía

Este artículo documenta el proceso real que usamos para construir LaunchPad API, una base de API lista para producción usando CodeIgniter 4, autenticación Shield y asistencia de IA de OpenCode.

**Ubicación del Proyecto**: `/`

**Stack Técnico**:
- PHP 8.2+
- CodeIgniter 4
- Shield Authentication
- MySQL (producción) / SQLite (desarrollo)
- Gestión de dependencias Composer

**Archivos Referenciados**:
- `AGENTS.md` - Guías del proyecto y documentación de decisiones
- `.opencode/skills/*.md` - Archivos de conocimiento de IA
- `composer.json` - Dependencias del proyecto

**Última Actualización**: 17 de febrero de 2026

---

*¿Tienes preguntas? ¿Estás construyendo tu propio proyecto? Conecta con nosotros—nos encantaría saber qué estás creando.*




