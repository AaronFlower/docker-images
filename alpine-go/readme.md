# Alpine for Go Web-Server

Alpine for go web-server to use.

## Build

```
docker build --rm -t local/alpine-go .
```

## Run
```
docker run -it -v ~/leetcode:/home/code --name=my-alpine-go local/alpine-go
```

## Login
```
docker exec -it my-alpine-go /bin/zsh
```

After run and login, you can test your go program.

Have a good try.

