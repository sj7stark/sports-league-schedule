# sports-league-schedule

The notebook in this repository contains a model for creating a schedule for a simple sports league. I used this problem to create a schedule for a Pokemon Draft League for a group of YouTubers.

# Problem Definition

Consider a sports style league with the following characteristics:
* There are 16 teams
* There are 10 weeks in the season
* Each team plays 1 match each week
* Each match has a home team and an away team
* Each team has 5 home games and 5 away games throughout the season
* Two teams can only face-off against each other at most once in a season

# Model Formulation

## Sets

$ w \in W$: The set of weeks (time periods) \
$ t \in T$: The set of teams

## Decision Variables

$ x_{wha}$: A binary variable that equals 1 if team $h \in T$ is home against team $a \in T, a \neq h$, during week $ w \in W$ and 0 otherwise

## Model

### Objective Function

$Min \space \space 0 \qquad$  (there is no objective, we just want a feasible schedule)

### Constraints

Each team plays exactly one match each week:

$$ \sum_{a \in T, a \neq i} x_{wia} + \sum_{h \in T, h \neq i} x_{whi} = 1, \qquad \forall w \in W, i \in T$$ 

Each team is the home team 5 times throughout the season:

$$ \sum_{w \in W}\sum_{a \in T, a \neq i} x_{wia} = 5, \qquad \forall i \in T$$

Each team is the away team 5 times throughout the season:

$$ \sum_{w \in W}\sum_{h \in T, h \neq i} x_{whi} = 5, \qquad \forall i \in T$$

Two teams can only face off against each other at most once during the season:

$$ \sum_{w \in W} x_{wij} + \sum_{w \in W} x_{wji} \leq 1, \qquad \forall i \in T, j \in T, j \neq i$$ 
