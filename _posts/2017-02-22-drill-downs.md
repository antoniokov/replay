---
layout: post
title: "Version 0.2. Drill Downs"
date: 2017-02-22T19:00:00Z
categories: release-notes
---

### Drill Downs

Previously it was only possible to see whether a team won or not:

![Premier League changes]({{ site.url }}/assets/images/posts/drill-downs/changes.png)

Now you can drill down to matches and teams:

<div class="fotorama">
    <img src="{{ site.url }}/assets/images/posts/drill-downs/drilldown.png">
    <img src="{{ site.url }}/assets/images/posts/drill-downs/team-drilldown.png">
</div>

### New Website

Initially the script itself and the website with examples 
had lived in the same repo and had used the same infrastructure.
This was embarrassing in many ways: 
unnecessary classes in CSS, testing nightmare and messy code...

So we separated the script and the website into 
[two](https://github.com/TargetProcess/replayTable) 
[different](https://github.com/TargetProcess/replayTable.com) 
repositories with independent deployment.

Check our new website out at [replaytable.com](https://replaytable.com/), 
you'll find new examples together with their code.

**Breaking change**. The only downside is that old embeds don't work any more. 
You should replace them with the new code provided next to each table. 
Note that the table height is no more constant due to the team level drill down.   

### Terms

We used to have a bunch of parameters like seasonName and roundName to specify terms. 
But with drill downs came even more labels and it became apparent that there's too much data- params to specify.
     
So we combined them into one parameter — [terms](https://github.com/TargetProcess/replayTable#terms). 
Specify the terms you need using an object like this: *{ 'round': 'Race', 'item': 'Driver' }*.

**Soon-to-be-breaking change**. The deprecated labelName parameters work for now but we'll get rid of them completely soon.


### Minor improvements

* **Breaking change**. The new default input type is *listOfMatches*.

* New [calculated columns](https://github.com/TargetProcess/replayTable#calculatedcolumns): 
goalsFor, goalsAgainst, goalsDifference.

* [*locationFirst*](https://github.com/TargetProcess/replayTable#locationfirst) parameter 
for determining the order of home and away teams.


* Layout and animation improvements.

* Ignoring the last empty string in CSV files.

* Major refactoring. The code has become much easier to understand, so contributions are welcome.  