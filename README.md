# Quantum Guayabita

## Introducción:

Guayabita is a typical Colombian's gambling game that can be described in the following four steps:

- N players with an amount of money M_i, each one, start with a minimum bet. This minimum bet is going to compose what we call the bank.
In this implementation and for the sake of simplicity, the minimum bet is one coin from each player.
- Once the bank with the minimum bet is created, the first player starts his turn. In each turn the corresponding player rolls a dice, after which the bank is created.
first throw the player must decide if he/she wants to play for the "all" (bet the same money as the total of the bank) or for the "minimum" (bet only one coin), once the decision is made the player must throw the dice again, if the new result is higher than the previous one the player wins and then he/she can take the minimum or the all of the bank, depending on his initial bet. If the player loses he must give the dealer the corresponding bet.
- The decision on the bet is conditional on the player's money compared to the bank. The player can go all-in only if he/she has enough money to back the bet.
- Finally, after the player wins or loses it is the turn of the next player. The game only ends when all players, except one, lose their money. Note that every time a player wins all in the bank it is necessary to create the minimum bets again.

In this project, inspired by the Qiskit Colombia fest spirit, we proposed a quantum version of this game. The purpose of such a implementation is to study how the inclusion of quantum strategies, as well as quantum entanglement and phases, can modified the results of the game for only two players, Alice and Bob. The results of the experiments based on the quantum implementation are compared to those of the classical one.

## Methodology:

### Classic Guayabita:

The implementation of the classic rules for guayabita are given in the file guayabita_classic.ipynb.
In the code there are two kinds of objects

Player(): Refers to the player, which has attributes for money and methods to roll the dice and make a bet.
Bank(): Referring to the bank, with attributes to count the money of the bet and the methods to add or subtract money from the players.

Additionally, some functions are defined

- strategy : Function that defines the classic strategy of the bet according to the result of the first die.
- Execution: Function to execute the game until one or both players involved lose all the money.
- plot_histogram: Function that returns the histogram of the total number of events "won" or "lost" by each player.
- plot_history: Function that returns the graph of the evolution of the players' and bank's money as a function of the rounds

### Quantum Implementation:

For the implementation of the Quantum Guayabita we build a circuit composed of two quantum and four classical registers.
Each player is represented by a qubit taking the values {|0>, |1>}, representing the "all" or "minimun" bet states respectively.
Then, the information associated with the money and the roll of the dice is no included in the quantum objects but in classical vectors wich are modified for the quantum bet state.

The implementation of the Quantum rules for  QuantumGuayabita are given in the copia_de_quantum_guayabita.ipynb file.

In the code there are two kinds of objects:

At first, unitary gates were implemented defining the strategies of each player. The bank is a classical figure which grabs the bets of the players and distributes the gamblings in every round. The dice also acts as a classical figure in order to determine the strategy and the win criteria.

We simulate the evolution of a game in the particular case of a entangled Bell states, exhibiting new game results which are not presented in the classical version