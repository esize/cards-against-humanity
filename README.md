# Cards Against Humanity Clone

## Tech Stack:

- React
- JWT
- Express
- Socket.io
- MongoDB

## Features:

- [ ] Enter a nickname
- [ ] Create a room
- [ ] Generates room code
- [ ] Select room options
- [ ] Join a room using room code
- [ ] Start the game
- [ ] Everyone is dealt 10 white cards
- [ ] Everyone is asked when they last pooped
- [ ] Card Czar order is generated with the person who pooped last going first
- [ ] A black card is choosen and displayed to all players
- [ ] Players can choose a card (Card Czar's cards are disabled)
- [ ] When all cards are submitted, the Czar chooses a card
- [ ] The person who played the winning card gets to keep the black card
- [ ] All white cards played are transferred to the discard pile
- [ ] Everyone's cards are replenished to 10
- [ ] Repeat the process
- [ ] Handle pick 2 cards
- [ ] Ending the game (based on options):
- [ ] All black cards have been played, so the haiku card ends the game
- [ ] A majority of players agree to stop the game
- [ ] Someone gets 5 black cards
- [ ] Tally the points and declare a winner
- [ ] Rando Cardrissian Mode
- [ ] Wheaton's Law Mode

## Backend Calls:

- [ ] Create a room: {nickname, rando?, wheaton? endGame}
- [ ] Join a room: {roomId, nickname}
- [ ] Start the game: {roomId, authHeader}
- [ ] Last poop time: {roomId, authHeader, poopTime}
- [ ] Play Card: {roomId, authHeader, [cardText]}
- [ ] Choose winning card: {roomId, authHeader, cardText}
- [ ] End game: {roomId, authHeader}
- [ ] Confirm end game: {roomId, authHeader}

## Backend Responses:

- [ ] roomCreated: {roomId, jwt}
- [ ] roomJoined: {roomId, players:[nickname]}
- [ ] newPlayer: (nickname)
- [ ] askPoop
- [ ] startRound: {czarNickname, blackCardText, [cards]}
- [ ] playerCardChoosen
- [ ] allCardsIn: [roundCards]- [ ] winningCardChoosen: {cardText, nickname}
- [ ] endGameInitiated
- [ ] gameEnded[{nickname, blackCards[cardText]}]

## DB Structure

```js
{
  [roomID]: {
    whiteDrawPile: [
      cardText
    ],
    blackDrawPile: [
      {
        text,
        pick: (1 | 2)
      }
    ],
    whiteDiscardPile: [
      cardText
    ],
    owner: playerId,
    poopOrder: [
      playerId
    ],
    players: [
      {
        id,
        socketId,
        nickname,
        blackCards: [
        {
          text,
          pick: (1 | 2)
        }
        ],
        whiteCards: [
          cardText
        ]
      }
    ]
    disconnectedPlayers [
      {
        id,
        socketId,
        nickname,
        blackCards: [
          {
            text,
            pick: (1 | 2)
          }
        ],
        whiteCards: [
          cardText
        ]
      }
    ]
  }
}
```
