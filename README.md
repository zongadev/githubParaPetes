# GitHub para Petes

> Una guía interactiva, cariñosa y ligeramente agresiva para sobrevivir a Git y GitHub sin romper el proyecto grupal.

## Qué es esto

Este repo está pensado para gente de la facultad que:

* no sabe qué hace `git pull`
* le tiene miedo a la terminal
* sube un `.zip` al grupo en vez de hacer commit
* piensa que **merge** es una materia de economía

La idea es aprender **haciendo**, con ejemplos simples, mini misiones y un poco de humor.

---

## Objetivos de aprendizaje

Al terminar este repo deberías poder:

1. clonar un repositorio
2. hacer cambios sin prender fuego todo
3. crear commits decentes
4. subir cambios a GitHub
5. traer cambios de otros
6. entender qué corno es una branch
7. resolver conflictos sin entrar en un brote psicótico

---

## Filosofía del curso

Git no es difícil.

Git tiene pinta de difícil porque:

* usa palabras raras
* da errores con actitud pasivo-agresiva
* si hacés cualquier cosa mal sentís que vas a borrar la tesis de alguien

Pero en el fondo, Git hace casi siempre estas 4 cosas:

* mirar archivos
* guardar cambios
* cambiar de versión
* sincronizar con GitHub

Si entendés eso, ya no sos un pete. Sos un pete en recuperación.

---

# Mapa del repo

## 0. Kit de supervivencia

Explica qué hay que instalar y cómo abrir Git Bash o la terminal.

## 1. Clonar sin llorar

Aprendés `git clone` y qué pasa cuando bajás un repo.

## 2. El santo trío

Aprendés:

* `git status`
* `git add`
* `git commit`

## 3. Subir tus cambios sin secuestrar el trabajo ajeno

Aprendés:

* `git push`
* cuándo te va a decir que no
* cómo no mandar fruta

## 4. Traer cambios del resto de los inútiles

Aprendés:

* `git pull`
* `git fetch`
* por qué conviene mirar antes de tocar

## 5. Branches: la magia de romper cosas en privado

Aprendés:

* `git branch`
* `git switch`
* `git checkout` si querés vivir en 2018

## 6. Conflictos

La parte donde dos personas editan lo mismo y Git dice: “arréglense ustedes”.

## 7. Pull requests

Para que el caos tenga una mínima supervisión.

## 8. Mini proyecto final

Van a tocar archivos distintos y después el mismo archivo para practicar conflictos y merge.

---

# Instalación

## Windows

Instalá:

* Git
* una cuenta de GitHub
* ganas de no mandar 48 archivos `.exe` al repo

Después abrí **Git Bash** o la terminal de VS Code.

## Verificar instalación

```bash
git --version
```

Si responde una versión, joya.
Si no responde, arrancamos mal pero se puede remontar.

---

# Primeros conceptos sin humo

## Repositorio

Una carpeta vigilada por Git.

## Commit

Una “foto” de tus cambios.

## Branch

Una línea de trabajo separada.

## Push

Mandar tus commits a GitHub.

## Pull

Traer commits de GitHub.

## Merge

Juntar cambios de distintas ramas.

## Conflicto

Cuando Git te mira y te dice: “yo hasta acá llegué”.

---

# Regla de oro

## Antes de tocar nada

```bash
git pull
```

## Después de tocar algo

```bash
git status
```

## Antes de subir

```bash
git status
```

## Cuando no entendés qué está pasando

```bash
git status
```

Sí. `git status` es tu pastor. Nada te faltará.

---

# Misión 1: Clonar el repo

## Objetivo

Tener el repo en tu compu.

```bash
git clone URL_DEL_REPO
```

Después:

```bash
cd github-para-petes
```

## Qué pasó acá

* `clone` copia el repo remoto a tu máquina
* `cd` entra a la carpeta

## Checkpoint

Corré:

```bash
git status
```

Si dice que estás en una branch y que no hay cambios, todo bien.

---

# Misión 2: Tu primer cambio sin delinquir

Editá un archivo, por ejemplo `presentaciones/tu_nombre.md`.

Poné algo así:

```md
# Hola, soy Gonza

Vine a aprender Git para dejar de mandar archivos_final_definitivo2_ahora_si.zip
```

Ahora corré:

```bash
git status
```

Vas a ver que Git detectó cambios.

---

# Misión 3: Add y commit

## Paso 1: preparar cambios

```bash
git add presentaciones/tu_nombre.md
```

## Paso 2: guardar cambios

```bash
git commit -m "Agrega presentación de Gonza"
```

## Qué significa

* `add` pone cambios en el área de preparación
* `commit` guarda esa versión en el historial

## Analogía falopa pero útil

* archivo editado = estás cocinando
* `git add` = serviste el plato
* `git commit` = le sacaste foto para Instagram

---

# Cómo escribir commits que no den vergüenza

## Buenos commits

* `Agrega archivo de presentación de Gonza`
* `Corrige typo en README`
* `Suma ejercicio de ramas`

## Commits horribles

* `cosas`
* `arreglo`
* `aaa`
* `ahora si`
* `dale hijo de puta funciona`

Ese último es emocionalmente válido, pero técnicamente pobre.

---

# Misión 4: Subir cambios

```bash
git push
```

## Qué hace

Manda tus commits al repositorio remoto en GitHub.

## Qué puede salir mal

### Caso 1: te dice que primero hagas pull

Significa que alguien subió algo antes que vos.

Entonces:

```bash
git pull
```

Y después:

