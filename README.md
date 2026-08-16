# my-college-basketball-shooting-profile
From the court, to the film room, to Python, this project combines basketball, film study, and data analysis. I analyzed all of my shot attempts from a college basketball season, categorizing each attempt across factors, including shot location and play context. I then used Python to analyze the data, uncover insights into my shooting profile!

# Table of Contents 
- Introduction
- Film Breakdown and Methodology
- Python Pandas Analysis
- Output using Plotly
- Conclusions

# Introduction
  After finishing my third college basketball season, I've wanted to look more deeply on the types of shots and offensive looks I've received as a player. 
  We use Synergy Sports Tech to watch and review film, and within the tech there is a list of all of your shots, and the type of shots you've received. Whether it was a "Spot-up" or "Cut". I wanted to be more specific on how and where I get my shots, and the quality of each look! Not only would I think this would be more beneficial for the team, to see where an average player gets their shots, but a great player-development opportunity to see my own weaknesses, in a more specific route! 
  Every player has a role within the court, and I wanted to pair my growing technical skills as an aspiring data analyst, and current film reviewing skills to ultimately maximize my role as a player and help out the team however I could! 

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

 
  
      
