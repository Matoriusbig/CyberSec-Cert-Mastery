# 🛡️ Comprender las redes informáticas

## 1. 🌐 ¿Qué es la Creación de Redes (Networking)?

En esencia, una red es simplemente **dos o más computadoras conectadas entre sí** para compartir datos, información o recursos.

- Piensa en ello como el sistema de carreteras de una ciudad. Las casas y edificios son las computadoras (puntos finales), y las carreteras son las conexiones que permiten que los automóviles (datos) viajen entre ellos.
- Para la ciberseguridad, es vital entender cómo se construyen estas "carreteras", quién puede usarlas y cómo vigilar el "tráfico" que pasa por ellas.

---

## 2. 🗺️ Tipos de Redes

Hay dos categorías principales que debes dominar:

### Red de Área Local (LAN)

- **Qué es:** Una red contenida en un área geográfica pequeña.
- **Ejemplo Práctico:**
    - La red de tu casa (conectando tu laptop, teléfono y Smart TV a tu router).
    - La red de una sola oficina o un solo piso de un edificio.

### Red de Área Amplia (WAN)

- **Qué es:** Una red que conecta múltiples LAN a través de largas distancias.
- **Ejemplo Práctico:**
    - **Internet** es la WAN más grande y conocida del mundo.
    - Una empresa con oficinas en Santiago y Nueva York que conecta sus redes internas (sus LAN) utiliza una WAN.

---

## 3. 🏗️ Dispositivos de Red (El Hardware)

Estos son los componentes físicos que construyen y dirigen las "carreteras" de la red.

- 📣 **Concentrador (Hub):**
    - **Qué es:** Es un dispositivo que centraliza la conexión de computadoras y otros aparatos, permitiendo que intercambien datos.
    - **Cómo funciona:** Cuando recibe datos en un puerto, los **retransmite a todos los demás puertos,** crea un solo **dominio de colisión**.
    - **Analogía:** Es como estar en una habitación y gritar un mensaje. Todos lo oyen, incluso si el mensaje era solo para una persona.
    - **Impacto en Seguridad:** Muy inseguro. Facilita el "sniffing" (escuchar tráfico ajeno) porque todos ven todos los datos. Hoy en día están obsoletos y son una bandera roja si los encuentras.
- 🚦 **Conmutador (Switch):**
    - **Qué es:** Un dispositivo "inteligente" que conecta dispositivos en una LAN.
    - **Cómo funciona:** Aprende la **dirección MAC** (**identificador único y permanente asignado a la tarjeta de red de cada dispositivo por su fabricante**) de cada dispositivo conectado a sus puertos. Cuando recibe datos, los envía *únicamente* al puerto del destinatario correcto (**dominio de colisión** separado).
    - **Analogía:** Es como un cartero eficiente dentro de un edificio de oficinas. En lugar de gritar el mensaje, lo entrega directamente al escritorio (puerto) correcto.
    - **Impacto en Seguridad:** Fundamental. Crea "dominios de colisión" separados, haciendo el *sniffing* mucho más difícil. Permite crear **VLANs** (Redes Virtuales), que son cruciales para segmentar la red (por ejemplo, separar la red de "Invitados" de la red "Corporativa").
- 🗺️ **Enrutador (Router):**
    - **Qué es:** El dispositivo que **conecta diferentes redes entre sí** (ej. tu LAN con Internet/WAN).
    - **Cómo funciona:** Toma decisiones basadas en **direcciones IP** **(Protocolo de Internet)**. Su trabajo es encontrar la "ruta" más eficiente para que los datos lleguen a su destino en *otra red*.
    - **Analogía:** Es el "GPS" o la "oficina de correos" de la red. Sabe cómo enviar una carta (paquete de datos) desde tu vecindario (LAN) a un vecindario en otra ciudad (otra red).
- 🛡️ **Cortafuegos (Firewall):**
    - **Qué es:** Un dispositivo de seguridad (hardware o software) que filtra el tráfico.
    - **Cómo funciona:** Se sitúa entre dos redes (generalmente tu LAN e Internet) e inspecciona el tráfico. Decide si permitir o bloquear ese tráfico basándose en un conjunto de reglas predefinidas **(Listas de Control de Acceso - ACLs).**
    - **Analogía:** Es el **guardia de seguridad** en la entrada de un edificio. Tiene una lista de quién puede entrar (reglas) y revisa la identificación de todos (paquetes de datos).
- 🗄️ **Servidor (Server):**
    - **Qué es:** Una computadora diseñada para "servir" de información o recursos a otras computadoras (clientes).
    - **Ejemplos Comunes:**
        - **Servidor Web:** Aloja sitios web (como el que estás leyendo).
        - **Servidor de Archivos:** Almacena archivos compartidos.
        - **Servidor de Correo:** Gestiona tus emails.
        - **Servidor de Base de Datos:** Almacena y gestiona datos.
- 💻 **Punto Final (Endpoint):**
    - **Qué es:** Cualquier dispositivo al final de un enlace de comunicación.
    - **Ejemplos Comunes:** Laptops, computadoras de escritorio, teléfonos móviles, tablets, impresoras de red, Smart TVs.
    - **Impacto en Seguridad:** A menudo son el eslabón más débil y el objetivo principal de los atacantes (phishing, malware).
    <img width="945" height="1142" alt="image" src="https://github.com/user-attachments/assets/e29ca35c-8883-46b1-9ed9-dc3caa220bff" />

---

## 4. 🔑 Conceptos Clave de Red

Si los dispositivos son el hardware, estos son el "lenguaje" y las "direcciones" que usan.

