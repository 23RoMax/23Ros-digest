---
title: "Sunday Is Golangday #1"
date: 2018-04-29T18:22:19+02:00
draft: false
categories: ["programming", "golang"]
tags: ["golang", "go", "sunday-funday"]
description: "Beginners Go tutorials and other funky things"
keywords: ["SQL", "programming", "SQL snippets", "23Ro", "sql", "magic"]
---

Sunday is Golangday will be a new series of golang related learnings of mine. As I have just started learning Golang, this will be mainly focusing on the basics of the go programming language.

<figure>
    <img src="/images/golang.jpg" alt="Golang" style="width: 650px;"/>
    <figcaption>Gopher image by <a href="https://reneefrench.blogspot.de/">Renee French</a>, licensed under <a href="https://creativecommons.org/licenses/by/3.0/">Creative Commons 3.0 Attributions license.</a></figcaption>
</figure>

# What is golang

Go (by Google) is a programming language created at Google in 2009. Not to be confused with Go! (a functional programming language developed by Francis McCabe, and Keith Clark and first appeared in 2003). [Golang](https://github.com/golang/go) or [Go](https://github.com/golang/go) by Google is an open source, statically typed language, in the tradition of C.

I do a lot of shell scripting, and often I need a connection with an rdbm systems that should handle multiple connections, therefore concurrency and multithreading are a very welcome thing to me. To this date, I wrote all of the shell scripts with the usage of psql commands for Postgres, or sqlite3, now I am hoping that I can build up all the tools for validating data in go.

>Go is an open source programming language
>that makes it easy to build simple,
>reliable, and efficient software.

Under [golang.org](https://golang.org) you can find out all about go. A very recommendable read about golang is ["Why you should learn go" on medium by Keval Patel](https://medium.com/@kevalpatel2106/why-should-you-learn-go-f607681fad65)

I recommend to take yourself 30 minutes and watch this **A Tour of Go** Video by Russ Cox.

You can also find this Video here: [golang.org](https://golang.org/).

Also I want to mention that AlphaGo Google Deep Mind's Go (Asian board game) which is the first computer programm beating a human in this game, is most likely only sharing the name, and not written in Go, but in C++, LUA and or others. According to my online research. If this is wrong, please let me know! (I mention this specifically because in a recent office discussion, we were unsure whether Go was used to develop AlphaGo).

But [Hugo](https://gohugo.io/), the static website engine I'm writing this blog with, is written in go. Much interesting!

# First steps in golang

Setting up a basic training environment is not necessary, if you do not want to build binaries yourself and run them indepently on your machine, and if you have internet. Under [https://play.golang.org/](https://play.golang.org/) everyone can run code in the playground, a webservice running on golang.org's servers. It basically just receives the code from the website, compiles, links, and runs it in a sandbox environment, and passes the outpout back to the website. Most of the standard libraries work, communication to the outside world is limited to stdout and stderr, and also it is limited on the CPU and execution time (for obvious reasons). It's sourcecode can be found [here](https://go.googlesource.com/playground).

Here you can see a cool towers of hanoi implementation in Go in the go playground: [Towers of Hanoi in Golang](https://play.golang.org/p/31rOVYnNcbX).

![Towers of Hanoi](/images/towers.gif)

## Installing golang in your environment

Except of my standard candidate windows, I haven't had any troubles setting up the golang toolchain. It's as easy as downloading the correct binary [here](https://golang.org/dl/) and installing it on your machine. On windows I had some problems with the environment variables and the powershell, but with a bit tinkering, I was able to solve it. As it is a couple of days ago, I do not remember the specific issue and solution.

A simple hello-world.go program can be written in any text editor (I use Visual Studio Code), and looks like this:

```go
package main

import "fmt"

func main() {
	fmt.Println("Sayonara, Hello World!")
}
```

Saved as a *.go file in your preferred folder, you can now execute

```shell
go run <yourfilename>.go
```

to let it compile, link, and run in your current shell instance. If you want to build you file and create a binary you need to run

```shell
go build <yourfilename>.go
```

Visual studio code offers a huge variaty of helpful plugins for working with go.

# Next steps

Next week I will talk about the explicity of this language and in how far variable declarations are close or not close to the classical C type. Also I will explain why I think that the Golang explicit variable declaration is even easier to read than the ones in C type languages.