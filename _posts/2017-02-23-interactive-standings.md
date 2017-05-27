---
layout: post
title: "Visualizing a sport season"
date: 2017-05-27T06:00:00Z
categories: main
---
One day I caught myself staring at the English Premier League table trying to remember the course of the season:

* Did Leicester took the lead from the start or was it a heroic finish that accounted for the victory?

* How did the winter transfers affect the results?

* I remember Southampton being deeeeeep down the table but they somehow have qualified for the Europa League. 
How did they manage to climb up?

* How did the Manchester derbies go?

![Premier League Table]({{ site.url }}/assets/images/posts/interactive-standings/premier-league-table.png)

The table hadn’t got any answers for me. So I began researching the alternatives.

### Form/Streak

<div class="fotorama">
    <img src="{{ site.url }}/assets/images/posts/interactive-standings/premier-league-form.png">
    <img src="{{ site.url }}/assets/images/posts/interactive-standings/nba-streak.png">
</div>

Form and streak columns help to recap the nearest past and are useful when a season is on and you’re watching closely.
However, they are of no avail after a season is finished.

They have become popular and are now featured on both
[Premier League](https://www.premierleague.com/tables) and [NBA](http://www.nba.com/standings) websites.


### Color-coded Table

<div class="fotorama">
    <img src="{{ site.url }}/assets/images/posts/interactive-standings/f1-wiki.png">
    <img src="{{ site.url }}/assets/images/posts/interactive-standings/mls.png">
</div>

One way to see the course of the whole season is through a color-coded table.

Learn information at your pace and drill down to a particular round...until you get hit by the overwhelming information density.
After a minute your brain begs you to stop and navigate back to cat videos on Youtube.

Also, there is no way to tell who was at the top after, say, the Belgium GP — Hamilton or Rosberg.


### Historical Standings

<div class="fotorama">
    <img src="{{ site.url }}/assets/images/posts/interactive-standings/nba-historical-standings.png">
    <img src="{{ site.url }}/assets/images/posts/interactive-standings/russian-premier-league-historical.png">
</div>

A true geek can dare to find a trend by comparing standings for a pair of dates.
However, it turned out that even I am not geekish enough (that means something, believe me).

But there's some good news here!
The data is just [laying around](http://www.basketball-reference.com/friv/standings.cgi?month=2&day=2&year=1990&lg_id=NBA)
waiting for somebody to show it properly.


### Standings + Positions History + Results

<div class="fotorama">
    <img src="{{ site.url }}/assets/images/posts/interactive-standings/wikipedia-combination-1.png">
    <img src="{{ site.url }}/assets/images/posts/interactive-standings/wikipedia-combination-2.png">
    <img src="{{ site.url }}/assets/images/posts/interactive-standings/wikipedia-combination-3.png">
</div>

This combination is a standard for ~~soccer~~ football season pages on Wikipedia.

It has almost no limit for exploration...if you love to scroll and have an infinite short-term memory capacity.


### Custom-built System

![League Replay]({{ site.url }}/assets/images/posts/interactive-standings/league-replay.png)

There is a [true season replay](http://cmoe.dk/leaguereplay/) with video highlights for EVERY game of the English Premier League.Pour a pint and relax in your seat.

However, this might be too much if you haven't got a spare hour and a pack of Guinness in the fridge. 

There's also a problem from a developer's perspective: systems like this are not reusable. 
Creating a replay for any other season requires days or even weeks of work.


### Visualization

![Tableau Visualization]({{ site.url }}/assets/images/posts/interactive-standings/tableau-premier-league-viz.png)

A plain line chart quickly turns into a mess as the number of teams and rounds increases beyond, so one should look for some creative options. 

Check out [the ways to reimagine sports standings](https://public.tableau.com/s/blog/2016/08/viz-roundup-reimagining-sports-standings) by Tableau users.
There a few dozens of visualizations out there but none of them are **both** intuitive and detailed enough to replace a simple standings table.


### Animated Standings

Well, I thought, if plain old standings are that good, 
why not work on enhancing them instead of inventing some super graphics that only a bunch of dataviz nerds would understand?

What a great idea! As it always turns out, some ~~asian kid~~ guy [did this in 2011](http://blog.scottlogic.com/2011/01/04/animating-html-ranking-tables-with-javascript.html)
when nothing was more sexy than JQuery:

![Tableau Visualization]({{ site.url }}/assets/images/posts/interactive-standings/animated-standings.gif)

Unfortunately, the script is far from easy to use and hasn’t been updated for years.


### Standings Made Right

So we teamed up with [Daria](https://github.com/dariak) and [Vitali](https://www.behance.net/butuk) to make standings great ~~again~~ for the first time.

And today is the day! We're happy to announce Replay Table, the standings of the data era:

<div class="replayTable" id="replay-english-premier-league"
     data-source="{{ site.url }}/assets/data/football/2016-2017/english-premier-league.json"
     data-format="football-data.org"
     data-order-by="points,goalsDifference,goalsFor"
     data-visualizer="sparklines">
</div>

Play around, travel through time, drill down to a team, explore the sparklines. Oh yeah.


### Replay Table

So what exactly is Replay Table? It's an [open-source](https://github.com/TargetProcess/replay-table) 
javascript library on top of D3.js designed for visualizing sport season results.

It has a straightforward declarative interface.
A table is just a div with replayTable class and a bunch of data- attributes:
{% highlight html %}
<div class="replayTable"
     data-source="{{ site.url }}/assets/data/football/2016-2017/english-premier-league.json"
     data-format="football-data.org"
     data-order-by="points,goalsDifference,goalsFor"
     data-visualizer="sparklines">
</div>
{% endhighlight %}

Include the scripts and the stylesheet in the head section of the page, apply some magic to the body — and you're ready to go:
{% highlight html %}
    <head>
        ...
        <script type="text/javascript" src="https://d3js.org/d3.v4.min.js"></script>
        <script type="text/javascript" src="https://unpkg.com/replay-table/dist/replay-table.min.js"></script>
        <link rel="stylesheet" type="text/css" href="https://unpkg.com/replay-table/dist/replay-table.css">
    </head>
    <body>
        ...
        <script type="text/javascript">replayTable.magic()</script>
    </body>
{% endhighlight %}

If you'd like to have more control over the table I am happy to say these three words to you:
npm install replay-table.

Check out the [docs](https://github.com/TargetProcess/replay-table#library) to learn how the library works and
what parameters are available for customization.

### Reusability

But what if you hate those british snobs und wollen den echten Fußball sehen. Kein Problem: 
<div class="replayTable" id="replay-german-bundesliga"
     data-source="{{ site.url }}/assets/data/football/2016-2017/german-bundesliga.json"
     data-format="football-data.org"
     data-order-by="points,goalsDifference,goalsFor"
     data-visualizer="sparklines">
</div>

All you have to do is replace the data-source attribute value with a proper json/csv.

Not into chasing a ball? No problemo, here is an Formula One season for you:
<div class="replayTable" id="replay-formula-one"
    data-source="{{ site.url }}/assets/data/formula-one/2016/formula-one-drivers.csv"
    data-preset="f1"
    data-extra-columns-number="1"
    data-columns="position,item,Team,points,points.change"
    data-labels="#,Driver,Team,Points">
</div>

The source code looks like this:
{% highlight html %}
<div class="replayTable"
    data-source="{{ site.url }}/assets/data/formula-one/2016/formula-one-drivers.csv"
    data-preset="f1"
    data-extra-columns-number="1"
    data-columns="position,item,Team,points,points.change"
    data-labels="#,Driver,Team,Points">
</div>
{% endhighlight %}

We've also made a table for the [NBA season](https://replaytable.com#basketball) to show the flexibility of Replay Table.

### License

We released Replay Table under MIT license so you don't need a permission to use it even on a commercial website.

We'd be happy to see oldschool standings giving way to the new visualizations.
