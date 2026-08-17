# My Own College Basketball Season Shooting Profile!
From the court, to the film room, to Python, this project combines basketball, film study, and data analysis. I analyzed all of my shot attempts from a college basketball season, categorizing each attempt across factors, including shot location and play context. I then used Python to analyze the data, uncover insights into my shooting profile!

# Table of Contents 
- Introduction
- Film Breakdown and Methodology
- Python Pandas Analysis
- Example Output 
- Conclusions

# Introduction
After finishing my third college basketball season, I wanted to take a deeper look at the types of shots and offensive opportunities I received throughout the season.

We use Synergy Sports Technology to watch and review film, and the platform provides a list of our shot attempts and the types of shots we receive, such as "Spot-Up" or "Cut." While this is useful, I wanted to go a step further. I wanted to understand not only what type of shot I was taking, but also how and where I was getting those shots, the offensive context surrounding them, and the quality of each look.

I believed this could be valuable from both a team and player-development perspective. From a team standpoint, understanding where and how players generate their shots can provide a more detailed picture of an offense. From a player-development standpoint, analyzing my own shot profile could help me identify weaknesses, recognize trends, and better understand where I can improve.

Every player has a specific role on the court, and I wanted to combine that idea with my growing technical skills as an aspiring data analyst and my experience reviewing basketball film. By turning film into structured data and analyzing my own shot attempts, my goal was to better understand my role as a player, identify opportunities for improvement, and ultimately find ways to maximize my impact on the court and help my team.

# Film Breakdown and Methodology

## Film Breakdown
When reviewing film, I looked at all 112 possessions of offense in which I've shot the ball. Within each shot, I manually tracked:
- Shot Number
  
- Origin:
  - Set Play: If play is within the basis of our offense.
  - Freelance: If play is not within the basis of our offense, and we as an offense are just playing basketball.
  - Transition: If play is within transition.
    
- Play type:
  - Pin Down: Within our offense, we run a lot of pin-down screens. I wanted to specifically look at my shooting percentages in the context of this play type.
  - Space: A common theme specifically in my role. When I space the floor and position myself on the floor within the parameters of our offense. 
  - Ball Screen: Common Basketball play within our offense
  - Dribble hand Off (DHO): Common Basketball play within our offense
  - Zoom: A basis of our secondary break (after transition). Common Play we run.
  - Cut
  - Isolation: Scoring by myself, with no play
 
- Shot Location:
  - Wing Three
  - Corner Three
  - Slot Area: 3 Point Area, next to top of keys, on the "lane-line"
  - Elbow Area
  - Short Corner
  - Deep Paint: Anything under the elbows, but above the restricted arc
  - Restricted Arc: Within Half Circle, by blocks (Mostly Layups)

