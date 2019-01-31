# Final Project for Tableau Visualization
Christopher B. Johnson
1/29/19

All visualizations can be found on Tableau Public [here](https://public.tableau.com/profile/chris1547#!/)

## Visualizing the baseball dataset
The data available affects how it should be displayed, so I'll summarize the default data types below:

Dimensions:
- Handedness (left or right)
- Player name

Measures:
- Batting average
- Player height
- number of home runs
- Player weight

### Feedback
I talked with a couple people about a few of my first iterations, and I've interspersed the feedback in between the iterations, as appropriate.  Generally, I tried to not explain the charts before they had a chance to look them over, but I did give them a general overview as to what the project was, what data was available for it, and that the questions/comments could be anything, but for starters : 'I don't get it' to 'I wish there were', or 'What about...' style responses are helpful (versus 'That's nice', which is typically much less useful). I will provide the comments in bulletized format below, according to the notes I took during the discussion.

### Design
While this is a simple, tidy dataset, we still need to define what it is that we're trying to show so we can create the story of how to get there.

#### Initial Design
Initially, I'm thinking that a useful story could be to show what the common physical characteristics are (height, weight, handedness) of the top 10% and bottom 10% of all players.  The player ranking would be determined by the batting average, and number of home runs of each player. It's likely that there is no simple correlation between the two, so I think for the initial design, I need to show a progression as to why the final charts were chosen.

To get a better feel for the data, let's start with some charts that show how the data is distributed.
- scatterplot of height vs. weight will show generally how the players are distributed (are they generally light and short? heavy and tall?)
  - perhaps create a ratio of height/weight?
- histogram of player batting averages : is it normal? are there outliers?
- histogram of home runs

One thing I noticed when scrolling briefly through the data is that home runs and batting average don't scale together, so it starts to raise the question of 'best'. Do we value home runs over batting average? It seems that consistent performance may be better than an all or nothing player. With that in mind, I think I should normalize the batting average and home runs, and then add them to create an 'overall performance' measure (at this time, I'll assume equal weights).

Next I'd like to include handedness in the investigation, so I'd like to create a split bar chart/histogram, where for each bucket of overall performance, the count is split up into left and right handers, so see if handedness seems to play a part in overall performance. It might be worthwhile to consider handedness specifically against batting average and home runs separately as well.

I sketched out a basic design by hand, which is part of the Git repository as tableauInitialDesignSketch.jpeg.  Then, I put a basic version of that into Tableau, labeled iteration 1.

#### Initial Design (udFinalProjectBaseball_iter1)
Most of this design came from the sketch I did.  However, as I started to browse through some examples of diagrams and how they might relate to this data, I liked the superhero chart in the Udacity examples, as it is a scatterplot comparing two dimensions, with the power indicated by size, and alignment indicated by color.  This might fit well with the player's height vs. weight in a scatterplot, with color indicating handedness, and size indicating either batting average, or home runs (or, from above, a power score combining those two measures). That was why I chose to make the summary visualization the way I did.

#### Feedback on the Initial Design (udFinalProjectBaseball_iter1)
Jason
- first storyboard :
  - you could see the distribution of the players, and there seemed to be a correlation between height and weight, which was to be expected
  - could you adjust the bin size? It seemed rather large
  - The large number of < 25 home run hitters prevented seeing any detail in the rest of the histogram
- second storyboard :
  - what about coloring handedness and keeping them on the same plot
  **-** plot labels were confusing/not helpful...what % of top players? (5, 10%)
  - there seemed to be no correlation with height/weight and performance
  - regarding the top%_hw_hand chart : maybe add a mean for each group to better summarize the data? perhaps with standard deviation describing how spread out the points were?
    - more specifically, as the discussion went on, maybe use a box plot?
- third storyboard :
  - no trend indicated
  - Avg. Avg was above the color legend
  - Tony is a little guy
  - Nothing really stands out. It's so busy, I don't really see much.

Ryan
- first storyboard :
  - there's definitely a correlation between the height and weight, as expected
  - tough to read histogram due to large discrepancy in scale. He expected to see a bimodal distribution in the home runs, due to average hitters and big hitters (or something like that, I don't follow baseball)
    - when I offered to remove the 0.000 average hitters for more resolution on that histogram, he definitely wanted to keep it there, as it was actually an interesting, unexpected result.
    - However, regarding the hist_avg chart, he mentioned that I needed to fix the x-axis to 0.000 versus the 0.00 since he didn't read it as batting averages with fewer decimal places.

- second storyboard :
  - not very readable
    - unsure what he was looking at...needed to be prompted about the top%, and like Jason, had the question as to what top %, and I wasn't sure either
  - noticed that the scale was changing (I had it set to auto)
  **-** pointed out that it's difficult to identify any trends/patterns because the changing scale keeps everything evenly distributed
  - did not easily read the handedness chart
    **-** however, noted that what's interesting there is that of the top players, the left and right handed top players look about even, but there are a LOT more right handed players in the league. There's probably something there.
    **-** put handedness in perspective of total players and it might show something interesting

- third storyboard
  - a lot of data layered together
    - are these top performers?
    - difficult to digest

#### My takeaway from the comments
Originally I was thinking that I needed a story leading to some conclusion with the data, but the general comments about the first two story slides were mostly of the sort : 'what are you trying to show?'.
  - I think I will provide a simpler storyboard with more data consolidated. Less is more.

The final storyboard was too busy. I think there was interesting information there, but I did not integrate it correctly. More work needed here.

Most significantly, the autoscaling of the axes was actually creating problems for me in creating a chart that showed a trend or pattern. I will fix this.

From a feature perspective, I liked where Ryan picked up on the left handed players possibly being more likely to be top performers since they are relatively a smaller part of the population. I will look into displaying that.

#### Second Design Iteration (udFinalProjectBaseball_iter2)
I had similar thoughts as the reviewers on the first design, although I did not pick up on everthing that they had mentioned.

My priorities in this iteration were :
- less is more. Fewer, but better views
- consolidate the home run and batting average problem which I felt was driving me to make more charts. Here I chose to create a metric of 'overallPerformance' which was a weighted average of batting average and home runs.
- The graphs were not good at displaying a lot of detailed information, but I felt that a table of information would better express the top ranking players.
- Add some filters that could be used to dynamically change the data.
- Experiment with other views.  I thought a pie chart might provide an interesting split of handedness for a given height or weight, and apparently Tableau will create a scatterplot of pie charts. Neat! In hindsight, not a good idea though.
- Provide a chart where you could quickly assess the best players and where they were on the height/weight spectrum, as well as handedness.

#### Feedback on Iteration 2
This feedback here was taken all at once due to time constraints on this project, so I was not yet able to incorporate the comments from the previous review.

Jason
- What is overallPerformance? How is it calculated?
- What do the sliders stand for?
- on the heightWeightHRAndHandedness chart, he missed the different sizes and their significance of showing home runs.
**-** noticed that the charts were auto-ranging (when compared to last iteration), which was obscuring ability to group players

Ryan
- overallPerformance not defined
- questions about how the filters worked
- we discussed the pie chart scatterplot
  - I mentioned that earlier in the day, I had realized that the pie chart sizes were simply total home runs for that point. It did not express the number of players over which those home runs were realized. This made the data not just worthless, but possibly misleading.
  **-** He mentioned that perhaps a measure of HRs/person as an efficiency metric for a given height/weight may be more useful
**-** one problem with selecting only all-stars is that everyone starts to look the same. Perhaps I needed to show some more contrasting data (including maintaining the chart scale) in order to discover patterns.
- hw_players chart gets very cluttered with the filters set to show most players
- where's Ted Williams? providing a filter on names would have allowed me to answer that question

#### My takeaway from the comments
- get rid of chart autoranging
- fix the chart titles
- make the charts less busy
- display percent of left handed players that are top performers of all left handed players in league (and also for other handedness)
- try a graph of HRs/person as a function of height/weight
- either find a way to better describe overallPerformance calculation, or remove it
- perhaps add a chart of top performers highlighted against others (dimmed) to look for trends

#### Other findings
- noticed that there were 2 Billy Mitchells in dataset, and when Tableau (under analysis tab) aggregated measures, it was messing up the data

### Final Design
Taking many of the comments into account, and from lessons learned in previous design iterations, I've created a storyboard that shows the player characteristics based on their overall performance.

What's interesting is that, given that roughly only 25% of the league players are left handed, of the left handed players, there are a greater percent of them that are top players than the other groups. Also, you can see a trend as you change the performance filter that most top players are between 71 and 74" in height, and weigh between 175 and 200 pounds.
