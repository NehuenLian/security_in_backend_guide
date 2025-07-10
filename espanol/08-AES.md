## 8. AES

AES (Advanced Encryption Standard) es un algoritmo de cifrado muy utilizado para proteger datos. Es un estándar común para cifrar comunicación HTTP de forma asimétrica, como vimos antes en TLS.

Sin embargo, otro de sus usos principales es cifrar datos en persistencia, conocido como **cifrado en reposo**. En este caso, AES se usa de forma **simétrica** para proteger datos cuyo contenido original debe poder recuperarse, como nombres, números de tarjetas, etc. Esto implica que no se pueden simplemente hashear, como ocurre con las contraseñas.

### ¿Cómo se aplica AES para cifrar en reposo?

1. El servidor toma los datos sensibles antes de almacenarlos.
2. Utiliza una clave AES para cifrarlos.
3. Guarda los datos cifrados en la base de datos.
4. Cuando es necesario acceder a esos datos, se descifran usando la misma clave.

### Consideraciones

- La clave AES debe estar protegida; si se filtra, todo lo cifrado con esa clave puede ser descifrado.
- Actualmente, para aumentar la seguridad, la clave suele almacenarse en servicios externos especializados, como **AWS KMS** o **Azure Key Vault**, para aislarla aún más.

