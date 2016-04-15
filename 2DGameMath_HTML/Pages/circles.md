#Circles
This is where things get a bit more interesting, not because of what a circle is, but because we can start interacting with a line!

A circle is just a ```Point``` and a ```Radius```.

```cs
class Circle {
    public Point Position;
    public float Radius;
}
```

##Drawing
Drawing a circle is not straight forward, we don't have a magic "Draw Circle" function in ```GraphicsManager```. Instead, we have to make our own ```Draw``` method for the humble cirlce. Drawing a circle is simple, we are just going to draw a lot of small lines that make up a circle shape!

To draw a circle, we take the middle point, and draw a line out by the radius. This is the start point, we then rotate that line by some number of degrees, this is the end point. We then draw a line from the start point to the end point.

The end point becomes the new start point, we rotate the line again, and the end of the line becomes the new end point. We keep doing this until we've rotated 360 degrees. The smaller the rotation angles you have, the more circular your circle will be.

```cs
int centrex=100,centrey=100;// centre of circle in pixel coords
int radius=50;

float two_pi=6.283f;

float angle_inc=1.0f/radius;
for(float angle=0.0f; angle<= two_pi;angle+=angle_inc){
    xpos=centrex+radius*cos(angle);
    ypos=centrey+radius*sin(angle);
    putpixel(x,pos,ypos,surface);
}
```

It's worth mentioning, this is not the most optimnal way to draw a circle! The most optimal way is the [Midpoint algorithm](https://en.wikipedia.org/wiki/Midpoint_circle_algorithm), if you're up for a challenge try to implement it yourself.

##Intersection
We have three primitives so far the point, the line and the circle. Let's write some functions to test if a point is inside the circle, or if a line intersects a circle. Let's start with the point. 

###Point Intersection
To see if a point is inside a circle, we create a line whose endpoints are the center of the circle and the point we're testing. If the length of that line is less than the radius of the circle, then the line is considered to be inside the circle.

**TODO: Image**

```cs
bool Contains(Point point) {
    // TODO: Fill this out!
}
```

###Line Intersection
Testing if a line intersects a circle is not much more difficult than testing if a point is contained within a circle. All we have to do is find the point on the line that is closest to the position (center) of the circle, and see if it is contained inside the circle.