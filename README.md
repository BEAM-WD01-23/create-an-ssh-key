# create an ssh key for GitHub

- [Video to follow along - similar to docs](https://www.youtube.com/watch?v=8X4u9sca3Io)


# Steps: 
1. Check if you have a ssh folder:
` ~/.ssh/config` 

This probably returns: 

`zsh: no such file or directory: /Users/your_name/.ssh/config`

2. Generate a key: replace the email with your email:

`ssh-keygen -t ed25519 -C "demo@example.com"`

This does the following: 
> Generating public/private ed25519 key pair.

> Enter file in which to save the key (/Users/your_name/.ssh/id_ed25519): 

Don't enter a prase, just press enter

> Enter passphrase (empty for no passphrase): 

> Enter same passphrase again: 

> Your identification has been saved in /Users/your-name/.ssh/id_ed25519

>Your public key has been saved in /Users/your-name/.ssh/id_ed25519.pub

**You now have a public and a private key!**
## Use this key for gitHub: 

1. On the terminal: activate the ssh agent:  
`eval "$(ssh-agent -s)"`
2. on the terminal: navigate to your home directory `cd ~`
3. List all files and folders `ls -a`
4. check if you have an `.ssh` folder and a `config` file by typing `open .ssh/config` or `ssh-add -l`
5. If not, add a file: `touch ~/.ssh/config`
6. Open the file with  visual studio code by typing 
`code config`

7. In the file: paste the following and save the file
```
Host github.com
  AddKeysToAgent yes
  IdentityFile ~/.ssh/id_ed25519
```

8. Go back to the terminal and navigate into the ssh folder:  `cd .ssh`

9. do the following: `ssh-add id_ed25519 `
10. show the content of your public key:
`cat id_ed25519.pub`
11. Copy the text now displayed. It starts with **ssh-ed25519** and ends with your email. 


12. Open the browser and go to your profile on GitHub and the setting *SSH and GPG keys* 
13. Click the button "New ssh key" and paste the text you copied from the terminal. 

14. Go back to the termial and confirm that it worked: `ssh -T git@github.com`

**Now you can clone using @ssh!**
