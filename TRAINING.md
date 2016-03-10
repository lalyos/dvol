## Start the plugin

```
docker run -d \
  -e DIR_PERM=0700 \
  -v /var/lib/dvol:/var/lib/dvol \
  --restart=always \
  -v /run/docker/plugins:/run/docker/plugin \
  -v /var/run/docker.sock:/var/run/docker.sock \
  --name=dvol-docker-plugin \
  lalyos/dvol:latest
```

## init dvol

```
dvol init names
```

## init db

```
docker exec -it psql psql -U postgres -tc "create table names (name varchar(20));"
add (){ NAME=${1:? reguired name};docker exec -it psql psql -U postgres -c "insert into names values ('$NAME');" }
alias all='docker exec -it psql psql -U postgres -tc "select * from names;"'
add odon
add bela
add jeno
```

## commit

```
dvol commit -m "3 ember"
```

## new brach

```
dvol checkout -b sok
add jolan
add piroska
add lujza

dvol commit
```

## switch back

```
dvol checkout master
all
dvol checkout sok
all
```

