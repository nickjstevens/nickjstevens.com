---
title: 'ANSYS Percentage Stress Error'
subtitle: ''
summary: Check mesh quality using a measure of percentage stress error.
authors:
- admin
tags:
- ANSYS
categories:
- Engineering
date: "2019-06-24T00:00:00Z"
lastmod: "2019-06-24T00:00:00Z"
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

ANSYS Workbench allows you to plot the absolute stress error energy (SERR), which is a measure of the discretisation error within the model. Error occurs for displacement-based problems because displacement compatibility is enforced resulting in a **continuous** displacement field from element to element, but a **discontinuous** stress field. To obtain more acceptable stresses, averaging of the element nodal stresses is done. The error due to this averaging can be quantified, which is how the stress error energy is calculated.

## The problem with stress error energy

Stress error energy can be plotted in ANSYS directly, and can be accessed as a User Defined Result as SERR. However, it is a measure of the absolute stress error, so a high stress error may be acceptable if it is also in a region where the strain energy is high in the model anyway. What we really want to know is the **percentage** stress error.

## Plotting the percentage stress error in ANSYS

The ANSYS percentage stress error can be considered as the stress error energy divided by the total strain energy. The strain energy can be accessed as a User Defined Result as ENERGYPOTENTIAL. So to plot the percentage stress error create a User Defined Result with the following formula:

    (SERR/ENERGYPOTENTIAL)*100

The *100 gets the result expressed as a percentage (%). The User Defined Result is also shown in the screenshot below:

{{< figure src="featured.png" title="ANSYS Percentage Stress Error Formula" >}}

You can now plot this User Defined Result which will give you a plot of the percentage stress error in ANSYS. This will help highlight areas where further mesh refinement is required. Typically you might want to aim for a percentage stress error below 5% or 10% in your region of interest. The screenshot below shows a plot of the percentage stress error. The mesh is coarse on purpose to demonstrate the method, and as expected, with high stress errors further mesh refinement is needed.

{{< figure src="Untitled-2f5757a1-3856-4525-b8bb-8acdcb1f3fd6.png" title="ANSYS Percentage Stress Error Plot" >}}

So in closing, having confidence in the level of mesh refinement in your model is important, and plotting percentage stress error is one way to do it. It complements other methods to review the model such as mesh quality checks, plotting stresses as “nodal fraction” or “elemental fraction”, and checking convergence with increased mesh density.