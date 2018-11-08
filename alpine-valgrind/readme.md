## Alpine for Valgrind

Valgrind always updates behinde the mac os, so we can use docker to run valgrind.

## Build

```
docker build --rm -t local/alpine-valgrind .
```

## Run
```
docker run -it -v ~/leetcode:/home/code --name=my-alpine local/alpine-valgrind
```

## Login
```
docker exec -it my-alpine /bin/zsh
```

After run and login, you can to build your cpp program in Alipine and to use valgrind to do memory-leak check.

Have a good try.