- **Ethernet (IEEE 802.3):** El estándar global para conexiones de red *cableadas*. Define cómo los dispositivos formatean los datos para enviarlos a través de un cable.
- **Direccionamiento de Dispositivos:** Cada dispositivo necesita dos tipos de direcciones.
    - 🌎 **Dirección MAC (Control de Acceso al Medio):**
        - **Qué es:** Una dirección *física* y (teóricamente) única, quemada en la tarjeta de red (NIC) por el fabricante.
        - **Formato:** `00-13-02-1F-58-F5` (12 dígitos hexadecimales).
        - **Analogía:** Es como el **número de serie o chasis (VIN) de un auto**. No cambia, sin importar dónde esté el auto. Se usa para la comunicación *dentro* de la misma LAN (trabajo del Switch).
    - 📮 **Dirección IP (Protocolo de Internet):**
        - **Qué es:** Una dirección *lógica* que identifica un dispositivo en una red.
        - **Formato (IPv4):** `192.168.1.1` (Cuatro números de 0 a 255).
        - **Analogía:** Es como la **dirección de tu casa** (`Calle Falsa 123`). Puede cambiar si te mudas (si te conectas a otra red). Se usa para la comunicación *entre* diferentes redes (trabajo del Router).

---

## 5. 🏙️ Diagramas de Red (Visualizando la Conexión)

### Ejemplo 1: Red de Pequeña Empresa

Así se ve una red corporativa básica.

<img width="479" height="370" alt="image" src="https://github.com/user-attachments/assets/a5593f4d-e4d1-4b73-b5bc-8c3babf2057d" />

- **Flujo:** El tráfico de Internet es filtrado *primero* por el Firewall. Luego, pasa al Switch, que lo distribuye inteligentemente a los dispositivos correctos (endpoints o servidores).

### Ejemplo 2: Red Doméstica Típica

En casa, la eficiencia de costos consolida dispositivos.

<img width="495" height="324" alt="image" src="https://github.com/user-attachments/assets/b21023eb-2fa4-44cc-889d-c22ecb03b85b" />

- **Diferencia Clave:** El dispositivo que te da tu proveedor de Internet (ISP) es un "todo en uno". Actúa como router (conecta tu casa a Internet), firewall (bloquea tráfico básico), switch (tiene varios puertos de cable) y punto de acceso (AP) inalámbrico.

---

## 6. 📚 Modelos de Red (Las Reglas del Juego)

Para que computadoras de diferentes fabricantes (Apple, Microsoft, Google) puedan hablar entre sí, necesitamos **estándares**. Los modelos de red son marcos conceptuales que dividen la compleja tarea de la comunicación en "capas".

### El Modelo OSI (Interconexión de Sistemas Abiertos)

El modelo OSI es el **modelo teórico de 7 capas**. Es tu "libro de texto" para entender *cada paso* de la comunicación.

| Capa | Nombre | Propósito Principal | Analogía (Enviar un paquete) |
| --- | --- | --- | --- |
| **7** | **Aplicación** | Interfaz de usuario-red. | Escribes un email en tu programa de correo. |
| **6** | **Presentación** | Formato de datos, encriptación. | El programa formatea el texto y cifra la conexión (SSL/TLS). |
| **5** | **Sesión** | Iniciar, mantener y terminar conexiones. | Se "abre la llamada" con el servidor de correo. |
| **4** | **Transporte** | Entrega de datos Host-a-Host (TCP/UDP). | Se decide *cómo* enviar: con acuse de recibo (TCP) o no (UDP). |
| **3** | **Red** | Direccionamiento y enrutamiento (IP). | Se pone la dirección del destinatario en el sobre (Paquete). |
| **2** | **Enlace de Datos** | Entrega de datos Nodo-a-Nodo (MAC). | Se mete el sobre en una bolsa de correo para el camión local (Trama). |
| **1** | **Física** | Transmisión de bits (cables, WiFi). | El camión (cable) transporta físicamente la bolsa (bits). |

### 📦 Encapsulación y Desencapsulación

Este es un concepto *crítico* que debes dominar.

- **Encapsulación (Bajar por las capas):** A medida que tus datos (email) bajan por el modelo OSI, cada capa añade su propio "encabezado" (header), como si metieras una carta en un sobre, luego ese sobre en una caja pequeña, y esa caja en una caja grande.
    - Capa 4 (Transporte) añade un encabezado TCP/UDP ➡️ Se llama **Segmento**.
    - Capa 3 (Red) añade un encabezado IP ➡️ Se llama **Paquete**.
    - Capa 2 (Enlace) añade un encabezado Ethernet ➡️ Se llama **Trama**.
- **Desencapsulación (Subir por las capas):** El receptor hace lo opuesto. Abre la caja grande, saca la caja pequeña, saca el sobre y finalmente lee la carta.

### El Modelo TCP/IP (El Modelo Práctico)

El modelo OSI es la teoría; **TCP/IP es la realidad**. Es el conjunto de protocolos que *realmente* utiliza Internet. Es una versión simplificada de 4 capas.

| Capa TCP/IP | Protocolos Clave | Capas OSI Equivalentes |
| --- | --- | --- |
| **Aplicación** | HTTP, SMTP, DNS, FTP | 5, 6, 7 (Sesión, Presentación, Aplicación) |
| **Transporte** | **TCP**, **UDP**, ICMP | 4 (Transporte) |
| **Internet** | **IP** (IPv4, IPv6) | 3 (Red) |
| **Interfaz de Red** | Ethernet, Wi-Fi | 1, 2 (Física, Enlace de Datos) |

