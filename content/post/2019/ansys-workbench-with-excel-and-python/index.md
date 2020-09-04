---
title: 'ANSYS Workbench with Excel and Python'
subtitle: ''
summary: Link ANSYS and Excel to automate the boring stuff
authors:
- admin
tags:
- ANSYS
- Excel
categories:
- Engineering
date: "2019-07-10T00:00:00Z"
lastmod: "2019-07-10T00:00:00Z"
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal point options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
image:
  caption: ''
  focal_point: ""
  preview_only: true

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []

---

If you are looking to drive ANSYS Workbench with Excel and Python, you may have come across the post by PADT here: [http://www.padtinc.com/blog/the-focus/workbench-and-excel-part-2-driving-workbench-from-excel-with-python](http://www.padtinc.com/blog/the-focus/workbench-and-excel-part-2-driving-workbench-from-excel-with-python). This was a really useful introduction, but I had some issues with getting the examples to work.

## Scripting ANSYS Workbench with Excel and Python

I didn’t have much luck getting the PADT examples to work without some modification, so if you’ve had the same issue then see below for the working files. The content consists of an ANSYS Workbench project (included in the Archived format below, so be sure to File>Restore Archive… to extract the project), an Excel sheet to run the analysis and extract the results, and a Python script to handle the interaction of Excel and ANSYS.

One of the improvements I made was to update the Excel sheet so that there should be no need to modify the VBA code – all the options can be configured via the orange input boxes, including running the analysis in Batch Mode for quicker and background solving.

The Workbench project includes the analysis and parameter variables that we want to vary. This will obviously depend on your own model and requirements. It also has the output parameters that we will read in to Excel once the analysis has completed.

The Python script is the interface between Excel and ANSYS and will need to be modified to suit your model, but it should be relatively self-explanatory. Essentially the Workbench input parameters are given values from the Excel sheet, then the analysis is solved, then the Workbench output parameters are given back to Excel.

The Excel sheet looks like this:

{{< figure src="featured.png" title="Excel worksheet to drive ANSYS and extract results" >}}

## Files for Scripting ANSYS Workbench with Excel and Python

- Excel Workbook: {{% staticref "files/TowerTool1.xlsm" "newtab" %}}TowerTool1.xlsm{{% /staticref %}}
- ANSYS Workbench Project: {{% staticref "files/ExcelTower1.wbpz.zip" "newtab" %}}ExcelTower1.wbpz.zip{{% /staticref %}}
- Python Script: {{% staticref "files/updateWB2.py" "newtab" %}}updateWB2.py{{% /staticref %}}

I hope these work for you, but if you have any issues or questions then get in touch.
