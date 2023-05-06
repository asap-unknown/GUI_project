# GUI_project
I made a GUI on rock paper scissors for a school project at  VSU
i added the code into the code section of this project
'''
Name: elijah johnson
Date May 2, 2023
Description: student makes new formated version of the RPS into a gui interface
'''
import random
from breezypythongui import EasyFrame

class RPSGame(EasyFrame):
    
    def __init__(self):
        EasyFrame.__init__(self, title="Rock, Paper, Scissors")
        self.addLabel(text="Enter your play:", row=0, column=0)
        self.play_entry = self.addIntegerField(value=0, row=0, column=1)
        self.addButton(text="Play", row=1, column=0, command=self.play_game)
        self.addLabel(text="", row=2, column=0, columnspan=2, sticky="NSEW")
        self.addLabel(text="Possible plays: Rock = 0, Paper = 1, Scissors = 2", row=3, column=0, columnspan=2)
        
    def play_game(self):
        # Define the list of possible plays
        plays = ['Rock', 'Paper', 'Scissors']

        # Get the player's play
        player_play = self.play_entry.getNumber()
        if player_play not in range(3):
            self.messageBox(title="Invalid Input", message="Please enter a valid input (0 for Rock, 1 for Paper, 2 for Scissors)")
            return
        player_play_str = plays[player_play]

        # Get the computer's play
        computer_play = random.choice(plays)
        computer_play_str = computer_play

        # Determine the winner
        if player_play_str == computer_play_str:
            result = "It's a tie!"
        elif (player_play_str == 'Rock' and computer_play_str == 'Scissors') or (player_play_str == 'Paper' and computer_play_str == 'Rock') or (player_play_str == 'Scissors' and computer_play_str == 'Paper'):
            result = "You win!"
        else:
            result = "Computer wins!"

        # Update the result label
        self.result_label = self.addLabel(text="You played: {}\nComputer played: {}\n{}".format(player_play_str, computer_play_str, result), row=4, column=0, columnspan=2)

# Instantiate and pop up the window
RPSGame().mainloop()

