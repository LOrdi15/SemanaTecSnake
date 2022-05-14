# SemanaTecSnake

from random import randrange, choice
from turtle import *
from freegames import square, vector

#Definimos Vectores
food = vector(0, 0)
snake = [vector(10, 0)]
aim = vector(0, -10)
speed = 100
contador = 0
lista_mov_food = [vector(20,0), vector(-20,0), vector(0,20), vector(0,-20)]

#Definimos formato de juego
colores = ['green','red']
color_snake = choice(colores)
colores.remove(color_snake)
color_food = choice(colores)
colores.remove(color_food)
print(color_snake, color_food, colores)

def faster():
    global speed
    speed -= 1

def slower():
    global speed
    speed += 1

def change(x, y):
    """Change snake direction."""
    aim.x = x
    aim.y = y


def inside(head):
    """Return True if head inside boundaries."""
    return -200 < head.x < 190 and -200 < head.y < 190
        
