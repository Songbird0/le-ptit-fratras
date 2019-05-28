# OS et version [testé]

Ubuntu 18.04

- download `docker-credential-pass`.
`wget` https://github.com/docker/docker-credential-helpers/releases/download/v0.6.0/docker-credential-pass-v0.6.0-amd64.tar.gz
- unpack `tar -xf docker-credential-pass-v0.6.0-amd64.tar.gz`
- i couldn't configure `$PATH` environment variable, so i copied unpacked file to `/usr/bin` directory.
- check that `docker-credential-pass` work. To do this, run command `docker-credential-pass`. 
You should see: `Usage: docker-credential-pass <store|get|erase|list|version>`.
- install gpg and pass. `apt install gpg pass`
- `gpg --generate-key`. Enter your name, mail, etc. 
You will get gpg-id like `5BB54DF1XXXXXXXXF87XXXXXXXXXXXXXX945A`. Copy it to clipboard.
- `pass init` (paste from clipboard)
- `pass insert docker-credential-helpers/docker-pass-initialized-check` and 
set the next password `pass is initialized`.
- `pass show docker-credential-helpers/docker-pass-initialized-check`. You should see "*pass is initialized*".
- `docker-credential-pass list`. You should see `{}` or another data. 
You shouldn`t see error like "*pass store is uninitialized*".
- `nano ~/.docker/config.json`. Set in root node the next line `"credsStore": "pass"` save ctrl+o.
- after docker login and etc.

## Source

https://github.com/docker/docker-credential-helpers/issues/102#issuecomment-388634452
