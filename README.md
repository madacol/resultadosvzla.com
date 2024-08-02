This is a fork of <https://github.com/xaiki/resultadosvzla.com> so it can be directly served by an HTTP server

---

After cloning that repository, I renamed most files to include the `.html` extension

```bash
rename 's/$/.html/' estado/*
rename 's/$/.html/' municipio/*
rename 's/$/.html/' parroquia/*
rename 's/$/.html/' centro/*
find mesa -type f -name "index.html" -exec sh -c 'mv "$0" "${0%/*}.html"; rm -r "${0%/*}"' {} \; # normalize filenames from `mesa/*/*/index.html` to `mesa/*/*.html`
rename 's/(\d+)$/$1.html/' mesa/*/*
```

Now you can run with any HTTP server that maps URL paths like `estado/3` to the file `estado/3.html`, like `http-server`:

```bash
npx http-server -p 8080
```
