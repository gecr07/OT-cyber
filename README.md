# OT-cyber

## Certificaciones en el tema

AUnque estas son muy caras.

- ISA 62443 Certification Path
- SANS
- CISA (not a certification but courses)

## Mandatory Reding Each Year

Tenemos varios recusos entre los que destacan:

- DBIR Data Breach Investigations Report
- ICS/OT Cyber Security
- Protect OT Cyber Security Podcast
-  Control Loop Dragons
-  Industrial Security Podcast

Estos se van actualizando año con año con los principales ataques brechas informacion etc.
  

## OT vs IT

En el contexto de la ciberseguridad, "OT" se refiere a "Tecnología Operativa" (Operational Technology) e "ICS" a "Sistemas de Control Industrial" (Industrial Control Systems).

Tecnología Operativa (OT): Se refiere al hardware y software que se utiliza para controlar y monitorear procesos físicos en industrias como la manufactura, la energía, el transporte y las utilities (servicios públicos como agua, electricidad, etc.). Los sistemas OT están diseñados para controlar maquinaria, infraestructura y otros equipos en entornos industriales y suelen estar separados de los sistemas de tecnología de la información (IT) tradicionales. Sin embargo, la convergencia de OT e IT está aumentando, lo que plantea nuevos desafíos de ciberseguridad.

Sistemas de Control Industrial (ICS): Son un subconjunto de la tecnología operativa y se refieren específicamente a los sistemas utilizados para controlar procesos industriales. Incluyen sistemas de control distribuido (DCS), sistemas de control de supervisión y adquisición de datos (SCADA) y otros sistemas de automatización. Estos sistemas son críticos para la operación de infraestructuras esenciales y, por lo tanto, son objetivos potenciales para ataques cibernéticos.

La seguridad en OT y ICS es fundamental debido a la naturaleza crítica de los procesos que controlan. Un ataque cibernético exitoso en estos sistemas puede tener consecuencias devastadoras, incluyendo interrupciones en la producción, daños a equipos costosos y, en casos extremos, riesgos para la seguridad humana y el medio ambiente.

Pues el OT es la infraestructura que esta en plantas y como regla ***No se debe permitir que el OT este directamente conectado al IT***

## ICS vs SCADA

En resumen, ICS es el término que abarca todos los sistemas de control utilizados en entornos industriales, mientras que SCADA se refiere a un tipo específico de ICS diseñado para la supervisión y control de procesos distribuidos geográficamente. Aque en el curso lo comparan con una LAN(ISS) y una WAN(SCADA).


## ISA 62443 The Gold Standard for ICS/OT Cyber Security

Este es un estandar del gobierno de Estados Unidos sobre como asegurar OT.

