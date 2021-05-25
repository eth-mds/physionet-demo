## Drat Repo

In order to generate the required `PACKAGES` files, `setup_bin_paths()` below can be run as

```r
setup_bin_paths <- function(base_path) {

  create_dirs <- function(dirs) {

    todo <- dirs[!dir.exists(dirs)]
    res <- vapply(todo, dir.create, logical(1L), recursive = TRUE)

    if (!all(res)) {
      stop("Directories\n  ", paste0(todo, collapse = "\n  "),
           "\n  could not be created\n", call. = FALSE)
    }
  }

  create_files <- function(dirs) {

    files <- file.path(dirs, "PACKAGES")
    todo <- files[!file.exists(files)]
    res <- file.create(todo)

    if (!all(res)) {
      stop("Files\n  ", paste0(todo, collapse = "\n  "),
           "\n  could not be created\n", call. = FALSE)
    }
  }

  setup_type <- function(type, vers) {

    versions <- sprintf("%1.1f", vers)

    base_dir <- dirname(utils::contrib.url(base_path, type))
    contrib_dirs <- file.path(base_dir, versions)

    create_dirs(contrib_dirs)
    create_files(contrib_dirs)
  }

  setup_type("win.binary", c(seq(3.2, 3.6, by = 0.1),
                             seq(4.0, 4.2, by = 0.1)))
  setup_type("mac.binary", seq(4.0, 4.1, by = 0.1))
  setup_type("mac.binary.mavericks", seq(3.2, 3.3, by = 0.1))
  setup_type("mac.binary.el-capitan", seq(3.4, 3.6, by = 0.1))
}

setup_bin_paths("docs")
tools::write_PACKAGES(file.path("docs", "src", "contrib"))
```

The selection of version numbers is taken from

* https://cran.r-project.org/bin/windows/contrib/
* https://cran.r-project.org/bin/macosx/contrib/
* https://cran.r-project.org/bin/macosx/el-capitan/contrib/
* https://cran.r-project.org/bin/macosx/mavericks/contrib/

