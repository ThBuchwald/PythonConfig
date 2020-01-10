# Create Excel files from Python

The (`xlsxwriter`)[https://xlsxwriter.readthedocs.io/index.html] module gives you the ability to write into the MS Excel `.xlsx` format. There is a great documentation on how to integrate this behaviour with `pandas`. The notebook shows an excerpt from the documentation; view the HTML [here](http://htmlpreview.github.io/?https://github.com/ThBuchwald/PythonConfig/blob/master/Excel_Integration/ExcelIntegration.html) and the notebook [here](https://nbviewer.jupyter.org/github/ThBuchwald/PythonConfig/blob/master/Excel_Integration/ExcelIntegration.ipynb).

A good alternative is (`openpyxl`)[https://openpyxl.readthedocs.io/en/stable/]. There is also (good documentation)[https://realpython.com/openpyxl-excel-spreadsheets-python/] for this module. This package reads from *and* writes to Excel.

`pandas` itself is also able to read and write to Excel, albeit with limited functionality.

(This article)[https://www.pyxll.com/blog/tools-for-working-with-excel-and-python/] from 2018 starts with the tool (`pyxll`)[https://www.pyxll.com/], which is an Excel add-in, i.e. a replacement for VBA, with Excel as front-end.