![image](https://github.com/gecr07/OT-cyber/assets/63270579/9ec5486d-b2c5-424d-8ec1-970bfe0d1653)

## Control System Types

### Field Devices

Estso dispositivos son sensores, actuadores, motores.

### PLC

Tienen su propio procesador, memoria y almacenamiento son programados usando software espacial y pueden trabajar en entornos rudos. ( Los atacantes es comun atacan este tipo de dispositivos comunmente). Aqui dice viene con dos modos tiene un interruptor fisico Program Mode y Run Mode ( y algunos modelos pueden traer mas). Program mode para hacer updates en el codigo. Run mode pues solo read only y para hacer solo su funcion. ( se puede hacer el update remoto o local). *** Se tienen que poner en modo RUN MODE para estar seguros***. 

### Distributed Control System (DCS)

Provee monitoreo y control de multiples sisttema estamos hablando de algo muy grande 35 000 algo asi. Allows for availability and control over multiple systems. Se asemeja al Active Directory en Windows.
Los DCS están diseñados para ser funcionales en instalaciones a gran escala, proporcionando control centralizado y funcionamiento continuo. Se utilizan comúnmente en industrias como la petroquímica, la farmacéutica, la energía, y otras operaciones de procesamiento y fabricación

### Supervisory Control and Data Acquisition (SCADA)

Provee monitorieo y control sobre sistemas remotos. Se utilizan para automatizar tareas en vez de mandar a trabajadores. Tuberías y distribución y transmisión de energía.

### Human Managment Interface (HMI)

Provides a graphical interface to allow human users to interact with a control system such as a PLC. Usan muchos de estos dispositivos Windows. ***ALGO QUE HAY QUE PROTEGER*** . Lo convierte en un objetivo principal a través de IP.

### Safety Instrumented System (SIS) ***SUPER IMPORTANTE***

Acts as a failsafe for an ICS/OT facility. Designed explicity to protect human life and the facility. Allow the site to be shutdown safely in the event an unsabe, or potenttially unsafe, condition is alerted on. Safety functions are designed as safety instrumented functions(SIF). Designed separately from the rest of the networks. El malware Triton en 2017 tenia la capacidad de desactivar estos sistemas lo que podria causar un incidente. Se puede decir que ese malwate tenia de target vidas humanas. Por ejemplo puede probocar una explocion. ( se recomienda ponerlo en un segmento aparte de todo) Para que un atacante si quiere tomar el control de esto tenga que estar en el sitio.

### Engineering Workstation (EWS)

SOn computadoras normales donde los ingenieros programan PLCs.Se tienen que tener contol de estos assets y de la informacion que ahi esta.

### Data Historian EASY TO ATTACK TARGET

Tipicamente es una base de datos tradicional corriengo un sistema operativo como Windows Server con un MS SQL Server. Se usa para procesar y guardar datos. Mucho de los entornos tienen multiples data historias para asegurar la aquitectura entre ICS/OT y IT networks. Los atacantes van intentar esto casi siempre. Se sacan estadistiicas de la red OT para la red IT.

## Other COntrol System Types

Existem as tipo de sistemas de control aunqueno tam apliamente usados como los anteriores pero por ejemplo uno muy famosos son los "RTU" remote terminal units.

## Wireshark

NOs puede servir para snifear la red y pues entiende muchos protocolos como el usando en la industria ModBus. Igual otros como S7 dmp3 backnet.


## Protocolos que se usan comunmente

Cada uno de estos protocolos tiene su propio conjunto de especificaciones y usos, pero todos interactúan con TCP/IP de una manera u otra para facilitar la comunicación a través de redes más grandes y más complejas, tanto dentro de la propia planta como a través de sitios remotos.

### Modbus

Modbus es uno de los protocolos de comunicación más antiguos y ampliamente utilizados en sistemas industriales. Puede operar sobre TCP/IP utilizando Modbus TCP o sobre una conexión serie como Modbus RTU o Modbus ASCII. Cuando se usa Modbus TCP, el protocolo utiliza TCP (Protocolo de Control de Transmisión) para garantizar la entrega confiable de comandos entre dispositivos de automatización.

Es uno de los mas comunes hoy en dia. Mobus corre ( supongo por defecto) en el puerto 502 TCP/IP. Funciona similar a SNMP permite leer y escribie system variables en cliente servidor configuration. Se pueden testear usando NMAP, Modbus-cli, Scapy, Metasploit, and others...

Modbus Function Codes

![image](https://github.com/gecr07/OT-cyber/assets/63270579/40809e42-3fbb-4507-92eb-6e970219978c)

Others

![image](https://github.com/gecr07/OT-cyber/assets/63270579/11f169c6-927a-4c96-bc0d-b214c365d434)

Entonces toma en cuenta que es un protocolo cliente servidor. Por ejemplo puedes hacer un request para preguntar si todos los PLC estan en modo read only.


### S7comm (Siemens S7 Communication)

S7comm es un protocolo propietario desarrollado por Siemens para la comunicación con sus sistemas de control lógico programable (PLC). Utiliza TCP/IP para la comunicación en redes Ethernet y es específicamente para la comunicación entre PLCs de Siemens y otras aplicaciones que necesitan leer/escribir datos desde y hacia los PLCs.

### OPC (OLE for Process Control)

OPC es un conjunto de estándares de comunicación diseñados para permitir la interacción entre diferentes sistemas de automatización industrial. Originalmente dependía de la tecnología OLE/COM de Microsoft, lo que significa que estaba más ligado a los sistemas Windows y no utilizaba directamente TCP/IP.

### OPC UA (OPC Unified Architecture)

OPC UA es la evolución de OPC y está diseñado para ser independiente de la plataforma, interoperable y seguro. Utiliza TCP/IP para la transmisión de datos y también soporta otros métodos como AMQP y MQTT, que son protocolos más modernos diseñados para sistemas de mensajería y IoT. OPC UA está estructurado para utilizar el modelo de cliente-servidor y puede funcionar sobre HTTPS, agregando una capa adicional de seguridad.

## Wireless Industrial Control Protocols
Los protocolos de control industrial inalámbricos pueden variar ampliamente, pero muchos de ellos, como WirelessHART o ISA100.11a, se basan en estándares que utilizan TCP/IP o adaptaciones de este para permitir la comunicación inalámbrica entre dispositivos. Estos protocolos están diseñados para soportar la fiabilidad y la seguridad necesarias en entornos industriales hostiles y suelen operar en capas superiores a las de la comunicación de red básica, proporcionando mecanismos para la gestión eficiente del espectro y la energía.




# Recursos

> https://github.com/ITI/ICS-Security-Tools