- Shot Type:
  - Catch and Shoot
  - Off Dribble (Take a dribble before being shot)
  - Fadeaway (fading from hoop)
  - Layup
  - Shot Fake: If I shot fake before my shot (on the three point line, or in the paint, I've marked it down)

- Contest Level:
  - High (Very Contested, no space)
  - Medium (Defender is in my distance)
  - Low (Defense is very little impacting my shot)
 
- Result:
  - Make
  - Miss
  - Fouled
 
## Methodology
After tracking each shot manually within Excel based on the figures above. I've constructed a process to properly analyze each shot. The process is as followed:

- Import Pandas and Plotly Express
- Load Shot Selections into Python
- Create Two Functions Analyzing the Shot:
  1. Analyze Shot
  2. Plot those results using Plotly Express
- Create a list of Lists, identifying the specific column or cross categories I want to look at

# Python Pandas Analysis: 
Created Two Functions that 
  1. Summarizes shot data given certain columns, which calculates total number of shots given that column, made shots, and the average
  2. Builds a grouped bar chart of shot percentage, split by x_col and
    colored by color_col, using the given color palette. Reused for
    every chart in this script.
```python

def summarize_shot_data(df, group_col):
    """
    Summarizes shot data by the given grouping column(s), calculating
    total shots, made shots, and make percentage for each group.
    """
    summary = (
        df.groupby(group_col)
        .agg(
            total_shots=('result', 'count'),
            made_shots=('result', lambda x: (x == 'Make').sum()),
            shot_percentage=('result', lambda x: (x == 'Make').mean() * 100),
        )
        .reset_index()
    )
    summary['shot_percentage'] = summary['shot_percentage'].round(1)
    return summary.sort_values(by='shot_percentage', ascending=False)


def plot_shot_percentage(summary, x_col, color_col, title, palette):
    """
    Builds a grouped bar chart of shot percentage, split by x_col and
    colored by color_col, using the given color palette. Reused for
    every chart in this script.
    """
    fig = px.bar(
        summary,
        x=x_col,
        y='shot_percentage',
        color=color_col,
        color_discrete_sequence=palette,
        barmode='group',
        text='shot_percentage',
        hover_data={'total_shots': True, 'made_shots': True},
        title=title,
        template='plotly_white',
    )
    fig.update_traces(texttemplate='%{text}%', textposition='outside')
    fig.update_layout(
        yaxis_title='Shot Percentage (%)',
        yaxis_range=[0, 100],
        xaxis_title=x_col,
        legend_title=color_col,
    )
    return fig

```

From there I created a list of different categories I wanted to look at and analyze. More specifically, each list within the set list has the following categories

- Columns to group by, x-axis column, color column, chart title, palette 

```python
chart_specs = [
        (['shotType', 'contestLevel'], 'shotType', 'contestLevel',
         'Shot % by Shot Type and Contest Level', px.colors.qualitative.Set1),
        (['shotLocation', 'contestLevel'], 'shotLocation', 'contestLevel',
         'Shot % by Shot Location and Contest Level', px.colors.qualitative.Set2),
        (['Origin', 'shotType'], 'Origin', 'shotType',
         'Shot % by Origin and Shot Type', px.colors.qualitative.Pastel),
        (['Origin', 'shotLocation'], 'Origin', 'shotLocation',
         'Shot % by Origin and Shot Location', px.colors.qualitative.Bold),
        (['Origin', 'contestLevel'], 'Origin', 'contestLevel',
         'Shot % by Origin and Contest Level', px.colors.qualitative.Dark2),
        (['shotType', 'playType'], 'shotType', 'playType', 
         'Shot % by Shot Type and Play Type', px.colors.qualitative.Set3),
        (['shotLocation', 'playType'], 'shotLocation', 'playType',
          'Shot % by Shot Location and Play Type', px.colors.qualitative.Set1)
          
    ]

```

Finally, within the list I've just created, I calculated and summarized the shot data, and plotted the summaries using each formula.

```python
final = []
for group_cols, x_col, color_col, title, palette in chart_specs:
        summary = summarize_shot_data(df, group_cols)
        fig = plot_shot_percentage(summary, x_col, color_col, title, palette)
        final.append(fig)
        fig.show()
```
# Example Output
## All Outputs are within the "Visuals" folder


# Conclusions
Its important to mention 112 shot attempts are a pretty small sample size, which played prevalent in the bar sizes throughout the graphs. However, it is clear from watching the film, and the analysis, that there are patterns within my shot profile that is worth noting.


## I need to work on my Shot Fake Game, and playing better off of a Closeout
From "Shot % by Shot type and Play Type". My role on the team is a shooter. Shoot 3's and play defense. From the stats, I shoot much better (40.4%) when I catch and shoot in space rather than a shot fake in between the initial closeout and shot (22.2%). A lot can be equated to the level of closeout, but regardless, this can be a huge separator between becoming more of a playmaker rather than a 1-trick pony. If I can get better at using that shot fake, and shooting, or passing and playing off of the initial closeout, it can be a beneficial addition to my game!

## I need to Shoot better from the Corner!
Across the board shooting corner three's need to be improved. Shot location across Play type, contest level, and Origin, shows that within a reasonable sample size, corner three's are very inefficient. Within shot location, in the lens of play types, when I space to the corner, I shoot 30% (8 percentage points BELOW my average). Especially as a floor spacer, who runs the floor and fills the corner, this is one of the more crucial aspects to improve my game. 

## Shooting is much more efficient within a Set Play rather than Free Lance
From "Shot % by Origin and Contest Level", this Datapoint makes sense, you will naturally shoot better in your offensive role, while running a set play (50% and over) rather than within freelance(Under 38%). You as a player know where your most efficient looks are, and its important to capitalize off of them. What's surprising when looking at freelance shots is when shots are highly contested, I shoot better than having shots wide open (10-26 High Contested vs 5-16 Low Contested)!

## Playing off of Pin Downs are very Effective
Within our offense, I shoot very effective off of a pin down. Whether I turn the ball downhill to the rim, or come off of it and shoot it, its very effective (43.7% off Wing three's - 5 percentage points greater than my average!) This needs to continue in order to be a true threat in our offense!

## Final Thoughts/Additions:

Throughout this project, I learned more about Synergy Sports, gained experience using Python’s NumPy and Plotly Express libraries, and developed my ability to draw conclusions from data and results. Overall, I thought this was a great opportunity to learn new skills and apply them to a meaningful project.

Additionally, I would love to analyze all of my possessions, either manually or by pulling raw stats, to determine which situations generate the most plays and where my offensive net rating is highest on the floor. Within the scope of this project, I would also love to plot these results on a basketball court so I can visually see where I shoot well and where I struggle.

  
      
