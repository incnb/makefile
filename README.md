# Makefile skeleton project

This is just a simple makefile-project skeleton which I using when
no need to use GNU Autotools or other Makefile-generators.

Features:

- Simple including pkg-config defined libraries(LIBS property)
- Making .tar.gz distrib files for emailing and other repository-free
  sharing(make dist)
- Objects and dependencies files generating in hidden folder for
  more short ls output
- Version autocheck from git tag and offset(with version.sh script)
- Auto ChangeLog.txt generation from git history
- Simple debug building(with gdb flags)
- CMake-like build output

---

This makefile can be used out-of-the-box only for c-projects and actually I
don't think it is expedient to make any changes in it, write new Makefile
for non-c project will be easier.

## How to use it?

```bash
$ mkdir project && cd project
$ git clone https://www.github.com/inickey/makefile/ ./ && git init
$ cat Makefile | sed 's/makefile/project/g' > Makefile
$ git add -A && git commit -m 'initial commit' && git tag v0.0
```

## How to version?

Versions in it is [MAJOR].[MINOR].[COMMIT]. Major and minor versions is
set manually with git tag command in tag-name format v[MAJOR].[MINOR]
```bash
$ git tag v1.2
```
This command will set major to 1 and minor to 2. Third part of version,
commit number will increments automatically, with every commit.
History in ChangeLog.txt will be cleaned with every new tag.

## How to code?

You just should paste any *.c and *.h files in root directory, make will
search every source file, compile it and then link all files together to
$(TARGET) property of makefile. If you use any libraries(for example
glib-2.0) you should paste it to LIBS property of makefile
```Makefile
LIBS = glib-2.0
```

---

Actually I use it only for beginning some new projects that I don't know
will complete or support(but there's some exceptions of this rule).
Usually later I changing it Makefile for GNU Autotools.
