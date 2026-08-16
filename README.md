# My Own College Basketball Season Shooting Profile!
From the court, to the film room, to Python, this project combines basketball, film study, and data analysis. I analyzed all of my shot attempts from a college basketball season, categorizing each attempt across factors, including shot location and play context. I then used Python to analyze the data, uncover insights into my shooting profile!

# Table of Contents 
- Introduction
- Film Breakdown and Methodology
- Python Pandas Analysis
- Output using Plotly
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
  1. Analyze Shot
  2. Plot those results using Plotly Express

I 

 
  
      
