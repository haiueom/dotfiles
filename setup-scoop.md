# Install Scoop

```powershell
iex (new-object net.webclient).downloadstring('https://get.scoop.sh')
set-executionpolicy unrestricted -s cu
```

# Install Packages

### Utils

```
scoop install 7zip curl sudo git openssh coreutils grep sed less
```

### Programming Languages

```
scoop install python ruby go nodejs
```

### WAMP Stack

```
scoop install apache mariadb php
iex (new-object net.webclient).downloadstring('https://gist.github.com/lukesampson/6546858/raw/apache-php-init.ps1')
```

### Console Theme

```
scoop install concfg pshazz
concfg export console-backup.json
concfg import solarized-dark
pshazz use ys
```

### Vim (opsional)

```
scoop install vim
'
set ff=unix
set cindent
set tabstop=4
set shiftwidth=4
set expandtab
set backupdir=$TEMP
' | out-file ~/.vimrc -enc oem -append
```

# Setup WAMP

## Apache

### Install apache as a service

```
sudo httpd -k install -n apache
```

### Run Apache:

```
sudo net start apache
```

If you open http://localhost in your browser, you should see a page saying that “It works!”.

Root dir:

```
pushd "$(scoop which httpd | split-path)\..\htdocs"
```

### Stop Apache:

```
sudo net stop apache
```

### Uninstall service:

```
sudo httpd -k uninstall -n apache
```

## Mysql

### Install mysql as a service

```
mysqld --install
mysqld --initialize
```

### Start mysql

```
sudo net start MySQL
```

### Stop mysql

```
sudo net stop MySQL
```

## Configure PHP

- https://github.com/ScoopInstaller/Scoop/wiki/Custom-PHP-configuration
