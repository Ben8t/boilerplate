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

=== "R"
    ```R
    library(tidyverse)

    param <- 123
    data <- readr::read_file("folder/file") %>% glue(., param=param)
    ```

## Read many data files

=== "Python"
```python
import glob
import json

files = glob.glob("./*.json")  # get all json files in currenty directory

def read_file(filepath: str) -> dict:
    with open(filepath, "r") as fopen:
        return json.load(fopen)

data = [read_file(item) for item in files]
```