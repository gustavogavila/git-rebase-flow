# Fluxo GIT

## Antes de iniciar uma nova feature
```
# Atualiza todos os repositórios remotos e limpa branchs remotas deletadas (--prune)
git fetch --all -p

# Faz o rebase com a branch remota principal
git rebase origin/main

# Cria a branch feature a partir da principal
git checkout -b feature/GUS-05

```

## Manter a branch de feature sempre atualizada com a principal
```
git fetch --all -p
git rebase origin/main

```

## No fim do dia, commitar as alterações e subir para branch de feature remota
```
git add .
git commit -m "Mensagem de commit"
git fetch --all -p
git rebase origin/main
git push origin feature/GUS-05

```

## No início do dia sempre atualizar com a branch principal
```
git fetch --all -p
git rebase origin/main

```

## Quando subir mais código para a branch de feature remota no final do próximo dia, dar um push forçado
Como estamos sempre atualizando nossa branch de feature privada local com a branch principal remota pública através do rebase, estamos constantemente reescrevendo nosso histórico de commits privado local. Consequentemente, quando subirmos o código para nosso branch de feature privada remota, o git vai acusar divergência e não vai deixar executar o push.
Apenas nesse caso, pode-se fazer um push forçado, pois estaremos apenas dizendo para o git "Agora esse é o histórico correto. Por favor, substitui na branch remota"

```
git push -f origin feature/GUS-05
```

## Resolver conflitos no momento de atualizar a branch de feature com a principal
```
# Resolve os conflitos manualmente
git status
git add .
git rebase --continue
# Edita a mensagem de commit de resolução de conflito
Resolução de conflitos

```

## Fazer limpeza nos commits antes de abrir o PR
```
git rebase -i origin/main
# Trocar "pick" por "s" de squash nos commits que vc quer remover
# Trocar "pick" por "e" de edit nos commits que vc quer deixar e editar a mensagem

# Se não houverem conflitos
git rebase --continue

# Edita a mensagem de commit que ficará e apaga as que serão removidas

# Sobe o código para a branch feature remota, provalvemente de modo forçado, pois o histórico foi modificado pelo rebase.
git push -f origin feature/GUS-5

## Abre o PR

```


