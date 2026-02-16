# Registro de Trabajo Receta


## 3. Crea un directorio denominado receta e inicializa un repositorio de git dentro del mismo mediante el comando apropiado.
```bash
mkdir receta
git init -b "main"
```

## 4. Verifica su correcta creación a través del comando git status y analiza la información que devuelve éste.
```bash

git status
	On branch main

	No commits yet

	nothing to commit (create/copy files and use "git add" to track)
```
Al no haber hecho ningún cambio dentro de nuestro repositorio este se encuentra vacio y por tanto sin nigun cambio sin hacer commit.

## 5. A continuación, crea dentro dos ficheros dentro del directorio
```bash
touch instruccines.txt ## Añadir contenido.
touch ingredientes.txt ## Añadir contenido.
git status
	On branch main

	No commits yet

	Untracked files:
  	(use "git add <file>..." to include in what will be committed)
		ingredientes.txt
		instrucciones.txt

	nothing added to commit but untracked files present (use "git add" to track)

git add ingredientes.txt instrucciones.txt
```

```bash

git status
	On branch main

	No commits yet

	Changes to be committed:
 	 (use "git rm --cached <file>..." to unstage)
		new file:   ingredientes.txt
		new file:   instrucciones.txt

git commit -m "Añadimos las instrucciones e ingredientes de la receta"
	[main (root-commit) 0ba4624] Añadimos las instrucciones e ingredientes de la receta
 	2 files changed, 10 insertions(+)
 	create mode 100644 ingredientes.txt
	 create mode 100644 instrucciones.txt

```
Despues de agregar contenido el working directory ya no esta vacio y por lo tanto 'git status' nos muestra cambios que tenemos que añadir al stagin area con el objetivo de hacer commit.

## 6. 7. 8.
```bash
git add ingredientes.txt instrucciones.txt
git commit -m "Añadimos las instrucciones e ingredientes de la receta"
```
El flag '-m' nos permite comentar el commit usando la misma linea de código.



## Añade 1/2 cebolla a la lista de ingredientes y la instrucción Disfrútalo! a la de instrucciones. Utiliza el comando necesario para visualizar en que han cambiado exactamente los ficheros del repositorio
```bash
echo "1/2 cebolla" >> ingredientes.txt 
echo "Disfrútalo! " >> instrucciones.txt

git diff
diff --git a/ingredientes.txt b/ingredientes.txt
	index 0e9d1d4..8b60850 100644
	--- a/ingredientes.txt
	+++ b/ingredientes.txt
	@@ -2,3 +2,4 @@
	 2 aguacates
	 2 limas
	 2 cucharaditas de sal
	+1/2 cebolla
diff --git a/instrucciones.txt b/instrucciones.txt
	index 654921c..6d9ec65 100644
	--- a/instrucciones.txt
	+++ b/instrucciones.txt
	@@ -4,3 +4,4 @@ Trocea la cebolla
 	Exprime la lima
	 Añade sal
 	Mezcla los ingredientes
	+Disfrútalo! 
```
Con git diff podemos observar que lineas se han añadido (+) en cada fichero.

## 10.
```bash
git add ingredientes.txt
$ git commit -m ”anade 1/2 cebolla”
$ git add instrucciones.txt
$ git commit # <-- Sin el flag -m
$ git log
	commit 1ec3e8ff89edd68bcea9f3134e1544fe5565800f (HEAD -> main)
	Author: Carlos Borges <c.borges.duran@gmail.com>
	Date:   Mon Feb 16 11:44:46 2026 +0100

    	Ultimas instrucciones

	Commit 6d4b665b326b3912e416a9eca1cec576406e4efa
	Author: Carlos Borges <c.borges.duran@gmail.com>
	Date:   Mon Feb 16 11:44:33 2026 +0100

    	Anade 1/2 cebolla

	Commit 0ba4624ee3b91a49ea2e150d1479dd07cb021507
	Author: Carlos Borgees Durán <c.borges.duran@gmail.com>
	Date:   Fri Feb 13 12:37:51 2026 +0100

	   Añadimos las instrucciones e ingredientes de la receta

$ git status
```
**¿Que efecto tiene no utilizar el flag -m al hacer commit?**
Al no usar el flag "-m" se nos abrira un editor de texto para asi poder introudcir una descripicón del commit más extendida.


## 11. Ejecuta el comando git log. ¿Qué información devuelve éste? ¿En que se diferencia de git status? ¿Que nos indica si lo usamos con el flag stat?
```bash
git log --stat

	commit 1ec3e8ff89edd68bcea9f3134e1544fe5565800f (HEAD -> main)
	Author: Carlos Borges <c.borges.duran@gmail.com>
	Date:   Mon Feb 16 11:44:46 2026 +0100

	    Ultimas instrucciones

	 instrucciones.txt | 1 +
	 1 file changed, 1 insertion(+)

	commit 6d4b665b326b3912e416a9eca1cec576406e4efa
	Author: Carlos Borges <c.borges.duran@gmail.com>
	Date:   Mon Feb 16 11:44:33 2026 +0100

	    anade 1/2 cebolla

	 ingredientes.txt | 1 +
	 1 file changed, 1 insertion(+)

	commit 0ba4624ee3b91a49ea2e150d1479dd07cb021507
	Author: Carlos Borgees Durán <c.borges.duran@gmail.com>
	Date:   Fri Feb 13 12:37:51 2026 +0100

	    Añadimos las instrucciones e ingredientes de la receta

	 ingredientes.txt  | 4 ++++
	 instrucciones.txt | 6 ++++++
	 2 files changed, 10 insertions(+)

```

La diferencia con status radica que este solo te muestra los cambios en local que no han sido todavía modificados, mientras que log nos da un resumen de todos los commits hechos a lao largo del proyecto

Usando el flag "--stat" obtendremos informacion sobre cuantas lineas  se han añadid
o ó eliminado.

## 12. 12. Revisa el contenido de un commit concreto (en este caso, el ultimo realizado) a través de su identificador hash mediante el comando git show <hash1>.
```bash
git show 1ec3e8ff89ed
commit 1ec3e8ff89edd68bcea9f3134e1544fe5565800f (HEAD -> main)
Author: Carlos Borges <c.borges.duran@gmail.com>
Date:   Mon Feb 16 11:44:46 2026 +0100

    Ultimas instrucciones

diff --git a/instrucciones.txt b/instrucciones.txt
index 654921c..6d9ec65 100644
--- a/instrucciones.txt
+++ b/instrucciones.txt
@@ -4,3 +4,4 @@ Trocea la cebolla
 Exprime la lima
 Añade sal
 Mezcla los ingredientes
+Disfrútalo! 
```

Mostrara solo la informacion del commit con ese numero de indetificación. Como vemos no hay que introducir el número completo si no una muestra de los primeros caracteres.

## 13. Visualiza las diferencias entre los dos últimos commits a través de sus respectivos hashes utilizando para ello el comando git diff <hash1> <hash2>
```bash
git show 1ec3e8ff89ed 6d4b665b32
```
Solo mostrara los commits con respectivas numeros de indetificación.



## Enlazar con repositorio remoto
```bash
git remote add origin git@github.com:cborges19/receta.git
git branch -M main
git push -u origin main
 ```
Primero tendremos que crear un repositorio en GitHub. Una vez realizado hay que enlazar el repositorio local con el remoto y también sus branchs. Por ultimo realizo un push para tener todo lo trabjado en el repositorio remoto.
