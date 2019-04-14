# Easter Bunny River Crossing Game
This is a web-based version of the river crossing game classic. The rules are as follows:

1. Click on the boatman to move to and fro, in between the two banks.
2. Click on the fox, Easter Bunny or Easter egg to move onto the raft or out of the raft.
3. At any one time, the fox and Easter Bunny cannot be left alone on any bank.
4. At any one time, the Easter Bunny and Easter egg cannot be left alone on any bank.
5. Only one passenger is allowed on the raft at any one time.

## HTML/CSS
- There is a nice HTML-generated background, but it's largely irrelevant except that it makes stuff look pretty.
- The game tokens - fox, Easter Bunny and Easter egg - are also generated via HTML/CSS and rendered within template divs. These divs are then hidden.
- The raft and boatman are rendered and placed on the left or right depending on the position of the raft.

## JavaScript
Most of this is object based. The objects have properties that keep track of game state and methods that alter the state.

### *game*
- *started* is *true* or *false* depending on whether the user has started the game.
- *paused* is *true* when the raft is moving; otherwise it is *false*. If the game is paused, clicking on the raft or game tokens does not work.
- *moves* is set to 0 when the game is reset, and incremented every time the raft is moved.
- *reset()* moves the raft and all game tokens to the left bank, resets *moves* to 0 and *started* to *false*.
- *start()* runs *reset()*, sets *started* to *true* and displays the appropriate message using *showMessage()*.
- *showMessage()* shows the user a message appropriate to the context, in the UI.
- *check()* examines the *position* proprty of each token to see if that the game is won/lost/in progress. Unless the game is still in progress, it runs *showMessage()* and stops the game.

### *passenger*
- *id* is either "fox", "bunny" or "egg".
- *position* is "leftBank", "rightBank" or "raft".
- *render()* uses an argument to determine which placeholder the token will appear in, and grabs the HTML/CSS of the appropriate template, depositing it into that placeholder. For instance, if the fox will be rendered on the right bank, the HTML/CSS content of *template_fox* will be copied and placed in *rightBank_fox*.
- *move()* first determines the destination to be moved to. If the token is on the raft, then it will be moved to the bank that the raft is at. Otherwise, if it is on the left or right bank, it will be moved onto the raft. Only one token can be on the raft at any time, so the user will be prompted if ths is attempted. If there are no issues, the *render()* method is used after clearing the current placeholder. At this point, the *game.check()* method is also run to see if the game has been won.

***fox*, *bunny* and *egg* are clones of the *passenger* object and behave in exactly the same way except that their ids are different.**

### *raft*
- *position* is "leftBank" or "rightBank".
- *move()* moves the raft and changes *position to either "leftBank" or "rightBank". As the raft is moving, *game.paused* is set to *true* until it has stopped moving. *game.check()* is also run to ensure that the raft hasn't left any game-ending token combinations alone on any bank.
