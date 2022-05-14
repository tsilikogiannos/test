#README FILE 
#ALGORITHMICS SATURDAY LESSON

from pygame import *
from random import randint

class game_sprite(sprite.Sprite):
    def __init__(self,player_image, p_x, p_y,p_speed):
        super().__init__()
        self.image = transform.scale(image.load(player_image), (65, 65))
        self.speed = p_speed
        self.rect = self.image.get_rect()
        self.rect.x = p_x
        self.rect.y = p_y
    def reset(self):
        window.blit(self.image, (self.rect.x, self.rect.y))

class Hero(game_sprite):
    def update_r(self):
        keys = key.get_pressed()
        if keys[K_LEFT] and self.rect.x > 5:
            self.rect.x -= self.speed
        if keys[K_RIGHT] and self.rect.x < win_width - 80:
            self.rect.x += self.speed
    def update_l(self):
        keys = key.get_pressed()
        if keys[K_w] and self.rect.x > 5:
            self.rect.x -= self.speed
        if keys[K_s] and self.rect.x < win_width - 80:
            self.rect.x += self.speed
    
#game scene 
back=(200,255,255)
win_width = 600
win_height =500
window= display.set_mode=((win_width, win_height))
window.fill(back)

game = True
finish = False
clock = time.Clock()
FPS = 60
