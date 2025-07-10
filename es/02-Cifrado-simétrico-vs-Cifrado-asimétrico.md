## Cifrado simétrico vs asimétrico

Existen varios tipos de cifrado, pero el simétrico y el asimétrico son los más utilizados en el contexto de la web. Recordando que en el cifrado se utiliza una clave para cifrar y descifrar, tenemos:

### Cifrado simétrico

El cifrado simétrico consiste en utilizar una única clave para cifrar y descifrar la información. Todos los mensajes cifrados con esta clave necesitan la misma clave para descifrar.

En arquitecturas como microservicios se llama **“Clave simétrica compartida”**, ya que todos los microservicios van a necesitar la clave para comunicarse, cifrar y descifrar mensajes. En cambio, en arquitecturas monolíticas o con un solo servidor, el servidor se encarga de cifrar y descifrar sin necesidad de compartir la clave, porque no hay otros actores que la necesiten.

Es común que se confunda este concepto, ya que el cifrado simétrico suele presentarse directamente en ejemplos con microservicios.

### Cifrado asimétrico

El cifrado asimétrico involucra dos claves en lugar de una: una clave pública y una clave privada.

**¿Cómo se generan estas claves?**  
Se generan a partir de ciertos parámetros matemáticos, dependiendo del algoritmo de cifrado elegido. Ambas claves se generan en conjunto una vez aplicado el algoritmo. Están vinculadas matemáticamente y siguen esta dinámica:

- La clave privada se mantiene en secreto.
- La clave pública puede compartirse con cualquier nodo/microservicio.

La clave del cifrado asimétrico es que con la clave pública solo se puede cifrar información, pero no tiene la capacidad de descifrar. Quien descifra la información solo es quien tiene la clave privada.
