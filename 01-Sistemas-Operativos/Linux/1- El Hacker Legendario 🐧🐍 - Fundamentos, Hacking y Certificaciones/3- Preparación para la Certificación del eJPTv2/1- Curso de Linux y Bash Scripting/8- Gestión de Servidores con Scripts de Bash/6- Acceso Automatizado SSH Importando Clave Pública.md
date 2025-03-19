
---

#SSH #Automatización #AccesoSinContraseña #ClaveSSH #Seguridad #Ciberseguridad #Linux #AutomatizaciónLinux #GestiónDeSistemas #AdministraciónDeSistemas #ClavePública #AccesoRemoto #ComandosLinux #SSHKey #AutenticaciónSegura

---
Para automatizar el acceso SSH utilizando claves públicas, puedes usar `ssh-keygen` para generar claves y `ssh-copy-id` para transferir la clave pública al servidor remoto.

### Comandos Explicados

#### 1. **ssh-keygen**

Este comando genera un par de claves SSH (una pública y otra privada) para autenticación segura.

**Estructura básica:**

```bash
ssh-keygen
```

- **Función:** Crea dos archivos:
    - `id_rsa`: La clave privada (se guarda localmente y nunca se comparte).
    - `id_rsa.pub`: La clave pública (se comparte con los servidores donde se desea acceder).
- **Resultado:** Autenticación sin contraseña en servidores que acepten la clave pública.

---

#### 2. **ssh-copy-id jeremyserver@192.168.1.106**

Este comando copia la clave pública generada por `ssh-keygen` al servidor remoto.

**Estructura básica:**

```bash
ssh-copy-id usuario@servidor
```

- **jeremyserver:** Usuario del servidor remoto.
- **192.168.1.106:** Dirección IP del servidor remoto.
- **Función:** Agrega la clave pública al archivo `~/.ssh/authorized_keys` del usuario remoto, permitiendo acceso SSH sin contraseña.





[[7- Automatización de Copias de Seguridad en Servidor SSH]]
[[11- Automatizar la Gestión de Usuarios en Linux]]
