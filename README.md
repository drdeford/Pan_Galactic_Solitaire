# Pan Galactic Solitaire

This repository contains working implmentations of Pan Galactic Solitaire (PGS), motivated by Peter Doyle's work on set-theoretic division. 

 ![alt text](https://github.com/drdeford/Pan_Galactic_Solitaire/blob/master/Figures/PGS_Intro.png "The opening window!")



<h2> Mathematical Background </h2>
In 1994, Peter Doyle and John Conway gave <a href="https://arxiv.org/pdf/math/0605779.pdf">a proof<a/> that you do not need the axiom of choice in order to divide by three - in the setting of set theory. That is, given two sets A and B together with a bijection between 3 x A and 3 X B construct a bijection between A and B without choice. This line of work is similar in flavor to the directed graph proof of the Cantor-Scroder-Bernstein Theorem, that if there are injective maps from A to B and B to A then there must be a bijective map between them. The general case of division by n remained open until Peter Doyle and Cecil Qiu produced <a href="https://math.dartmouth.edu/~doyle/docs/four/four.pdf">this paper</a> in 2015 which solved the general case conclusively.  <a href="https://arxiv.org/pdf/1504.02179.pdf"> This paper</a> by Rich Schwartz contains a clean, expository proof of their main result (along with some whimsical pictures of chickens).  
 
  <h2> Infinite Games  </h2>

 The general proof works by considering a set of rules for an infinite card game where the cards are arranged in an n x A grid (with columns indexed by elements of A) and elements of the set B are represented by the ranks of the cards, so that together with the n suits the original bijection from n x A to n x B gives us a completely filled grid. A set of rules for iteratively rearranging the cards (playing the game) that does not invoke choice and eventually returns the desired bijection from A to B gives the result. The name 'Pan Galactic' is due to Peter Doyle, who believes that "This is the ‘right way’ to approach division, and some definite fraction of intelligent life forms in the universe  will  have  discovered  it."
 
 <h2> Finite Games  </h2>
 
 During my first year of graduate school, we experimented with many variant rule sets using a standard deck. In this case, |B|=13 and you begin by dealing the cards in a 4 x 13 grid and then making a series of moves from some permissible set, with the eventual hope of arranging all of the cards so that each column contains only a single rank. Thus, the family of Pan Galactic Solitaire (PGS) games was born, as a large collection of possible sets of permissible rules were considered. Having played many games of PGS by hand, I wondered if we could implement these solitaire games on a computer. After encoding one popular set of rules, I was able to  implement several basic strategies for game play, evaluating their win probabilities in a Monte Carlo fasion. Some of these are described on pages 7-8 of the <a href="https://math.dartmouth.edu/~doyle/docs/four/four.pdf">Doyle and Qiu paper</a>. The versions presented here grew out of this project. 
 
 <h2> Playing EasyPGS</h2>
 This section describes how to play the easyPGS variant provided here. 
 <h4> Starting the game </h4>
 The source folder contains two zip directories - a Windows executable version and the Python Source. To run either, simply download the corresponding .zip file and extract the contents. For the Windows version, double clicking "easypgs.py" will start the game. The Python source includes versions for both Python 2 and Python 3, as well as some more difficult rule sets. In either case, you can start the game by typing python easypgs.py in your favorite terminal. Then, click the "Play Game" button to get playing.
 
 <h4> Game Rules </h4>
 
 As described above, the main gameplay area is a 4 x 13 grid of cards, shown in the figure below. The rows are each indexed by a suit - from bottom to top spades, hearts, diamonds, clubs. A card is in its home row if the suit of the card matches the index of the row. For example, the 2 of spades is in its home row in the example figure. The goal of the game is to have each column consist of all four of the cards of a single rank, with each of them in its corresponding home row.
 
  
  ![alt text](https://github.com/drdeford/Pan_Galactic_Solitaire/blob/master/Figures/PGS_1.png "The game window")
  
  
  There are two ways to move cards around the grid in this version of PGS: 
 <ol>
 <li> <b>Swap: </b> If a card A is in its home row and there is another card B in its same column that has the same suit as A then B can be exchanged in the grid with the card C that is uniquely specified by the rank of A and the suit of the row that B currently occupies. To perform this move in the game, click on card B (the one that isn't in its home row). The figures below show some examples. In the first figure, notice that in the leftmost column the 9 of hearts is in its home row so we can use it as card A. In that same column we have the 3 of hearts (card B) which we can exchange for the 9 of clubs (card C), since the 3 is in the club row. Performing this change now allows us to use the 9 of clubs (card A) to exchange the 6 of clubs (card B) for the 9 of diamonds (card C). Next, we can complete the column of 9s using the 9 of diamonds (card A) to swap the 8 of diamonds (card B) for the 9 of spades (card C).
 
  ![alt text](https://github.com/drdeford/Pan_Galactic_Solitaire/blob/master/Figures/PGS_8.png "Swap 9s")
  ![alt text](https://github.com/drdeford/Pan_Galactic_Solitaire/blob/master/Figures/PGS_9.png "Swap 9s")
  ![alt text](https://github.com/drdeford/Pan_Galactic_Solitaire/blob/master/Figures/PGS_10.png "Swap 9s")
  ![alt text](https://github.com/drdeford/Pan_Galactic_Solitaire/blob/master/Figures/PGS_11.png "Swap 9s")
  
  Although this move seems complicated, a little bit of practice is usually enough to get a feel for the right way to apply it. 
</li>
 <li> <b>Cycle: </b> You may perform a cycle move if at least three of the cards in a column share a rank. This move exchanges the card not in its home row with the appropriate card of the rank that matches the majority of the column. To perform this move in the game, click on the card that doesn't match the majority of the column.

 The figure below shows an example in the 3s column where the cycle move can be applied twice in succession: first in the hearts row to swap the 3 of hearts for the nine of diamonds and then in the diamonds row to swap the 9 of diamonds for the three of diamonds, completing the column: 
   ![alt text](https://github.com/drdeford/Pan_Galactic_Solitaire/blob/master/Figures/PGS_5.png "Cycle 3s")
   ![alt text](https://github.com/drdeford/Pan_Galactic_Solitaire/blob/master/Figures/PGS_6.png "Cycle 3s")
   ![alt text](https://github.com/drdeford/Pan_Galactic_Solitaire/blob/master/Figures/PGS_7.png "Cycle 3s")
</li>
 </ol>

  <h4> Interface </h4>
  The bottom of the game window has some information about the current game and buttons for highlighting permissible moves and interacting with the game state. The moves counter shows how many swap and cycle steps you have performed in this game. There are several interesting questions about the average number of steps it takes for a game to end or the minimal number of steps needed to win. The shuffle and redeal buttons restart the game with a new card layout and the help, options, and quit buttons are hopefully self-explanatory. 
  
  The top row of buttons gives highlights pairs of cards which can be swapped with backgrounds of the same color. The None button turns off all suggestions, the All button shows all possible swaps, and the buttons labelled with a suit show the moves that correspond to a card in that suits home row. The figure below shows a board with this highlighting for the spade moves, since it is possible to swap the 9 of spades for the 7 of diamonds, since the 7 of spades is in the top row directly above the 9 and similarly it is possible to swap the 2 of spades for the ace of diamonds, since the ace of spades is in the top row directly above the 2. 
  
  ![alt text](https://github.com/drdeford/Pan_Galactic_Solitaire/blob/master/Figures/PGS_2.png "Permissible spade moves")

  The full set of permissible moves can look a little overwhelming when viewed all at once. Additionally, it is possible for a single card to be allowed to swap with multiple partners, in which case, just a single color pair is displayed. After each move, the game window resets to showing none of the hints. 
  ![alt text](https://github.com/drdeford/Pan_Galactic_Solitaire/blob/master/Figures/PGS_3.png "Permissible all moves")
  ![alt text](https://github.com/drdeford/Pan_Galactic_Solitaire/blob/master/Figures/PGS_lots.png "Permissible all moves")


  <h4>End of the game </h4>
  Once all of the cards in a row have the same rank and are in the proper row that column is turned face down, as the cards may no longer move. You win if all of the cards are eventually turned face down. You lose if you reach a state with no possible moves. Not all games are winnable (understatement). An example of a lost game is below, since after 33 moves it is no longer possible to swap or cycle any cards.
    ![alt text](https://github.com/drdeford/Pan_Galactic_Solitaire/blob/master/Figures/PGS_12.png "Lost game :(") 

  
<h4> Easy?PGS</h4>
Most games of easyPGS are unwinnable, at least as far as we can tell with Monte Carlo simulations, which seems to belie the "easy" moniker. The reason this version is called easyPGS is that the original rules did not allow you to make the moves of type 2 described in the previous section. This led to many more unwinnable games and a much less satisfactory playing experience (from my perspective). PGS purists, who despair at the attention spans of millenials like myself, can play with the original rule set in the python source directory.  



