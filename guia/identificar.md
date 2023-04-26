---
layout: page
title: Identificar
subtitle: El tipo de bloqueo
---


Algunas preguntas que podemos hacernos inicialmente son las siguientes:

* ¿Está bloqueado *todo* internet o solo unas *páginas o servicios*?

* ¿El bloqueo es en la red celular o es el internet fijo o ambas?

* ¿El bloqueo sucede solo en un ISP, en varios o en todos lo que hay en la zona de la caida?

* ¿ Si el bloqueo no es *total*, qué servicios o páginas de internet específicos están siendo bloqueados?

---  
## Bloqueos Físicos
Físicamente hay dos formas fundamentales en que se puede cortar la conexión a internet:
### Corte de cables:
Esta sería la forma mas "dura" de generar un bloqueo y normalmente termina en un bloqueo **total**.
### Jamming:
Esta técnica consiste en generar "ruido electromagnético" con un aparato en un lugar, de tal forma que las ondas de radio que reciben o envían los dispositivos invlucrados en las conexiones (teléfonos, antenas de telefonía celular o dispositivos wifi) no puedan encontrar o distinguir las señales legítimas que se pierden con el ruido generado por el *jammer* (aparato que genera el ruido electromagenético).

 Esto normalmente ocasiona una caida **total**  del servicio de internet y en la mayoría de las casos tambén bloquea las llamadas de la red celular. 
 
 En el contexto de los bloqueos de internet el jamming se usa para bloquear el internet movil o wifi. Sin embargo puede usarse para bloquear otros tipos de conexiones que usan ondas de radio como los satélites, conexiones bluetooth, packet radio, etc.

## Bloqueos Lógicos
En este caso nos referimos a los bloqueos se suceden en los servidores o dispositivos que transportan los datos o las conexiones (routers, firewalls, muddle boxes, etc)

### Bloqueo por DNS:
Es la forma mas común de bloquear al acceso a una página o un servicio de internet. Normalmente cuando nos conectamos a internet, nuestros dipositivos usan los servidores de DNS de los ISPs a lo que nos estamos conectado. 

Si el ISP manipula este servidor puede proveernos una IP que no corresponde a la página o al servicio a que queremos acceder y normalmente nos redireccionará a una página controlada por el mismo ISP que nos informará del bloqueo. 

Por ejemplo, si intentamos entrar a www.google.com y esta página está bloqueada por DNS, cuando nuestros dispositivos consulten (internamente) cual es la direccion IP de google no nos responderá con la verdadera sino con otra negándonos el acceso a www.google.com.

En la mayoría de los casos es posible esquivar este bloqueo cambiando las direcciones IP de los servidores de DNS que haya tomado nuestro dispositivo automáticamente.

### Bloqueo de direcciones IP:
Igualmente, los ISPs pueden bloquear el acceso a un dirrección o a un grupo de recciones IP que traten de ser accedidas por sus clientes.

Este tipo de bloqueo es mas dificil de esquivar que el de DNS ya que aunque cambiemos las direcciones IP de los servidores DNS de nuestro dispositivo no podremos llegar al destino final de nuestra conexión porque otros aparatos ajenos a nuestro manejo bloquearán la conexión.

Usar VPNs, proxys, SOCKS, Tor, i2p u otros servicios de anonimización de conexiones puede ser útil a la hora de esquivar este tipo de bloqueo, sin embargo, es posible bloquear total o parcialmente estos servicios.

### Bloqueo de protocolos (puertos):
Normalmente las conexiones de internet no solo requieren una direccion IP para llegar a su destino, sino un número de puerto que (normalmente, de nuevo) corresponde a un protocolo de comunicaciones, por ejemplo cuando nos conectamos a una página web cuya conexion es insegura el puerto correspondiente es el 80, si la página es segura el puerto será el 443 o cuando enviamos un correo desde un cliente com Thunderbird nos conectamos con el el puerto 25.

