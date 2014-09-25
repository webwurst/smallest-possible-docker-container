Smallest Possible Docker Container
==================================

All credit goes to [Adriaan de Jonge - Create the smallest possible Docker container](http://blog.xebia.com/2014/07/04/create-the-smallest-possible-docker-container/)!

tl;dr

    $ git clone https://github.com/webwurst/smallest-possible-docker-container.git
    $ cd smallest-possible-docker-container

    $ docker run -ti -v $(pwd):/gopath/bin google/golang \
      go get github.com/adriaandejonge/helloworld

    $ ldd helloworld
    $ ls helloworld -l

    $ docker run -ti -v $(pwd):/gopath/bin -e "CGO_ENABLED=0" google/golang \
      go get -a github.com/adriaandejonge/helloworld

    $ ldd helloworld
    $ ls helloworld -l

    $ docker run -ti -v $(pwd):/gopath/bin -e "CGO_ENABLED=0" google/golang \
      go get -a -ldflags '-s' github.com/adriaandejonge/helloworld

    $ ldd helloworld
    $ ls helloworld -l

    $ docker build --tag helloworld .
    $ docker images helloworld

    $ docker run -p 8080:8080 helloworld
