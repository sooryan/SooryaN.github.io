---
title: Haskell Summer of Code Testimonial
date: 2016-09-14 19:10:39
tags:
---
This blog post marks the end of a pretty awesome summer!

The Haskell Summer of Code was a great learning experience and a wonderful opportunity to be a part of an open source organization and gain insight into its workings (It’s a lot more work than I thought it would be and kudos to you guys for keeping things running as smoothly as they have been running!)

A shout out to various people at \#haskell for offering their guidance and helping me with my various doubts and my mentors for their guidance and for handing me a free rein.

You guys make haskell a lot more accessible to everyone :-)

[](#A-quick-overview "A quick overview")A quick overview
--------------------------------------------------------

I got the opportunity to contribute to [Hackage](http://hackage.haskell.org/), the Haskell community’s central
package archive of open source software.

It was the first time I got to work on an existing codebase of this scale (along with it being my first large Haskell project).

While I didn’t get to do everything I’d laid out in my [proposal](/2016/05/20/Hackage-Improvements/) (which in hindsight
seems a tad grandiose), I feel I’ve got the more important parts done.

The consolidated PR is [here](https://github.com/haskell/hackage-server/pull/514) and is
pending a review as I type this.

[](#Summary "Summary")Summary
-----------------------------

What’s been done:

1.  **Tags**

    Previously, the tags didn’t get much love. They reflected the category in the `.cabal` file and whether or not it was a library/
    executable.

    Now, any user can propose additional tags to packages from the package page after which the package maintainers/trustees can accept
    or discard them using a clickable UI. The proposed tags can be seen at `/package/:pkgname/tags`

    This also brought about the need for tag aliasing wherein a trustee can merge tags together.

2.  **Browsable Package Index View**

    There is now a new route at `/packages/browse` with browsable of all the packages uploaded to Hackage.

    ![Screenshot of main search interface](/assets/hsoc/search_index.png)

    A similar interface is present for filtering in the tag and category pages.

    If tagging picks up, it’ll become a lot easier to search for packages.

3.  **Reverse Dependencies**

    Reverse dependencies used to be a Hackage feature until it was discontinued for being a memory hog.

    It’s been rewritten as a `PackageId -> PackageId` mapping and looks to be performing reasonably as far as memory consumption is
    concerned.

    The main package page lists out the number of direct and indirect dependencies with more details available at `/package/:package/reverse` while the overall picture is available at `/packages/reverse`.

    In addition, after wasting far too much time trying to get d3.js to scale to about 10000 nodes, a WebGL visualisation of packages and
    their dependencies is available at `/packages/graph`.

    ![A visualization of the package database](/assets/hsoc/package_graph.png)

4.  **Voting**

    The voting was a low hanging fruit that needed to be addressed. Some tweaks were made to the voting algorithm along with a shiny new UI
    to accompany it (You can rate a package out of 3 lambdas!).

    ![A screenshot of the new voting interface](/assets/hsoc/hackage_rating.png)

5.  **Some Minor Tweaks**

    In addition, there were a few minor changes that were made along the way.

    A lot of the HTML code was restructured into separate templates as opposed to a single large file. The `Html.hs` file is still terribly large and could do with further breakup.
    Some changes were also made to the package page such as displaying executables and suggesting related packages among other things.

[](#Future-work "Future work")Future work
-----------------------------------------

There’s still quite a bit that can be done with regards to the areas worked on and I’d love to continue to work on the features and see them to completion.

-   The graph of packages and their dependencies is still rather basic.
    More interactivity and additional views can add to its utility.

-   Reinstating the reverse dependencies feature allows for some fairly complex questions to be answered like finding similar packages using
    dependencies, analysing build reports to make diagnoses, suggesting tags.  
    It can also be used to calculate page-rank or analyse where dependencies are being dropped over time leading to a better popularity metric.