# Guide to connect Heroku and Github via SSH

> Working on Ubuntu 18.04 LTS and Win 10

Create SSH key in your machine:

```
$ ssh-keygen -t rsa -b 4096 -C "my@email.com" 
```

Check if "id_rsa" and "id_rsa.pub" were created:

```
$ ls -al ~/.ssh
```

id_rsa.pub is public and it's shared with github and heroku to secure the connection between your machine connection and the servers.

Check if "ssh-agent" is up and running:

```
$ eval "$(ssh-agent -s)"
```

Now register the file, then when we connect with SHH, this file will be used. To register, run:

```
$ ssh-add ~/.ssh/id_rsa
```

We get the public key value, and you must to copy to the clipboard:
```
$ cat ~/.ssh/id_rsa.pub
```

Then, go to GitHub's setting -> SSH Keys -> New SSH key, and paste the public key, then save.

Check the connection:

```
$ ssh -v git@github.com
```

Set the Heroku public key:

```
$ heroku keys:add
```

Create a new Heroku project, the name must be unique:

```
$ heroku create unique-names-application
```

This create a remote branch, then when yopu run "git remote", origin and heroku branches must be appear.
In "package.json" you must specify the script that initialice the app: "start":"node file-route.js"
Define ports environment variable, Heroku will give a port -> const port = process.env.PORT || 3000

Push to Heroku:

```
$ git push heroku master
```
