- 👋 Hi, I’m @Kartal77
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Kartal77/Kartal77 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->import random

# Define the deck of cards
suits = ['Hearts', 'Diamonds', 'Clubs', 'Spades']
ranks = ['Ace', '2', '3', '4', '5', '6', '7', '8', '9', '10', 'Jack', 'Queen', 'King']
deck = [(rank, suit) for rank in ranks for suit in suits]

# Shuffle the deck
random.shuffle(deck)

# Function to deal a card from the deck
def deal_card():
    return deck.pop()

# Function to calculate the value of a hand
def calculate_hand_value(hand):
    values = {
        'Ace': 11, '2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9, '10': 10, 'Jack': 10, 'Queen': 10, 'King': 10
    }
    hand_value = sum(values[card[0]] for card in hand)
    num_aces = sum(1 for card in hand if card[0] == 'Ace')

    while num_aces > 0 and hand_value > 21:
        hand_value -= 10
        num_aces -= 1

    return hand_value

# Start the game
player_hand = []
dealer_hand = []

player_hand.append(deal_card())
dealer_hand.append(deal_card())
player_hand.append(deal_card())
dealer_hand.append(deal_card())

# Game loop
game_over = False

while not game_over:
    player_score = calculate_hand_value(player_hand)
    dealer_score = calculate_hand_value(dealer_hand)

    print("Player's hand:", player_hand, "Value:", player_score)
    print("Dealer's hand:", dealer_hand[0])  # Show only one dealer card

    if player_score == 21 or dealer_score == 21:
        if player_score == 21:
            print("Player wins with Blackjack!")
        else:
            print("Dealer wins with Blackjack!")
        game_over = True
    else:
        choice = input("Do you want to 'hit' or 'stand'? ").lower()
        
        if choice == 'hit':
            player_hand.append(deal_card())
            player_score = calculate_hand_value(player_hand)

            if player_score > 21:
                print("Player busts! Dealer wins.")
                game_over = True
        elif choice == 'stand':
            while dealer_score < 17:
                dealer_hand.append(deal_card())
                dealer_score = calculate_hand_value(dealer_hand)

            print("Dealer's hand:", dealer_hand, "Value:", dealer_score)

            if dealer_score > 21:
                print("Dealer busts! Player wins.")
            elif dealer_score > player_score:
                print("Dealer wins.")
            elif dealer_score < player_score:
                print("Player wins.")
            else:
                print("It's a tie.")

            game_over = True
        else:
            print("Invalid choice. Please enter 'hit' or 'stand'.")

    print()# Define the card suits and ranks
suits = ['♠', '♥', '♦', '♣']
ranks = ['A', '2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K']

# Function to create the ASCII art representation of a card
def create_card_art(suit, rank):
    suit_symbols = {'♠': '♠', '♥': '♥', '♦': '♦', '♣': '♣'}
    rank_symbols = {'A': 'A', 'K': 'K', 'Q': 'Q', 'J': 'J', '10': '10'}

    # Top border of the card
    top_border = '┌─────────┐'

    # Middle rows of the card
    suit_rank_row = f'│ {rank_symbols.get(rank, rank):<2}{suit_symbols[suit]}       │'
    rank_row = '│         │'
    suit_row = f'│    {suit_symbols[suit]}    │'
    rank_suit_row = '│         │'
    bottom_border = '└─────────┘'

    # Combine all rows to create the card art
    card_art = [top_border, suit_rank_row, rank_row, suit_row, rank_suit_row, bottom_border]

    return card_art

# Generate and display card art for each card in a deck
for suit in suits:
    for rank in ranks:
        card_art = create_card_art(suit, rank)

        # Add a border around the card art
        bordered_card_art = ['╔═════════╗']
        for row in card_art:
            bordered_card_art.append(f'║{row}║')
        bordered_card_art.append('╚═════════╝')

        # Print the bordered card art
        for row in bordered_card_art:
            print(row)
        print()
# Initialize the score variable
score = 0

# Function to add points to the score
def add_points(points):
    global score
    score += points

# Function to subtract points from the score
def subtract_points(points):
    global score
    score -= points

# Function to reset the score to zero
def reset_score():
    global score
    score = 0

# Example usage:
add_points(10)  # Add 10 points to the score
print("Current score:", score)  # Print the current score

subtract_points(5)  # Subtract 5 points from the score
print("Current score:", score)  # Print the updated score

reset_score()  # Reset the score to zero
print("Current score:", score)  # Print the reset score

# Define the card suits and ranks
suits = ['♠', '♥', '♦', '♣']
ranks = ['A', '2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K']

# Function to create the ASCII art representation of a card
def create_card_art(suit, rank):
    suit_symbols = {'♠': '♠', '♥': '♥', '♦': '♦', '♣': '♣'}
    rank_symbols = {'A': 'A', 'K': 'K', 'Q': 'Q', 'J': 'J', '10': '10'}

    # Top border of the card
    top_border = '┌─────────┐'

    # Middle rows of the card
    suit_rank_row = f'│ {rank_symbols.get(rank, rank):<2}       │'
    rank_row = '│         │'
    suit_row = f'│    {suit_symbols[suit]}    │'
    rank_suit_row = '│         │'
    bottom_border = '└─────────┘'

    # Combine all rows to create the card art
    card_art = [top_border, suit_rank_row, rank_row, suit_row, rank_suit_row, bottom_border]

    return card_art

