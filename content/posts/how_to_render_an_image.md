+++
title = "How to render an image"
date = "2021-07-30T21:48:59+08:00"
author = "Soorya Narayan"
authorTwitter = "" #do not include @
cover = ""
tags = ["graphics", "math"]
keywords = ["", ""]
description = "A brief overview of how to render an image with a computer"
showFullContent = false
draft = true
+++

rendering an image lol

```python
def rasterize():
    colors = [0] * framebuffer_dimensions
    depth  = [∞] * framebuffer_dimensions

    for triangle t in scene:
        t_proj = project(t, camera)
        if (t_proj in viewport):
            for sample s in t_proj:
                if t_proj.depth < depth[s]:
                    depth[s] = t_proj.depth
                    color[s] = calc_color(t_proj, s)


def ray_trace():
    for sample s in viewport:
        r = ray through s that originates from the camera

        r.tri = NULL
        r.t_min = inf
        for triangle t in scene:
            hit = intersects(s, r)
            if (hit and hit.t < r.min_t):
                r.tri = t
                r.min_t = hit.t
        color[s] = calculate_color(r.tri, hit point)
```
