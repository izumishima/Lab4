import turtle
import random

# Create a turtle object
t = turtle.Turtle()

# Hide the turtle and set speed
t.speed(10)  # 1 is slow, 10 is fast, 0 is instant
t.hideturtle()

# Create a window to draw in
# Create a new turtle screen and set its background color
screen = turtle.Screen()
screen.bgcolor("darkblue")
# Set the width and height of the screen
screen.setup(width=600, height=600)
# Clear the screen
t.clear()

def draw_polygon(t, sides, length):
    """Draws a regular polygon with a given number of sides and side length."""
    angle = 360 / sides
    for _ in range(sides):
        t.forward(length)
        t.left(angle)


def draw_pumpkin(t, x, y, radius):
    """Draws a pumpkin (orange circle) at the given (x, y) location with a green stem."""
    t.penup()
    t.goto(x, y)
    t.pendown()
    t.fillcolor("orange")
    t.begin_fill()
    t.circle(radius)
    t.end_fill()

    # Drawing the stem
    t.fillcolor("green")
    t.begin_fill()
    t.left(80)  # Point upwards
    t.forward(radius // 2)
    t.left(80)
    t.forward(radius // 5)
    t.left(80)
    t.forward(radius // 2)
    t.left(80)
    t.forward(radius // 5)
    t.end_fill()

def draw_eye(t, x, y, size):
    """Draws one triangular eye at the given (x, y) position."""
    t.penup()
    t.goto(x, y)
    t.pendown()
    t.fillcolor("yellow")
    t.begin_fill()
    draw_polygon(t, 3, size)
    t.end_fill()

def draw_mouth(t, x, y, width):
    """Draws a jagged mouth using a series of connected lines."""
    t.penup()
    t.goto(x, y)
    t.pendown()
    t.fillcolor("yellow")
    t.begin_fill()
    for _ in range(5):  # Create a simple zigzag mouth
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
    """Draws a star at the given (x, y) position."""
    t.penup()
    t.goto(x, y)
    t.pendown()
    t.fillcolor("white")
    t.begin_fill()
    for _ in range(5):
        t.forward(size)
        t.right(144)  # 144 degrees is the angle to form a star
    t.end_fill()
def draw_sky(t, num_stars):
    """Draws a starry sky with the given number of stars."""
    for _ in range(num_stars):
        x = random.randint(-300, 300)
        y = random.randint(150, 300)
        size = random.randint(15, 35)
        draw_star(t, x, y, size)


# Example usage
draw_star(t, 0, 150, 30)  # Star in the sky
draw_star(t, 0, 180, 20)

# Draw three jack-o-lanterns
draw_pumpkin(t, -300, -250, 175)
draw_eye(t, -270, 10, 30)  # Left eye
draw_eye(t, -200, -10, 30)  # Right eye
draw_mouth(t, -250, -60, 125)  # Mouth

draw_pumpkin(t, 50, -180, 150)
draw_eye(t, 130, -120, 25)
draw_eye(t, 120, -40, 25)
draw_mouth(t, 175, -100, 100)

draw_pumpkin(t, -200, -170, 150)
draw_eye(t, -100, -200, 30)
draw_eye(t, -60, -130, 30)
draw_mouth(t, -20, -160, 200)

# Draw the night sky
draw_sky(t, 30)

# Close the turtle graphics window when clicked
turtle.exitonclick()
