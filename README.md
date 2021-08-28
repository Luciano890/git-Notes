# git-Notes
notas avanzadas de git

# Menú

- [help](#help)
- [diff](#diff)
- [amend](#amend)
- [log](#log)
  - [stat](#stat)
- [cherry-pick](#cherry-pick)
- [reset](#reset)
  - [soft](#soft)
  - [mixed](#mixed)
  - [hard](#hard)
- [reflog](#reflog)
- [tag](#tag)
- [show](#show)
- [stash](#stash)
- [fetch](#fetch)
- [pull rebase](#pull-rebase)
- [rebase](#rebase)
  - [interactivo](#interactivo)
- [switch](#switch)
- [restore](#restore)
  - [staged](#staged)
  - [wortree](#worktree)
  - [source](#source)
- [grep](#grep)
- [flag](#flag)
- [merge octopus](#merge-octopus)

---

## help

Para obtener ayuda de los comandos

`git <comando> -h` o `git <comando> -help`

## diff

Sirve para observar los cambios remotos y locales

`git diff`

> Diferencias entre un commit y otro

`git diff <hash1> <hash2>`

> hash ejemplo: a9fb66f2e9

> Diferencias entre tags

`git diff <tag1>...<tag2>`

## amend

Sirve para sobreescribir un commit 

`git commit --amend`

## log

Sirve para ver el historial de los commit

`git log`

### stat

Sirve para ver los archivos modificados de un commit

`git log --stat`

## cherry-pick

Sirve para copiar commits de un branch a otro

`git cherry-pick <hash>`

## reset

Sirve para devolver a estados de un commit

### soft

- "elimina" los commits posteriores al commit al que estas haciendo el reset
- conserva los cambios en el stage area
- conserva los cambios que tengas en tus archivos (working directory)

`git reset --soft <hash>`

### mixed

- "elimina" los commits posteriores al commit al que estas haciendo el reset
- Deshace los cambios en el stage area
- conserva los cambios que tengas en tus archivos (working directory)

`git reset <hash>`

### hard

- "elimina" los commits posteriores al commit al que estas haciendo el reset
- Deshace los cambios en el stage area
- Deshace los cambios que tengas en tus archivos (working directory)

`git reset --hard <hash>`

## reflog

Historial completos del branch

`git reflog`

## tag

Etiquetar diferentes versiones a un commit especifico

`git tag <version> <hash>`

**Ejemplo**

`git tag v0.0.1 <hash>`

> el hash es opcional solo si estamos en el commit que va a tener el tag

### Anotados

**Ejemplo 1**

`git tag -a <version>`

**Ejemplo 2**

`git tag -a <version> -m <mensaje>`

## show

Muestra información

**Ejemplo**

`git show v1.0.1`

**Ejemplo 2**

`git show master`

**Ejemplo 3**

`git show <hash>`

## stash

Guardar cambios sin hacer commit

* `git stash` en el branch donde se quiere hacer esto
* `git stash list` listar las cosas del stash
* `git stash apply` aplicar los cambios guardados en el stash
* `git stash drop` borrar stash de la pila de cambios
* `git stash pop` apply y drop, al mismo tiempo

## fetch

Pregunta al remoto si hay cambios importantes

`git fetch origin`

## pull rebase

pull sin commit, evita cambios recursivos

`git pull --rebase <branch>`

## rebase

Modifica los commits de tal manera que el grafo de commit quede plano

`git rebase`

### interactivo

Aplasta commits a uno solo, al colocar en el prefijo de los hashes el comando squash y pick al commit donde se van ha aplastar

![image aplastar commit](https://user-images.githubusercontent.com/62488915/131203242-c003375e-a4aa-4988-8688-fb619b83a349.png)

`git rebase -i HEAD~4`

![imagen rebase interactivo](https://user-images.githubusercontent.com/62488915/131203113-ebfe3035-8af2-4f5b-8c52-a557255ef0f2.png)

## switch

Caracteristica nueva de git, parecida al chekout

1. Cambiar de rama

`git switch <branch>`

2. Crear una rama

`git switch -c <newbranch>`

3. Craer ramas en blanco

`git switch --orphan <newbranch>`

4. Descartar cambios al cambiar de rama

`git switch --discard-changes <newbranch>`

## restore

Deshace cambios hechos en un archivo

`git restore <nombre-archivo>`

### staged

Devolver los cambios de staging area al working directory

`git restore --staged <nombre-archivo>`

### worktree

Deshace cambios de todas partes

`git restore --staged --worktree <nombre-archivo>`

### source

Deshace cambios de un hash

`git restore --source=<hash> <nombre-archivo>`

## grep

Buscar ocurrencias dentro del código fuente actual

`git grep <nombre-metodo>`

`git grep <nombre-metodo> --<fuente>` busca especificamente en la fuente dada

## flag

Dividir un commit en varios parches

[parte 1](https://www.youtube.com/watch?v=x62NzXLvCTM&list=PLTd5ehIj0goMCnj6V5NdzSIHBgrIXckGU&index=29)

[parte 2](https://www.youtube.com/watch?v=mMRDe60mjD8&list=PLTd5ehIj0goMCnj6V5NdzSIHBgrIXckGU&index=30)

## merge octopus

Hacer merge de varios branches

`git merge <dat1> <dat2> <dat3> ...`
