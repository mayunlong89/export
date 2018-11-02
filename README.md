export version 0.2.2 Beta
=========================
export is an R package to easily export active R graphs and statistical output 
in publication quality to Microsoft Office (Word, PowerPoint and Excel), HTML and Latex.

Useful links: 

* Report a bug: 
[**Bug report**]
(http://github.com/tomwenseleers/export/issues "please provide a reproducible example"). 
If you report a bug, try to send a reproducible example and don't forget to send the result of 
    
        sessionInfo()
        
Features
--------
* Save active R graphs or ggplot2, lattice or base R plots in publication 
  quality to Microsoft Word, Powerpoint, or various other bitmap or 
  vector formats using a single command with sensible defaults.
* Fully editable Powerpoint vector format output, enabling manual tidy-up of plot layout.
* Save the output of statistical analysis in R as tables in Excel, Word, PowerPoint, Latex or HTML documents.
* Customize formatting of R outputs.

Installation
------------

### Dependencies

export needs some R packages ; run the following script to install them if needed.

    install.packages("officer")
    install.packages("rvg")
    install.packages("openxlsx")
    install.packages("ggplot2")
    install.packages("flextable")
    install.packages("xtable")
    install.packages("rgl")
    install.packages("stargazer")
    install.packages("tikzDevice")
    install.packages("xml2")
    install.packages("broom")
    

### Github

**Get the latest official release from CRAN:**  

    install.packages("export")
    library(export)


### Github

**Get the latest development version:**  

    install.packages("devtools")
    library(devtools)
    devtools::install_github("tomwenseleers/export")

  
Getting Started
---------------

    library(export)
       
    ?graph2ppt
    ?graph2doc
    ?graph2svg
    ?graph2png
    ?table2ppt
    ?table2tex
    ?table2excel
    ?table2doc
    ?table2html

    ## export of ggplot2 plot
    library(ggplot2)
    qplot(Sepal.Length, Petal.Length, data = iris, color = Species, 
          size = Petal.Width, alpha = I(0.7))
    # export to Powerpoint      
    graph2ppt()      
    graph2ppt(file="ggplot2_plot.pptx", aspectr=1.7)
    # add 2nd slide with same graph 9 inches wide and A4 aspect ratio
    graph2ppt(file="ggplot2_plot.pptx", width=9, aspectr=sqrt(2), append=TRUE) 
    # add 3d slide with same graph with fixed width & height
    graph2ppt(file="ggplot2_plot.pptx", width=6, height=5, append=TRUE) 
    # export to Word
    graph2doc()
    # export to bitmap or vector formats
    graph2svg()
    graph2png()
    graph2tif()
    graph2jpg()

    ## export of aov Anova output
    fit=aov(yield ~ block + N * P + K, npk)
    x=summary(fit)
    # export to Powerpoint
    table2ppt(x=x)
    table2ppt(x=x,file="table_aov.pptx")
    table2ppt(x=x,file="table_aov.pptx",digits=4,append=TRUE)
    table2ppt(x=x,file="table_aov.pptx",digits=4,digitspvals=1,
              font="Times New Roman",pointsize=16,append=TRUE)
    # export to Word
    table2doc(x=x)
    # export to Excel
    table2excel(x=x, file = "table_aov.xlsx",digits=4,digitspvals=1,
                sheetName = "Anova_table", add.rownames = TRUE)
    # export to Latex
    table2tex(x=x)
    # export to HTML
    table2html(x=x)

  
License
-------
The export package is licensed under the GPLv2.