> TCP vs. UDP (Capa 4):
> 
> - **TCP (Protocolo de Control de Transmisión):** Orientado a la conexión. Es **confiable**. Verifica que cada paquete llegue en orden (como una llamada telefónica). Usa el "saludo de tres vías".
> - **UDP (Protocolo de Datagramas de Usuario):** Sin conexión. Es **rápido** pero no confiable. Simplemente "lanza" los datos y espera que lleguen (como enviar una postal).
> - **Ejemplos:**
>     - Usas **TCP** para cosas que *deben* ser perfectas: cargar un sitio web, enviar un email, descargar un archivo.
>     - Usas **UDP** para cosas donde la *velocidad* es más importante que la perfección: streaming de video (un píxel perdido no importa), juegos en línea, llamadas de voz (VoIP).

---

## 7. 📮 Protocolos de Internet (IPv4 vs. IPv6)

### IPv4

- **Qué es:** La versión "clásica" de direccionamiento IP.
- **Formato:** 32 bits (ej. `216.12.146.140`).
- **El Problema:** Solo permite ~4.3 mil millones de direcciones. **Ya se agotaron**.
- **Solución Temporal (Direcciones Privadas):** Se crearon rangos de direcciones que *no* son enrutables en Internet y pueden ser reutilizadas por cualquiera en su LAN privada.
| Rango | Uso Común |
| :--- | :--- |
| `10.0.0.0` a `10.255.255.254` | Redes corporativas grandes |
| `172.16.0.0` a `172.31.255.254` | Redes corporativas medianas |
| `192.168.0.0` a `192.168.255.254` | Redes domésticas y de pequeñas oficinas |
- **Loopback:** `127.0.0.1` siempre se refiere a "esta misma máquina". Es usado para pruebas (hacer `ping 127.0.0.1` es la primera prueba de diagnóstico de red).

### IPv6

- **Qué es:** La nueva generación.
- **Formato:** 128 bits (ej. `2001:0db8:0000:0000:0000:ffff:0000:0001` o `2001:db8::ffff:0:1` de forma acortada).
- **Beneficios:**
    - **Espacio de Direcciones:** Prácticamente ilimitado (340 sextillones de direcciones).
    - **Seguridad Mejorada:** **IPsec** (que cifra los paquetes) está integrado en el protocolo, no es un añadido opcional como en IPv4.
    - **Mejor QoS:** (Calidad de Servicio) para priorizar tráfico (como video).

---

## 8. 📶 Redes Inalámbricas (Wi-Fi)

- **Qué es:** Un estándar (IEEE 802.11) que permite la conexión a una red usando ondas de radio en lugar de cables.
- **Facilidad de Uso:** Permite la movilidad y es fácil de implementar.
- **Riesgo de Seguridad:** ¡Enorme! Tu "red" ya no termina en la pared; se transmite por el aire. Un atacante puede intentar romper tu red desde el estacionamiento.
- **Desde la perspectiva de un atacante:** Una red cableada requiere acceso físico (conectar un cable). Una red inalámbrica solo requiere estar dentro del rango de la señal.

---

## 9. 🚪 Puertos y Protocolos (Puertas y Servicios)

Este es uno de los conceptos más importantes para la ciberseguridad.

### Puertos Físicos vs. Lógicos

- **Puerto Físico:** El enchufe en un switch o router donde conectas un cable Ethernet.
- **Puerto Lógico (Socket):** Un número (0-65535) que actúa como una "puerta" en una computadora (una dirección IP). Permite que una sola IP gestione múltiples conversaciones a la vez, dirigiendo el tráfico al servicio correcto.

> Analogía:
> 
> - La **Dirección IP** es la dirección del edificio (`192.168.1.1`).
> - El **Puerto Lógico** es el número del apartamento o puerta (`80`, `443`, `22`).
> - El **Protocolo** (TCP/UDP) es *cómo* tocas la puerta (con acuse o no).

### Tipos de Puertos Lógicos

- **Puertos Conocidos (0-1023):** Reservados para servicios estándar (ej. HTTP, FTP, SSH).
- **Puertos Registrados (1024–49151):** Usados por aplicaciones específicas (ej. Microsoft SQL Server en el 1433).
- **Puertos Privados o Dinámicos (49152–65535):** Usados por tu computadora para conexiones temporales (ej. cuando tu navegador visita un sitio web, usa un puerto dinámico para recibir la respuesta).

### Protocolos Seguros vs. Inseguros (Crítico para Seguridad)

Un atacante que realiza *sniffing* en una red puede leer todo el tráfico enviado por protocolos inseguros (texto plano). Tu trabajo es forzar el uso de las alternativas seguras.

| Puerto (Inseguro) | Protocolo | Descripción del Riesgo | Puerto (Seguro) | Protocolo (Alternativa Segura) |
| --- | --- | --- | --- | --- |
| 21 | **FTP** | Transfiere archivos, pero las **credenciales van en texto plano**. | 22 | **SFTP** (SSH File Transfer) |
| 23 | **Telnet** | Administración remota. **Toda la sesión es en texto plano**. ¡Puedes robar la contraseña! | 22 | **SSH** (Secure Shell) |
| 25 | **SMTP** | Envío de correo. Originalmente no cifrado. | 587 / 465 | **SMTPS** (con STARTTLS o SSL/TLS) |
| 80 | **HTTP** | Tráfico web. **Todo el sitio se ve en texto plano**. | 443 | **HTTPS** (HTTP sobre TLS) |
| 143 | **IMAP** | Lectura de correo. Envía credenciales y correos en texto plano. | 993 | **IMAPS** (IMAP sobre SSL/TLS) |
| 389 | **LDAP** | Consultas de directorio (usuarios, contraseñas). En texto plano. | 636 | **LDAPS** (LDAP sobre SSL/TLS) |

---

## 10. 🤝 Estableciendo la Conexión (3-Way Handshake de TCP)

Para establecer una conexión **confiable** (TCP), el cliente y el servidor realizan un "saludo" de tres pasos:

