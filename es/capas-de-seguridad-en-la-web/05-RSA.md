## 5. RSA

RSA es un algoritmo criptográfico **asimétrico**. Aunque puede usarse para cifrar datos, en este contexto nos interesa su aplicación a **firmas digitales**, como alternativa a HMAC para firmar tokens.

Su objetivo y uso es el mismo que HMAC (firma, verificación), pero su implementación es distinta.

RSA resuelve ciertas limitaciones de HMAC:

- HMAC requiere que todos los servicios compartan la misma clave (en caso de microservicios). Esto dificulta la escalabilidad y, si se filtra la clave, cualquiera puede firmar tokens válidos.

Como vimos en el cifrado asimétrico, RSA genera una **clave pública** y una **clave privada**, vinculadas matemáticamente.

### Proceso de firma con RSA

1. Se toma el payload del JWT y se genera su hash.  
2. Se cifra el hash utilizando la clave privada.  
3. El resultado se agrega al token como atributo `"signature"`.

Ahora, cualquiera que tenga la clave pública puede verificar los tokens sin exponer la clave privada y sin necesidad de conocerla. Pero sólo pueden firmar tokens los servicios que tengan la clave privada.

### Puntos clave

- Lo que está firmado con la clave privada sólo se puede verificar usando la clave pública.  
- La responsabilidad está dividida entre nodos firmantes y nodos verificadores. Los verificadores no pueden firmar y los firmantes no pueden verificar, siguiendo el principio de responsabilidad única.  
- Si el JWT trae configurado en su payload un algoritmo de firma distinto al definido en el servidor, se rechaza automáticamente y ni siquiera se intentará firmarlo, siguiendo el principio de *fail-fast*. Esto ayuda a prevenir ataques como el *algorithm confusion*.  
- RSA es más seguro, pero consume más recursos y poder de cómputo.  
- No tiene mucho sentido utilizarlo en arquitecturas monolíticas.
