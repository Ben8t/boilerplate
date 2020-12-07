# I/O

## Read template file

=== "Python"
    ```python
    from jinja2 import Template

    def read_template(template_file: str) -> Template:
        with open(template_file, "r") as template_open:
            return Template(template_open.read())
    ```

    ```python
    template = read_template("folder/file")
    param = 123
    data = template.render(param=param)
    ```
    
    [Jinja documentation](https://jinja.palletsprojects.com/)

=== "R"
    ```R
    library(tidyverse)

    param <- 123
    data <- readr::read_file("folder/file") %>% glue(., param=param)
    ```
