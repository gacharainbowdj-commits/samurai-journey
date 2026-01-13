# samurai-journey
HTML5 RPG Game
# Text-based adventure game: Samurai's Journey
def display_intro():
    print("""
    -----------------------------------
    Welcome to "The Samurai's Journey"
    -----------------------------------
    In ancient Japan, you are a brave samurai tasked with protecting your village.
    A mysterious curse has fallen upon your land, and only the Sacred Katana can lift it.
    To find the katana, you must journey through the haunted forest, climb Mount Fuji, 
    and face mythical creatures.
    """)
    
def haunted_forest():
    print("\nYou enter the haunted forest. The trees whisper, and the air feels heavy.")
    print("A fox spirit (kitsune) appears, blocking your path.")
    choice = input("Do you (1) Bow respectfully or (2) Draw your sword? Enter 1 or 2: ")
    
    if choice == "1":
        print("\nThe kitsune nods and grants you safe passage, gifting you a charm for protection.")
        return True  # Proceed safely
    elif choice == "2":
        print("\nThe kitsune becomes enraged, and you are forced to retreat. You lose time.")
        return False  # Setback
    else:
        print("\nInvalid choice. The kitsune disappears, leaving you confused. Try again.")
        return haunted_forest()

def mount_fuji():
    print("\nYou reach the base of Mount Fuji. The path ahead is treacherous.")
    print("A tengu (mountain spirit) challenges you to a duel of wits.")
    riddle = input("The tengu asks: 'I speak without a mouth and hear without ears. What am I?': ")
    
    if riddle.lower() == "echo":
        print("\nThe tengu is impressed by your wisdom and clears the path for you.")
        return True  # Pass the challenge
    else:
        print("\nThe tengu laughs and sends you back down the mountain. You lose time.")
        return False  # Setback

def final_challenge():
    print("\nYou reach the Sacred Shrine at the summit.")
    print("A dragon emerges, guarding the Sacred Katana. It demands proof of your worth.")
    choice = input("Do you (1) Offer the charm from the kitsune or (2) Fight the dragon? Enter 1 or 2: ")
    
    if choice == "1":
        print("\nThe dragon recognizes your wisdom and bravery. It grants you the katana.")
        print("You return to your village and lift the curse. Victory is yours!")
        return True  # Win the game
    elif choice == "2":
        print("\nYou fight valiantly, but the dragon is too powerful. You are defeated.")
        return False  # Lose the game
    else:
        print("\nInvalid choice. The dragon grows impatient. Try again.")
        return final_challenge()

def play_game():
    display_intro()
    if haunted_forest():
        if mount_fuji():
            if final_challenge():
                print("\nCongratulations, Samurai! You have completed your journey and saved your village.")
            else:
                print("\nYou failed the final challenge. Your village remains under the curse.")
        else:
            print("\nYou failed to pass Mount Fuji. Your journey ends here.")
    else:
        print("\nYou failed to pass the haunted forest. Your journey ends here.")

# Run the game
play_game()
# ==============================
# SAMURAI'S JOURNEY – CHAPTER 2
# ==============================

inventory = []
player_health = 100

def show_status():
    print("\n-----------------------")
    print("Health:", player_health)
    print("Inventory:", inventory)
    print("-----------------------")

def village_elder():
    print("\nYou return to your village.")
    print("The Elder looks worried.")
    print("\nElder: 'The curse has grown stronger.'")
    print("Elder: 'Kuro-Oni sleeps beneath Aokigahara Forest.'")
    print("Elder: 'You must collect the THREE SPIRIT SEALS.'")

def forest_challenge():
    global player_health
    print("\nYou enter Aokigahara Forest.")
    print("A restless Yurei (ghost) appears!")

    choice = input("Do you (1) Pray or (2) Attack? ")

    if choice == "1":
        print("\nThe Yurei calms down and vanishes.")
        print("You receive the Spirit Seal of Compassion.")
        inventory.append("Compassion Seal")
    else:
        print("\nThe Yurei attacks you!")
        player_health -= 20
        print("You defeat it, but you are wounded.")
        inventory.append("Compassion Seal")

def shrine_challenge():
    global player_health
    print("\nYou reach an Abandoned Shrine.")
    print("An Onryo Priest blocks your path!")

    answer = input("Solve the riddle to purify him.\n"
                   "'What shines but has no light?' ")

    if answer.lower() == "wisdom":
        print("\nThe priest bows and fades peacefully.")
        print("You receive the Spirit Seal of Faith.")
        inventory.append("Faith Seal")
    else:
        print("\nWrong answer! The priest attacks!")
        player_health -= 25
        print("You defeat him after a fierce battle.")
        inventory.append("Faith Seal")

def mountain_cave():
    global player_health
    print("\nYou enter the Mountain Cave of Echoes.")
    print("A Tengu warrior challenges you.")

    choice = input("Do you (1) Accept duel or (2) Show respect? ")

    if choice == "2":
        print("\nThe Tengu respects your humility.")
        print("You receive the Spirit Seal of Balance.")
        inventory.append("Balance Seal")
    else:
        print("\nThe duel is fierce!")
        player_health -= 30
        print("You win through strength.")
        inventory.append("Balance Seal")

def kuro_oni_final():
    print("\nDark clouds gather...")
    print("Kuro-Oni awakens!")

    if len(inventory) == 3:
        print("\nYou use all three Spirit Seals.")
        print("Kuro-Oni is purified!")
        print("\n🏆 TRUE ENDING: You saved Japan.")
    else:
        print("\nYou lack the Spirit Seals.")
        print("You defeat Kuro-Oni, but darkness remains.")
        print("\n🔥 BITTERSWEET ENDING.")

def play_chapter_2():
    village_elder()
    show_status()

    forest_challenge()
    show_status()

    shrine_challenge()
    show_status()

    mountain_cave()
    show_status()

    kuro_oni_final()

# START CHAPTER 2
play_chapter_2()

