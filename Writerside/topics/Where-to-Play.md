# Where to Play

## Software play options

### Javascript

The Javascript version of **Mǽrstánas** uses a simple, randomized computer opponent.

[Play now](https://jaerrib.codeberg.page/maerstanas_js/) or check out the [source code](https://codeberg.org/jaerrib/maerstanas_js)

### Python

#### Flask

This version uses the [Flask](https://flask.palletsprojects.com/en/3.0.x/) framework and is deployed on [Fly.io](https://fly.io/). It incorporates a computer opponent that bases its moves on running numerous simulations and weighting the results. Players can currently play using the traditional or simple scoring rules. 

[Play now](https://maerstanas-python.fly.dev/) or check out the [source code](https://codeberg.org/jaerrib/maerstanas_python)

#### Django

This version uses the [Django](https://www.djangoproject.com/) framework and is a full-stack web application. Players are able to log in to play asynchronous games against other players or play unranked games against variants of the bots ported from the Flask version.  

[Play now](https://maerstanas.fly.dev/) or check out the [source code](https://codeberg.org/jaerrib/maerstanas-webapp)

This version uses the Python-based [Django](https://www.djangoproject.com/) web framework and is a full-stack web application. An account is required. However, players can play against bots on different difficulties or play asynchronous games against other players! Games and play records can be saved to reference later.  

[Play now](https://maerstanas.fly.dev/) or check out the [source code](https://codeberg.org/jaerrib/maerstanas_python)

#### Pygame

This version uses [Pygame](https://www.pygame.org/) and needs to be installed locally to play. The simulation engine used for the Flask and Django versions was first utilized here.  

Check out the [source code](https://codeberg.org/jaerrib/maerstanas_python/src/branch/pygame)

## Print-and-play option

The original print-and-play version can be found [here](https://codeberg.org/jaerrib/maerstanas/releases)

## Alternative play option

If you don't have access to stones, feel free to use the included page of game boards. **Mǽrstánas** is similar to Tic-Tac-Toe in that players can just alternate writing an *X* or an *O* in place of the stones. You can also just draw a 7x7 grid if you find yourself without a printer and need to pass the time! Just remember that **Mǽrstánas** is *not* Tic-Tac-Toe, and the rules and win conditions are different.

<img src="../images/mini-boards.svg" alt="image of several small boards" width="800" border-effect="line"/>
