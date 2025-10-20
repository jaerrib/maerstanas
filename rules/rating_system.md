# Mǽrstánas Rating System

## Overview

The Elo rating system was invented in the 1960s by Arpad Elo, a Hungarian‑American physics professor and chess master, and was officially adopted by the U.S. Chess Federation in 1960 and by FIDE (the international chess federation) in 1970. ([Wikipedia](https://en.wikipedia.org/wiki/Elo_rating_system))

In historical terms, it’s a very modern invention, and it definitely did not exist in the Anglo‑Saxon period. However, when adapting Mǽrstánas to an online, multiplayer platform, I wanted to implement a rating system that could be used to compare players' skill level. Therefore, I adapted the Elo system to my game. What follows is a written explanation of the Python code included in the app I wrote. ([Source code on Codeberg](https://codeberg.org/jaerrib/maerstanas-webapp))

> It should be noted that the calculations express ratings with decimals. My online system tracks this internally but presents rounded ratings in the user interface. So, someone with a rating of 1191.7 would see this value as 1192. Personally, I like the whole number approach, but as this system is neither formal nor widely used, use whatever makes you happy.  

---

### Player Ratings

- **Starting Rating:** Every new player begins with a rating of **1000**.
- **How Ratings Change:** After each game, both players’ ratings are adjusted based on the result and the relative strength of their opponents.
- **The K‑Factor:** The maximum adjustment from a single game is **32 points**.

### Wins and Losses

- If you win, your rating goes up.
- If you lose, your rating goes down.
- The exact number of points gained or lost depends on how strong your opponent was compared to you:
  - Beating a higher‑rated opponent gives you more points.
  - Beating a much lower‑rated opponent gives you only a few points.
  - Losing to a much lower‑rated opponent costs you more points.
  - Losing to a much higher‑rated opponent costs you only a few points.

### Ties

- If the game ends in a tie, both players’ ratings move toward each other:
  - The lower‑rated player gains points.
  - The higher‑rated player loses points.
- The closer the ratings already are, the smaller the adjustment.

This system ensures that ratings reflect not just wins and losses, but also the strength of the opponents you face.

## Detailed Explanation

### Rating overview

Players can calculate their own ratings after each match using a simple Elo-style method. New players start at 1000. Each result changes ratings by up to 32 points, scaled by how likely the result was based on both players’ current ratings.

---

### What you need

- **Current ratings:** Each player’s rating before the match.
- **Result:** Win, loss, or tie.
- **K-factor:** Use $K = 32$ for every match.

---

### Core formulas

- **Rating difference**
  
  $$
  \text{diff} = R_{\text{opponent}} - R_{\text{you}}
  $$

- **Expected score (your chance of a point)**
  
  $$
  E = \frac{1}{1 + 10^{\left(\frac{\text{diff}}{400}\right)}}
  $$

- **Score by result**
  
  $$
  S =
  \begin{cases}
  1 & \text{if you win} \\
  0.5 & \text{if you tie} \\
  0 & \text{if you lose}
  \end{cases}
  $$

- **Rating update**
  
  $$
  R_{\text{new}} = R_{\text{old}} + K \cdot (S - E)
  $$

---

### Step-by-step for a win or loss

1. **Compute diff**
   
   $$
   \text{diff} = R_{\text{opponent}} - R_{\text{you}}
   $$

2. **Compute your expected score**
   
   $$
   E = \frac{1}{1 + 10^{\left(\frac{\text{diff}}{400}\right)}}
   $$

3. **Set your actual score $S$**
   - **Win:** $S = 1$
   - **Loss:** $S = 0$

4. **Update your rating**
   
   $$
   R_{\text{new}} = R_{\text{old}} + 32 \cdot (S - E)
   $$

5. **Update your opponent’s rating**
   - Your opponent’s expected score is $1 - E$.
   - Their actual score is the opposite of yours (win = 0 for them, loss = 1).
   
   $$
   R_{\text{new, opp}} = R_{\text{old, opp}} + 32 \cdot \big((1 - S) - (1 - E)\big)
   $$

---

### Step-by-step for a tie

1. **Compute absolute difference**
   
   $$
   \text{diff} = |R_{\text{you}} - R_{\text{opponent}}|
   $$

2. **Compute expected score for the higher-rated player**
   
   $$
   E_{\text{higher}} = \frac{1}{1 + 10^{\left(\frac{\text{diff}}{400}\right)}}
   $$

3. **Both players use $S = 0.5$**
   
   $$
   R_{\text{new}} = R_{\text{old}} + 32 \cdot (0.5 - E)
   $$

   - For the higher-rated player, use $E = E_{\text{higher}}$.
   - For the lower-rated player, use $E = 1 - E_{\text{higher}}$.

---

### Examples

#### Win example (1200 vs. 1000, higher-rated player wins)
- **You:** $R_{\text{you}} = 1200$, **Opponent:** $R_{\text{opp}} = 1000$
- **diff:** $1000 - 1200 = -200$
  
  $$
  E = \frac{1}{1 + 10^{\left(\frac{-200}{400}\right)}} \approx \frac{1}{1 + 10^{-0.5}} \approx 0.76
  $$

- **Win $S = 1$:**
  
  $$
  \Delta R \approx 32 \cdot (1 - 0.76) \approx 7.7
  $$
  
  - **Winner new rating:** $1200 + 7.7 \approx 1207.7$
  - **Loser new rating:** Opponent’s expected score $= 1 - 0.76 = 0.24$
    
    $$
    \Delta R_{\text{opp}} = 32 \cdot (0 - 0.24) \approx -7.7
    $$
    
    New rating $1000 - 7.7 \approx 992.3$

#### Upset win example (1000 vs. 1200, lower-rated player wins)
- **diff:** $1200 - 1000 = 200$
  
  $$
  E = \frac{1}{1 + 10^{\left(\frac{200}{400}\right)}} \approx 0.24
  $$

- **Win $S = 1$:**
  
  $$
  \Delta R \approx 32 \cdot (1 - 0.24) \approx 24.3
  $$
  
  - **Winner new rating:** $1000 + 24.3 \approx 1024.3$
  - **Loser new rating:** $1200 + 32 \cdot (0 - 0.76) \approx 1200 - 24.3 = 1175.7$

#### Tie example (1200 vs. 1000)
- **diff (absolute):** $|1200 - 1000| = 200$
  
  $$
  E_{\text{higher}} \approx 0.76,\quad E_{\text{lower}} \approx 0.24
  $$

- **Both use $S = 0.5$:**
  
  - **Higher-rated new rating:** $1200 + 32 \cdot (0.5 - 0.76) \approx 1200 - 8.3 = 1191.7$
  - **Lower-rated new rating:** $1000 + 32 \cdot (0.5 - 0.24) \approx 1000 + 8.3 = 1008.3$

---

### Quick reference

- **Start:** Everyone begins at 1000.
- **K-factor:** Always 32.
- **Expected score:** 

  $$
  E = \frac{1}{1 + 10^{\left(\frac{R_{\text{opp}} - R_{\text{you}}}{400}\right)}}
  $$

- **Update:** 

  $$
  R_{\text{new}} = R_{\text{old}} + 32 \cdot (S - E)
  $$

- **Scores:** Win = 1, Tie = 0.5, Loss = 0.  
- **Direction:** Upsets cause big swings; predictable results cause small swings.
