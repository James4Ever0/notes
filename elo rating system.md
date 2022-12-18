---
title: elo rating system
created: '2022-12-18T18:42:44.068Z'
modified: '2022-12-18T20:10:04.932Z'
---

# elo rating system

[Elo rating system](https://github.com/theubermanishere/elo-rating-system) is a method for calculating the relative skill levels of players in two-player games such as chess. It is named after its creator Arpad Elo, a Hungarian-American physics professor.

The basic idea behind the Elo rating system is that each player is assigned a rating, and the difference between the ratings of two players determines the expected outcome of a match between them. If a higher-rated player wins, their rating will increase, while the rating of the lower-rated player will decrease. If the lower-rated player wins, the opposite will happen. The amount of change in the ratings depends on the difference between the ratings and the result of the match.

Here is an example of how the Elo rating system can be implemented in Python:

```python
def elo_rating(rating1, rating2, k, result):
    # Calculate the expected score for each player
    expect1 = 1 / (1 + 10 ** ((rating2 - rating1) / 400))
    expect2 = 1 / (1 + 10 ** ((rating1 - rating2) / 400))
 
    # Calculate the new ratings for each player
    if result == 1:
        # Player 1 wins
        rating1 = rating1 + k * (1 - expect1)
        rating2 = rating2 + k * (0 - expect2)
    elif result == 0:
        # Player 2 wins
        rating1 = rating1 + k * (0 - expect1)
        rating2 = rating2 + k * (1 - expect2)
 
    return rating1, rating2
```
This function takes four arguments:

rating1: The current rating of player 1.
rating2: The current rating of player 2.
k: The "k-factor", which determines the amount of change in the ratings. A higher k-factor means more change.
result: The result of the match, where 1 indicates a win for player 1 and 0 indicates a win for player 2.
The function returns a tuple containing the updated ratings for both players.




