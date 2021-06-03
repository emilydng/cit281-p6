## Project 6

``` markdown
Goals and Outcomes

  - Gain experience creating and working classes with inheritance
  - Gain more experience creating and working with classes
  - Gain more experience debugging code
  - Gain more experience using a generic block of code to process data
  - Gain more experience interpreting functional descriptions and specifications to complete an assignment
  - Gain more experience writing and executing non-web server Node.js JavaScript code using VSCode
  - Practice using modern JavaScript syntax
  - Gain more experience working with static data

```

p6.js

```rouge
  /*
    CIT 281 Project 6
    Emily Deng
  */

  class Shape {
      constructor(sidesArray) {
          this.sides = sidesArray;
      }
      perimeter() {
          return this.sides ? this.sides.reduce((x, y) => (x + y)) : 0;
      }
  }

  /* test works
  console.log(new Shape([5, 10]).perimeter());  // 15
  console.log(new Shape([1, 2, 3, 4, 5]).perimeter()); // 15
  console.log(new Shape().perimeter()); // 0
  */

  class Rectangle extends Shape {
      constructor(length = 0, width = 0) {
          super([length, width, length, width]);
          this.length = length;
          this.width = width;
      }
      area() {
          return this.length * this.width;
      }
  }

  /* test works
  console.log(new Rectangle(4, 4).perimeter());  // 16
  console.log(new Rectangle(4, 4).area());  // 16
  console.log(new Rectangle(5, 5).perimeter()); // 20
  console.log(new Rectangle(5, 5).area()); // 25
  console.log(new Rectangle().perimeter()); // 0
  console.log(new Rectangle().area()); // 0
  */

  class Triangle extends Shape {
      constructor(sideA = 0, sideB = 0, sideC = 0) {
          super([sideA, sideB, sideC]);
          this.sideA = sideA;
          this.sideB = sideB;
          this.sideC = sideC;
      }
      area() {
          const total = (this.sideA + this.sideB + this.sideC)/2
          return Math.sqrt(total*(total - this.sideA)*(total - this.sideB)*(total - this.sideC))
      }
  }

  /* test works
  console.log(new Triangle(3, 4, 5).perimeter());  // 12
  console.log(new Triangle(3, 4, 5).area());  // 6
  console.log(new Triangle().perimeter()); // 0
  console.log(new Triangle().area()); // 0
  */

  // Array of sides arrays
  const data = [ [3, 4], [5, 5], [3, 4, 5], [10], [] ];

  for (const sides of data) {
      let shape = null;
      switch(sides.length) {
          case 2:
              shape = new Rectangle(sides[0], sides[1]);
              break;
          case 3:
              shape = new Triangle(sides[0], sides[1], sides[2]);
              break;
          default:
              console.log(`Shape with ${sides.length} ${sides.length === 0 ? 'side' : 'sides'} unsupported`);
              continue;

      }
      console.log(`${shape.constructor.name} with sides ${sides.toString()} has perimeter of ${shape.perimeter()} and area of ${shape.area()}`);
  }


```
