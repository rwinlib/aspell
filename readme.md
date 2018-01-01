# Aspell

In `PKGBUILD` set `--disable-shared` and in `/mingw32/lib` temporary rename `libiconv.dll.a` and `libintl.dll.a` to prevent static linking. Then compile with rtools.

```sh
RCONFIG="/c/Progra~1/R/R-3.4.2/bin/i386/R CMD config"
CXX11="`$RCONFIG CXX11`"
CXX11STD="`$RCONFIG CXX11STD`"
export CXX="$CXX11 $CXX11STD"
export CC="`$RCONFIG CC` $CPPFLAGS"
export LIBS="-L/mingw32/lib -lintl -liconv"
```

Especially note we set `-lintl -liconv` to fix static linking.