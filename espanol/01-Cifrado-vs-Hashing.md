## Cifrado y hashing: diferencias entre cada uno

Tanto el cifrado como el hashing tienen el fin de proteger datos, pero con diferente enfoque según la naturaleza del dato a proteger y el contexto.

### Cifrado

Consiste en transformar datos que estén en texto plano en un formato codificado, esto se hace usando una clave.

Para obtener el dato original, se necesita descifrarlo y para descifrarlo se necesita también una clave definida previamente por el desarrollador.

La característica que más diferencia al cifrado del hashing es que es reversible (puede recuperarse el dato una vez ya no se necesite ocultarlo o se lo quiera leer), esto se hace descifrándolo.

Se utiliza cuando la información necesita ser leída o procesada nuevamente más adelante, como mensajes, números de tarjeta, datos clínicos, etc.

**Ejemplo:**

Supongamos que usamos la clave `"clave1"` para cifrar un texto. Si queremos cifrar el mensaje `"Hola mundo"`, aplicamos el algoritmo con esa clave y obtenemos un texto cifrado, por ejemplo:

```
3f1e9a7bc2a3e8c5f67a69e70f3c4c2a
```

Para leer el mensaje original, aplicamos el algoritmo inverso (descifrado) usando la misma clave. Así recuperamos:

```
Hola mundo
```

### Hashing

El hashing es un método unidireccional de cubrir el contenido real de un dato para protegerlo. Lo que significa que, a diferencia del cifrado, no es reversible: no se puede recuperar el dato original de ninguna forma una vez fue hasheado, no hay clave para volver a hacerlo, es un “viaje de ida”.

Transforma el dato en una cadena de longitud fija, que se compone de caracteres sin significado alguno pero determinados por el contenido original.

El hashing se utiliza en casos donde justamente no se necesite recuperar el dato a proteger, como contraseñas, o para verificar la integridad o la legitimidad de un dato.

**Ejemplo:**

Si aplicamos un algoritmo de hashing sobre el texto `"Hola mundo"`, obtenemos un valor como:

```
d9e3f04a363698763cfc3c3cc50a757e7ce2e6a95b2a31eb3e4f639a2e2e3f28
```

Este valor es único para ese texto, pero no es posible volver al texto original desde él. El hashing es un proceso de “viaje de ida”: una vez aplicado, no puede revertirse.