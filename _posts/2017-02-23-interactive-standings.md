---
layout: post
title: "Interactive Standings"
date: 2017-02-23T06:00:00Z
categories: main
---
It started with me looking at Premier League table and asking questions:

* Did Leicester took the lead from the begining or was it a heroic finish that brought the victory?

* How did the winter transfers affect the results?

* I remember Southampton being deeeeeep down the table but they somehow have qualified for the Europa League. 
How did they manage to climb up?

![Premier League Table]({{ site.url }}/assets/images/posts/interactive-standings/premier-league-table.png)

Static table hadn’t got any answers for me. So I began researching the alternatives.

### Form/Streak

<div class="fotorama">
    <img src="{{ site.url }}/assets/images/posts/interactive-standings/premier-league-form.png">
    <img src="{{ site.url }}/assets/images/posts/interactive-standings/nba-streak.png">
</div>

Form columns have recently become popular and appeared on both
[Premier League](https://www.premierleague.com/tables) and [NBA](http://www.nba.com/standings) websites.

They’re useful when a season is on and you’re watching closely but are of no avail after a season’s finished.


### Historical Standings

![Premier League Table]({{ site.url }}/assets/images/posts/interactive-standings/nba-historical-standings.png)

Okay, so the data is [out there](http://www.basketball-reference.com/friv/standings.cgi?month=2&day=2&year=1990&lg_id=NBA) in the world! However, good luck trying to find trends by clicking links and scrupulously comparing tables.


### Color-coded Table

<div class="fotorama">
    <img src="{{ site.url }}/assets/images/posts/interactive-standings/f1-wiki.png">
    <img src="{{ site.url }}/assets/images/posts/interactive-standings/mls.png">
</div>

These tables are [widely used](https://en.wikipedia.org/wiki/2015_Formula_One_season#Results_and_standings) in Formula One world. They allow to learn information at your pace and drill down to a particular race. But the information density is overwhelming even for 20 races — imagine how this table would look like for a season with 38 stages. Also, there is no way to tell who was at the top after the Belgium GP, Hamilton or Rosberg.


### Custom-built System

![League Replay]({{ site.url }}/assets/images/posts/interactive-standings/league-replay.png)

This is a [true season replay](http://cmoe.dk/leaguereplay/) with video highlights for EVERY game. Pour a pint and relax in your seat.

However, this might too much if you don't have 45 minutes and a Guinness in the fridge. 

There's also a problem from a developer's perspective: systems like this are not reusable. 
Creating a replay for any other season requires days or even weeks of work.


### Visualization

![Tableau Visualization]({{ site.url }}/assets/images/posts/interactive-standings/tableau-premier-league-viz.png)

A simple line chart turns out to be too cluttered even for ten teams so one should look for more creative options. 
Check out the [ways to reimagine sports standings](https://public.tableau.com/s/blog/2016/08/viz-roundup-reimagining-sports-standings) by Tableau users.

There a few dozens of visualizations out there but none of them is both intuitive and detailed enough to replace a simple standings table.


### Animated Standings

Well, I thought, if plain old standings are that good, 
why not work on enhancing them instead of inventing some super graphics that only a bunch of dataviz nerds would understand?

What a great idea! Sure, that's why some guy [coded it in 2011](http://blog.scottlogic.com/2011/01/04/animating-html-ranking-tables-with-javascript.html):

![Tableau Visualization]({{ site.url }}/assets/images/posts/interactive-standings/animated-standings.gif)

(Un)fortunately, the script is far from ideal and hasn’t been updated for years.


### Replay Table

So I wrote a ~~javascript framework~~ script that transforms season results into interactive standings. Check it out, click replay:
<div class="replayTable"
    data-csv="{{site.url}}/assets/data/football/2015-2016/english-premier-league.csv"
    data-input-type="listOfMatches"
    data-item-name="Team"
    data-use-rounds-numbers="true"
    data-table-name="english-premier-league">
</div>

Play around, drill down to round and team levels.

Oh yeah. All the data right inside a plain old standings table. But what about reusability? No problemo, just replace the input file for [any other football league](https://replaytable.com/examples/football/2015-2016/). Not into football? Okay, here are Replay Tables for [Formula One](https://replaytable.com/examples/formula-one/2016/) and [NBA](https://replaytable.com/examples/basketball/2015-2016/).

### Quick start

1.&nbsp;Begin with a [csv file]({{site.url}}/assets/data/football/2015-2016/english-premier-league.csv) that looks like this:

<table class="">
    <colgroup><col/> <col/> <col/> <col/> <col/></colgroup>
    <tbody> 
        <tr> 
            <td>Date</td>
            <td>Home Team</td>
            <td>Score</td>
            <td>Away Team</td>
            <td>Score</td>
        </tr>
        <tr> 
            <td>08.08.2015</td>
            <td>Bournemouth</td>
            <td>0</td>
            <td>Aston Villa</td>
            <td>1</td>
        </tr>
        <tr> 
            <td>08.08.2015</td>
            <td>Chelsea</td>
            <td>2</td>
            <td>Swansea</td>
            <td>2</td>
        </tr>
        <tr> 
            <td>08.08.2015</td>
            <td>Everton</td>
            <td>2</td>
            <td>Watford</td>
            <td>2</td>
        </tr>
        <tr> 
            <td>...</td>
            <td>...</td>
            <td>...</td>
            <td>...</td>
            <td>...</td>
        </tr>
    </tbody>
 </table>
 
You can find one on [Football Data](http://www.football-data.co.uk/data.php) or in [our gallery](https://replaytable.com/#examples).
     
2.&nbsp;Include Replay Table script and stylesheet:
    {% highlight html %}
    <head>
        ...
        <link rel="stylesheet" type="text/css" href="//cdn.jsdelivr.net/replay-table/latest/replay-table.css">
    </head>
    <body>
        ...
        <script type="text/javascript" src="//cdn.jsdelivr.net/replay-table/latest/replay-table.min.js"></script>
    </body>
    {% endhighlight %}

3.&nbsp;Place a <span class="code-word">div</span> with <span class="code-word">replayTable</span>  class on your page and supply a link to the csv file using data-csv attribute:
    {% highlight html %}
    <div class="replayTable"
        data-csv="/path/to/file.csv">
    </div>
    {% endhighlight %}   
4.&nbsp;Enjoy!

Customizing via <span class="code-word">data-</span> attributes is easy peasy, check out [our docs](https://github.com/TargetProcess/replayTable#customization) for the details.

### License

Replay Table is [open-source](https://github.com/TargetProcess/replayTable) with MIT license. It is free for any website.<br>
The project is developed by me (Anton Iokov) and Daria Krupenkina using the [orange time](http://www.openwork.org/targetprocess/) at [Targetprocess](https://www.targetprocess.com/).<br>
Feel free to write to [@antoniokov](https://twitter.com/antoniokov) or [anton.iokov@targetprocess.com](mailto:anton.iokov@targetprocess.com) 
in case you need help integrating Replay Table into your website.


<script type="text/javascript" src="https://cdn.jsdelivr.net/replay-table/latest/replay-table.min.js"></script>