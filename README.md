# mmap test

## Test if mmap works using internal docker filesystem

``` bash
$ docker run --rm -it eugeneware/mmap
hello
world
mmap works from internal filesystem - hoorah!
```

## Test if mmap works using volume mapping:

Mape sure `local.txt` is in your current directory. This tests if the
volume that you're mapping from can run `mmap()`. In the case of
virtualbox's `vboxvfs` it can't. See [this issue](https://www.virtualbox.org/ticket/819)
for more details.

``` bash
$ docker run --rm -it -v `pwd`/local.txt:/app/test.txt eugeneware/mmap
hello
world
mmap works from local file - hoorah!
```

If you get any other error message and don't see the contents of the file
then there is an issue with `mmap()` or the file system stopping access
to the file.

## Build it yourself

``` bash
$ docker build -t eugeneware/mmap .
...
```