1. **[Cliente] ➡️ [Servidor]: `SYN`**
    - **Cliente dice:** "Hola servidor, ¿estás ahí? Me gustaría sincronizar una conexión contigo."
2. **[Servidor] ➡️ [Cliente]: `SYN-ACK`**
    - **Servidor dice:** "¡Hola cliente! Recibí tu solicitud (`ACK`). Yo también quiero sincronizarme contigo (`SYN`)."
3. **[Cliente] ➡️ [Servidor]: `ACK`**
    - **Cliente dice:** "¡Recibido (`ACK`)! La conexión está establecida. Aquí van los datos."

Solo después de estos tres pasos, la transferencia de datos (ej. la carga del sitio web) comienza.

---

# 🛡️ Comprendiendo Amenazas y Ataques de Red

### 1. SIEM: Más Allá de un Colector de Logs

Un error común es ver el **SIEM (Security Information and Event Management)** como un simple repositorio de logs. Su verdadero valor está en generar **inteligencia accionable**.

- **Definición Práctica:** Es una "torre de control" que agrega datos de *todas* tus fuentes (firewalls, servidores, endpoints) y los correlaciona en tiempo real para encontrar patrones que un humano no vería.
- **Inteligencia Accionable:** No se trata de decir "ocurrió un evento". Se trata de decir "está ocurriendo algo *ahora mismo* que precede a un ataque".
- **Ejemplo del Podcast:** Joe Sullivan enfatiza la detección en la **fase de reconocimiento**.
    - **Evento (Ruido):** Un log de firewall muestra un escaneo de puertos desde una IP.
    - **Inteligencia (Señal):** El SIEM correlaciona ese escaneo con:
        1. Un correo de phishing recibido por un usuario (log del email gateway).
        2. Ese usuario visitando un sitio web malicioso (log del proxy).
        3. Intentos de enumeración de Active Directory desde la máquina de ese usuario (log de Windows).
    - **Acción:** El SIEM dispara una alerta de alta prioridad. El equipo de Respuesta a Incidentes (IR) puede aislar esa máquina *antes* de que el atacante logre el movimiento lateral o la exfiltración de datos.

### 2. Amenazas en la Nube: Nuevos Vectores, Mismos Principios

La nube no es inherentemente más o menos segura, simplemente tiene una **superficie de ataque diferente**. El modelo de amenazas cambia de la seguridad física de la red a la **gestión de permisos e identidades (IAM)**.

- **Ejemplo (Brecha de Capital One):**
    - **Vulnerabilidad:** Una **Falsificación de Solicitud del Lado del Servidor (SSRF)** en una aplicación web.
    - **Mecánica del Ataque:** El atacante (una amenaza interna) usó la aplicación vulnerable para "engañar" al servidor y hacerle una petición a sí mismo.
    - **Objetivo:** El **Servicio de Metadatos de la Instancia (IMDS)**. Este es un servicio interno de la nube (169.254.169.254) que la máquina virtual usa para obtener sus propias credenciales de acceso.
    - **Resultado:** El atacante usó el SSRF para consultar el IMDS, robar credenciales temporales y usarlas para acceder y exfiltrar datos de buckets S3.
    - **Lección:** La configuración incorrecta de IAM y la falta de protección contra SSRF fueron la causa raíz. Los principios de *mínimo privilegio* y *defensa en profundidad* siguen siendo reyes.

### 3. Ataques a la Cadena de Suministro: El Enemigo Interno

¿Cómo atacas a una organización que es una fortaleza? Atacas a sus proveedores de confianza.

- **Ejemplo (SolarWinds / Sunburst):**
    - **Vector:** Los atacantes comprometieron el **servidor de compilación** de SolarWinds.
    - **Técnica Brillante (y aterradora):** No modificaron el código fuente (que sería detectado). Inyectaron su malware *después* de la compilación pero *antes* de que el software fuera firmado digitalmente.
    - **Resultado:** Miles de clientes descargaron una actualización *legítima y firmada* de SolarWinds Orion que contenía un *backdoor*.
    - **Evasión:** El malware permaneció inactivo durante semanas. Luego, se comunicó con su **Comando y Control (C2)** usando tráfico que *imitaba* el tráfico normal de Orion, evadiendo la detección de los NIDS.
    - **Lección:** No puedes confiar ciegamente en el software de terceros, incluso si está firmado. La segmentación de red (para limitar lo que un servidor de monitoreo puede hacer) y el *threat hunting* (para buscar comportamientos anómalos) son cruciales.

### 4. Ofensiva Informada: La Diferencia Clave

Estos términos a menudo se usan incorrectamente. Saber la diferencia es vital.

- **🕵️‍♂️ Threat Hunting (Caza de Amenazas):**
    - **Mentalidad:** "Ya estamos comprometidos. ¿Cómo los encontramos?" (Asume la brecha).
    - **Acción:** Búsqueda *proactiva* y *continua* de Indicadores de Compromiso (IoCs) o Tácticas, Técnicas y Procedimientos (TTPs) *dentro* de tu red. No esperas una alerta.
    - **Ejemplo:** "Sabemos que el grupo APT-X usa `certutil.exe` para descargar payloads. Voy a buscar en *todos* los logs de endpoints ejecuciones de `certutil.exe` que se conecten a IPs externas."
- **🎯 Pruebas de Penetración (Pentesting):**
    - **Mentalidad:** "¿*Podemos* entrar? ¿Qué tan lejos podemos llegar?"
    - **Acción:** Un ataque *simulado*, *autorizado* y con un *objetivo* definido para encontrar y explotar vulnerabilidades y demostrar el impacto en el negocio.
    - **Ejemplo:** "Contratamos a un equipo para simular un ataque real y ver si pueden robar los datos de la base de clientes."
