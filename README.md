

# Define elements and their strengths
elements = {
    "Fire": "Air",
    "Water": "Fire",
    "Earth": "Water",
    "Air": "Earth"
}

# Player class
class Player:
    def __init__(self, name, element):
        self.name = name
        self.element = element
        self.health = 3  # Each player has 3 lives

    def attack(self, opponent):
        print(f"\n{self.name} attacks {opponent.name} using {self.element}!")
        if elements[self.element] == opponent.element:
            print(f"Super effective! {opponent.name} loses a life!")
            opponent.health -= 1
        else:
            print(f"It’s not very effective... {opponent.name} takes no damage.")

# Game Setup
print("Welcome to Element Clash!")
name1 = input("Player 1, enter your name: ")
name2 = input("Player 2, enter your name: ")

print("\nChoose your element: Fire, Water, Earth, or Air.")
player1 = Player(name1, input(f"{name1}, choose your element: ").capitalize())
player2 = Player(name2, input(f"{name2}, choose your element: ").capitalize())

# Main Game Loop
while player1.health > 0 and player2.health > 0:
    player1.attack(player2)
    if player2.health <= 0:
        print(f"\n{player2.name} has been defeated! {player1.name} wins!")
        break

    player2.attack(player1)
    if player1.health <= 0:
        print(f"\n{player1.name} has been defeated! {player2.name} wins!")
        break

    print(f"\n{player1.name} has {player1.health} health left.")
    print(f"{player2.name} has {player2.health} health left.")

print("\nGame Over!")
