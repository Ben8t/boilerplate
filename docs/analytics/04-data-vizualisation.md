# Data-Vizualisation

## Custom ggplot theme

```R
custom_theme <- function(){
  list(
    theme(plot.margin=unit(c(1,2,1,1), "cm")),
    theme(
      panel.grid.minor=element_line(color="#DCDCDC"),
      panel.grid.major=element_line(color="#DCDCDC"),
      panel.border=element_blank(),
      panel.background=element_blank(),
      axis.ticks=element_line(),
      axis.line.x=element_line(size=0.2, linetype="solid", colour="black"),
      axis.line.y=element_line(size=0.2, linetype="solid", colour="black"),
      axis.text.x=element_text(size=15), 
      axis.text.y=element_text(size=15),
      axis.title.x=element_text(size=20),
      axis.title.y=element_text(size=20),
      legend.title=element_text(size=20),
      legend.text=element_text(size=20)
    ),
    theme(text=element_text(family="Object Sans", face="bold", size=12))
  )
}
```

## Save plot

```R
ggsave(plot, bg="white", width = 30, height = 20, units = "cm", dpi = 300)
```

## Basic Plotnine (Python)

```python
from plotnine import ggplot, geom_point, geom_line, labs, ggsave

plot = (
    ggplot(data, aes(x="x", y="y", color="color"))
    + geom_line()
    + labs(x="x_label")
)

ggsave(plot, "plot.png")
```

## Plot distribution differences between two value

```python
import numpy as np
import pandas as pd
from plotnine import ggplot, aes, labs, aes, geom_histogram, theme_minimal

data = pd.DataFrame({"column_a":np.random.randint(0, 100, 5000), "column_b":np.random.randint(0, 100, 5000)})

melted_data = (
    data
    .melt(id_vars=[], value_vars=["column_a", "column_b"])
)

(
    ggplot(melted_data, aes(x="value", fill="variable"))
        + geom_histogram(binwidth=10, position="dodge", color="white")
        + labs(x="Value", y="Count")
        + theme_minimal()
)
```