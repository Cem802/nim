# Nim Game in Python

This project is an implementation of the game of Nim in Python. In this game, a human player competes against an AI. The AI learns the game throught reinforcement learning.

## How to Play

The game starts with a number of piles, each with a certain number of objects. Players take turns removing any number of objects from a single pile. The player who takes the last object loses.

## Project Structure

The main file of the project is `nim.py`. This file contains the implementation of the game logic, the AI player, and the human player interaction.

## Running the Game

To run the game, simply execute the `nim.py` file in a Python environment.

## AI Player 

The AI player uses a strategy to choose its actions. It will always make the optimal move, unless the epsilon parameter is set to True, in which case it will sometimes make random moves for exploration purposes.

## Training

The NimAI class is an implementation of an AI player for the game of Nim. It uses a form of reinforcement learning called Q-learning to learn how to play the game effectively.
The train function is where the AI player learns to play the game. It does this by playing a number of games against itself and updating its knowledge after each move. Here's how the process works:

- A new instance of the NimAI class is created.
- A loop is started that runs for n iterations. n is the number of games the AI will play to train itself.
- A new game of Nim is created inside of the loop.
- A dictionary is created to keep track of the last move made by each player. It is used to update the Q-values later.
- A while loop created that continues until the games ends. In each iteration, the AI chooses an action, makes a move, and then updated its Q-values based on the result.
- An if statement checks if the game has ended. If it has, it updated the Q-values for the last state and action of each player with a rewared of -1 for the loser and 1 for the winner.
- And if the game hasn't ended, but the current player has made at least one move before, it updates the Q-value for the last state and action of the current player with a reward of 0.
- The player.update function is where the Q-learning happens. It updates the Q-value for a given state and action based on the reward received and the maximum Q-value for the new state. This is done according to the Q-learning formula:
**Q(state, action) = Q(state, action) + α * (reward + γ * max(Q(new_state)) - Q(state, action))**
where α is the learning rate and γ is the discount factor. The learning rate determines how much the AI learns from each update, while the discount factor determines the importance of future rewards.

## Example explanation

Let's say we have a robot in a grid world with 4 actions (up, down, left, right). The robot gets a reward of +1 when it reaches the goal, and a reward of 0 otherwise. The Q-values are initialized to 0.

The robot starts in state S and chooses an action A (e.g., "up") based on its current Q-values (all 0 at the start).

The robot performs the action, ending up in a new state S' and receiving a reward R.

The robot updates the Q-value for the state-action pair (S, A) using the Q-learning formula. If the robot is not at the goal, the reward R is 0, and the new Q-value will be a fraction of the maximum Q-value in the new state S'. If the robot is at the goal, the reward R is 1, and the new Q-value will be a fraction of 1 plus the maximum Q-value in the new state S'.

The robot repeats steps 1-3 for a number of episodes, gradually learning the Q-values for each state-action pair.

Over time, the Q-values will converge to the true values, and the robot will learn to choose the actions that lead to the goal.
