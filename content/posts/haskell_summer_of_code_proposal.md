+++
title = "Hackage Improvements: HSoC proposal"
date = "2016-05-20T23:19:12+08:00"
author = "Soorya Narayan"
authorTwitter = "" #do not include @
cover = ""
tags = ["haskell", "open_source", "hsoc"]
keywords = ["", ""]
description = "I participated in the 2016 Haskell Summer of code working on Hackage, the haskell community's repository of software. Here is the accepted proposal."
showFullContent = false
+++

I participated in the 2016 Haskell Summer of code working on Hackage, the haskell community's repository of software. Here is the accepted proposal.

## [](#What-is-the-goal-of-your-project "What is the goal of your project?")What is the goal of your project?

Hackage 2.0 offers a lot of features but some of them aren’t fleshed out fully or could use some additions Issuimprove usability and functionality. This project aims at addressing a few of them.

- Issue Tracker:

  - for filing bugs in Hackage web interface and other hackage related issues with a hook to notify the developers
  - To handle package requests: There are two types of requests that can be filed
    - Bounds Request: Request to change package metadata – i.e. upper/lower bounds on deps. This can be done with a “revision” by a maintainer or a hackage trustee without a new upload.
    - Orphan Request: Request a package to be disowned, e.g. when the maintainer is inactive and the package has been flagged out-of-date for a long time.

- Modifications to the Package Page:

  - Allow for provisions to add wiki/mailing list links for relevant discussions: Very often, at least with older packages, there seems to be very few usage guidelines and examples. Linking to discussions elsewhere can get a new user upto speed
  - Keep track of reverse dependencies (Related Fun Addition: A visualization that maps dependencies and reverse dependencies across all packages (I just love graphs!))
  - A better interface for votes: It’s not very usable right now. Making the UI for voting more obvious and easy to use would help eg a clickable star based system
  - Add a last updated stamp (very few packages have it at present. It’s not easy to identify how recent/relevant the package is)

- Tags and Categories:

  - Abandon categories and switch over to tags completely. Categories and Tags seem to more or less serve the same purpose. It makes sense to have multiple tags describe a package as opposed to having it being fit into a rigid category.
  - Social tagging: (This can be an opt-in feature for maintainers) A system to allow for any user to propose new tags with only the maintainers allowed to accept. This will greatly increase package discoverability. Again, hooks would need to be added to notify the maintainers of any new suggestions.

- Better searching:

Searching at present doesn’t offer very much.

| Package Name | Author | Version | Description | Tags | Last Updated | Votes | Downloads |
| ------------ | ------ | ------- | ----------- | ---- | ------------ | ----- | --------- |
|              |        |         |             |      |              |       |           |

Using a template like above

- Extend search to filter based on tags (multiple tags), module names, author names etc
- Allow for packages to be ordered by downloads, update times, reverse dependencies etc
- Allow for autocompletion by partial name search

## [](#Can-you-give-some-more-detailed-design-of-what-precisely-you-intend-to-achieve "Can you give some more detailed design of what precisely you intend to achieve?")Can you give some more detailed design of what precisely you intend to achieve?

### [](#Issue-tracker "Issue tracker")Issue tracker

