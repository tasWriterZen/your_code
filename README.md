import pygame
import sys

# Initialize Pygame
pygame.init()

# Set up the screen
screen_width = 800
screen_height = 600
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Simple Pygame Example")

# Colors
black = (0, 0, 0)
white = (255, 255, 255)

# Player properties
player_size = 50
player_x = (screen_width - player_size) // 2
player_y = screen_height - player_size - 10
player_speed = 5

# Main game loop
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Get the state of all keys
    keys = pygame.key.get_pressed()
    
    # Update player position based on key presses
    if keys[pygame.K_LEFT]:
        player_x -= player_speed
    if keys[pygame.K_RIGHT]:
        player_x += player_speed
    if keys[pygame.K_UP]:
        player_y -= player_speed
    if keys[pygame.K_DOWN]:
        player_y += player_speed

    # Keep the player within the screen boundaries
    player_x = max(0, min(player_x, screen_width - player_size))
    player_y = max(0, min(player_y, screen_height - player_size))

    # Clear the screen
    screen.fill(black)

    # Draw the player
    pygame.draw.rect(screen, white, (player_x, player_y, player_size, player_size))

    # Update the display
    pygame.display.update()

# Quit Pygame
pygame.quit()
sys.exit()
