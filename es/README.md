# Seguridad para Backend: Guía teórica simple de cifrado, hashing y autenticación

*Por [github.com/NehuenLian](https://github.com/NehuenLian)*

---

Esta guía está enfocada a programadores backend que recién comienzan en el área o que, si bien ya comenzaron, pasaron por alto algunos conceptos de seguridad.

La idea es que sea un punto intermedio entre lo técnico y lo sencillo, es decir, que no sea un documento extremadamente técnico pero que tampoco se convierta en información poco útil debido a su simpleza.

---

## Requisitos previos

Esta guía da por hecho que el lector conoce los siguientes temas:

- Protocolo HTTP.
- Arquitectura Cliente-Servidor.
- Qué es una API.
- Nociones de arquitectura de sistemas/software (monolitos/microservicios).

---

## Temas a cubrir

- Diferencia entre cifrado y hashing.
- Cifrado simétrico vs asimétrico.
- Distintas capas de seguridad:
  - Cifrado TLS.
  - Creación de Tokens, firmas digitales y validación de las mismas.
  - Hashing de contraseñas.
  - Cifrado en persistencia.
- Flujo al crear una cuenta en una página web o servicio.
- Flujo al iniciar sesión en un sitio.
