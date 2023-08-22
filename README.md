# BlackjackGame.py
Blackjack 

import random

deck = [2, 3, 4, 5, 6, 7, 8, 9, 10, 2, 3, 4, 5, 6, 7, 8, 9, 10, 2, 3, 4, 5, 6, 7, 8, 9, 10, 2, 3, 4, 5, 6, 7, 8, 9, 10,'J', 'Q', 'K', 'A' ,'J', 'Q', 'K', 'A','J', 'Q', 'K', 'A','J', 'Q', 'K', 'A' ]

playerHand = []
dealerHand =[]

playerIn = True 
dealerIn = True

def dealCard(turn):
    card = random.choice(deck)
    turn.append(card)
    deck.remove(card)

for _ in range (2):
    dealCard(dealerHand)
    dealCard(playerHand)

def total(turn):
    total = 0
    face = ['A', 'K', 'Q', 'J']
    ace_11 = 0
    for card in turn:
        if card in range (1,11):
            total += card
        elif card in ['K', 'Q', 'J']:
            total += 10
        else:
            total += 11
            ace_11 += 1
    while ace_11 and total > 21:
            total -= 10 
            ace_11 -= 1
    return total
def  reveal_dealer_hand():
    if len(dealerHand) == 2:
        return dealerHand[0]
    if len(dealerHand) > 2:
        return dealerHand[0] , dealerHand[1]

while dealerIn or playerIn:
    print(f"Dealer had a hand of {reveal_dealer_hand()} and X card")
    print(f"You have a hand of {playerHand} for a total of {total(playerHand)}")
    if playerIn:
        stay_or_hit = input("Stay or hit:\n1. Stay\n2. Hit")
    if total(dealerHand) >= 17:
        dealerIn = False
    else: 
        dealCard(dealerHand)
    if stay_or_hit == '1':
        playerIn = False
    
    
    if stay_or_hit == '2':
        dealCard(playerHand)
        print(f"You have a hand of {playerHand} for a total of {total(playerHand)}")
        stay_or_hit = input("Stay or hit:\n1. Stay\n2. Hit")
    
    
    if total(dealerHand) >= 21:
        break
        dealerIn = False
    elif total(playerHand) >= 21:
        break
        playerIn = False

    
if total(playerHand) == 21:
            print(f"\nYou have {playerHand} for a total of {total(playerHand)} and the dealer had a hand of {dealerHand} for a total of {total(dealerHand)}")
            print(f"\nBlackjack! You win!")
elif total(dealerHand) == 21:
            print(f"\nYou have {playerHand} for a total of {total(playerHand)} and the dealer had a hand of {dealerHand} for a total of {total(dealerHand)}")
            print(f"\nYou lose! Dealer has blackjack!")
elif total(playerHand) > 21:
            print(f"\nYou have {playerHand} for a total of {total(playerHand)} and the dealer had a hand of {dealerHand} for a total of {total(dealerHand)}")
            print(f"\nYou bust! Dealer wins!")
elif total(dealerHand) > 21:
            print(f"\nYou have {playerHand} for a total of {total(playerHand)} and the dealer had a hand of {dealerHand} for a total of {total(dealerHand)}")
            print(f"\nDealer busts! You win!")
elif 21 - total(playerHand) < 21 - total(dealerHand):
            print(f"\nYou have {playerHand} for a total of {total(playerHand)} and the dealer had a hand of {dealerHand} for a total of {total(dealerHand)}")
            print(f"You win!")
elif 21 - total(dealerHand) < 21 - total(playerHand):
            print(f"\nYou have {playerHand} for a total of {total(playerHand)} and the dealer had a hand of {dealerHand} for a total of {total(dealerHand)}")
            print(f"Dealer wins!")
        
