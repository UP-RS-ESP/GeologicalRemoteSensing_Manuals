# Install Pandoc (ubuntu)
```
sudo apt install pandoc texlive-latex-recommended texlive-xetex texlive-luatex pandoc-citeproc etoolbox wkhtmltopdf
```

# With eisvogel
```
pandoc --number-sections --listings -H auto_linebreak_listings.tex --variable papersize=a4paper --variable urlcolor=cyan --variable papersize=a4paper -s Geological_Remote_Sensing_Additional_Software.md -o Geological_Remote_Sensing_Additional_Software.pdf --template eisvogel --toc -V toc-title:"Additional Remote Sensing, GIS, and Spatial-Analysis Software"
```

```
pandoc --number-sections --listings -H auto_linebreak_listings.tex --variable papersize=a4paper --variable urlcolor=cyan --variable papersize=a4paper -s Geological_Remote_Sensing_Python_Setup.md -o Geological_Remote_Sensing_Python_Setup.pdf --template eisvogel --toc -V toc-title:"Python Setup - Installation and Environment"
```

```
pandoc --number-sections --listings -H auto_linebreak_listings.tex --variable papersize=a4paper --variable urlcolor=cyan --variable papersize=a4paper -s Geological_Remote_Sensing_SSH_Setup.md -o Geological_Remote_Sensing_SSH_Setup.pdf --template eisvogel
```