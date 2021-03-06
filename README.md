# tombola.js

Random/chance generation methods, geared towards creating procedural generation, generative art/music etc. It's a simple set of functions put together for my own use, but hopefully useful to others. Features like weighted functions, and a persistent deck which can be drawn from, can simplify the process of creating interesting outcomes.

**Basic Generation**
-

###range
```javascript
tombola.range( min, max );
```
>*returns: integer*

Randomly generates a whole number in the range from 'min' to 'max'.

-

###dice
```javascript
tombola.dice( sides, die );
```
>*returns: integer*

Randomly generates a whole number from the total of simulated dice rolls.

-

###fudge
```javascript
tombola.fudge( strength, die );
```
>*returns: integer*

Randomly generates a positive or negative modifier (or zero), based on the concept of ["Fudge dice"](https://en.wikipedia.org/wiki/Fudge_%28role-playing_game_system%29#Fudge_dice). 

-

###chance
```javascript
tombola.chance( chance, possibility );
```
>*returns: boolean*

Randomly generates a true or false based on a probability fraction, e.g a 'chance' of 1 and 'possibility' of 5 will give the function a 1 in 5 chance of returning true.

-

###percent
```javascript
tombola.percent( percentage );
```
>*returns: boolean*

Randomly generates a true or false based on a probability percentage. e.g a 'percentage' of 25 will give the function a 25% chance of returning true.

-

**Weighting**
-

###weightedNumber
```javascript
tombola.weightedNumber( [weight1, weight2, etc...] );
```
>*returns: integer*

Randomly generates a whole number with a weighted probability. e.g using weights of [10, 5, 5] would pick a number between 1 - 3, where 1 is twice as likely to be returned than either 2 or 3.

-

###weightedItem
```javascript
tombola.weightedItem( [item1, item2, etc...] , [weight1, weight2, etc...] );
```
>*returns: item from array*

Randomly picks from an array of items (can be strings, numbers, objects etc) with a weighted probability. e.g using the items ['cat', 'dog', 'tortoise'] and using weights of [10, 5, 5] would randomly return one of the pets, but 'cat' would be twice as likely to be returned than either 'dog' or 'tortoise'.

-

###weightedFunction
```javascript
tombola.weightedFunction( [function1, function2, etc...] , [weight1, weight2, etc...] );
```
>*returns: executes a given function*

Randomly picks from an array of functions, using a weighted probability, and executes that function. e.g using an array of functions [blur, fade, dissolve], and using weights of [10, 5, 5] would randomly call one of the given functions, but the function 'blur' would be twice as likely to be picked than either 'fade' or 'dissolve'.

-

**Clusters**
-

###cluster
```javascript
tombola.cluster( min, max, spread, quantity );
```
>*returns: integer array*

Randomly generates an array of whole numbers, which are clustered around a randomly selected point between 'min' and 'max'. 'spread' sets how wide the cluster is, e.g if the center of the cluster is 50, and 'spread' is set to 10, generated numbers can be anything from 40 to 60 (-10 and +10 of 50). The chance is evenly distributed.

-

###clusterFudge
```javascript
tombola.clusterFudge( min, max, strength, die, quantity );
```
>*returns: integer array*

Randomly generates an array of whole numbers, which are clustered around a randomly selected point between 'min' and 'max', same as tombola.cluster(); The difference is that chance is not evenly distributed, it can be weighted so that generated numbers are more heavily distributed around the center of the cluster. Higher 'strength' and fewer 'die' will give a more even distribution, while lower 'strength' and more 'die' will make a more center-heavy cluster. 'strength' and 'die' refer to ["Fudge dice"](https://en.wikipedia.org/wiki/Fudge_%28role-playing_game_system%29#Fudge_dice) properties (see tombola.fudge();). 'strength' x 'die' = the total spread of the cluster.

-

**Persistent Deck**
-

###deck
```javascript
var DECK = new tombola.deck( [item1, item2, etc...] );
```
Creates an instance of tombola.deck(); It's a persistant deck/hat/tombola which can contain a set of items which can be randomly drawn from, added to, looked at or shuffled. A simple example would be if you wanted a set of names to be drawn from a hat in a random order and without repetition.

-

###draw
```javascript
DECK.draw( index? );
```
>*returns: item*

Selects an item from the deck, either randomly or at a given index, and removes the item from the deck so that it won't be drawn again.

-

###look
```javascript
DECK.look( index? );
```
>*returns: item*

Selects an item from the deck, either randomly or at a given index, but leaves the item in the deck so that it may be looked at or drawn again.

-

###insert
```javascript
DECK.insert( item, index? );
```
Adds an item to the deck, either randomly or at a given index.

-

###shuffle
```javascript
DECK.shuffle();
```
Randomly shuffles the order of the deck contents.

-

###show
```javascript
DECK.show();
```
>*returns: item array*

Simply returns a list of the deck contents in their current state.

