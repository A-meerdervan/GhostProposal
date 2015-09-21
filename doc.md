## Design Document Ghost App

Alex van der Meer

10400958

a.meerdervan@gmail.com

###Design deciscions

I added a pdf containing a class diagram of the app. All android activity's are represented by a class diagram, additional to these activity's there are three other classes. 
Next these other classes and their relevance are discussed per class. 

#The GameEngine class
The GameEngine class contains the dictionary. The dictionary is a large object and has to be read in to the app at launch time. If the dictionary would be in the game controlling activity, then when this activity closes and reopens the dictionary has to be initialized again. This happens when the game controlling activity would call on the screen that shows the winner(clossing the game activity) and then start a new game from there. To initialize this dictionary there is a FillDictionaryFromFile function. 
Now that the GameEngine class has the dictionary it is straightforward to also have it contain all functions that do operations on the dictonary. Therefore the class is called GameEngine, since it has al the tools to play the game in the sence of checking wheter a newly added letter makes the player win or lose, or just continue. This is done by the GameEndedAfterLetter function. This function should return a bool so that the GhostGameActivity class only needs to use a simple if statement to determine what to do after the input of a new letter. The ReasonForWinning attribute should be a string that is assigned by the GameEndeAfterLetter function. This attribute can than be passed to the WinnerScreenActiviy class for use of displaying on the screen.
What is not shown in the pdf is that all activity classes have a <<uses>> relationship with the GameEngine class.The GameEngine class has an atribute Language, every activity needs to know the current language to know in which language to display. 

#The Players and Player classes
This class contains all the information about players. Multiple activities need this information so it is bundled in a sepparate class. It has atrributes to identify the current players and the previous. 
The current players are used in the GhostGameActivity class to be able to display their names. The GhostSetupActivity needs the previous players so that it can put their names as a default/suggestion value in the textboxes. In this way the user does not have to retype the names after each game.
For more comfort for the user, all previously used player names displayed in these same boxes. The history of players can be accesed trough the PlayersArray atribute in the Players class. Here only the names of the players are required, however the GhostHighscoresActivity class needs both the names and the scores. To combine this the PlayersArray atribute combines player scores and names. This is done using objects of a Player class with atributes score and name. Now we will discuss the methods that the Players class needs. It needs to be able to add new players, hence the AddPlayer method. In the settings activity there is an option to remove all players hence the RemoveAllPlayers method. The app should remember its user history after closing, therefore there are two methods added, 1 that fills the class from a file and one that writes to a file. 
The last method to be discussed is the SortArrayOnHighscore method. The highscores page should display the highscores in order, this method takes care of this. 



