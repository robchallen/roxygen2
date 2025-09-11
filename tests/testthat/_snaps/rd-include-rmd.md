# invalid syntax gives useful warning

    Code
      . <- roc_proc_text(rd_roclet(), block)
    Message
      x <text>:2: @includeRmd requires a path.

# useful warnings

    Code
      . <- roc_proc_text(rd_roclet(), block)
    Message
      x <text>:3: @includeRmd Can't find Rmd 'path'.

