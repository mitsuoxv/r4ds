# Rではじめるデータサイエンス

本レポは「Rではじめるデータサイエンス」第2版　日本語版　試作品のソースです。
本書の作成には[Quarto](https://quarto.org/)を使っています。

## Images

### Omnigraffle drawings

-   Font: 12pt Guardian Sans Condensed / Ubuntu mono

-   Export as 300 dpi png.

-   Website font is 18 px = 13.5 pt, so scale dpi to match font sizes: 270 = 300 \* 12 / 13.5.
    (I also verified this empirically by screenshotting.)

    ``` r
    #| echo: FALSE
    #| out.width: NULL
    knitr::include_graphics("diagrams/transform.png", dpi = 270)
    ```

### Screenshots

-   Make sure you're using a light theme.
    For small interface elements (eg. toolbars), zoom in twice.

-   Screenshot with Cmd + Shift + 4.

-   Don't need to set dpi:

    ``` r
    #| echo: FALSE
    #| out.width: NULL
    knitr::include_graphics("screenshots/rstudio-wg.png")
    ```

### O'Reilly

To generate book for O'Reilly, build the book then:

```{r}
# pak::pak("hadley/htmlbook")
htmlbook::convert_book()

html <- list.files("oreilly", pattern = "[.]html$", full.names = TRUE)
file.copy(html, "../r-for-data-science-2e/", overwrite = TRUE)

pngs <- list.files("oreilly", pattern = "[.]png$", full.names = TRUE, recursive = TRUE)
dest <- gsub("oreilly", "../r-for-data-science-2e/", pngs)
fs::dir_create(unique(dirname(dest)))
file.copy(pngs, dest, overwrite = TRUE)
```

Then commit and push to atlas.

## コントリビューター行動規範

本書で学習するコミュニティは、[コントリビューター行動規範](https://www.contributor-covenant.org/ja/version/2/1/code_of_conduct/code_of_conduct.txt)を用いています。
本書にコントリビュートすると、その条項に従うと同意したことになりますので、ご留意を。
