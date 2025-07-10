## 3. Tokens y firmas digitales

### ¿Qué es un token?

Un token es un objeto de datos que contiene información y actúa como identificador.

Son emitidos por el servidor, y se incluyen dentro de las solicitudes (por ejemplo, en el header) para que el servidor pueda verificar si ese token fue emitido por él mismo y, por ende, si la solicitud es legítima. Uno de los tokens más comunes es el **JWT (JSON Web Token)**.

Un JWT tiene tres partes, codificadas en formato Base64:

1. Header  
2. Payload  
3. Signature

### ¿Cómo se firma un JWT?

Cuando un servidor emite un JWT, el flujo es el siguiente:

1. El servidor recibe los datos.  
2. Crea el token. El token emitido va a estar vinculado a ese usuario y va a usarse para identificarlo.  
3. El servidor firma el token.  
4. El servidor le envía ese token al cliente.  
5. El cliente almacena ese token (por ejemplo, en `localStorage`) y lo incluye dentro de las siguientes solicitudes que envíe.  
6. Cada vez que el servidor recibe una solicitud con el token, verifica la firma y la validez.

### ¿Y cómo se firma un token?

Para firmar tokens se utilizan algoritmos de firma, los más comunes son:

- **HMAC (simétrico)**  
- **RSA (asimétrico)**  

Ambos se usan dependiendo del caso.
