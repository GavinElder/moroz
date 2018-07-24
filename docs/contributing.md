# Contributing

Welcome! If you're looking to help, this document is a great place to start!

## Building the project

To build Moroz from source, you will need [Go 1.10](https://golang.org/dl/) or later installed.

``` bash
# if GOPATH is unset:
# export GOPATH=${HOME}/go

# clone repo into GOPATH:
git clone git@github.com:groob/moroz $GOPATH/src/github.com/groob/moroz
cd $GOPATH/src/github.com/groob/moroz

# download dependencies and build:
dep ensure
cd cmd/moroz; go install; cd -
```

# Run

`moroz`
See `moroz -h` for a full list of options.

``` bash
Usage of moroz:
  -configs string
    	path to config folder (default "../../configs")
  -event-logfile string
    	path to file for saving uploaded events (default "/tmp/santa_events")
  -http-addr string
    	http address ex: -http-addr=:8080 (default ":8080")
  -tls-cert string
    	path to TLS certificate (default "server.crt")
  -tls-key string
    	path to TLS private key (default "server.key")
  -version
        print version information
```

## Git workflow

Go requires that your repo lives in `$GOPATH/src/github.com/micromdm/micromdm` even if you're trying to push to your github fork. To work with a forked copy, use a git remote.
Example:

``` bash
# clone repo into GOPATH:
git clone git@github.com:groob/moroz.git $GOPATH/src/github.com/groob/moroz

# add your remote/upstream
git remote add groob git@github.com:groob/moroz.git

# update from origin/master
git pull --rebase

# create a branch
git checkout -b my_feature

# push changes from my_feature to your fork.
#    -u, --set-upstream    set upstream for git pull/status
git push -u groob
```

## If you're new to Go

Go is a bit different from other languages in its requirements for how it expects its programmers to organize Go code files in directories.
First, Go requires a folder, called a workspace (you can name it anything you'd like) to exist for go source, dependencies, etc. Before Go 1.8 the path to this folder must always be set in the environment variable `GOPATH` (example: `export GOPATH=/Users/groob/code/go`). As of Go 1.8 the default `GOPATH` is set to `$HOME/go` but you can still set it to whatever you like.
Your `GOPATH` must have thee subfolders: `bin`, `pkg`, and `src`. Any code you create must live inside the `src` folder. It's also helpful to add `$GOPATH/bin` to your environment's `PATH` as that is where `go install` will place go binaries that you build. This makes it so that binaries that are insalled can just be invoked by name rather than their full page.

A few helpful resources for getting started with Go:

* [Writing, building, installing, and testing Go code](https://www.youtube.com/watch?v=XCsL89YtqCs)
* [Resources for new Go programmers](http://dave.cheney.net/resources-for-new-go-programmers)
* [How I start](https://howistart.org/posts/go/1)
* [How to write Go code](https://golang.org/doc/code.html)
* [GOPATH on the go wiki](https://github.com/golang/go/wiki/GOPATH)

To build Moroz you will need to:

1. Download and install [`Go`](https://golang.org/dl/)
2. Make a workspace directory and set the `GOPATH` as explained above.
3. Install [`dep`](https://github.com/golang/dep) via the command `go get -u github.com/golang/dep/...`
Note that `dep` is a very new project itself. If you're running trouble with the `dep ensure` command, ping @groob in the #micromdm channel on Slack.
4. `mkdir -p $GOPATH/src/github.com/groob`
5. `git clone git@github.com:groob/moroz.git` the project into the above folder.
The repo must always be in the folder `$GOPATH/src/github.com/groob/moroz` even if you forked the project. Add a git remote to your fork to track upstream.
6. `dep ensure` The `dep` command will download and install all necessary dependencies for the project to compile.
7. `go build` or `go install`
8. File an issue or a pull request if the instructions are unclear or problems pop-up for you.
