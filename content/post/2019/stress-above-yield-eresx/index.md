---
title: 'Elastic-Plastic Analysis in ANSYS Gives Stress Above Yield'
subtitle: ''
summary: Understand why ANSYS reports stresses above yield and how to fix it
authors:
- admin
tags:
- ANSYS
- simulation
categories:
- Engineering
date: "2019-07-17T00:00:00Z"
lastmod: "2019-07-17T00:00:00Z"
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

If you’ve ever turned on bilinear elastic-perfectly-plastic properties, you may have wondered why sometimes an elastic-plastic analysis in ANSYS gives stress above yield.

# Why is the stress above yield?

If you have specified a bilinear stress-strain curve then you may wonder how the stress can be above yield. It certainly makes reviewing contour plots difficult and open to challenges. The reason why the stress can be above yield in ANSYS is due to how ANSYS handles extrapolation of stresses from integration points to nodes. The default behaviour is as follows:

- If element is fully elastic (no active plasticity, creep, or swelling nonlinearities), **extrapolate the integration point results to the nodes**. If any portion of the element is plastic (or other active material nonlinearity), **copy the integration point results to the nodes**.

This means that if an element integration point exceeds yield, then this limit will be copied to the nodes – which is what we would want. The issue comes when an adjacent element has stresses at the integration points that are below yield, in which case the default behaviour is to extrapolate these stresses, which often means extrapolating stresses to above yield – not what we want!

The command which changes this default behaviour is `ERESX`. The ANSYS manual entry is as follows:

{{< figure src="Untitled-bc2dc94f-1e6e-40a8-82b2-db8946241461.png" title="ANSYS Manual Entry for ERESX" >}}

# Changing the Default Integration Point Extrapolation Settings

The `ERESX` command controls the extrapolation settings. So it’s a simple matter of using `ERESX,NO` to force ANSYS to copy the integration point stresses to the nodes. This ensures that stresses will never exceed yield as the stresses at the integration points can never exceed yield.

If you are using Workbench, then a command snippet can be used to change this behaviour – I don’t think there is a way to change the settings directly in the Workbench interface.

# Let’s See an Example

So the two figures below show the same analysis, one with default settings and the other using `ERESX,NO`. Yield in this example is set as 700 MPa. You can see that with the default settings, using an elastic-plastic material model, that stresses are significantly above yield.

{{< figure src="Untitled-4b3737e5-1e7e-4b34-a016-f18cf04787fd.png" title="Elastic-Plastic Stress in ANSYS Exceeds 700 MPa Yield with Default Settings" >}}

{{< figure src="featured.png" title="Elastic-Plastic Stress in ANSYS Limited to 700 MPa Yield with `ERESX,NO`" >}}


# Closing Remarks

It goes without saying that disabling extrapolation should be done with care and whilst ensuring sufficient mesh refinement. One way to check if the is refined enough is to review [percentage stress error](https://nickjstevens.com/post/2019/ansys-percentage-stress-error/). Check out command `ERESX` and see if it can help you better understand and interact with your model.