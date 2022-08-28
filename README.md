# Guide to connect Heroku and Github via SSH

> Working on Ubuntu 18.04 LTS, Mac and Win 10

- [x] Create SSH key in your machine:

```
$ ssh-keygen -t rsa -b 4096 -C "my@email.com" 
```

- [x] Check if `id_rsa` and `id_rsa.pub` were created:

```
$ ls -al ~/.ssh
```

> `id_rsa.pub` is public and it's shared with github and heroku to secure the connection between your machine and the servers.

- [x] Check if `ssh-agent` is up and running:

```
$ eval "$(ssh-agent -s)"
```

- [x] Now register the file, then when we connect with SHH, this file will be used. To register, run:

```
$ ssh-add ~/.ssh/id_rsa
```

> We get the public key value, now we have to copy to clipboard:

```
$ cat ~/.ssh/id_rsa.pub
```

> Now, go to GitHub's setting -> SSH Keys -> New SSH key, and paste the public key, then save.

- [x] Check the connection:

```
$ ssh -v git@github.com
```

- [x] Set the Heroku public key:

```
$ heroku keys:add
```

- [x] Create a new Heroku project, the name must be unique:

```
$ heroku create unique-names-application
```

> This create a remote branch, then when you run `git remote origin`, heroku branches would appear.
In `package.json` you must specify the script that initializes the app: `"start":"node file-route.js"`
>
> Define ports environment variable, Heroku will give a port -> const port = process.env.PORT || 3000

- [x] Push to Heroku:

```
$ git push heroku master
```
