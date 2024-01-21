# Git Setup Script

How to setup git the first time

```bash
sudo apt install git ssh
git config --global user.name <user name here>
git config --global user.email <email here>
git config --global core.editor vim
```

#### Generate Key

```bash
cd ~/.ssh
ssh-keygen -t ed25519 -C "<comment>"
```

#### Add key to ssh-agent

- might not be needed, see if logout-login helps
- alternately restart ssh service (update this)

```bash
eval $(ssh-agent -s)
ssh-add <path/to/private/key>
```

#### Add config for Gitlab in `~/.ssh/config`

```bash
# GitLab.com
Host gitlab.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/gitlab_com_rsa

# Private GitLab instance
Host gitlab.company.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/example_com_rsa
```

#### Add SSH key to Gitlab account

On gitlab go to `Preferences -> SSH Keys` and copy the public key over there.

#### Test if you can connect

```bash
ssh -T git@gitlab.com
```

#### Debug if can't connect

```bash
ssh -Tv git@gitlab.example.com
ssh -Tvv git@gitlab.example.com
ssh -Tvvv git@gitlab.example.com
```

## Behind Proxy

Are you working behind a transparent proxy and setting up ssh is a bit too
complicated ?  
How about this ?

Use personal access tokens.

1. Generate a personal access token in gitlab.
2. Copy the personal access token.
3. Use it like this while cloning the repository.

```bash
git clone https://username:your-token@gitlab.com/your-username/your-repository.git
```

You don't need to supply the username and password each time.

## Gitignore

- [ ] To-Do: Add complete Notes about Gitignore
      [Link](https://www.freecodecamp.org/news/gitignore-file-how-to-ignore-files-and-folders-in-git/)
- [ ] To-Do: Add Notes about Repository Mirroring
- [ ] To-Do: Rename Repository to Git Notes
- [ ] To-Do: Add notes about git bare repository setup for dotfiles.