# geometry.js
Some useful structures for graphics programming in JavaScript I guess...

### Structures included
- [x] **Point** `(x, y)`
- [x] **Size** `(width, height)`
- [x] **Rectangle** `(Point, Size)`
- [x] **Circle** `(Point, radius)`
- [x] **Point3D** `(x, y, z)`
- [x] **Size3D** `(width, height, depth)`
- [x] **Cube** `(Point3D, Size3D)`
- [x] **Sphere** `(Point3D, radius)`
- [x] **Line** `(Point, Point)`
- [x] **Line3D** `(Point3D, Point3D)`
- [x] **Polygon** `(optional Point[])`
- [x] **Polygon3D** `(optional Point3D[])`

### NodeJS require all
```javascript
const { Size, Point, Rectangle, Circle, Point3D, Size3D, Cube, Sphere, Line, Line3D, Polygon, Polygon3D } = require('./geometry.js');
```

### Some examples
#### Point
Get angle between two points in degrees
```javascript
const a = new Point(0, 0);
const b = new Point(40, 40);
console.log(a.angleTo(b).degrees);
```

Get distance between two points
```javascript
const a = new Point(50, 50);
const b = new Point(100, 400);
console.log(a.distanceTo(b));
```

#### Rectangle
Determine if a rectangle is completely inside another rectangle
```javascript
const a = new Rectangle(new Point(0, 0), new Size(20, 15));
const b = new Rectangle(new Point(5, 5), new Size(10, 8));
console.log(b.isInside(a));
```

#### Circle
Determine if two circles intersect
```javascript
const a = new Circle(new Point(-20, -20), 40);
const b = new Circle(new Point(50, 50), 90);
console.log(b.intersectsWith(a));
```

#### Cube
Determine if two cubes intersect
```javascript
const a = new Cube(new Point3D(0, 0, 0), new Size3D(200, 50, 50));
const b = new Cube(new Point3D(100, 0, 0), new Size3D(200, 50, 50));
console.log(a.intersectsWith(b));
```

#### Point3D
Get distance between two points in 3d space
```javascript
const a = new Point3D(0, 0, 0);
const b = new Point3D(100, 100, 100);
console.log(a.distanceTo(b));
```

#### Sphere
Determine if two spheres intersect
```javascript
const a = new Sphere(new Point3D(0, 0, 0), 300);
const b = new Sphere(new Point3D(200, 0, 0), 300);
console.log(a.intersectsWith(b));
```

Determine if a sphere is completely inside another sphere
```javascript
const a = new Sphere(new Point3D(0, 0, 0), 300);
const b = new Sphere(new Point3D(30, 30, 0), 190);
console.log(b.isInside(a));
```

#### Line
Get line's length and angle between it's two points in radians
```javascript
const line = new Line(new Point(0, 0), new Point(100, 100));
console.log(line.length());
console.log(line.angle().radians);
```

#### Polygon
Create a polygon from array of points
```javascript
const polygon = new Polygon(
    new Point(1500, 1000),
    new Point(1154.5084971874737, 524.4717418524233),
    new Point(595.4915028125263, 706.1073738537634),
    new Point(595.4915028125263, 1293.8926261462366),
    new Point(1154.5084971874735, 1475.5282581475767)
);
```

Drawing the polygon above to HTML5 canvas (or nodejs)
<img src="https://i.ibb.co/XsvYkcF/image.png" align="right">
```javascript
ctx.lineWidth = 50;
ctx.strokeStyle = '#348feb';
ctx.fillStyle = '#0f0f0f';

ctx.beginPath();
polygon.Points.forEach((point, i)=>{
   if (i==0) ctx.moveTo(point.X, point.Y);
   ctx.lineTo(point.X, point.Y);
});
ctx.closePath();

ctx.fill();
ctx.stroke();
```