- **📋 Análisis de Vulnerabilidades (Scanning):**
    - **Mentalidad:** "¿Qué *vulnerabilidades conocidas* tenemos?"
    - **Acción:** Un escaneo (generalmente automatizado) que compara el software y las configuraciones de tus sistemas con una base de datos de vulnerabilidades conocidas (CVEs).
    - **Ejemplo:** "Ejecutar un escáner Tenable/Nessus/Qualys cada semana para encontrar servidores a los que les falten parches de seguridad."

### 5. El Impacto Real: Por Qué Existe la Regulación

Los ataques tienen consecuencias en el mundo real, lo que impulsa la creación de estándares.

- **Ejemplo (Incidente de TJ Maxx):**
    - **Vector:** Una red Wi-Fi insegura (WEP) en una tienda.
    - **Fallo Clave:** **Falta de segmentación de red.** El atacante pudo "pivotar" desde la red Wi-Fi de la tienda hasta la red corporativa que procesaba los datos de tarjetas de crédito (CHD).
    - **Consecuencia:** Robo de ~94 millones de números de tarjetas de crédito.
    - **Impacto en la Industria:** Este incidente fue un catalizador masivo para la adopción y el cumplimiento estricto del **Estándar de Seguridad de Datos de la Industria de Tarjetas de Pago (PCI DSS)**.
    - **Lección (PCI DSS):**
        - No es una *ley*, es una **obligación contractual** con las marcas de tarjetas (Visa, Amex, etc.). Si no cumples, te pueden multar o revocar tu capacidad de procesar pagos.
        - Un pilar de PCI es la **segmentación** para reducir el *alcance* (scope). La red que almacena, procesa o transmite datos de tarjetas debe estar *totalmente aislada* del resto de la red.

---

## 🐛 El Bestiario: Léxico de Amenazas

Un resumen rápido de los tipos de amenazas comunes.

| **Amenaza** | **Definición Práctica** | **Ejemplo Práctico** |
| --- | --- | --- |
| **Suplantación (Spoofing)** | Falsificar una identidad (IP, MAC, email) para parecer una fuente confiable. | Un atacante envía un email que *parece* venir de `soporte@tuempresa.com` (Email Spoofing). |
| **Phishing** | Un ataque de ingeniería social (generalmente por email) para engañar al usuario y hacer que revele información sensible. | Un email de "Netflix" que dice "Tu pago fue rechazado, haz clic aquí para actualizar tus datos" y te lleva a una página de inicio de sesión falsa. |
| **DoS / DDoS** | **Denegación de Servicio (Distribuida).** Inundar un sistema con tanto tráfico que los usuarios legítimos no pueden acceder a él. | Una *botnet* (ejército de dispositivos IoT infectados) envía millones de peticiones a un sitio web, saturando su servidor y ancho de banda. |
| **Virus** | Código malicioso que se adjunta a un programa legítimo y requiere *intervención humana* (ej. abrir un archivo) para propagarse. | Abres un `factura.exe` adjunto en un email. El virus se ejecuta e infecta otros archivos `.exe` en tu sistema. |
| **Gusano (Worm)** | Similar a un virus, pero es **autorreplicante** y se propaga *sin* intervención humana, explotando vulnerabilidades de red. | El gusano *WannaCry* escaneaba la red en busca de sistemas vulnerables a EternalBlue (SMBv1) y se propagaba a ellos automáticamente. |
| **Troyano (Trojan)** | Software que se disfraza de algo útil (un juego, un "limpiador de PC") pero contiene una carga maliciosa (payload). | Descargas un "crack" para Photoshop. Al ejecutarlo, instala en secreto un *keylogger* que roba tus contraseñas. El ransomware es un payload común de troyanos. |
| **Ataque en Ruta (MitM)** | **Man-in-the-Middle.** El atacante se sitúa *entre* dos partes (ej. tú y tu banco) e intercepta, lee o modifica la comunicación. | Te conectas al Wi-Fi "Gratis_Aeropuerto". El atacante intercepta tu tráfico y roba tu cookie de sesión cuando inicias sesión en una red social. |
| **APT (Amenaza Persistente Avanzada)** | Un actor de amenazas (a menudo un estado-nación) con alta sofisticación, recursos y paciencia, cuyo objetivo es el espionaje o sabotaje a largo plazo. | El grupo *SolarWinds* (APT29) es un ejemplo perfecto. Estuvieron en las redes de las víctimas durante meses (persistente) usando técnicas avanzadas. |
| **Amenaza Interna (Insider)** | Una amenaza que proviene de dentro de la organización (empleado, ex-empleado, contratista). Puede ser maliciosa o accidental. | *Maliciosa:* Un empleado descontento roba la base de datos de clientes antes de renunciar. *Accidental:* Un empleado de finanzas cae en un phishing y le da sus credenciales al atacante. |
| **Ransomware** | Malware que **cifra** los archivos de la víctima y exige un pago (rescate), generalmente en criptomonedas, a cambio de la clave de descifrado. | Un empleado abre un adjunto malicioso, y en minutos, todos los archivos del servidor compartido de la empresa están cifrados con la extensión `.locked`. |

---

## 🛡️ El Escudo: Herramientas de Detección y Prevención

No existe una "bala de plata". La seguridad se logra mediante una **defensa en profundidad** (múltiples capas de controles).

### 1. Detección y Monitoreo

- **IDS (Sistema de Detección de Intrusos):** 🚨 Es la "alarma de humo". Detecta actividad sospechosa y alerta, pero *no* la detiene.
    - **HIDS (Basado en Host):** Se instala en un *endpoint* (servidor, portátil). Monitorea eventos internos como llamadas al sistema, cambios en archivos de configuración y logs. *Ejemplo: Wazuh, OSSEC.*
    - **NIDS (Basado en Red):** Se coloca en un punto de la red (como un "tap" o puerto espejo) para analizar el *tráfico*. Busca firmas de ataques conocidos. *Ejemplo: Snort, Suricata.*
