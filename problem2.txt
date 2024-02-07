# Revision number 02/07/2024
## Begin Talha Ali (02/07/2024) 

import random

# Populate treasure chest with items
def populate_treasure_chest(num_items):
    items = ['Gold Coin', 'Silver Coin', 'Crown Jewel', 'Silver Ring', 'Gold Necklace', 'Precious Gem', 'Silver Goblet']
    return random.choices(items, k=num_items)

# Main game function
def pirate_game():
    treasure_chest = populate_treasure_chest(20)  # Populate with 20 items
    bank_account = 100  # Starting bank account
    print("Welcome to the Pirate's Game of Chance!")

    while bank_account > 0 and treasure_chest:
        print(f"\nYour bank account has {bank_account} doubloons.")
        wager = int(input("How many doubloons do you want to wager on your grab? "))
        
        if wager > bank_account:
            print("You don't have enough doubloons to make that wager. Try again.")
            continue
        
        grabbed_item = treasure_chest.pop()
        print(f"You grabbed a {grabbed_item} from the treasure chest!")

        if "Gold" in grabbed_item:
            print("Yarrr! You struck gold! You win double your wager.")
            bank_account += 2 * wager
        else:
            print("Arrr! No gold this time. You lose your wager.")
            bank_account -= wager
        
        if bank_account <= 0:
            print("Alas, you've run out of doubloons! The game is over.")
            break

        if not treasure_chest:
            print("The treasure chest is empty! The game is over.")
            break

# Run the game
pirate_game()


# Revision number 02/07/2024
## End Talha Ali
# SE1 Group 3