# I/O

## Read Jinja file template

```python
from jinja2 import Template

def read_template(query_template_file: str) -> Template:
    with open(query_template_file, "r") as query_template:
        return Template(query_template.read())
```

