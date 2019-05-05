# Pan Galactic Solitaire

This repository contains working implmentations of Pan Galactic Solitaire (PGS), motivated by Peter Doyle's work on set-theoretic division. 


<h2> Mathematical Background </h2>
In 1994, Peter Doyle and John Conway gave <a href="https://arxiv.org/pdf/math/0605779.pdf">a proof<a/> that you do not need the axiom of choice in order to divide by three - in the setting of set theory. That is, given two sets A and B together with a bijection between 3 x A and 3 X B construct a bijection between A and B without choice. This line of work is similar in flavor to the directed graph proof of the Cantor-Scroder-Bernstein Theorem, that if there are injective maps from A to B and B to A then there must be a bijective map between them. The general case of division by n remained open until Peter Doyle and Cecil Qiu produced <a href="https://math.dartmouth.edu/~doyle/docs/four/four.pdf">this paper</a> in 2015 which solved the general case conclusively.  <a href="https://arxiv.org/pdf/1504.02179.pdf"> This paper</a> by Rich Schwartz contains a clean, expository proof of their main result (along with some whimsical pictures of chickens).  
 
  <h2> Infinite Games  </h2>

 The general proof works by considering a set of rules for an infinite card game where the cards are arranged in an n x A grid (with columns indexed by elements of A) and elements of the set B are represented by the ranks of the cards, so that together with the n suits the original bijection from n x A to n x B gives us a completely filled grid. A set of rules for iteratively rearranging the cards (playing the game) that does not invoke choice and eventually returns the desired bijection from A to B gives the result. The name 'Pan Galactic' is due to Peter Doyle, who believes that "This is the ‘right way’ to approach division, and some definite fraction of intelligent life forms in the universe  will  have  discovered  it."
 
 <h2> Finite Games  </h2>
 
 During my first year of graduate school, we experimented with many variant rule sets using a standard deck. In this case, |B|=13 and you begin by dealing the cards in a 4 x 13 grid and then making a series of moves from some permissible set, with the eventual hope of arranging all of the cards so that each column contains only a single rank. Thus, the family of Pan Galactic Solitaire (PGS) games was born, as a large collection of possible sets of permissible rules were considered. Having played many games of PGS by hand, I wondered if we could implement these solitaire games on a computer. After encoding one popular set of rules, I was able to  implement several basic strategies for game play, evaluating their win probabilities in a Monte Carlo fasion. Some of these are described on pages 7-8 of the <a href="https://math.dartmouth.edu/~doyle/docs/four/four.pdf">Doyle and Qiu paper</a>. The versions presented here grew out of this project. 
 
 <h2> Playing EasyPGS</h2>
 This section describes how to play the easyPGS variant provided here. 
 <h4> Starting the game </h4>
 The source folder contains two zip directories - a Windows executable version and the Python Source. To run either, simply download the corresponding .zip file and extract the contents. For the Windows version, double clicking "easypgs.py" will start the game. The Python source includes versions for both Python 2 and Python 3, as well as some more difficult rule sets. In either case, you can start the game by typing python easypgs.py in your favorite terminal. Then, click the "Start Game" button to get playing.
 
 ![alt text](https://github.com/drdeford/Pan_Galactic_Solitaire/blob/master/Figures/PGS_Intro.png "The opening window!")
 <h4> Game Rules </h4>
 
 As described above, the main gameplay area is a 4 x 13 grid of cards, shown in the figure below. 
 
  ![alt text](https://github.com/drdeford/Pan_Galactic_Solitaire/blob/master/Figures/PGS_1.png "The game window!")
  
  
<h4> Easy?PGS</h4>
Most games of easyPGS are unwinnable, at least as far as we can tell with Monte Carlo simulations, which seems to belie the "easy" moniker. The reason this version is called easyPGS is that the original rules did not allow you to make the moves of type 2 described in the previous section. This led to many more unwinnable games and a much less satisfactory playing experience (from my perspective). PGS purists, who despair at the attention spans of millenials like myself, can play with the original rule set in the python source directory.  

