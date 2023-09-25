# nccs-handbook

Research handbook for NCCS data. 

## Citations


Use regular end of document citation styles: 

https://quarto.org/docs/authoring/footnotes-and-citations.html#sec-citations

Follow Urban's authoring guide: 

https://urbaninstitute.github.io/editorial-styleguide/ (see "documentation" section). 

All references should appear in the bibtex file: 

https://github.com/UrbanInstitute/nccs-handbook/blob/main/references.bib



## Quarto Notes:

### Margin Figures

Figures that you create using code cells can be placed in the margin by using the `column: margin` code cell option. If the code produces more than one figure, each of the figures will be placed in the margin.

```{r}
#| label: fig-mtcars
#| fig-cap: "MPG vs horsepower, colored by transmission."
#| column: margin
#| echo: fenced

library(ggplot2)
mtcars2 <- mtcars
mtcars2$am <- factor(
  mtcars$am, labels = c('automatic', 'manual')
)
ggplot(mtcars2, aes(hp, mpg, color = am)) +
  geom_point() +
  geom_smooth(formula = y ~ x, method = "loess") +
  theme(legend.position = 'bottom')
```

### Margin Tables

You an also place tables in the margin of your document by specifying `column: margin`.

```{r}
#| column: margin
#| echo: fenced

knitr::kable(
  mtcars[1:3, 1:3]
)
```

### Other Content

You can also place content in the margin by targeting the margin column using a div with the .`column-margin` class. For example:

``` md
::: {.column-margin}
We know from *the first fundamental theorem of calculus* that for $x$ in $[a, b]$:

$$\frac{d}{dx}\left( \int_{a}^{x} f(u)\,du\right)=f(x).$$
:::
```

::: column-margin
We know from *the first fundamental theorem of calculus* that for $x$ in $[a, b]$:

$$\frac{d}{dx}\left( \int_{a}^{x} f(u)\,du\right)=f(x).$$
:::

### Margin References

Footnotes and the bibliography typically appear at the end of the document, but you can choose to have them placed in the margin by setting the following option\[\^1\] in the document front matter:

``` yaml
---
reference-location: margin
citation-location: margin
---
```

With these options set, footnotes and citations will (respectively) be automatically be placed in the margin of the document rather than the bottom of the page.

For example, according to @irs-2022f 501(c)(3) organizations indicate which exempt purpose(s) they advance when they file Form 1023 or 1023-EZ to apply for recognition of exemption from federal income tax (aka "tax-exempt status") [@irs-2014b; @irs-2020a].

### Asides

Asides allow you to place content aside from the content it is placed in. Asides look like footnotes, but do not include the footnote mark (the superscript number). [This is a span that has the class `aside` which places it in the margin without a footnote number.]{.aside}

``` markdown
[This is a span that has the class aside which places it in the margin without a footnote number.]{.aside}
```

### Margin Captions

For figures and tables, you may leave the content in the body of the document while placing the caption in the margin of the document. Using `cap-location: margin` in a code cell or document front matter to control this. For example:

```{r}
#| label: fig-cap-margin
#| fig-cap: "MPG vs horsepower, colored by transmission."
#| cap-location: margin
#| echo: fenced

library(ggplot2)
mtcars2 <- mtcars
mtcars2$am <- factor(
  mtcars$am, labels = c('automatic', 'manual')
)
ggplot(mtcars2, aes(hp, mpg, color = am)) +
  geom_point() +
  geom_smooth(formula = y ~ x, method = "loess") +
  theme(legend.position = 'bottom')
```
