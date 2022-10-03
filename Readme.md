This file contains a project called hangman where the aim is to guess letters in a unknown word while trying to not lose all your lives. It uses a list manipulations and control flow statements to simulate game states

Milestone 1: creating variables for the game

inherently the game uses variables that would simulate real game play, i intialised the following variables:

 Parameters:
    ----------
    word_list: list
        List of words to be used in the game
    num_lives: int
        Number of lives the player has
    
    Attributes:
    ----------
    word: str
        The word to be guessed picked randomly from the word_list
    word_guessed: list
        A list of the letters of the word, with '_' for each letter not yet guessed
        For example, if the word is 'apple', the word_guessed list would be ['_', '_', '_', '_', '_']
        If the player guesses 'a', the list would be ['a', '_', '_', '_', '_']
    num_letters: int
        The number of UNIQUE letters in the word that have not been guessed yet
    num_lives: int
        The number of lives the player has
    list_letters: list
        A list of the letters that have already been tried
        
   The datatypes are shown above
   
   Milestone 2: checked if the guessed character  is in the word
   
   I imported the random module to make use of the random choice when choosing a word for the game from the word_list
   
   following on from milestone 1, after choosing the random word, as indicated by initialising the variables. I have to iteratively ask the user for a input of a letter to be used as a guess
   i decided to use a while loop. This while loop will continously ask for a input but using a few conditional if statements, i can control the flow of decidions making
       
       while(True):
            letter = input("please type a character to guess the word: ");
            print("\n")
            if(len(letter) != 1 & letter.isalpha() ):
                letter = input("Please, enter just one character: ")
                print("\n")
            else:
                if letter in self.list_letters:
                    print (f"{letter} was already tried")
                    print("\n")
                
                else:
                    print("you have typed valid letter...lets check")
                    print("\n")
                    self.check_letter(letter)
                    self.list_letters.append(letter)
                break
   
   The decision making is based on: if letter length is not more than 1 and if letter is alphabetic
   
   there were two reasons for that, one you cannot guess more than one letter at a time and the only acceptable input are alphabatic characters
   
   finally we check whether if it is in the list of previously tried letters otherwise pass to the check function
   
   Milestone 3: check if guessed character is in the word
   
   Following on from milestone 2, we check in letter is in the word, if not we minus one from their life and ask again for a input
   
  since the input doesn't descrimanante against upper or lower case, we first use the lower method to check if it the word first
  
        if(letter.lower() in self.word):
following on we then enumerate through the word, making a not of everytime there is a match, since the letter can occur twice         
            for idxp, letter_in_word in enumerate(self.word):
                if(letter_in_word == letter.lower()):
 
 then we add it in the position using the idxp which indiciates the index position               
 
            self.word_guessed[idxp] = letter
then we minus the number of unique words
           
           self.num_letters -= 1
        else:
            self.num_lives -= 1
            print("you have guessed wrong and lost a life")
            print("\n")
            
 Milestone 4: create the game loop:
 
 For thie milestone, since we had set everything in place by breaking it into functions, the logic just iteratres through a loop till either num of unique words = 0 or letter
 
 hile((game.num_letters != 0) & ( game.num_lives != 0)):
        game.ask_letter()
        
        
    if(game.num_letters == 0):
            print("congratulations you won")
            print("\n")
    elif(game.num_lives == 0):
            print(f"you ran out of lives. The word was {game.word}")
            print("\n")
