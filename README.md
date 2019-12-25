# go-webssh
1.13.5 

## sshd
> 浏览器共享远程linux终端  
> %GOPATH%=D:\goPro  
## 安装
>  修改 core/ssh.go 里面的账号密码地址等信息。 也可以自己修改成用密钥登录。
```go
func NewSshClient() (*ssh.Client, error) {
	config := &ssh.ClientConfig{
		Timeout:         time.Second * 5,
		User:            "root",
		HostKeyCallback: ssh.InsecureIgnoreHostKey(), //这个可以， 但是不够安全
		//HostKeyCallback: hostKeyCallBackFunc(h.Host),
	}
	//if h.Type == "password" {
	config.Auth = []ssh.AuthMethod{ssh.Password("123456")}
	//} else {
	//	config.Auth = []ssh.AuthMethod{publicKeyAuthFunc(h.Key)}
	//}
	addr := fmt.Sprintf("%s:%d", "192.168.31.186", 22)
	c, err := ssh.Dial("tcp", addr, config)
	if err != nil {
		return nil, err
	}
	return c, nil
}

```

```shell script

go build main.go
go run  main.go 

```

## 前端
> 我测试的时候用得是 vue，你可以放进你们项目里面。在web/vue/index.vue里面，记得修改32行的 后端地址

> 也可以自己弄个普通 index.html ，放一个websocket连接即可。

>  web/html  是普通版本index.html，未测试，仅供参考！


## demo

![SQL](static/demo/demo1.jpg)
