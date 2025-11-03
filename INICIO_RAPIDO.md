# Inicio Rápido - Clonar este Repositorio

## ✅ Método más simple (recomendado)

Abre tu terminal y ejecuta:

```bash
git clone https://github.com/ignacioriverosurrutia/skills-intro-to-github.git
cd skills-intro-to-github
```

¡Eso es todo! 🎉

## 🆘 ¿Tienes problemas?

### El comando no funciona

1. **¿Tienes Git instalado?**
   ```bash
   git --version
   ```
   Si ves un error, instala Git desde: https://git-scm.com/

2. **¿Estás conectado a internet?**
   Verifica tu conexión.

3. **¿El error menciona "authentication"?**
   - GitHub ya no acepta contraseñas simples
   - Necesitas un Personal Access Token
   - Ve a: Settings → Developer settings → Personal access tokens

### Alternativa sin Git

Si Git no funciona, descarga el ZIP:

1. Ve a: https://github.com/ignacioriverosurrutia/skills-intro-to-github
2. Click en el botón verde "Code"
3. Click en "Download ZIP"
4. Extrae el archivo

## 📖 Más ayuda

- Ver: [GUIA_CLONACION.md](./GUIA_CLONACION.md) para guía completa
- Ver: [README.md](./README.md) para instrucciones detalladas

## 🚀 Después de clonar

```bash
# Verifica que estés en el repositorio
git status

# Crea tu propia rama
git checkout -b mi-primera-rama

# Haz un cambio (por ejemplo, crea un archivo)
echo "# Mi primer cambio" > mi-archivo.md

# Guarda el cambio
git add mi-archivo.md
git commit -m "Mi primer commit"

# ¡Felicidades! Has usado Git exitosamente
```

---

**¿Aún necesitas ayuda?** Lee [GUIA_CLONACION.md](./GUIA_CLONACION.md) para solucionar problemas específicos.