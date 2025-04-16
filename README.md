import turtle
import random


t = turtle.Turtle()


t.speed(10)  
t.hideturtle()


screen = turtle.Screen()
screen.bgcolor("darkblue")

screen.setup(width=600, height=600)

t.clear()

def draw_polygon(t, sides, length):
    angle = 360 / sides
    for _ in range(sides):
        t.forward(length)
        t.left(angle)


def draw_pumpkin(t, x, y, radius):
    t.penup()
    t.goto(x, y)
    t.pendown()
    t.fillcolor("orange")
    t.begin_fill()
    t.circle(radius)
    t.end_fill()


    t.fillcolor("green")
    t.begin_fill()
    t.left(80)
    t.forward(radius // 2)
    t.left(80)
    t.forward(radius // 5)
    t.left(80)
    t.forward(radius // 2)
    t.left(80)
    t.forward(radius // 5)
    t.end_fill()

def draw_eye(t, x, y, size):
    t.penup()
    t.goto(x, y)
    t.pendown()
    t.fillcolor("yellow")
    t.begin_fill()
    draw_polygon(t, 3, size)
    t.end_fill()

def draw_mouth(t, x, y, width):
    t.penup()
    t.goto(x, y)
    t.pendown()
    t.fillcolor("yellow")
    t.begin_fill()
    for _ in range(5):
        t.forward(width // 5)
        t.left(100)
        t.forward(width // 5)
        t.right(100)
    t.end_fill()


draw_pumpkin(t, 0, -300, 150)  # Draw the pumpkin
draw_eye(t, -40, -30, 30)  # Left eye
draw_eye(t, 45, -45, 30)  # Right eye
draw_mouth(t,  -150, -100, 200)  # Mouth

def draw_star(t, x, y, size):
    t.penup()
    t.goto(x, y)
    t.pendown()
    t.fillcolor("white")
    t.begin_fill()
    for _ in range(5):
        t.forward(size)
        t.right(144)
    t.end_fill()
def draw_sky(t, num_stars):

    for _ in range(num_stars):
        x = random.randint(-300, 300)
        y = random.randint(150, 300)
        size = random.randint(15, 35)
        draw_star(t, x, y, size)



draw_star(t, 0, 150, 30)
draw_star(t, 0, 180, 20)


draw_pumpkin(t, -300, -250, 175)
draw_eye(t, -270, 10, 30)
draw_eye(t, -200, -10, 30)
draw_mouth(t, -250, -60, 125)

draw_pumpkin(t, 50, -180, 150)
draw_eye(t, 130, -120, 25)
draw_eye(t, 120, -40, 25)
draw_mouth(t, 175, -100, 100)

draw_pumpkin(t, -200, -170, 150)
draw_eye(t, -100, -200, 30)
draw_eye(t, -60, -130, 30)
draw_mouth(t, -20, -160, 200)


draw_sky(t, 30)


turtle.exitonclick()
