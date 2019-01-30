# udTableauProject
final project for Tableau visualization

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

#### Design iteration 1
As I started to browse through some examples of diagrams and how they might relate to this data, I liked the superhero chart in the Udacity examples, as it is a scatterplot comparing two dimensions, with the power indicated by size, and alignment indicated by color.  This might fit well with the player's height vs. weight in a scatterplot, with color indicating handedness, and size indicating either batting average, or home runs (or, from above, a power score combining those two measures)
