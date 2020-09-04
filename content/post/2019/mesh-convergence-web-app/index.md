---
title: 'Mesh Convergence Web App'
subtitle: ''
summary: A free and easy web app for mesh convergence studies
authors:
- admin
tags:
- simulation
categories:
- Engineering
date: "2019-06-19T00:00:00Z"
lastmod: "2019-06-19T00:00:00Z"
featured: true
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal point options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
image:
  caption: 'Mesh convergence web app'
  focal_point: ""
  preview_only: true

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []

---

Mesh convergence is one of the cornerstones of engineering verification, and to provide users with the best tools I’m happy to launch my [Mesh Convergence Web App](https://5saa6uexu443lbp7.anvilapp.net/). It’s free, easy and addresses a hugely important aspect of simulation governance. 

I've [previously written about the importance mesh convergence](https://nickjstevens.com/post/2019/richardson-extrapolation-and-grid-convergence/), and the first iteration provided an Excel spreadsheet to implement the Grid Convergence Index. The [web app](https://5saa6uexu443lbp7.anvilapp.net/) is one step closer to the user, running the code in the browser on almost any device. Simply enter the results (stresses, displacements, anything) from three different meshes, in order of coarsest to finest, and Calculate the predicted exact answer. There are some checks in place to warn the user if the results are problematic.

Here is a screenshot of the web app in action, providing an estimated exact answer, along with 95% Confidence Interval values.

{{< figure src="featured.png" title="Mesh Convergence Web App" >}}

I hope you find this useful and easy-to-use.

## Behind the Scenes

For those interested, the web app is built using [Anvil](https://anvil.works/), which means the entire software stack can be controlled with python, as well as providing an interactive editor. It really has been a pleasurable experience, and I’d recommend anyone taking first steps into the world of software to take a look. As I start out I am using the free tier (hence the human unfriendly URL for the web app!) but as I test out the waters with other ideas I’ll be looking to upgrade and make a more permanent home for the mesh convergence web app.

### Feedback

I think the web app should be useful to practising engineers, and I’d love to hear any feedback, comments or suggestions. Perhaps you have a useful feature that I could add, or perhaps an idea for a different web app in the engineering domain. Either way, I’d love to hear from you.