
# Practice: Pygame Bouncing Circle Class

## Objective

> *In this project, you'll define and use a Python class to create an animated circle.*
>
> *Your class will contain two attributes, the constructor method, a move method, and a draw method*


## Sample Output

![Bouncing Circles class output](https://github.com/nwct-programming/nwct-programming-bouncing-circle-class-bouncing-circle-class/blob/e02c27f8fa3aa6dd3b389afccfa5c7ed4f5b820e/bouncing-circles-output.png)



## Project Tasks

- Import these modules into your `main.py` file:
  - pygame
  - sys
  - random
  - config
- Define a class named `Circle`

---

### The constructor ( ) method

- Will take three parameters: `self, radius, color`
- Add two attributes to your class: `radius` and `color`
- Then add **a regular variable** named `buffer` underneath the two attributes
  - Set the value of your `buffer` variable to **10**
  - You'll use the `buffer` variable to prevent Pygame from drawing your circles on the edge of your screen
- Next, generate the **random** x and y values for the center point of your circle, like so:

```python
self.x = random.randint(self.radius + buffer, config.WINDOW_WIDTH - self.radius - buffer)
self.y = random.randint(self.radius + buffer, config.WINDOW_HEIGHT - self.radius - buffer)
```
---

- Then, select at random from a list an x- and y-value that will determine how the circle moves horizontally and vertically in the Pygame window
```python
# Assign random values for horizontal and vertical movement
self.change_x = random.choice([-5, -4, -3, -2, -1, 1, 2, 3, 4, 5])
self.change_y = random.choice([-5, -4, -3, -2, -1, 1, 2, 3, 4, 5])
```

---

### Defining the move ( ) method

- Define a method named `move()`
- This method will take one parameter: `self`
- In the body of the `move()` method, update the x- and y- value for the center point of your circle by adding a randomly selected value between -5 and 5 to the value of x and y, like so:

```python
self.x += self.change_x
self.y += self.change_y
```
---
- Next, make the circle bounce off the left and right and top and bottom of the Pygame window:

```python
# Bounce off the left and right walls
if self.x <= self.radius or self.x >= config.WINDOW_WIDTH - self.radius:
    self.change_x *= -1

# Bounce off the top and bottom walls
if self.y <= self.radius or self.y >= config.WINDOW_HEIGHT - self.radius:
    self.change_y *= -1
```
---

### Defining the draw ( ) method

- Define another method named `draw()` inside your `Circle` class
- The `draw()` method will take two parameters: `self` and `screen`
- To the body of the `draw()` method, add the line of code that draws the circle:
```python
pygame.draw.circle(screen, self.color, (int(self.x), int(self.y)), self.radius)
```

---

### Update your main ( ) function

- Towards the top of your `main()` function, create a list of circles named `circles` using your `Circle` class:

```python
# Define this list ABOVE the running = True line of code that appears
# just above your WHILE loop in the main( ) function
circles = [
    Circle(25, config.RED),
    Circle(30, config.GREEN),
    Circle(35, config.BLUE),
    Circle(40, config.DARKORANGE)
]
```
---
- Inside your WHILE loop, add a FOR loop that uses the `move()` method to animate your circles:

```python
while running:
    running = handle_events()

    for circle in circles:
        circle.move()

    screen.fill(config.WHITE)

```
---
- Underneath the line of code that fills in the screen background with WHITE, add another FOR loop that DRAWS all the circles in the `circles` list:

```python
screen.fill(config.WHITE)

# Second FOR loop that draws the circles onto the Pygame screen
for circle in circles:
    circle.draw(screen)
```

---




