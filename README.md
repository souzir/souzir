import pygame
from eng.ENGINE_PLAYER import Hero

pygame.init()

# ЭКРАН
Screen_Width = 1500
Screen_Height = 800
screen = pygame.display.set_mode((Screen_Width, Screen_Height))
pygame.display.set_caption("Наша Игра")
bg = pygame.image.load(r"C:\Users\Thunderobot\OneDrive\Рабочий стол\IMPORTANT\GAME\RESOURCES\Images\COIN.png")
BG = pygame.transform.scale(bg, (1500,  800))
# ЦВЕТА
white = (255, 255, 255)
black = (0, 0, 0)
red = (255, 0, 0)
blue = (0, 0, 255)

# СОЗДАНИЕ ГЕРОЯ
hero = Hero(Screen_Width // 2, Screen_Height // 2)  # Создаём героя один раз перед циклом

# Игровой ЦИКЛ
running = True
clock = pygame.time.Clock()

while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False 

    # Управление героем
    keys = pygame.key.get_pressed()
    hero.move(keys)

    # Обновление анимации
    hero.update_anim()

    # Отрисовка
    screen.fill(black)  # Очистка экрана
    screen.blit(BG, (0, 0)) # Позиция и отрисовка фона
    hero.draw(screen)  # Отрисовка героя

    # Обновление экрана
    pygame.display.flip()

    # Ограничение FPS
    clock.tick(60)

# Завершение работы
pygame.quit()
