# non-text nodes in links fails

    Code
      markdown("[`foo` bar][x]", tag = tag)
    Message
      x foo.R:10: @title (automatically generated) markdown links must contain plain text.
      i Problematic link: x
    Output
      [1] ""
    Code
      markdown("[__baz__][x]", tag = tag)
    Message
      x foo.R:10: @title (automatically generated) markdown links must contain plain text.
      i Problematic link: x
    Output
      [1] ""

# short and sweet links work

    Code
      out1 <- roc_proc_text(rd_roclet(),
      "\n    #' Title\n    #'\n    #' See [11pkg::function()], [11pkg::object].\n    #' @md\n    foo <- function() {}")[[
        1]]
    Message
      x <text>:4: @description refers to unavailable topic 11pkg::function.
      Caused by error in `find.package()`:
      ! there is no package called '11pkg'
      x <text>:4: @description refers to unavailable topic 11pkg::object.
      Caused by error in `find.package()`:
      ! there is no package called '11pkg'

---

    Code
      out1 <- roc_proc_text(rd_roclet(), block)[[1]]
    Message
      x <text>:4: @description refers to unavailable topic stringr::bar111.

# resolve_link_package name clash

    Code
      resolve_link_package("pkg_env", "roxygen2", test_path("testMdLinks2"), list(
        tag = tag))
    Message
      x foo.R:10: @title (automatically generated) Topic "pkg_env" is available in multiple packages: pkgload and rlang.
      i Qualify topic explicitly with a package name when linking to it.
    Output
      [1] NA

