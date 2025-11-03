# Guía Completa de Clonación del Repositorio

Esta guía te ayudará a resolver el problema "No se pudo clonar" paso a paso.

## Verificaciones previas

### 1. ¿Tienes Git instalado?

Abre tu terminal o línea de comandos y ejecuta:

```bash
git --version
```

Si ves un número de versión (por ejemplo, `git version 2.39.0`), Git está instalado correctamente.

**Si no está instalado:**

- **Windows**: Descarga desde [git-scm.com](https://git-scm.com/download/win)
- **macOS**: Ejecuta `xcode-select --install` o descarga desde [git-scm.com](https://git-scm.com/download/mac)
- **Linux**: 
  - Ubuntu/Debian: `sudo apt-get install git`
  - Fedora: `sudo dnf install git`
  - Arch: `sudo pacman -S git`

### 2. ¿Tienes conexión a internet?

Verifica que puedas acceder a GitHub:

```bash
ping github.com
```

## Métodos de clonación

### Método 1: HTTPS (Recomendado para principiantes)

Este es el método más sencillo y funciona en todas partes:

```bash
git clone https://github.com/ignacioriverosurrutia/skills-intro-to-github.git
```

**Ventajas:**
- No requiere configuración adicional
- Funciona a través de firewalls
- Fácil de usar

**Desventajas:**
- Puede pedir credenciales con frecuencia

### Método 2: SSH (Recomendado para usuarios frecuentes)

Requiere configuración inicial, pero es más conveniente a largo plazo:

```bash
git clone git@github.com:ignacioriverosurrutia/skills-intro-to-github.git
```

**Para configurar SSH:**

1. Genera una llave SSH:
```bash
ssh-keygen -t ed25519 -C "tu-email@ejemplo.com"
```

2. Copia tu llave pública:
```bash
cat ~/.ssh/id_ed25519.pub
```

3. Agrégala a GitHub:
   - Ve a GitHub.com → Settings → SSH and GPG keys
   - Click "New SSH key"
   - Pega tu llave pública

### Método 3: GitHub CLI

Si tienes GitHub CLI instalado:

```bash
gh repo clone ignacioriverosurrutia/skills-intro-to-github
```

### Método 4: GitHub Desktop

1. Descarga [GitHub Desktop](https://desktop.github.com/)
2. Instala la aplicación
3. Ve a File → Clone repository
4. Busca `ignacioriverosurrutia/skills-intro-to-github`
5. Selecciona la ubicación local
6. Haz clic en "Clone"

## Errores comunes y soluciones

### Error 1: "fatal: unable to access... Could not resolve host"

**Causa**: Problema de conexión a internet o DNS

**Solución**:
```bash
# Verifica tu conexión
ping 8.8.8.8

# Verifica que puedes alcanzar GitHub
ping github.com

# Si ping funciona pero git no, verifica tu configuración de proxy
git config --global --get http.proxy
git config --global --get https.proxy
```

### Error 2: "fatal: Authentication failed"

**Causa**: Credenciales incorrectas o caducadas

**Solución**:

1. Si usas HTTPS, GitHub ya no acepta contraseñas. Necesitas un Personal Access Token:
   - Ve a GitHub.com → Settings → Developer settings → Personal access tokens → Tokens (classic)
   - Genera un nuevo token con permisos de "repo"
   - Usa el token como contraseña cuando Git te lo pida

2. Configura Git para recordar credenciales:
```bash
git config --global credential.helper store
```

### Error 3: "fatal: repository not found"

**Causa**: URL incorrecta o falta de permisos

**Solución**:
```bash
# Verifica la URL exacta
# Debe ser: https://github.com/ignacioriverosurrutia/skills-intro-to-github.git

# Verifica que el repositorio exista visitando:
# https://github.com/ignacioriverosurrutia/skills-intro-to-github
```

### Error 4: "Permission denied (publickey)"

**Causa**: Problema con llaves SSH

**Solución**:
```bash
# Verifica que tu llave SSH esté cargada
ssh-add -l

# Si no hay llaves, agrega la tuya
ssh-add ~/.ssh/id_ed25519

# Prueba la conexión SSH con GitHub
ssh -T git@github.com
```

### Error 5: "fatal: destination path already exists"

**Causa**: Ya existe una carpeta con ese nombre

**Solución**:
```bash
# Opción 1: Clona en una ubicación diferente
git clone https://github.com/ignacioriverosurrutia/skills-intro-to-github.git mi-copia-github

# Opción 2: Elimina la carpeta existente (¡cuidado!)
rm -rf skills-intro-to-github
git clone https://github.com/ignacioriverosurrutia/skills-intro-to-github.git

# Opción 3: Navega a otra ubicación
cd ..
git clone https://github.com/ignacioriverosurrutia/skills-intro-to-github.git
```

### Error 6: "SSL certificate problem"

**Causa**: Problema con certificados SSL (común en redes corporativas)

**⚠️ ADVERTENCIA DE SEGURIDAD**: La siguiente solución temporal desactiva la verificación SSL y **NO debe usarse en entornos de producción** o para información sensible. Esto hace que tu conexión sea vulnerable a ataques man-in-the-middle.

**Solución temporal** (SOLO para entornos de desarrollo/prueba aislados):
```bash
# ⚠️ USAR CON EXTREMA PRECAUCIÓN
git config --global http.sslVerify false
```

**Solución recomendada y segura**:
```bash
# Actualiza los certificados de tu sistema
# Windows: Reinstala Git desde git-scm.com
# macOS: Actualiza certificados del sistema operativo
# Linux: sudo apt-get install ca-certificates --reinstall

# O configura el certificado correcto en lugar de desactivar SSL
git config --global http.sslCAInfo /path/to/certificate.pem
```

## Verificación de clonación exitosa

Después de clonar, verifica que todo esté bien:

```bash
# Navega al directorio
cd skills-intro-to-github

# Verifica el estado
git status

# Deberías ver: "On branch main"

# Lista los archivos
ls -la

# Deberías ver: README.md, .git/, y otros archivos
```

## Clonación alternativa: Descargar como ZIP

Si ningún método de Git funciona, puedes descargar el repositorio directamente:

1. Ve a https://github.com/ignacioriverosurrutia/skills-intro-to-github
2. Haz clic en el botón verde "Code"
3. Selecciona "Download ZIP"
4. Descomprime el archivo

**Nota**: Este método no incluye el historial de Git, solo los archivos actuales.

## Configuración recomendada de Git

Después de clonar exitosamente, configura Git:

```bash
# Configura tu nombre
git config --global user.name "Tu Nombre"

# Configura tu email
git config --global user.email "tu-email@ejemplo.com"

# Configura el editor predeterminado
git config --global core.editor "nano"  # o "vim", "code", etc.

# Verifica tu configuración
git config --list
```

## Próximos pasos

Una vez clonado el repositorio:

1. **Explora los archivos**: `ls -la`
2. **Crea una rama**: `git checkout -b mi-rama`
3. **Haz cambios**: Edita archivos con tu editor favorito
4. **Confirma cambios**: `git add .` y `git commit -m "Mensaje"`
5. **Sube cambios**: `git push origin mi-rama`

## ¿Todavía tienes problemas?

Si después de seguir esta guía aún no puedes clonar:

1. **Verifica los logs detallados**:
```bash
GIT_TRACE=1 GIT_CURL_VERBOSE=1 git clone https://github.com/ignacioriverosurrutia/skills-intro-to-github.git
```

2. **Busca ayuda**:
   - [Stack Overflow](https://stackoverflow.com/questions/tagged/git)
   - [GitHub Community](https://github.community/)
   - [Documentación oficial de Git](https://git-scm.com/doc)

3. **Reporta el problema**:
   - Abre un issue en este repositorio
   - Incluye el mensaje de error completo
   - Menciona tu sistema operativo
   - Incluye la versión de Git (`git --version`)

---

**Actualizado**: Noviembre 2025
**Mantenedor**: ignacioriverosurrutia