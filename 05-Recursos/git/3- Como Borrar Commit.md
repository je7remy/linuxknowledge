Para borrar el **antepenúltimo commit** de tu historial en Git, sigue estos pasos:

---

## 🔎 1️⃣ Identificar el commit que quieres borrar

Ejecuta este comando para ver el historial de commits:

```bash
git log --oneline
```

Ejemplo de salida:

```
a1b2c3d (HEAD -> main) Último commit
d4e5f6g Penúltimo commit
h7i8j9k (commit que quieres borrar)
l0m1n2o Commit anterior al que quieres borrar
```

El commit **h7i8j9k** es el antepenúltimo.

---

## 🔥 2️⃣ Opción 1: Usar `git rebase -i` (Método recomendado si no has hecho `push`)

Si **aún no has hecho `push`**, usa `rebase interactivo`:

```bash
git rebase -i HEAD~3
```

Esto abrirá un editor de texto con algo así:

```
pick d4e5f6g Penúltimo commit
pick h7i8j9k (commit que quieres borrar)
pick l0m1n2o Commit anterior
```

1. **Cambia** `pick` por `drop` en la línea del commit que quieres eliminar.
    
    ```
    pick d4e5f6g Penúltimo commit
    drop h7i8j9k (commit que quieres borrar)
    pick l0m1n2o Commit anterior
    ```
    
2. **Guarda y cierra el editor**.
    
3. Si todo está bien, sube los cambios con:
    
    ```bash
    git push --force origin main
    ```
    

⚠ **Precaución:** `--force` **reescribe la historia del repositorio**, lo cual puede causar problemas si otros ya han hecho `pull`.

---

## 🚀 Opción 2: Usar `git reset` (Método drástico)

Si quieres borrar el commit **y todo lo que vino después**:

```bash
git reset --hard h7i8j9k^
```

Esto hará que el **antepenúltimo commit y todos los posteriores desaparezcan**. Luego, si ya habías hecho `push`, fuerza la actualización con:

```bash
git push --force origin main
```

⚠ **Cuidado:** Esto eliminará commits posteriores al que quieres borrar. Úsalo solo si estás seguro.

---

## ✅ ¿Qué opción elegir?

- **Si quieres borrar solo ese commit y dejar los demás intactos**, usa `git rebase -i`.
- **Si quieres borrar ese commit y todo lo que vino después**, usa `git reset --hard`.