At present, to file any issues, users will have to contact the authors/maintainers (who may no longer be active). By having a public
tracker for hackage related issues, issues will have a much higher visibility and thus, a higher chance of being resolved.  
As for implementation, a new acid-state instance with a web front end should be straightforward. A sample schema can be like in
[bug.yaml](https://gist.github.com/SooryaN/10e7cdfd5ced92561c919537890d092b#file-bug-yaml).

### [](#Reverse-Dependencies "Reverse Dependencies")Reverse Dependencies

Keeping track of reverse dependencies could help usability in a number of ways. For instance, along with efficient tagging, it’ll allow for
suggesting related packages, for exploring, and also for calculating a PackageRank(tm).  
The implementation is still an open issue though. It could be implemented using an external store or something simple like a csv or a json file. Using acid-state to simply count and list the reverse dependencies without storing the actual branching details is also a possibility.

### [](#Votes "Votes")Votes

This will involve reusing the code behind [http://hackage.haskell.org/packages/votes](http://hackage.haskell.org/packages/votes)
to accomodate an out of 5 stars rating system. The average rating of a package will be appended to the search/ browse page. The user can click and vote on packages either in the search page itself or in the individual package pages.

### [](#Tags "Tags")Tags

At present, the `.cabal` file of a package has a category field. The same field can be extended to hold multiple values that can be parsed
into tags.  
This would ensure that existing packages arent affected in any way. A far as social tagging is concerned, a simple “opt in to tagging?”
message can be appended to the upload page.

### [](#Search "Search")Search

Relevant issues to fix:

- Substring search ([\#208](https://github.com/haskell/hackage-server/issues/208))
- Searching and Coalescing Tags ([\#27](https://github.com/haskell/hackage-server/issues/27)), ([\#24](https://github.com/haskell/hackage-server/issues/24))

Additions:  
This will involve redesigning the present search page and devising a method to integrate substring search into the present keyword-based
search in order to implement autocompletion and partial name search. One approach would be to build a prefix tree with the words in the
corpus as keys and their frequencies as values.

## [](#Do-you-have-a-mentor-in-mind "Do you have a mentor in mind?")Do you have a mentor in mind?

I talked to dcoutts, hvr and sclv at \#hackage and they said that they’d be ready to mentor/ assign a mentor for the summer.

## [](#What-deliverables-do-you-think-are-reasonable-targets "What deliverables do you think are reasonable targets?")What deliverables do you think are reasonable targets?

- An issue tracker
- A method to handle reverse dependencies
- Improvements to tagging
- An improved search experience

## [](#Can-you-outline-an-approximate-schedule-of-milestones "Can you outline an approximate schedule of milestones?")Can you outline an approximate schedule of milestones?

### [](#Before-June-12th "Before June 12th")Before June 12th

I’ll use this period to get acquainted my the mentor and become familiar with the hackage codebase.  
I’ll also plan out what to do in the later phases, possibly with mockups and blog posts and solicit feedback for these plans. At the end of this period, I should have a roadmap of what to do and how to do it.

### [](#June-13th-July-13th "June 13th - July 13th")June 13th - July 13th

I’ll finish up with the tagging and the issue tracker along with their integration into the package pages.

### [](#July-13th-August-5th "July 13th - August 5th")July 13th - August 5th

This period would be spent working on and the search algorithm and interface

### [](#August-5th-August-25th "August 5th - August 25th")August 5th - August 25th

I’ll be working through an efficient way to keep track of reverse dependencies.

### [](#After-August-25th "After August 25th")After August 25th

Any remaining time will be spent fine tuning the work done in the first two months, writing documentation and cleaning up the codebase

## [](#In-what-ways-will-this-project-benefit-the-wider-Haskell-community "In what ways will this project benefit the wider Haskell community?")In what ways will this project benefit the wider Haskell community?

Along with GHC and Cabal, Hackage forms the core of the Haskell ecosystem. Improvements here should help the community as a whole.

## [](#What-relevant-experience-do-you-have "What relevant experience do you have?")What relevant experience do you have?

I’ve just finised the sophomore year of my bachelors in computer science.

I’ve been using and have been a supporter of free software since high school and have been programming for about 4 years. I’ve worked mainly
in python, javascript and C++ and have built and maintained multiple websites.  
I was introduced to functional programming when I learnt scheme a little over a year ago. I fell in love with the elegance of haskell over the last half year en route to becoming convinced that it a much better paradigm for writing programs in.  
I’ve used haskell in university for my OS course that involved multithreading. I’ve implemented a subset of scheme in Haskell and also
dabbled around in building parsers for toy languages.

## [](#In-what-ways-do-you-envisage-interacting-with-the-wider-Haskell-community-during-your-project "In what ways do you envisage interacting with the wider Haskell community during your project?")In what ways do you envisage interacting with the wider Haskell community during your project?

The haskell community is in general very helpful and I regularly hang around in \#haskell and [/r/haskell](http://www.reddit.com/r/haskell)
and am part of the Haskell learning Group on slack. Whenever stackoverflow has failed me in the past, I’ve turned to them and am
confident I’d be able to find help there if my mentor is otherwise occupied.

I have a [blog](http://soorya.dev/) set up (with nothing on it yet) and if accepted, I’ll keep track of the developments there and post
updates to reddit and planet haskell.
