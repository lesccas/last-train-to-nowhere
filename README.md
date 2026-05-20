# Last Train to Nowhere 🚂👁️
### Arquitectura y Metodología Colaborativa en Godot

Bienvenido al repositorio oficial de **Last Train to Nowhere**. Este documento detalla la arquitectura del proyecto, la metodología de trabajo en equipo y el flujo de control de versiones utilizado durante el desarrollo.

---

## 👥 Equipo de Desarrollo
* [**Coraima Mera Rodríguez**](https://github.com/CoraimaMR)
* [**Windely Moronta Acosta**](https://github.com/WindelyM)
* [**Lucía Escoto Castro**](https://github.com/lesccas)
* [**Kemuel Viruet Montaño**](https://github.com/KemiVM)

---

## 1. 📌 Introducción
**Last Train to Nowhere** es una novela visual de terror psicológico que explora la culpa reprimida, el duelo y los mecanismos de defensa de la mente tras un trauma. 

Toda la historia es, en realidad, el viaje mental y espiritual de Kaito (el protagonista) mientras se debate entre la vida y la muerte en la camilla de un hospital. Se encuentra atrapado en un "limbo" con forma de red de metro infernal tras haber provocado un accidente de coche mortal.

### 🛠️ Detalles Técnicos y Métricas
* **Motor:** [Godot Engine 4.6](https://godotengine.org)
* **Gestión de Diálogos:** Plugin **Dialogic**
* **Elenco de Personajes:** Kaito, Aiko, Haru y El Guía.
* **Duración del Desarrollo:** ~4 semanas (20 de abril al 16 de mayo de 2026).
* **Actividad del Repositorio:** +120 commits | 27 Pull Requests integrados con éxito.
* **URL del Repositorio:** [https://github.com/lesccas/last-train-to-nowhere](https://github.com/lesccas/last-train-to-nowhere)

---

## 2. 📅 Organización del Equipo y Metodología
Para optimizar el desarrollo paralelos, la narrativa se estructuró en cuatro actos independientes asignados individualmente:


| Acto | Título | Responsable |
| :--- | :--- | :--- |
| **Acto 1** | La ilusión de la normalidad | Kemuel |
| **Acto 2** | El descenso de las reglas | Windely |
| **Acto 3** | El peso de la culpa | Coraima |
| **Acto 4** | El juicio final | Lucía |

* **Comunicación:** El equipo combinó sesiones presenciales en el aula con coordinación remota continua a través de WhatsApp.
* **Colaboración:** Se gestionó mediante invitación directa a los integrantes como colaboradores con permisos de escritura en el repositorio central de GitHub.

---

## 3. 🌲 Control de Versiones: Git y GitHub
Utilizamos **Git** como sistema de control de versiones distribuido, lo que permitió a cada desarrollador disponer de una copia local idéntica y completa del proyecto para trabajar sin dependencias de red constantes.

### 🗺️ Áreas de Trabajo de Git
1. **Working Directory:** Espacio local donde se modifican y crean los archivos del juego.
2. **Staging Area:** Zona intermedia de preparación antes de confirmar los cambios.
3. **Repositorio Local:** Almacenamiento definitivo de los commits en la máquina del desarrollador.
4. **Repositorio Remoto (GitHub):** Plataforma en la nube para la sincronización del equipo.

### 🗂️ Organización de Ramas y Archivos
* **Estructura limpia:** El primer paso del proyecto fue definir el árbol de carpetas de los actos y *assets* para mitigar conflictos de colisión de archivos en Godot.
* **Modelo de Ramas:** Una rama principal (`main`) siempre funcional y libre de errores, acompañada de ramas secundarias individuales por cada desarrollador.
* **Integración:** El código se unificó exclusivamente mediante la aprobación de **Pull Requests** hacia `main`.

---

## ⌨️ Guía de Comandos Principales Utilizados

### Inicialización y Configuración
```bash
git init                            # Crea un nuevo repositorio local.
git config --global user.name "Nom" # Configura el nombre del desarrollador a nivel global.
git config --global user.email "em" # Configura el correo electrónico a nivel global.
```

### Gestión de Archivos y Commits
```bash
git status                          # Muestra el estado actual de los archivos.
git add <archivo>                   # Añade un archivo específico al área de staging.
git add .                           # Añade todos los cambios del directorio actual a staging.
git commit -m "mensaje"             # Genera un punto de guardado con un mensaje descriptivo.
git log                             # Muestra el historial completo de commits.
git log --oneline                   # Muestra el historial resumido en formato de una sola línea.
```

### Trabajo con el Repositorio Remoto
```bash
git remote add origin <URL>         # Vincula el repositorio local con el servidor remoto.
git push origin <rama>              # Sube los commits locales a la rama remota especificada.
git pull                            # Descarga e integra los cambios de la rama remota actual.
git clone <URL> .                   # Clona un repositorio remoto en el directorio actual.
```
> 💡 *Nota:* `git pull` descarga por defecto la rama activa. Para traer actualizaciones de otras ramas se debe especificar `git pull origin <rama>`.

### Deshacer Cambios
```bash
git checkout <IDCommit> -- <fich>   # Restaura un fichero específico a un estado anterior.
git reset HEAD <fichero>            # Saca un archivo del área de staging sin perder los cambios.
git reset --hard                    # Elimina todos los cambios locales y vuelve al último commit.
```
> 💡 *Nota:* Utilizar `git checkout <IDCommit>` (sin especificar un fichero) nos lleva a un estado de *detached HEAD* (viaje al pasado). Permite experimentar de forma segura. Para regresar al presente se puede usar `git checkout <rama>` (sin guardar) o crear una rama nueva.

### Trabajo con Ramas
```bash
git branch <NuevaRama> <RamaCopia>  # Crea una nueva rama tomando como base otra existente.
git switch <nombreRama>             # Cambia el entorno de trabajo a una rama existente.
git checkout <nombreRama>           # Cambia de rama trayendo los archivos correspondientes.
git branch -a -v                    # Lista de forma detallada todas las ramas locales y remotas.
git merge <ramaOrigen>              # Fusiona la rama indicada dentro de la rama actual activa.
git branch -d <nombreRama>          # Elimina una rama secundaria de forma segura (ya fusionada).
```

### Etiquetas (Tags)
```bash
git tag -a <nombreID> -m "mensaje"  # Crea una etiqueta anotada (ej. hitos o versiones del juego).
git tag                             # Lista todas las etiquetas existentes en el proyecto.
git push origin <IDEtiqueta>        # Sube una etiqueta específica al repositorio remoto.
```

### 🙈 Archivo `.gitignore`
Para evitar subir metadatos locales, configuraciones de usuario o archivos binarios pesados generados por el motor, implementamos un archivo `.gitignore` en la raíz del proyecto que descarta:
* Carpeta cache y datos locales de Godot: `.godot/`
* Exportaciones e intermediarios: `/android/`
* *Assets* crudos de diseño no optimizados o temporales.

---

## 4. 🔄 Flujo de Trabajo Colaborativo con GitHub

### Configuración Inicial
El repositorio base fue creado por la administradora del proyecto. Los integrantes se unieron mediante invitaciones directas de colaboración con permisos de escritura. La vinculación inicial se realizó mediante:
```bash
git remote add origin https://github.com/lesccas/last-train-to-nowhere.git
git push origin main
```

### Estrategia de Trabajo Diario
Cada desarrollador gestionó su propio entorno de trabajo de forma aislada a través de su rama nominal. El flujo diario establecido para garantizar la estabilidad del proyecto consistió en:

1. **Sincronización:** Actualizar la rama local trayendo los últimos cambios estables integrados en la rama principal (`git pull origin main`).
2. **Desarrollo Local:** Trabajar en las escenas, scripts o recursos de Dialogic correspondientes dentro de la rama personal asignada.
3. **Confirmación:** Realizar commits locales frecuentes y atómicos de los avances del día.
4. **Publicación y Revisión:** Subir la rama a GitHub (`git push origin <mi-rama>`) y abrir un **Pull Request** para revisar e integrar los cambios de forma transparente con el resto del equipo.
