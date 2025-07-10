## Capas de seguridad

A continuación, voy a explicar las distintas capas de seguridad que hay desde abajo hacia arriba, para mostrar cómo se va construyendo la seguridad en distintos niveles.

### 3. Cifrado TLS

TLS es un protocolo criptográfico que funciona debajo de la capa de aplicación (ver modelo OSI). Su función es cifrar las comunicaciones entre el cliente y el servidor, convirtiendo las peticiones HTTP en HTTPS para que el contenido no pueda ser leído ni alterado fácilmente.

TLS también funciona con claves asimétricas: una pública que se envía al cliente, y una privada que se mantiene en el servidor. La clave pública se encarga de cifrar los paquetes que van a ser enviados al servidor, y el servidor utiliza su clave privada para descifrar los mensajes que le llegan.

TLS se establece al validar una conexión segura entre el cliente y el servidor, este proceso se denomina **Handshake**, que no se va a profundizar demasiado en esta guía.

Dentro del handshake, se encuentran varios pasos al establecerse el protocolo TLS, estos pasos involucran un intercambio de claves bastante engorroso, así que voy a intentar explicarlo a continuación de la manera más amigable posible.

Una vez configurado qué cifrado se va a utilizar para los paquetes (esto lo hace el servidor automáticamente al negociar los parámetros del Handshake con el cliente).

Sabiendo que el servidor posee las dos claves (pública y privada):

1. El cliente inicia la conexión al servidor (por ejemplo, ingresando a un sitio con `https://`).
2. El servidor envía su clave pública al cliente.
3. El cliente genera una nueva clave, esta vez es una clave simétrica AES temporal.
4. Luego, el cliente cifra esa clave simétrica con la clave pública del servidor y se la envía.  
5. El servidor usa su clave privada para descifrar esa clave que le envió el cliente.

Luego de este proceso, la conexión ya se encuentra cifrada para poder enviar peticiones y recibir información de forma segura.

TLS puede parecer complejo por dentro, pero la realidad es que esto ocurre automáticamente, el desarrollador casi nunca tiene que preocuparse, se maneja sin intervención manual.

### Tips relevantes

- Si el descifrado falla significa que la clave no viene de un cliente legítimo.  
- Si el cifrado es correcto se acepta y a partir de ahora todos los paquetes viajarán cifrados.  
- Todo este proceso ocurre dentro del handshake.  
- La seguridad viene del hecho de que sólo el servidor tiene la clave privada para poder descifrar.

