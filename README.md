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
- *paused* is *true* when the raft is moving; otherwise it is *false*.
- *moves* is set to 0 when the game is started, and incremented every time the raft is moved.

### *placeholder*

### *raft*
