# Run

1. log in to workbench. copy the cookie token.
2. run this in sso-portal: ``WORKBENCH_COOKIE='workbench-backend=<value copied from DevTools>' pnpm dev``
3. visit https://localhost:5173
4. If access denied, delete domain security policies: chrome://net-internals/#hsts


# Mount and deploy to test server

> [!info]
> I have 192.168.133.22 mapped to reports.nexxar.com in C:\Windows\System32\drivers\etc\hosts

### Mounting SFTP Directory in Windows

1. Install [SFTP Drive](https://www.nsoftware.com/sftp/drive/)
2. Create New Connection with Drive letter "R", user "sso", Password
	- server: `reports.nexxar.com`
	- user: `sso`
	- pw: `couGa7oe7Ceeghithahd`
	- port: 22
	- laufwerksbuchstabe: `R`

### Mounting SFTP Directory in WSL

> [!info]
> This is a direct sshfs connection from WSL to the server's IP — it does not depend on the Windows R: drive being mounted, they're independent connections.

1. First send your public ssh key to Infra.
2. Install sshfs

```bash
sudo apt install sshfs
```

3. Create the mount point:

```bash
mkdir -p /mnt/r
```

4. Mount:

```bash
sshfs -o IdentityFile=/home/stefan/.ssh/id_ed25519,reconnect,ServerAliveInterval=15,ServerAliveCountMax=3 sso@192.168.133.22:/ /mnt/r
```

If not working try: `sudo sshfs -o allow_other,IdentityFile=/home/stefan/.ssh/id_ed25519 sso@192.168.133.22:/ /mnt/r`

5. deploy:

```
   scripts/deploy_dev.sh
```

8. Unmount:
9. 
```bash
fusermount -u /mnt/r
```


# Errors

- ChunkLoadError: 
	reason: Was about folder and file rights.
	fix: filezilla: statistics folder to "755" and files within to "644"

# Test user

- **Shell Workshop login:** `workshop@shell.com` -> `uEJxp5etA?`
- **Kion ar20 jtb:** `jtb@tobler.at` -> `cHRu+4gGJi`
- **Demo user:** `demo@nxr.com` (can be found in WB) -> `1234Nexxar%`
- **Demo user:** `testuser@test.com` (can be found in WB) -> `np8+mSzwfg`
- **Miriam Lenzing AR25:** `miriam@test.at` `h7UJjeuZ&K`

# Worbench REST API

- `https://wiki.nexxar.com/software_wiki/workbench-backend-api/`
- `/clients/`
- `/clients/{clientName}/reports`

# Long term: Live Stats Pro — Create our own statistic presentation

- Backend: Hedwig via WB
- Frontend: Vite React Typescript
- report manager links to live-statistics.nexxar.com with query params including client and report
- react eco system support for pdf creation and charts
- for seperation of concern and parallel development (report manager will be updated to vue3)