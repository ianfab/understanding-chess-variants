# Understanding chess
This is a collection of ideas for algorithms to discover chess knowledge and content in a systematic way, preferably using generic [chess variant tools](https://github.com/ianfab/Fairy-Stockfish/wiki/Related-projects) based on [Fairy-Stockfish](https://github.com/ianfab/Fairy-Stockfish) for a consistent framework applicable to many games. As this knowledge mostly already exists for chess itself, using it on chess first and foremost serves as a test of the hypotheses and algorithms. Once they generate good results they can however be applied to a large variety of chess variants where corresponding knowledge and data is very limited or non-existent, to hopefully generate useful chess variant understanding, tools, and data.

## Basic game statistics
Some basic statistics can give indication about a game's characteristics, such as duration, balancedness, complexity, etc.

* Game length
* Result distribution
* Branching factor

See https://github.com/ianfab/chess-variant-stats.

## Piece values
Human understandable piece values free from engine-specific search and evaluation artifacts could e.g. be obtained using logistic regression, as already done for [chess](https://www.r-bloggers.com/2015/06/big-data-and-chess-what-are-the-predictive-point-values-of-chess-pieces/) and [atomic](https://www.gilgamath.com/atomic-two.html), but based on high-level engine games in order to be independent from human data. For increased stability the set of positions could be restricted by requiring a minimum number of subsequent moves without changes of material balance (captures, promotions) in order to get a more static piece valuation.

See https://github.com/ianfab/chess-variant-stats.

## Openings
UCT intuitively should be a reasonable choice to create an opening tree with a good balance between breadth, depth, and conciseness in an algorithmic fashion. The MCTS search could either be integrated into the engine itself or be implemented separately, allowing the use of arbitrary (also alpha-beta) UCI engines for the evaluation.

See https://github.com/ianfab/chess-variant-mcts.

## Tactics
Tactic puzzles could be defined as a sequence of best moves by one side where any suboptimal play leads to a significantly worse position. In lack of perfect game theoretical results a heuristical engine analysis defines the evaluation.

This is explored at https://github.com/ianfab/chess-variant-puzzler.

## Strategy
A plan could potentially be defined as the frequent co-occurrence of unordered or ordered pairs or tuples of moves in a search tree or principal variation of a given position. This would be analogous to linguistic co-occurrence of words in phrases. The collection, efficient storage, and analysis of the co-occurrence matrix of moves is an open question. Similar to the opening analysis this might also benefit from applying it to the nodes/paths in a UCT tree.

Co-occurrence could also be applied to opponent moves, especially subsequent plies, in order to identify counter-moves like recaptures, defenses, etc.

First experiments are at https://github.com/ianfab/chess-metrics.

## Characteristics/Style
The character of a position, whether it is positional or tactical, simple or complex, could partially be identified by the entropy of the probability distribution of moves (e.g.., from an MCTS search) of a position, variation, or tree. Further criteria are to be identified.

First experiments are at https://github.com/ianfab/chess-metrics.

## Endgames
Endgame knowledge should ideally be crafted using tablebases. In lack thereof a first step can be to do a frequency analysis of occuring material distributions in high-level engine self-play games, as well as to collect the WLD statistics for each endgame in the generated data. This can also include the identification of sufficient/insufficient mating material.

See https://github.com/ianfab/chess-variant-stats.
