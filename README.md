```
variant: flatcar
version: 1.0.0
passwd:
  users:
    - name: core
      password_hash: "HASH"
```

# HASH Password

```
mkpasswd --method=SHA-512 "password" >> flatcar.yaml
```

# BUTANE

```
wget -O butane https://github.com/coreos/butane/releases/latest/download/butane-x86_64-unknown-linux-gnu && chmod +x butane
```

# Convert X.yaml to X.ign

```
./butan flatcar.yaml > flatcar.ign
```

# Install Flatcar
```
sudo flatcar-install -d /dev/sdX -i flatcar.ign
```

# Run Portainer container (*inside flatcar OS*)

```
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v ./portainer_data:/data portainer/portainer-ce:lts
```
