import pygame
import sys

# Initialize Pygame
pygame.init()

# Constants
WIDTH, HEIGHT = 800, 600
WHITE = (255, 255, 255)
AIRPLANE_SPEED = 5

# Create the game window
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Aviator Game")

# Load assets
background = pygame.image.load("background.jpg")
airplane = pygame.image.load("airplane.png")

# Initial position of the airplane
airplane_x = WIDTH // 2 - airplane.get_width() // 2
airplane_y = HEIGHT - airplane.get_height()

# Main game loop
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        airplane_x -= AIRPLANE_SPEED
    if keys[pygame.K_RIGHT]:
        airplane_x += AIRPLANE_SPEED

    # Drawing
    screen.blit(background, (0, 0))
    screen.blit(airplane, (airplane_x, airplane_y))

    pygame.display.update()

# Quit the game
pygame.quit()
sys.exit()
