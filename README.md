# Single-Draw
import random

class tripDrawHand(object):

    drawsRem = 3


suitDictionary = {0:'clubs', 1:'diamonds', 2:'hearts', 3:'spades'}
#rankDictionary = {1:'ace', 2:'2', 3:'3', 4:'4',5:'5',6:'6',7
rankDictionary = {1:'ace',11:'jack',12:'queen',13:'king'}
class rsCard(object):

    def __init__(self, deckInteger):
        rsCard.suit = suitDictionary[(deckInteger-1)//13]
        rsCard.rank = deckInteger%13
        if rsCard.rank == 0:    'King'
            rsCard.rank = 13

        

#    def getCard(self):
#        return [rsCard.rank, rsCard.suit]
        



def rsHand(handList):     
    rsHand=[]
    if not handList:
        print('no cards!')
    else:
        for card in handList:
            cardByRank = rsCard(card)
            rsHand.append([cardByRank.rank, cardByRank.suit])
    return rsHand

        
def noPairVal(cards):
""" Returns a number between 0 and <1 representing the strength of
a no-pair hand. The idea is to allow for quick comparison and sorting.
The input, cards, is a list of integers from 1 to 52.
"""
    value = 0
    if not cards:
        return value
    else:
        cards.sort()
        for j in range(len(cards)):
            value = value + (cards[j])*100**(-j-1)
        return value

def unpairedRanks(cards):
    noPairList = []
    for card in cards:
        noPairList.append(card[0])
    noPairList = list(set(noPairList))
    return noPairList
    

if __name__ == '__main__':

    deck = [i+1 for i in range(52)]
    hand = random.sample(deck, 5)
    print(hand)
    firstCard = rsCard(hand[0])
    if firstCard.rank >1 and firstCard.rank <11:
        print(firstCard.rank, 'of', firstCard.suit)
    else:
        print(rankDictionary[firstCard.rank], 'of', firstCard.suit)
            
    fiveCards = rsHand(hand)
    print(fiveCards)
    lowballValue = noPairVal(unpairedRanks(fiveCards))
    print(lowballValue)
