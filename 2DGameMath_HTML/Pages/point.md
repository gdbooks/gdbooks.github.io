#Points
The simplest of all geometry is a point. We're going to use a simple Point class that will be useful later:

```cs
class Point {
    public float X;
    publuc float Y;
}
```

Let's add a few constructors. First is the default, it will create the point at 0, 0

```cs
public Point() {
    X = 0.0f;
    Y = 0.0f;
}
```

Next, one that takes X and Y

```cs
public Point(float x, float y) {
    X = x;
    Y = y;
}
```
###Copy Constructor
And let's do what's called a **Copy Constructor**, this will allow us to make new Point objects quickly by typing: ```Point p2 = new Point(p1);```.

```cs
public Point(Point p) {
    X = p.X;
    Y = p.Y;
}
```

From now on, all our geometry classes are going to contain a copy constructor! This should save us a lot of typing in the future.