- **SIEM (Gestión de Eventos e Info. de Seguridad):** 🧠 La "torre de control". Como se vio antes, ingiere logs de *todas* las demás herramientas (HIDS, NIDS, Firewalls, AD) para correlacionar eventos y encontrar el "panorama general" del ataque. *Ejemplo: Splunk, Elastic SIEM, QRadar.*

### 2. Prevención y Protección

- **IPS (Sistema de Prevención de Intrusos):** ⛔️ Es un "guardia de seguridad armado". Es un IDS que tiene la capacidad de *bloquear* activamente el tráfico malicioso que detecta, en lugar de solo alertar.
- **Firewall:** 🧱 El "control fronterizo". Filtra el tráfico de red (entrante y saliente) basándose en un conjunto de reglas (puertos, IPs, protocolos).
    - **Firewalls de Próxima Generación (NGFW):** Son "más inteligentes". Pueden inspeccionar el contenido real de los paquetes (Capa 7) y entender qué *aplicación* está generando el tráfico (ej. bloquear Facebook pero permitir Salesforce, aunque ambos usen HTTPS).
- **Anti-malware / Antivirus:** 🔬 El "médico" del endpoint. Escanea archivos en busca de *firmas* de malware conocido (detección basada en firmas) o comportamientos sospechosos (detección heurística/comportamiento).

### 3. La Filosofía del CISO: Volver a lo Básico

Joe Sullivan y el documento de la Casa Blanca lo resumen perfectamente: la tecnología avanzada es inútil si no dominas los fundamentos.

1. **Inventario de Activos:** No puedes proteger lo que no sabes que tienes.
2. **Gestión de Parches:** Aplica actualizaciones de seguridad. La mayoría de las brechas explotan vulnerabilidades *ya conocidas* para las que existe un parche.
3. **Reducir la Superficie de Ataque:** Deshabilita servicios y protocolos innecesarios.
4. **Segmentación de Red:** (Lección de TJ Maxx). Aísla las redes críticas. Un atacante en la red de invitados no debería poder ver los servidores de la base de datos.
5. **Logs, Monitoreo y Alertas:** (Lección de SIEM). Asegúrate de estar registrando la actividad y de que *alguien* esté revisando esas alertas.
6. **Copias de Seguridad (Backups):** Tu mejor defensa contra el ransomware. Asegúrate de que estén *offline* (inmutables) y pruébalas regularmente.

---

# 🛡️ Infraestructura, Nube y Arquitectura de Red Segura

## 1. Infraestructura Física: El Centro de Datos On-Premises

Cuando una organización decide **poseer y operar** su propio centro de datos, asume la responsabilidad total de la infraestructura física. Esto requiere una planificación detallada de varios componentes clave:

### 🕋 Centro de Datos y Armarios de Cableado

La capa física es la base de la seguridad. Protegerla es vital para minimizar daños.

- **Componentes Críticos:** Aloja servidores, switches, conexiones de red/teléfono y equipos de ISP.
- **Seguridad:** El acceso físico no autorizado a un armario de cableado puede comprometer toda la red.

### 💨 HVAC (Calefacción, Ventilación y Aire Acondicionado)

Los equipos de alta densidad generan una enorme cantidad de calor.

- **Estándar de Operación:** El rango óptimo recomendado es entre **18°C y 27°C** (64°F - 81°F).
- **Monitorización:** Es esencial usar múltiples sensores (superior, medio, inferior del rack) para medir la temperatura.
- **Riesgos Adicionales:** No solo es el calor; el polvo, los contaminantes y las fugas de agua/gas deben ser monitoreados con alarmas integradas. Un fallo de HVAC puede llevar a un apagado automático de los servidores (pérdida de disponibilidad) o a daños permanentes.

### ⚡ Energía

La electricidad es la sangre del centro de datos. Debe ser constante y limpia.

- **Suministro Ininterrumpido (UPS):** Son baterías de respaldo dimensionadas para soportar la carga crítica (servidores) el tiempo suficiente para que arranquen los generadores.
- **Generadores de Respaldo:** Suministran energía a largo plazo durante un apagón. Deben ser dimensionados para soportar tanto la carga crítica como la infraestructura de apoyo (HVAC, luces, etc.).
- **Pruebas:** Es vital probar regularmente el sistema de *failover* (conmutación por error) a la alimentación alternativa.

### 🔥 Sistemas contra Incendios

Un desafío único: el agua (usada para apagar incendios) destruye los equipos electrónicos.

- **Rociadores (Sprinklers):** Generalmente requeridos por código en edificios comerciales.
- **Riesgo:** El agua y la electricidad no se mezclan. Una fuga o activación puede ser tan destructiva como el fuego.
- **Solución (Sistemas de Tubería Seca):** Una mitigación común. Las tuberías sobre el centro de datos están vacías. El agua solo se libera en esa sección cuando un sensor detecta *activamente* un incendio, reduciendo el riesgo de fugas accidentales.

### 🔄 Redundancia

El concepto clave de la **alta disponibilidad (HA)**. Diseñar sistemas con componentes duplicados para que no exista un punto único de fallo (SPOF - Single Point of Failure).

- **Ejemplo de Energía:** Un servidor con dos fuentes de alimentación (PSU), cada una conectada a un UPS diferente. Cada UPS está conectado a una línea eléctrica distinta, y esas líneas están respaldadas por generadores redundantes (quizás con diferentes tipos de combustible, ej. diésel y gas natural).
- **Ejemplo de Servicios:** Una organización crítica (como un hospital) puede contratar a dos compañías eléctricas diferentes y estar en dos redes eléctricas separadas.
<img width="791" height="713" alt="image" src="https://github.com/user-attachments/assets/f7218c39-6672-4826-80cf-d46c7d3708fa" />

