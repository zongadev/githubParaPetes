# GitHub para Petes

> Una guía interactiva, cariñosa y ligeramente agresiva para sobrevivir a Git y GitHub sin romper el proyecto grupal.

## Qué es esto

Este repo está pensado para gente de la facultad que:

* no sabe qué hace `git pull`
* le tiene miedo a la terminal
* sube un `.zip` al grupo en vez de hacer commit
* piensa que **merge** es una marca de ropa

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
Github lo podes manejar desde dos lugares. Uno creado hace recientemente poco que es su aplicacion llamada GitHub Desktop LA CUAL NO VAMOS A USAR HASTA QUE USTEDES NO ENTIENDAN GIT ASI NO SON UNO NENES IA. Y la que vamos a ver nosotros que es basicamente manejar Git desde la consola.
Pq es util saber manejarlo desde la consola? qsy flaco preguntale al chat.

Para arrancar hay que instalar git en nuestra terminal de linux y setear el ssh (vimos en redes que es un ssh btw, espero les resulte interesante implementarlo. Omar no estaba gaga del todo al final de cuentas).

Arrancamos instalando como ya sabemos (creo que ya lo hicieron pero no pasa nada)

`sudo apt install git`
Sencillo. Logro desbloqueado: instalaste git

Ahora hay que setear la ssh. Que es ssh: video de [que es ssh en 27 segundos:]( https://www.youtube.com/watch?v=GBIIQ0kP15E)

Arrancamos con:
```
git config --global user.name "Tu Nombre"
git config --global user.email "tu_email@ejemplo.com"
```
Generas una clave SSH asociada a tu correo, para esto es importante saber en donde estamos parados pq va a generar un archivo:
`ssh-keygen -t ed25519 -C "tu_email@ejemplo.com"`
Le dan enter hasta que este, no pongan ninguna contrasena, simplemente enter.

Ahora levantamos el agente (no pregunten):
```
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```
Y la parte donde los que tienen windows wsl no se si les va a funcionar:
Copian su clave ssh:
`cat ~/.ssh/id_ed25519.pub`
Van a su cuenta de github -> Settings -> SSH and GPG keys -> New SSH key.
Pegan la clave donde dice "key" y le ponen un nombre que quieran.

Prueban la conexion: `ssh -T git@github.com` y le van a tener que escribir 'yes' al ser la primera vez.

LISTO, INSTALARON Y CONFIGURARON GIT, LOS FELICITO.

---
# Primeros conceptos posta, agarrate catalina

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

Bien, arrancamos basicon basicon.
Que es clonar? Bascimanete es
> Traeme todo lo que esta en GitHub a mi compu
No solamente trae archivos sino informacion acerca del repositorio y demas boludeces.
Para clonar, lo que haces es copiar la URL del repositorio (o apretar el boton verde y copiar ahi) y en tu consola, parado donde queres que se haga la CARPETA del repositorio ejecutas
```git clone URL_DEL_REPO```. 
A partir de ahi podes abrir la carpeta (cd) y revisar que todo este bien. Como lo reviso:
```bash
cd github-para-petes
git status
```
### Qué pasó acá

* `clone` copia el repo remoto a tu máquina
* `cd` entra a la carpeta

Si todo salio bien te tendria que decir algo tipo *On branch main. Nothing to commit, working tree clean*. Basicamente te dice literalmente el estado del repositorio en tu pc.

ESTO ES EL PASO INICIAL. Ahora esa carpeta tiene un archivo oculto llamado .git, en base a eso ya no necesitas clonar sino hacer requests al servidor. 

BIEN, TERMINASTE EL PRIMER COSO, TODAVIA NO ESTOY ORGULLOSO DE VOS PERO PODES SEGUIR PARA DARME UNA ALEGRIA.

---

# Misión 2: Tu primer cambio sin delinquir

Editá un archivo, por ejemplo `presentaciones/tu_nombre.md`.

Poné algo así:

```md
# Hola, soy * nombre del inoperante *

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
Con el add basicamente haces eso, agregar. Le decis a git: "*yo a esto que toquetee lo quiero subir al repositorio*"
add agrega CAMBIOS, no archivos. Es decir, si vos modificas un archivo, tenes que hacer un add.
Los add se hacen siempre al final, no creas un archivo, le haces un add y despues lo modificas.
El `git add .` agrega todo los cambios que esten dentro  de la carpeta. Es util? si. Es recomendado? no. Porque te agrega archivos de mas, como por ejemplo los codigos compilados mas los codicos .c
## Paso 2: guardar cambios

```bash
git commit -m "Agrega presentación de nombre_del_inoperante"
```

### Qué significa

* `add` pone cambios en el área de preparación
* `commit` guarda esa versión en el historial
---

# Cómo escribir commits que no den vergüenza

## Buenos commits

* `Agrega archivo de presentación de Gonza`
* `Corrige typo en README`
* `Suma ejercicio de ramas`

## Malos commits

* `cosas`
* `arreglo`
* `aaa`
* `ahora si`
* `dale hijo de puta funciona`

Ese último es emocionalmente válido, pero técnicamente pobre.

No hace falta que sean tan formales aca, pero si la idea es que logre explicar bien que carajos agregaron y bla bla. CREO que el commit lleva un nombre y una descripcion, con el nombre alcanza.
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

### Temita particular
Nosotros utilizamos el repo de protocolos (el del profe) pero simplemente para verlo, no para subir cosas. El tema es que nosotros igual modificamos las cosas del repo y agregamos nuestros archivos. Es por eso que al pullear es muy muy probable que te tire algun error. Lo que nosotros usamos en este caso es: `git pull --rebase --autostash`.
- autostash: guarda automaticamente en un stash todos los cambios locales nuestros para despues sacarlos.
- sobreescribe todos los cambios sobre lo que nosotros hagamos hecho (asi que guarda si modifican directamente el archivo del profe, la idea es que tengan sus copias)

---

# Misión 5: Branches aka ramas

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

Trabajás en una rama para no romper la principal y despues si no hay superposiciones la fusionas con la principal.

Es como hacer experimentos en un laboratorio y no en el comedor de tu casa.

---

# Cuándo usar branches

Usalas cuando:

* vas a agregar una feature
* vas a tocar varias cosas
* no querés romper `main`
* querés fingir profesionalismo industrial

No hace falta crear una branch para cambiar una coma en un archivo o incluso por nada hace falta usar branches, pero conviene practicar igual.

---

# Misión 6: Pull request explicado.
Aclaracion: jamas use esto pq siempre trabaje solo asi que estamos en bolas todos. No se ni donde se hacen ni como se hacen xd

Una **pull request** es básicamente:

> “Che, hice estos cambios. ¿Los revisan y los metemos al proyecto?”

Sirve para:

* revisar cambios
* comentar código
* evitar que cualquiera entre con una topadora a `main`

---

# Conflictos: el boss final

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
ATENCION: suele ser un bardo lo que te muestra git en los conflictos. Que conviene? abrir ambos codigos y chequear. Es un plomo realmente pero bueno, c'est la vie.

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

## Flujo normal si trabajás solo en una tarea en branch

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
NO SIGNIFICA QUE PUEDAN TOQUETEAR COMO SI NADA

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
│   ├── emi.md
│   ├── matiDS.md
│   └── rochi.md
└── tarea/
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
