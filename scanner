import pygame
import random

pygame.init()

# Constants
SCREEN_WIDTH, SCREEN_HEIGHT = 640, 480
SNAKE_SIZE = 20
WHITE = (255, 255, 255)
RED = (255, 0, 0)

# Initialize screen
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
pygame.display.set_caption("Snake Game")

# Snake initial position and speed
snake_pos = [[100, 50]]
snake_speed = 10
snake_direction = 'RIGHT'

# Food initial position
food_pos = [random.randrange(1, SCREEN_WIDTH // SNAKE_SIZE) * SNAKE_SIZE,
            random.randrange(1, SCREEN_HEIGHT // SNAKE_SIZE) * SNAKE_SIZE]

# Main game loop
while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            quit()
        elif event.type == pygame.KEYDOWN:
            if event.key == pygame.K_UP and snake_direction != 'DOWN':
                snake_direction = 'UP'
            elif event.key == pygame.K_DOWN and snake_direction != 'UP':
                snake_direction = 'DOWN'
            elif event.key == pygame.K_LEFT and snake_direction != 'RIGHT':
                snake_direction = 'LEFT'
            elif event.key == pygame.K_RIGHT and snake_direction != 'LEFT':
                snake_direction = 'RIGHT'

    # Move the snake
    if snake_direction == 'UP':
        snake_pos[0][1] -= SNAKE_SIZE
    if snake_direction == 'DOWN':
        snake_pos[0][1] += SNAKE_SIZE
    if snake_direction == 'LEFT':
        snake_pos[0][0] -= SNAKE_SIZE
    if snake_direction == 'RIGHT':
        snake_pos[0][0] += SNAKE_SIZE

    # Check if the snake eats the food
    if snake_pos[0] == food_pos:
        food_pos = [random.randrange(1, SCREEN_WIDTH // SNAKE_SIZE) * SNAKE_SIZE,
                    random.randrange(1, SCREEN_HEIGHT // SNAKE_SIZE) * SNAKE_SIZE]
    else:
        snake_pos.pop()

    # Draw everything
    screen.fill(WHITE)
    for pos in snake_pos:
        pygame.draw.rect(screen, RED, pygame.Rect(pos[0], pos[1], SNAKE_SIZE, SNAKE_SIZE))
    pygame.draw.rect(screen, RED, pygame.Rect(food_pos[0], food_pos[1], SNAKE_SIZE, SNAKE_SIZE))

    pygame.display.flip()

    # Game over if snake hits the boundaries
    if snake_pos[0][0] >= SCREEN_WIDTH or snake_pos[0][0] < 0 or \
            snake_pos[0][1] >= SCREEN_HEIGHT or snake_pos[0][1] < 0:
        pygame.quit()
        quit()

    # Game over if snake collides with itself
    for block in snake_pos[1:]:
        if snake_pos[0] == block:
            pygame.quit()
            quit()

    pygame.time.Clock().tick(snake_speed)