# Generate and display card art for each card in a deck
for suit in suits:
    for rank in ranks:
        card_art = create_card_art(suit, rank)

        # Add a border around the card art
        bordered_card_art = ['╔═════════╗']
        for row in card_art:
            bordered_card_art.append(f'║{row}║')
        bordered_card_art.append('╚═════════╝')

        # Print the bordered card art with decorative characters
        print('┏━━━━━━━━━┓')
        for i, row in enumerate(bordered_card_art):
            if i == 2:
                print(f'┃ {rank:<2}     ┃')
            elif i == 3:
                print(f'┃    {suit}    ┃')
            else:
                print(row)
        print('┗━━━━━━━━━┛')
        print()

import pygame

# Initialize the pygame module
pygame.init()

# Load the music file
pygame.mixer.music.load('music_file.mp3')

# Play the music
pygame.mixer.music.play()

# Add a delay to allow the music to play
pygame.time.delay(5000)  # Milliseconds (5 seconds in this example)

# Stop the music
pygame.mixer.music.stop()

# Quit the pygame module
pygame.quit()

import pygame

# Initialize the pygame module
pygame.init()

# Load the winning applause sound
winning_sound = pygame.mixer.Sound('winning_sound.wav')

# Load the losing "ha" sound
losing_sound = pygame.mixer.Sound('losing_sound.wav')

# Function to play the winning applause sound
def play_winning_sound():
    winning_sound.play()

# Function to play the losing "ha" sound
def play_losing_sound():
    losing_sound.play()

# Example usage:
play_winning_sound()  # Play the winning applause sound
pygame.time.delay(5000)  # Delay for 5 seconds
play_losing_sound()  # Play the losing "ha" sound

# Quit the pygame module
pygame.quit()
import time

# Function to animate text with delay between each character
def animate_text(text, delay):
    for char in text:
        print(char, end='', flush=True)
        time.sleep(delay)
    print()

# Example usage:
animate_text("Welcome to the game!", 0.1)  # Animate the text with a delay of 0.1 seconds between each character
class Colors:
    RED = '\033[91m'
    GREEN = '\033[92m'
    YELLOW = '\033[93m'
    BLUE = '\033[94m'
    END = '\033[0m'

# Function to print colored text
def print_colored_text(text, color):
    print(f'{color}{text}{Colors.END}')

# Example usage:
print_colored_text("This text is in red", Colors.RED)
print_colored_text("This text is in green", Colors.GREEN)
import time

# Function to animate text with delay between each character
def animate_text(text, delay):
    for char in text:
        print(char, end='', flush=True)
        time.sleep(delay)
    print()

# Example usage:
animate_text("Welcome to the game!", 0.1)  # Animate the text with a delay of 0.1 seconds between each character
class Colors:
    RED = '\033[91m'
    GREEN = '\033[92m'
    YELLOW = '\033[93m'
    BLUE = '\033[94m'
    END = '\033[0m'

# Function to print colored text
def print_colored_text(text, color):
    print(f'{color}{text}{Colors.END}')

# Example usage:
print_colored_text("This text is in red", Colors.RED)
print_colored_text("This text is in green", Colors.GREEN)
import pygame

# Initialize the pygame module
pygame.init()

# Load the winning applause sound
winning_sound = pygame.mixer.Sound('winning_sound.wav')



# Function to play the winning applause sound
def play_winning_sound():
    winning_sound.play()



# Example usage:
play_winning_sound()  # Play the winning applause sound
pygame.time.delay(5000)  # Delay for 5 seconds
play_losing_sound()  # Play the losing "ha" sound

# Quit the pygame module
pygame.quit()
# Function to send an invitation to a friend
def send_invitation(friend_name):
    print(f"Inviting {friend_name} to play the game!")

# Function to check if the user wants to send an invitation
def check_send_invitation():
    response = input("Do you want to invite a friend to play? (yes/no): ")
    if response.lower() == "yes":
        friend_name = input("Enter your friend's name: ")
        send_invitation(friend_name)
    else:
        print("Okay, maybe next time!")

# Example usage:
check_send_invitation()  # Check if the user wants to send an invitation
from PIL import Image, ImageDraw

# Set the size of the image
image_width = 800
image_height = 600

# Create a blank image with a white background
image = Image.new('RGB', (image_width, image_height), color='white')
draw = ImageDraw.Draw(image)