```bash
git push
```

### Caso 2: hay conflicto

No grites. Es normal. Está todo hablado más abajo.

---

# Misión 5: Branches

## Crear una branch

```bash
git switch -c mi-rama
```

## Ver en qué branch estás

```bash
git branch
```

La branch actual aparece con `*`.

## Cambiar de branch

```bash
git switch main
```

## Idea clave

Trabajás en una rama para no romper la principal.

Es como hacer experimentos en un laboratorio y no en el comedor de tu casa.

---

# Cuándo usar branches

Usalas cuando:

* vas a agregar una feature
* vas a tocar varias cosas
* no querés romper `main`
* querés fingir profesionalismo industrial

No hace falta crear una branch para cambiar una coma en un archivo si están aprendiendo entre amigos, pero conviene practicar igual.

---

# Misión 6: Pull request explicado sin humo corporativo

Una **pull request** es básicamente:

> “Che, hice estos cambios. ¿Los revisan y los metemos al proyecto?”

Sirve para:

* revisar cambios
* comentar código
* evitar que cualquiera entre con una topadora a `main`

---

# Conflictos: el boss fight

## Cuándo pasa

Cuando dos personas cambian la misma parte del mismo archivo.

Git te muestra algo así:

```text
<<<<<<< HEAD
Tu cambio
=======
Cambio de tu compañero
>>>>>>> rama-del-otro
```

## Qué hacer

Tenés que editar ese archivo y decidir:

* dejar tu versión
* dejar la del otro
* combinar ambas

Después:

```bash
git add archivo_conflictivo

git commit -m "Resuelve conflicto en archivo_conflictivo"
```

## Importante

Git no odia a nadie.
Git solamente no puede leer la mente de los integrantes del grupo.

---

# Guía ultra corta de supervivencia

## Flujo normal si trabajás solo en una tarea

```bash
git pull
git switch -c nombre-de-mi-rama
# editás cosas
git status
git add .
git commit -m "Describe tu cambio"
git push -u origin nombre-de-mi-rama
```

Después hacés el pull request.

## Flujo simple si trabajan todos directo sobre main

```bash
git pull
# editás cosas
git status
git add .
git commit -m "Describe tu cambio"
git push
```

No es lo más prolijo, pero para una materia a veces alcanza.

---

# Cosas que NO hay que hacer

## 1. No subas esto

* `node_modules`
* ejecutables
* archivos temporales
* 18 PDFs duplicados
* contraseñas
* archivos gigantes porque sí

## 2. No hagas esto

* editar en GitHub y en local al mismo tiempo sin saber qué hacés
* borrar carpetas porque “total seguro Git las recuerda” sin revisar
* hacer commit de todo con `git add .` sin mirar
* pushear a `main` como un animal si acordaron usar branches

## 3. No nombres archivos así

* `tp final posta final.md`
* `codigo bueno.c`
* `version_nueva_2_ahora_si_definitiva_FINAL.c`

---

# Git ignore, el patovica del repo

Archivo: `.gitignore`

Sirve para decirle a Git:

> “esto no lo mires, maestro”

Ejemplo:

```gitignore
*.exe
*.o
__pycache__/
.vscode/
.env
```

---

# Ejercicio práctico grupal

## Ronda 1

Cada integrante crea su archivo en `presentaciones/`.

Objetivo: practicar clone, add, commit y push.

## Ronda 2

Cada integrante crea una branch y agrega una línea a `ranking-de-materias.md`.

Objetivo: practicar branches y pull requests.

## Ronda 3

Dos personas editan exactamente la misma línea.

Objetivo: ver un conflicto real y resolverlo sin entrar en llanto técnico.

---

# Cheat sheet del bien

```bash
git clone URL
git status
git add archivo
git add .
git commit -m "mensaje"
git pull
git push
git branch
git switch -c nueva-rama
git switch main
```

---

# FAQ del estudiante desesperado

## “¿Git y GitHub son lo mismo?”

No.

* **Git** = herramienta de control de versiones
* **GitHub** = página/plataforma donde alojás repositorios Git

## “¿Si borro algo localmente desaparece para siempre?”

No necesariamente. Git guarda historial si hiciste commit.

## “¿Puedo romper todo?”

Sí.
Pero menos de lo que pensás, y muchas veces se arregla.

## “¿Tengo que saber terminal sí o sí?”

Para aprender bien, sí conviene.
Después podés usar interfaz gráfica, pero primero entendé qué pasa.

---

# Propuesta de estructura real del repo

```text
github-para-petes/
├── README.md
├── .gitignore
├── presentaciones/
│   ├── gonza.md
│   ├── juan.md
│   └── maria.md
├── misiones/
│   ├── 01-clone-y-status.md
│   ├── 02-add-y-commit.md
│   ├── 03-push-y-pull.md
│   ├── 04-branches.md
│   └── 05-conflictos.md
└── desafios/
    ├── ranking-de-materias.md
    └── archivo-conflictivo.md
```

---

# Frases célebres del repo

* “No era un bug, era una feature pedagógica.”
* “Un `git push --force` al repo grupal y se pudre.”
* “`git status` antes de actuar, como mirar a ambos lados antes de cruzar.”
* “La diferencia entre una persona tranquila y un simio con teclado suele ser una branch.”

---

# Cierre

Si llegaste hasta acá, ya no estás en cero.

Tal vez sigas siendo medio pete en Git.
Pero ahora sos un pete con herramientas.

Y eso, en sistemas, ya te pone por encima de mucha gente.