Los IPSs pueden bloquear el acceso a un puerto de estos asociado a una dirección IP, a un cojunto de direcciones IPs o simplemente a cualquier conexión que trate de alcanzar un puerto específico.

Es importante saber, que la asignación de estos puertos corresponde a un estandar que no necesariamente tiene que cumplirse, por ejemplo un servidor web inseguro no necesariemente se tiene que encontrar en el puerto 80 sino que puede operar en cualquiera como el 8080 o el 1234. 

Cambiar el puerto estandar de un servicio de internet puede ser una forma de evadir este tipo de bloqueos. igualmente los metodos de evasion mencionados en el **bloqueo por IP* pueden ser útiles en estos casos.

### BLoqueo de rutas:
Cuando queremos hacer una conexión a través de internet, nuestros dispositivos le "dicen" a nuestro ISP que queremos llegar a una dirección IP específica. A su vez, nuestro ISP consulta una tabla de *rutas* que le indican hacia donde debe enviar nuestra conexión, esta tabla no necesariamente tiene la ruta donde se encuentra el servidor con la IP a la que queremos acceder, sino que de acuerdo a esa tabla envía la conexión a otro enrutador que contiene otra tabla que le indica a donde enviar la conexión y así sucesivamente hasta llegar al servidor final.

Si el ISP bloquea una de estas rutas nos impedirá llegar a ciertos lugares de internet. En este caso aplican las estrategias de evasión usadas en el bloqueo por IP o por protocolo.

### Denial of Service:
Este bloqueo no sucede en los ISPs sino en el destino final de nuestra conexión y pude deberse a dos factores fundamentales:

1. Un ataque de denegación de servicio distribuido (DDoS) que consiste en enviar una cantidad enorme de conexiones a un servidor de tal forma que otras conexiones legítimas no puedan ser procesadas por el servidor porque ha exedido sus capacidades.
2. un cyberataque que simplemente "daña" el servidor al que queremos conectarnos impidiendo su normal funcionamiento.

Evadir este ataque no depende de quien inicializa la conexión sino de los encargados del servidor en cuestión y normalmente se debe contrar los servicios de un CDN (Content Delivery Network) que mitigue este tipo de ataques.
 
### Bloqueo por inspección de paquetes:
El Deep Packet Inspection (o la inspección profunda de paquetes, en español) es una técnica de montioreo de los datos que llevan las conexiones que hacemos. Si nuestra conexion no es segurura (no está encriptada) el ISP puede ver todos los datos que enviamos y recibimos y con base en esto bloquear una conexión. Por otro lado, si nuestra conexión es segura, se pueden usar metadatos de la conexión como el tamañom la hora o el origen para bloquear una conexión.

Evadir este tipo de bloqueo es complicado, y depnderá del tipo de inspección que haga el ISP, sin embargo es poco común como método de bloqueo y es mas bien usada con fines de vigilancia.

### Bloqueo basado en la inicialización de conexiones seguras (TLS/SSL/HTTPS):

Este tipo de bloque es poco común pero se ha visto en uso por el Gran Firewall de China.

Antes de que una conexión *segura* sea segura se transmiten una serie de datos de forma *no segura* que permiten inicializar la conexión *segura*. Con base en estos datos un ISP puede tomar la determinación de bloquear una conexión.

Existen metodos de de evasión experimentales para este tipo de bloqueo y vigilancia que están en desarrollo, sin embargo los métodos descritos en bloqueos por IP o por protocolo son válidos para este tipo de bloqueo.

---
## Nota sobre los métodos de evasión:

Es importante notar que los métodos de evasión descritos en esta seccion son posibilidades que se tienen que explorar en el momento del bloqueo, por ejempo, es posible que un bloqueo por DNS no se pueda evadir con una VPN por que el protocolo de la VPN está bloqueado o un Bloque de IP corresponda precisamente a las direcciones IP de los nodos de entrada de Tor. Por lo tanto, no siempre funcionan y en algunos casos se necesitará una combinación de estos para poder evadir el bloqueo.
