# Dicas de Github para Linux




Se você ainda não usou/instalou git favor visite: [Link](https://github.com/padoinedson/tips/blob/main/git.md)

# CRIAÇÃO DA CONTA 


> Acesse https://github.com/ e crie a sua conta





## clonar os repositórios remotos da disciplina com modo de acesso do servidor remoto http

$ git clone https://github.com/padoinedson/sd2023.git

$ git clone https://github.com/padoinedson/sd2023exercicios.git




# CONFIGURAÇÃO  

## 1o. trocar o modo de acesso do servidor remoto (http -> ssh)

### listar servidor remoto

$ cd sd2023exercicios  
$ git remote -v

> origin  https://github.com/padoinedson/sd2023exercicios.git (fetch)  
> origin  https://github.com/padoinedson/sd2023exercicios.git (push)  
> verifique que está como https  


### trocar o modo de acesso
$ git remote set-url origin `git@github.com:padoinedson/sd2023exercicios.git`


### verificar o modo de acesso
$ git remote -v

> origin  git@github.com:padoinedson/sd2023exercicios.git (fetch)  
> origin  git@github.com:padoinedson/sd2023exercicios.git (push)  
> agora está como ssh





## 2o. criar uma chave ssh com o seu login do github


$ sudo apt install ssh

> substitua `seu-login-no-git-hub` pelo seu `login` no github  

$ ssh-keygen -t ed25519 -C `seu-login-no-github@github.com`

$ eval ` "$(ssh-agent -s)"  `

$ ssh -vT ` seu-login-no-git-hub@github.com `

$ ssh-add `~/.ssh/id_ed25519`

$ cat ` ~/.ssh/id_ed25519.pub `

> adicionar a chave púclica para o github em ` settings ` - `SSH and GPG keys `  
> copie ela para a sua conta  (não cole os espaços ou quebra de linha)


Add-WindowsCapability -Online -Name OpenSSH.Client

Set-Service -Name 'ssh-agent' -StartupType 'Manual'

Start-Service ssh-agent

ssh-keygen -t ed25519 -C "your-email@example.com"

ssh-add "$env:USERPROFILE\.ssh\id_ed25519"

Get-Content "$env:USERPROFILE\.ssh\id_ed25519.pub" | Set-Clipboard



# UTILIZAÇÃO  


## copiar as modificações do servidor para o repositório local

$ git pull






## adicionar um arquivo
 
$ resolva os exercicios no arquivo e salve dentro da pasta com nome `ex-seunome.c`

$ git status

$ git add `ex-seunome.c`.txt

$ git status

$ git commit -m "entregando exercicio n"



## copiar as modificações do repositório local para o servidor `github`

$ git push 













* [Link](https://docs.github.com/pt/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)



## adicionar ssh
* [Link](https://docs.github.com/pt/github/authenticating-to-github/connecting-to-github-with-ssh)



## trocar https por ssh
* [Link](https://docs.github.com/pt/github/getting-started-with-github/getting-started-with-git/managing-remote-repositories#switching-remote-urls-from-https-to-ssh)




## adicionar colaboradores
* [Link](https://docs.github.com/pt/github/setting-up-and-managing-your-github-user-account/managing-access-to-your-personal-repositories/inviting-collaborators-to-a-personal-repository)



### site 
* [Link](http://git-scm.com/)