# Draw a landscape image using various shapes and colors
draw.rectangle((0, 0, image_width, image_height), fill=(0, 128, 0))  # Green background
draw.rectangle((0, image_height // 2, image_width, image_height), fill=(135, 206, 250))  # Light blue sky
draw.rectangle((0, image_height // 2, image_width, image_height // 2 + 100), fill=(244, 164, 96))  # Sandy ground
draw.ellipse((100, 100, 300, 300), fill=(255, 255, 0))  # Yellow sun
draw.polygon([(400, image_height // 2), (550, 250), (700, image_height // 2)], fill=(0, 128, 0))  # Green hill

# Save the image as a file
image.save('landscape.png')

# Show the image
image.show()
class Chair:
    def __init__(self, chair_number):
        self.chair_number = chair_number

    def sit(self):
        print(f"Chair {self.chair_number}: Someone is sitting on me.")

    def stand_up(self):
        print(f"Chair {self.chair_number}: Someone stood up from me.")


class Table:
    def __init__(self):
        self.chairs = [Chair(1), Chair(2), Chair(3), Chair(4)]

    def occupy_chair(self, chair_number):
        if 1 <= chair_number <= 4:
            self.chairs[chair_number - 1].sit()
        else:
            print("Invalid chair number.")

    def vacate_chair(self, chair_number):
        if 1 <= chair_number <= 4:
            self.chairs[chair_number - 1].stand_up()
        else:
            print("Invalid chair number.")


# Create a table with chairs
table = Table()

# Example usage:
table.occupy_chair(2)  # Someone sits on chair 2
table.vacate_chair(2)  # Someone stands up from chair 2
import pygame

# Initialize the pygame module
pygame.init()

# Load the drum sound
drum_sound = pygame.mixer.Sound('drum_sound.wav')

# Function to play the drum sound
def play_drum_sound():
    drum_sound.play()

# Example usage:
play_drum_sound()  # Play the drum sound

# Quit the pygame module
pygame.quit()
import pygame
import random

# Initialize the pygame module
pygame.init()

# Load explosion sound effects
explosion_sounds = [
    pygame.mixer.Sound('explosion1.wav'),
    pygame.mixer.Sound('explosion2.wav'),
    pygame.mixer.Sound('explosion3.wav')
]

# Load lightning images
lightning_images = [
    pygame.image.load('lightning1.png'),
    pygame.image.load('lightning2.png'),
    pygame.image.load('lightning3.png')
]

# Function to play a random explosion sound effect
def play_random_explosion_sound():
    random.choice(explosion_sounds).play()

# Function to display a random lightning image on the screen
def display_random_lightning_image(screen, screen_width, screen_height):
    lightning_image = random.choice(lightning_images)
    x = random.randint(0, screen_width - lightning_image.get_width())
    y = random.randint(0, screen_height - lightning_image.get_height())
    screen.blit(lightning_image, (x, y))
    pygame.display.flip()

# Example usage:
play_random_explosion_sound()  # Play a random explosion sound effect
display_random_lightning_image(screen, screen_width, screen_height)  # Display a random lightning image on the screen

# Quit the pygame module
pygame.quit()
import pygame

# Initialize the pygame module
pygame.init()

# Set the screen size
screen_width = 800
screen_height = 600

# Create the game window
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Card Game")

# Load the card images
card_images = {
    'Ace': pygame.image.load('ace.png'),
    'King': pygame.image.load('king.png'),
    'Queen': pygame.image.load('queen.png'),
    'Jack': pygame.image.load('jack.png')
}

# Function to draw a card on the screen
def draw_card(card_name, x, y):
    card_image = card_images[card_name]
    screen.blit(card_image, (x, y))
    pygame.display.update()

# Example usage:
draw_card('Ace', 100, 100)  # Draw an Ace card at position (100, 100)

# Game loop
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

# Quit the pygame module
pygame.quit()
import pygame

# Initialize the pygame module
pygame.init()

# Set the screen size
screen_width = 800
screen_height = 600

# Set the button size and position
button_width = 200
button_height = 100
button_x = (screen_width - button_width) // 2
button_y = (screen_height - button_height) // 2

# Set the colors
background_color = (255, 255, 255)
button_color = (0, 128, 255)
button_hover_color = (0, 0, 255)

# Create the game window
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Game")

# Function to draw the button
def draw_button():
    pygame.draw.rect(screen, button_color, (button_x, button_y, button_width, button_height))
    font = pygame.font.SysFont(None, 48)
    text = font.render("Start Game", True, (255, 255, 255))
    text_rect = text.get_rect(center=(button_x + button_width / 2, button_y + button_height / 2))
    screen.blit(text, text_rect)

# Game loop
running = True
while running:
    screen.fill(background_color)
    draw_button()
    pygame.display.update()

    # Event handling
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        elif event.type == pygame.MOUSEMOTION:
            mouse_pos = pygame.mouse.get_pos()
            if button_x <= mouse_pos[0] <= button_x + button_width and button_y <= mouse_pos[1] <= button_y + button_height:
                button_color = button_hover_color
            else:
                button_color = (0, 128, 255)
        elif event.type == pygame.MOUSEBUTTONDOWN:
            mouse_pos = pygame.mouse.get_pos()
            if button_x <= mouse_pos[0] <= button_x + button_width and button_y <= mouse_pos[1] <= button_y + button_height:
                print("Game started!")

# Quit the pygame module
pygame.quit()