---

## 2. Acuerdos, Proveedores y Servicios

La infraestructura no siempre se gestiona internamente. Aquí es donde entran los acuerdos y los proveedores externos.

### 🤝 Memorandos (MOU/MOA) vs. Acuerdos de Nivel de Servicio (SLA)

Ambos son acuerdos, pero con propósitos muy diferentes, cruciales para la **Continuidad del Negocio (BC)** y **Recuperación ante Desastres (DR)**.

- **MOU (Memorando de Entendimiento) / MOA (Memorando de Acuerdo):**
    - **Definición:** Un acuerdo (a menudo no vinculante legalmente) entre dos o más partes que describe un plan de cooperación.
    - **Propósito:** Generalmente para BC/DR. Establece que las partes se ayudarán mutuamente en caso de una emergencia.
    - **Ejemplo Práctico:** El **Hospital A** y el **Hospital B** (que son competidores) firman un MOA. Si un incendio inhabilita al Hospital A, pueden enviar personal y sistemas críticos a operar temporalmente desde las instalaciones del Hospital B.
- **SLA (Acuerdo de Nivel de Servicio):**
    - **Definición:** Un **contrato legalmente vinculante** que define el nivel de servicio específico que un proveedor debe entregar a un cliente.
    - **Propósito:** Define métricas granulares, rendimiento y penalizaciones.
    - **Ejemplo Práctico:** Un SLA con un proveedor de nube debe especificar:
        - **Disponibilidad:** "99.99% de tiempo de actividad mensual".
        - **Rendimiento:** "Acceso a los datos de respaldo en menos de 10 minutos".
        - **Soporte:** "Dos técnicos Nivel 2 disponibles 24/7/365".
        - **Seguridad:** "Derecho del cliente a auditar el cumplimiento normativo".
        - **Estrategia de Salida:** Cómo y en qué formato se devolverán los datos del cliente al finalizar el contrato.

> ¡Cuidado! 👁️ Al revisar un SLA de nube, "100% de accesibilidad" debe ser definido. ¿Es acceso directo a tus datos, o solo acceso al portal web del proveedor? Los equipos legales deben revisar esto minuciosamente.
> 

### 👨‍💼 Proveedor de Servicios Gestionados (MSP)

Una empresa externa que gestiona de forma proactiva los activos o funciones de TI de un cliente.

- **Servicios Comunes:**
    - Gestión de infraestructura de TI completa.
    - Servicio de *Help Desk* (Mesa de Ayuda).
    - Gestión de nóminas.
    - Monitoreo y respuesta de seguridad (ej. **MDR - Managed Detection and Response**), donde el MSP supervisa firewalls y herramientas de seguridad.

---

## 3. ☁️ Computación en la Nube (Cloud Computing)

La nube es un modelo de entrega de servicios de TI, no un lugar. La definición estándar de la industria proviene del **NIST SP 800-145**:

> "Un modelo para permitir el acceso a la red ubicuo, conveniente y bajo demanda a un conjunto compartido de recursos informáticos configurables (como redes, servidores, almacenamiento, aplicaciones y servicios) que se pueden aprovisionar y liberar rápidamente con un mínimo esfuerzo de gestión o interacción del proveedor de servicios."
> 

### ✨ Características Esenciales

- **Servicio Medido:** Pagas solo por lo que usas (como la electricidad).
- **Reducción de Costos (TCO):** Elimina la necesidad de comprar y mantener hardware (reduce el *CapEx*).
- **Elasticidad y Escalabilidad Rápida:** Puedes escalar recursos (hacia arriba o hacia abajo) en minutos, sin necesidad de comprar hardware.
- **Agrupación de Recursos (Resource Pooling):** El proveedor comparte sus recursos entre múltiples clientes (multitenancy).
<img width="929" height="564" alt="image" src="https://github.com/user-attachments/assets/bbc22ddb-35a5-4b51-acff-e3d837b0bf25" />

### 📦 Modelos de Servicio (La Matriz de Responsabilidad)

El modelo de servicio define **quién gestiona qué**.

| **Modelo** | **El Cliente Gestiona (Tú)** | **El Proveedor Gestiona (Cloud)** | **Ejemplo Práctico** |
| --- | --- | --- | --- |
| **SaaS** (Software) | Tus Datos, Acceso de Usuario | **TODO:** Aplicación, Runtime, OS, Hardware, Red. | **Gmail, Salesforce, Office 365** |
| **PaaS** (Plataforma) | Tus Aplicaciones, Tus Datos | Runtime, Middleware, OS, Servidores, Red. | **Heroku, AWS Elastic Beanstalk** |
| **IaaS** (Infra.) | Aplicaciones, Datos, Runtime, OS | **Solo lo básico:** Servidores, Almacenamiento, Red. | **AWS EC2, Google Compute Engine** |

### 🌐 Modelos de Implementación

Definen **dónde** reside la nube y **quién** puede acceder a ella.

- **Pública:** Alojada por un CSP (como AWS, Azure, GCP) y vendida al público general. Los recursos son compartidos.
- **Privada:** Infraestructura de nube dedicada exclusivamente a una sola organización. Puede estar alojada *on-premise* o por un tercero, pero no es compartida.
- **Híbrida:** Una combinación de nube pública y privada, orquestadas para trabajar juntas. Permite mantener datos críticos en la nube privada mientras se usa la pública para cargas de trabajo elásticas o menos sensibles.
- **Comunitaria:** Compartida por varias organizaciones que tienen intereses comunes (ej. regulaciones, misión). Ejemplo: Una nube para el sector financiero o para agencias gubernamentales.

