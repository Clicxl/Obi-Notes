#coding #python
Manim is a [[Python]] based mathematical animation render written by 3blue1brown and maintained by the community \.
[Link](https://docs.manim.community/)


#### Animations
- `Create()` - Draws the arguments inside it from start to end like a curve.
- `Write()` - Writing Animation for text and Outline first then fill colour animation for polygons.
- `DrawBorderThenFill()` - Outline first then fill colour animation

### Notes
-  `run_time`: This argument sets the maximum amount of time that animation should play
- `to_edge(<UP,LEFT,RIGHT,BOTTOM>, buff=<float>)`: This method is applied to all mobjects to displace them to the respective positions and the buff argument is like a margin to all sides of the mobject. It takes in the position args like UP LEFT RIGHT BOTTOM UR (Up right) UL ... 
- `animate()`: This method is used on mobjects to animate them around after being drawn.