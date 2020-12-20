## phynotate
This R package is a collection of `{shiny}` modules for interactive annotation of phylogeny plots. There are two main ways to use the modules, in an interactive `R` session or by 'embedding' in an existing `{shiny}` app.

**Interactive R session**

In many cases we either obtain a phylogeny (or other tree-like structure that can be converted to an object of class `phylo`) by running some analysis in `R`, or we load a phylogeny created by another program into `R` for further analyses or visualization. Although there is certainly no reason why we couldn't write `ape`, `phytools`, or `ggtree` code to create and save a custom plot of our tree, often, we just want to take a quick look, make some minor edits by clicking with a mouse and close the tree. This last part is a bit more difficult for a novice user of phylogeny plotting packages that is acustomed to an interface like `FigTree` or `Dendroscope`. `phynotate` attempts to fill this niche. To save a some time on making a decent figure through a GUI without writing the `phylo` object to file and leaving the `R` session.

An example workflow. We run some exciting analysis that results with 100 trees and we need to glimpse tree 54: 

```{r, eval = FALSE}
library(ape)

Trees <- replicate(n = 100, expr = rcoal(30), simplify = FALSE)
Trees[[54]]

# Phylogenetic tree with 30 tips and 29 internal nodes.
# 
# Tip labels:
#	 t9, t8, t14, t5, t23, t27, ...
#
# Rooted; includes branch lengths.
```

Opening a `{shiny}` app within our browser with tree 54 ready to customize is then as easy as:

```{r}
make_phynotate(phylogeny = Trees[[54]], draw_modules = "LPTB", annotation_module = TRUE)
```

![`phynotate` started from a local `R` session.](man/figures/trees-54.png)

<p align="center"><img src="man/figures/trees-54.png" width="1200px"></p>




**Embedding in `{shiny}`**

`phynotate` is entirely made up of `{shiny}` modules and their helpers (mostly not exported) or wrappers (like `make_phynotate()`.

**TODO:**

This is a work in progress and there are many features yet to be implemented:

2. tips missing for circular layouts
4. nodes 
5. ladderize
5. root
6. prune
6. name clade
7. color branches in clade
8. color tips in clade
9. map variable onto branch weight
10. map variable onto branch color
11. map variable onto tip symbol
12. map variable onto tip color
11. map variable onto node symbol
12. map variable onto node color
13. scale bar
14. axis