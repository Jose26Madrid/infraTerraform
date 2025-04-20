# 📁 infraTerraform

Este repositorio actúa como **almacenamiento centralizado** de los resultados de ejecución de Terraform aplicados desde pipelines externas.

Cada vez que se ejecuta la pipeline del repositorio [`deploy/terraform`](https://github.com/Jose26Madrid/terraform), se genera un archivo con la salida de `terraform apply` o `terraform destroy` y se gestiona automáticamente desde GitHub Actions.

---

## 📄 ¿Qué se guarda aquí?

- Archivos `.txt` con la salida de Terraform por repositorio.
- El nombre del archivo corresponde al nombre del repositorio de origen (por ejemplo: `terraform.txt`).
- Estos archivos contienen logs legibles directamente desde la web de GitHub.

---

## 🔁 Funcionamiento

Desde la pipeline remota:

1. Si se ejecuta `terraform apply`:
   - Se genera un archivo `<REPO>.txt` con la salida completa del comando.
   - Se sube automáticamente a este repositorio si no existía previamente.

2. Si se ejecuta `terraform destroy`:
   - El archivo `<REPO>.txt` correspondiente se elimina del repositorio.
   - Se hace commit del cambio y se sube automáticamente.

---

## 🛡 Control de versiones

Cada modificación en este repositorio es realizada automáticamente por **GitHub Actions**, con mensajes como:

- `📦 Añadiendo salida de Terraform para <REPO>`
- `🧹 Eliminando salida de Terraform para <REPO> tras destroy`

---

## ℹ️ Notas

- Este repositorio **no contiene código Terraform**, solo los resultados de su ejecución.
- No edites manualmente los archivos `.txt`, ya que serán gestionados por la pipeline.

---

## 📄 Licencia

Este proyecto está bajo la licencia MIT. Consulta el archivo `LICENSE` para más detalles.
