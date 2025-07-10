## 8. Conclusión sobre las capas de seguridad

En la web existen al menos cuatro capas principales de seguridad que trabajan en conjunto para proteger datos y comunicaciones:

1. **Certificado X.509:** identifica y legitima al servidor mediante una cadena de confianza firmada por una Autoridad Certificadora (CA).  
2. **Cifrado TLS (HTTPS):** protege la comunicación entre cliente y servidor usando cifrado asimétrico para intercambio seguro de claves y cifrado simétrico para la transmisión.  
3. **Firma de tokens (HMAC, RSA):** asegura la integridad y autenticidad de tokens usados para validar solicitudes y sesiones.  
4. **Hashing de contraseñas (con SALT) y cifrado en reposo:** protege las credenciales de usuario y datos sensibles almacenados para evitar accesos no autorizados.  

### Metodología común para validar legitimidad

- En cifrado **simétrico**, se recalculan strings o firmas usando la misma clave secreta compartida.  
- En cifrado **asimétrico**, se recalculan firmas con la clave pública, sin exponer la clave privada.
