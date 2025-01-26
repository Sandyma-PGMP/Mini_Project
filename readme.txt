TO FLIP A CARD
->To flip the card when clicked, a class flip is added to the element. For that, let’s select all memory-cardelements withdocument.querySelectorAll. Then loop through them wit forEach and attach an event listener. Every time a card gets clicked flipCard function will be fired. The this variable represents the card that was clicked. The function accesses the element’s classList and toggles the flip class:

To produce the 3D flip effect, we will add the [perspective] property to.memory-game. That property sets how far in thezplane the object is from the user. The lower the value the bigger the perspective effect. For a subtle effect, let’s apply1000px:

To the.memory-cardelements let’s addtransform-style: preserve-3d, to position them in the 3D space created in the parent, instead of flattening it to thez = 0plane ([transform-style])

 both.front-face and .back-face are stacked up onto each other, because they are absolutely positioned. Every element has aback face, which is a mirror image of itsfront face. The property [backface-visibility] defaults tovisible, so when we flip the card, what we get is the pattern back face.

MATCH CARDS


When we click the first card, it needs to wait until another card is flipped. The variableshasFlippedCardandflippedCardwill manage the flip state. In case there is no card flipped,hasFlippedCard is set to true and flippedCard is set to the clicked card. Let’s also switch the toggle method to add:

So now, when the user clicks the second card, we will fall into the else block in our condition. We will check to see if it’s a match. In order to do that, let’s identify each card.

Whenever we feel like adding extra information to HTML elements, we can make use of [data attributes]. By using the following syntax:data-, where,can be any word, that attribute will be inserted in the element’s dataset property. So, let’s add a data-emoji to each card:

So now we can check for a match by accessing both cards dataset. Let’s extract the matching logic to its own method checkForMatch()and also set hasFlippedCard back to false. In case of a match,disableCards()is invoked and the event listeners on both cards are detached, to prevent further flipping. Otherwise,unflipCards()will turn both cards back by a 1500ms timeout that removes the.flipclass:

SHUFFLE FUNCTION
When display: flex is declared on the container,flex-itemsare arranged by the following hierarchy: _group_ and _source_ order. Each group is defined by the [order] property, which holds a positive or negative integer. By default, each flex-item has its order property set to 0, which means they all belong to the same group and will be laid out by source order. If there is more than one group, elements are firstly arranged by ascending group order.

There is 12 cards in the game, so we will iterate through them, generate a random number between 0 and 12 and assign it to the flex-itemorderproperty:

In order to invoke the shuffle function, let’s make it a [Immediately Invoked Function Expression (IIFE)]