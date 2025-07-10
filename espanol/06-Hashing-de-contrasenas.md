## 6. Hashing de contraseñas

Cuando nos registramos en un sitio e ingresamos nuestra contraseña, esta debe guardarse en la base de datos de forma segura para protegerla ante posibles robos o filtraciones.

### ¿Cómo se protege la contraseña?

Al crear una cuenta, tus datos se insertan en la base de datos. Luego, tu contraseña se **hashea** y pasa de ser el texto original a un conjunto de caracteres que representan la contraseña, pero sin ser el texto original.

No necesitamos recuperar la contraseña original, y esto no es un problema, es intencional.

### ¿Cómo se verifica la contraseña?

Cuando iniciamos sesión con nuestra contraseña, el servidor vuelve a aplicarle el hash y lo compara con el hash guardado en la base de datos. Si coinciden, la contraseña es correcta, ya que siempre produce el mismo resultado para la misma entrada.

### Algoritmos para hashear contraseñas

No todos los algoritmos son recomendables para proteger contraseñas. Por ejemplo, algoritmos como **SHA256** o **MD5** no son adecuados porque son demasiado rápidos, permitiendo que un atacante pruebe millones de combinaciones por segundo (ataques de fuerza bruta).

Para hashing de contraseñas se recomiendan algoritmos diseñados para esta tarea, como:

- **bcrypt**
- **argon2**

### ¿Por qué se recomiendan estos algoritmos?

Porque consumen más recursos y son más lentos, lo que dificulta los ataques de fuerza bruta. Además, permiten ajustar su consumo de CPU y memoria.

### Uso de SALT

A estos algoritmos se les puede agregar un **SALT**, una capa extra de seguridad.

- Un **SALT** es un valor aleatorio que se agrega a la contraseña antes de hashearla.
- Asegura que dos contraseñas iguales produzcan hashes diferentes.
- Previene ataques como las *rainbow tables*.

### Ejemplo

Si tomamos la contraseña:

```
contraseña123
```

Y le aplicamos un SALT, podría quedar algo así:

```
c0ntr@s3ñ4!23
```

Luego, aplicamos el hash (por ejemplo con bcrypt) y el resultado sería algo como:

```
$2b$12$N9qo8uLOZMRZo5i.u8rJu5PfF6ylCx7jRy8T/HhXqJvW
```

