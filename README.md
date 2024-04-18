# comandos-git

git init => criar um novo repositorio vazio dentro da pasta

git status

<associar endereço remoto (do github) com o endereço do computador>

git remote add origin <link do repositorio no github>

git add . => adiciona todos os arquivos prontos para a nuvem

git commit -m "nome do commit"

git push origin <branch>

-------------------

git pull origin <branch> -> para puxar do github

fork:
https://docs.github.com/pt/get-started/quickstart/fork-a-repo

git clone (para forks ou não):
https://docs.github.com/pt/repositories/creating-and-managing-repositories/cloning-a-repository

-------------------

trocar branch

https://git-scm.com/docs/git-checkout
https://pt.stackoverflow.com/questions/411048/como-criar-uma-nova-branch-no-github

-------------------
git config 
https://git-scm.com/book/pt-br/v2/Come%C3%A7ando-Configura%C3%A7%C3%A3o-Inicial-do-Git

erros:
Git Error "fatal: invalid branch name: init.defaultBranch ="
https://stackoverflow.com/questions/64349920/git-error-fatal-invalid-branch-name-init-defaultbranch

! [rejeitado] mestre -> mestre (buscar primeiro)
https://stackoverflow.com/questions/28429819/rejected-master-master-fetch-first

Resolvendo o erro “fatal: refusing to merge unrelated histories” no Git
https://community.umbler.com/br/t/resolvendo-o-erro-fatal-refusing-to-merge-unrelated-histories-no-git/657

You have not concluded your merge (MERGE_HEAD exists)
https://stackoverflow.com/questions/11646107/you-have-not-concluded-your-merge-merge-head-exists
https://horadecodar.com.br/resolver-o-erro-you-have-not-concluded-your-merge/

-------------------

se o commit nao funcionar, tentar:
https://cursos.alura.com.br/forum/topico-erro-ao-execultar-git-push-74711

se após a troca de branch local, o commit não funcionar por já haver commit 
anterior:
https://stackoverflow.com/questions/28429819/rejected-master-master-fetch-first

-------------------
