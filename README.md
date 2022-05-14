# SemanaTecSnake
# Enlace 
[GIF PRUEBA](https://makeagif.com/i/qdqSwi)

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
        
def move():
    """Move snake forward one segment."""
    global contador
    contador += 1
    head = snake[-1].copy()
    head.move(aim)

   if not inside(head) or head in snake:
        square(head.x, head.y, 9, 'red')
        update()
        return
    snake.append(head)
   if head == food:
        print('Snake:', len(snake))
        food.x = randrange(-15, 15) * 10
        food.y = randrange(-15, 15) * 10
    else:
        snake.pop(0)

   clear()
    for body in snake:
        square(body.x, body.y, 9, 'black')
    square(food.x, food.y, 9, 'green')
    update()
    ontimer(move, 100)


setup(420, 420, 370, 0)
hideturtle()
tracer(False)
listen()
onkey(lambda: change(10, 0), 'Right')
onkey(lambda: change(-10, 0), 'Left')
onkey(lambda: change(0, 10), 'Up')
onkey(lambda: change(0, -10), 'Down')
move()
done()

