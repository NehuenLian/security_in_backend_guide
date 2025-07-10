## 7. HMAC

HMAC es un algoritmo de firma, de las siglas **Hash-based Message Authentication Code**, que utiliza una clave secreta o compartida (dependiendo de si la arquitectura en cuestión es monolítica o de microservicios).

Consiste en “extraer” las partes del token y realizar una serie de pasos y cálculos para agregar una firma a ese token.

### Pasos para firmar un token con HMAC

1. Se toma el header y el payload, y se concatenan para obtener un string resultante.  
2. A ese string resultante se le agrega la clave secreta.  
3. Sobre el resultado (string + clave secreta) se aplica una función hash, que será la firma del token.  
4. Esta firma (hash) se agrega al token como valor del atributo `"signature"`.

Una vez el token está firmado, el servidor podrá verificar si ese token es legítimo cuando le llegue.

### ¿Cómo verifica el servidor un token firmado con HMAC?

Cuando el servidor recibe un JWT firmado previamente, antes de aprobar la solicitud tiene que verificarlo.

El servidor vuelve a recalcular la firma del token haciendo el mismo procedimiento que realizó para firmarlo por primera vez.

Si la firma resultante es idéntica a la firma del JWT, significa que ese token fue firmado por ese servidor y por lo tanto es legítimo.

---

### Aclaración sobre la “clave compartida”

En HMAC se le llama “clave compartida” pero esto no siempre es así.

- En una arquitectura de **microservicios**, todos los microservicios tienen que compartir esa clave, ya que todos necesitan validar JWTs y recalcular firmas.  
- En arquitecturas **monolíticas**, la clave no se comparte con nadie; sólo la tiene el único servidor disponible, que la utiliza para validar los tokens que recibe.

Este concepto es el mismo principio del cifrado simétrico.