---

## 4. 📐 Diseño y Arquitectura de Red Segura

Diseñar una red segura se basa en principios de control, aislamiento y capas.

### 🏰 Defensa en Profundidad (Defense in Depth)

La filosofía de seguridad fundamental: **la seguridad debe ser en capas**. No se debe depender de un solo control (como un firewall perimetral). Si un atacante supera una capa, debe encontrarse con otra.

- **Ejemplo del Castillo:** Un castillo no solo tiene un muro exterior. Tiene un foso, el muro, guardias en el muro, una puerta fortificada, guardias internos y finalmente una bóveda cerrada con llave.
- **Capas en Ciberseguridad:**
    1. **Políticas y Concienciación** (Control Administrativo)
    2. **Físico** (Cerraduras, guardias)
    3. **Perímetro** (Firewall principal, Honeypots)
    4. **Red Interna** (Segmentación, IDS/IPS internos)
    5. **Host** (Antivirus, EDR, Parches, Firewall de Host)
    6. **Aplicación** (WAF, escaneo de código)
    7. **Datos** (Cifrado, Gestión de Acceso - IAM)
<img width="932" height="701" alt="image" src="https://github.com/user-attachments/assets/2268e6c6-bb96-4024-949d-b765fb09bf6d" />

### ⛔ Confianza Cero (Zero Trust)

Un modelo de seguridad moderno que evoluciona la Defensa en Profundidad.

- **Filosofía Central:** "Nunca confíes, siempre verifica" (Trust No One, Verify Everything).
- **Suposición:** Asume que la red *ya está comprometida*. Los atacantes *ya están dentro*.
- **Enfoque:** La seguridad no se basa en el *perímetro* (dónde estás), sino en la *identidad* (quién eres). Se requiere autenticación y autorización **frecuentes** para **cada recurso**, sin importar desde dónde te conectes.
- **Ejemplo del Concierto:**
    - *Defensa en Profundidad:* Muestras tu ticket en la puerta principal y puedes vagar libremente, incluso quizás colarte en el backstage.
    - *Confianza Cero:* Muestras tu ticket en la puerta (Perímetro), te lo vuelven a escanear para entrar a la sección de pista (Segmento), y te piden una credencial especial para entrar al backstage (Recurso).
<img width="927" height="569" alt="image" src="https://github.com/user-attachments/assets/7b861bb9-efbb-4214-ada5-9cda85990447" />

### 🧩 Segmentación de Red y Aislamiento

La segmentación es la *práctica* de dividir una red grande en sub-redes más pequeñas y aisladas para controlar el flujo de tráfico (especialmente el tráfico **Este-Oeste** o lateral).

| **Técnica** | **Definición** | **Propósito Principal** |
| --- | --- | --- |
| **VLAN** (Virtual LAN) | Segmentación **Lógica** a Nivel 2 (en switches). Agrupa dispositivos sin importar su conexión física. | Organizar la red, limitar *broadcast*. Ej: VLAN de VoIP, VLAN de Invitados. |
| **DMZ** (Zona Desmilitarizada) | Una subred aislada entre Internet (no confiable) y la red interna (confiable). | Alojar servicios públicos (servidor web, email) sin exponer la red interna. |
| **Microsegmentación** | Segmentación **extremadamente granular** (a nivel de *workload* o aplicación individual). | **Prevenir el movimiento lateral**. Es un pilar de *Zero Trust*. Ej: El Servidor Web-A *solo* puede hablar con la BBDD-A por el puerto 3306, y nada más. |

### 🤖 Riesgos de IoT y Sistemas Embebidos

- **Dispositivos Embebidos:** Computadoras con funciones limitadas dentro de un sistema mayor (impresoras, HVAC, dispositivos médicos).
- **IoT (Internet de las Cosas):** Dispositivos conectados a Internet (cámaras, termostatos, TVs).
- **El Riesgo:** A menudo tienen múltiples vectores de red (Wi-Fi, Bluetooth), son difíciles de parchear y tienen contraseñas débiles. Un termostato inteligente comprometido puede ser la puerta de entrada a la red corporativa.
- **La Solución:** **Segmentación estricta**. Todos los dispositivos IoT deben estar en su propia **VLAN** o segmento de red, **aislados** y sin acceso a los servidores críticos.

### 🚪 Control de Acceso a la Red (NAC)

Un sistema NAC actúa como el "guardia de seguridad" en la puerta de la red (cableada o inalámbrica).

- **Función:** Interroga a los dispositivos *antes* de permitirles el acceso a la red.
- **Validación de Postura (Posture Assessment):** Comprueba que el dispositivo cumple con la política de seguridad.
    - ¿Tiene el antivirus actualizado?
    - ¿Tiene los últimos parches del SO?
    - ¿Es un dispositivo corporativo o un BYOD?
- **Acción:** Basado en la política, el NAC puede:
    1. **Permitir** acceso total.
    2. **Denegar** el acceso.
    3. **Poner en Cuarentena** en una VLAN restringida (ej. solo con acceso a Internet, o solo a los servidores de remediación para actualizarse).
<img width="451" height="336" alt="image" src="https://github.com/user-attachments/assets/5fb8d156-89f8-4e8e-ad25-47f72ea823cb" />

### 🔒 Red Privada Virtual (VPN)

Crea un **túnel de comunicación** (generalmente cifrado) que permite extender una red privada sobre una red no confiable (Internet).

- **Acceso Remoto:** Un empleado trabajando desde casa se conecta a la red corporativa como si estuviera físicamente en la oficina.
- **Sitio-a-Sitio:** Conecta dos oficinas (ej. Santiago y Lima) de forma segura a través de Internet, como si fueran una sola red.
