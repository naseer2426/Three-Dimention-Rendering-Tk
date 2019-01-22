# About The Program
This is a program that takes in 3D coordinates and colours of a shape, and renders a 3D shape

![alt text](https://github.com/naseer2426/Three-Dimention-Rendering-Tk/tree/master/Program_sample_gifs/cone.gif "Cone")

![alt text](https://github.com/naseer2426/Three-Dimention-Rendering-Tk/tree/master/Program_sample_gifs/cube.gif "Cube")

# Maths Behind the Scenes
The maths used in the program is super interesting! :heart_eyes:. Below are the different problems that needed to be solved for making this program:

- ## Converting 3D Coordinates into 2D pixel locations
  ![](https://github.com/naseer2426/Three-Dimention-Rendering-Tk/tree/master/Proof_pics/1.JPG)
  ![](https://github.com/naseer2426/Three-Dimention-Rendering-Tk/tree/master/Proof_pics/2.JPG)
  ![](https://github.com/naseer2426/Three-Dimention-Rendering-Tk/tree/master/Proof_pics/3.JPG)
  ![](https://github.com/naseer2426/Three-Dimention-Rendering-Tk/tree/master/Proof_pics/4.JPG)
  ![](https://github.com/naseer2426/Three-Dimention-Rendering-Tk/tree/master/Proof_pics/5.JPG)

- ## Rendering only the sides in front
  - First the program calculates the equation of the plane that each side belongs to using 3 points on that side. An inequality is created from this equation.
  - A point is chosen on the line normal to the plane to be the view point. The program renders all the sides whose inequality is satisfied by this view point.

- ## Changing the angle of view
  - The program keeps track of 2 points: The normal vector to the plane of vision and a refernece point.
    - This reference point starts at (0,1,0). Connecting this point to the origin gives us our "Virtual Y Axis".
    - Another point is calculated by finding the sin product of the reference point and normal. Connecting this point to the origin gives our "Virtual X Axis"
  - When you hold the mouse and drag it across the screen, the program calculates the change in x and y directions.
    - The change in the x direction is used to rotate the reference point and normal around the virtual y axis.
    - The change in the y direction is used to rotate the reference point and normal around the virtual x axis.
    - Then the equations of virtual x and y axis are updated.
  - When converting the 3D coordinates to 2D, the program rotates the reference point along with the above calculated (x', y', z') and finds the angle (gaama) between the "virtual y axis" and the real y axis.
  - Then the program rotates all the points by -gaama along z axis. This gives us totally 3 axis of rotations using which the user can freely view any orientation of the 3D object.

- ## Changing the shade of the colours depending on view point
  - The program calculates normal vector to each side is calculated using the plane equation that side belongs to.
  - Then the program calculates the angle between the line connecting view point to the origin and the normal vector of each side.
  - The RGB values of each colour are multiplied by the cos value of this angle.
