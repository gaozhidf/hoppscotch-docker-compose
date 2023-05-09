# hoppscotch-docker-compose

- self hosted hoppscotch with docker-compose
- ref: 
  - https://hoppscotch.io/
  - https://docs.hoppscotch.io/documentation/self-host/install-and-build/

#### setup docker and docker-compose

```bash
# install docker
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh

# install docker-compose
curl -L https://github.com/docker/compose/releases/download/1.18.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

#### setup your environment

```bash
git clone https://github.com/gaozhidf/hoppscotch-docker-compose.git
cp .env.example .env
```

#### prepare data

```
mkdir data

# user to postgresql data
chown -R 1000:1000 data
```

#### run docker-compose

```bash
docker-compose up -d
```

#### init data

```bash
docker exec -it hoppscotch-backend bash
pnpm exec prisma migrate deploy
```

#### web

- app web: http://localhost:3000
- admin web: http://localhost:3100
- mail web: http://localhost:1080

