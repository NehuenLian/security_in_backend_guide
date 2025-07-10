## 4. Certificado X.509

Un certificado X.509 es una credencial que se utiliza para identificar a una entidad (como un servidor). Además de asegurar que el servidor es legítimo, también sirve para cifrar la comunicación y firmar datos para garantizar su autenticidad.

El certificado es emitido y firmado por una entidad llamada **Autoridad Certificadora (CA)**, y hay varias alrededor del mundo.

- Físicamente, una CA es también un servidor o conjunto de servidores, que operan bajo políticas de seguridad muy estrictas para emitir certificados.

Cuando un cliente (como un navegador) quiere conectarse a un servidor, durante el proceso de **Handshake**, el servidor envía su certificado al cliente y este lo verifica.

### ¿Cómo se verifica el certificado?

Todos los navegadores tienen almacenada una lista de CAs donde buscan y averiguan la legitimidad del certificado recibido.

### Proceso de verificación dentro del Handshake (simplificado):

1. El cliente inicia con un `ClientHello`.  
2. El servidor responde con un `ServerHello` y envía su certificado.  
3. El cliente verifica que ese certificado sea válido, consultando a las CAs que tiene almacenadas.  
4. Si todo está bien, continúa el proceso del Handshake para establecer la sesión y cifrarla.

### Funcionamiento criptográfico del certificado X.509

Es un mecanismo de cifrado asimétrico, que funciona con una clave pública y una clave privada.

- La clave pública está alojada en el certificado X.509.  
- La clave privada está en el servidor. Este es el par asimétrico.

La CA que emite el certificado tiene su propia clave privada y la usa para firmarlo. Esta firma es el resultado de aplicar un hash a los datos del certificado más la clave privada de la CA.

El cliente calcula el hash del contenido del certificado recibido y usa la clave pública de la CA para verificar la firma digital que lo acompaña. Si la verificación es exitosa, significa que el certificado es válido y fue firmado por una CA confiable.

### Tip

- A veces el certificado del servidor no está firmado directamente por una CA raíz, sino por una CA intermedia. En ese caso, el servidor también envía la cadena de certificados intermedios para que el cliente pueda construir la “cadena de confianza” hasta una CA raíz conocida.
