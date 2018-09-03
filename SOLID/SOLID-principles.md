# SOLID Principles of OOP
Are a set of OOP design principles whose first letters form a mnemonic acronym which are broadly used in software development.

**S - Single Responsibility Principle**
------------------
This principle states that every class should have responsibility over a single part of a functionality and this responsibility should be enclosed within the class. A responsibility here means "A reason to change". This means that a class should have only one reason to change.

Example - Bad Style
***
```
class EmailSender {
  constructor(token, formEmail, fromName){}
  public sendEmail(customerID, emailNotificationType)
  {
    //STEP1: load customer details
    //STEP2: get email content
    //STEP3: send email (using SmtpClient class)
  }

  public getEmailContent(customer, emailNotificationType)
   {
    // Build the email notification content
   }
}
```
Example - Good Style
***
```
class CustomerRespository {
  public getCustomer(id)
  {
    // logic load customer from Database
  }
}

class EmailContentBuilder {
  public getEmailContent (customerDetails)
  {
    // logic to build email content
  }
}

class EmailSender {
 public sendEmail(emailaddress, subject, bodycontent)
  {
    //logic to send email out
  }
}
```
**O - Open-Closed Principle**
------------------
This principle states that components(classes, modules, functions, etc.) should be extendable while also impossible to modify. This means that while it's behavior can change by extending it's functionality, the underlining source code need not change. A way of extending it's without changing the source code is by inheritance or the use of interfaces.

Example - Bad Style
***
```
/*
calculating the area for more type of shapes would require modification to the 
AreaCalculator class which violates this principles
*/
class Rectangle {
  constructor(width, height){
    this.width = width;
    this.height = height;
  }
}

class AreaCalculator {

    static area(shape) {
      return shape.width * shape.height;
    }
    
    static areaSum(shapes) {
      let sum=0;
      shapes.forEach((shape)=>{
        sum += this.area(shape)
        })
      return sum
    }
}

const shapeOne = new Rectangle(2, 3)
const shapeTwo = new Rectangle(2, 3)
// can calculate area
console.log(AreaCalculator.areaSum(shapeTwo));
console.log(AreaCalculator.areaSum([shapeOne,shapeTwo]));
```

Example - Good Style
***
```
/*
calculating the area for more type of shapes would require only adding new types
of shapes that have their corresponding method for calculating their area
*/
class Rectangle {
  constructor(width, height){
    this.width = width;
    this.height = height;
  }
  area(){
    return this.width * this.height
  }
}

class AreaCalculator {
    
    static areaSum(shapes) {
      let sum=0;
      shapes.forEach((shape)=>{
        sum += this.area(shape)
        })
      return sum
    }
}
```
**L - Liskov substitution principle**
------------------
This principle states that components(objects) that use pointers or references to base classes must be able to use objects of derived classes without knowing it. This principle is mostly about the when it's right to extend a class vs using some other strategy such as composition.

Example - Bad Style
***
```
/*
It becomes clear with this Example that ThreeDBoard is not a very good substitution for 
Board because we cannot play the ThreeDBoard as a Board game because the ThreeDBoard expects a z position which is meaning less to Board even though they seem to express a is-a relationship
*/
class Board {
  constructor(height, width, tile){
    this.height = height;
    this.width = width;
    this.tile = tile;
  }
  calculateScore(move){
    console.log('You scored some points')
  }

  moveTile(fromX,fromY,toX,toY){
    // logic to move tile to different positions
  }

  removeTile(x, y){
    // logic to remove tile from board whenever an opposing player crosses it
  }
}

class ThreeDBoard extends Board {
  constructor(height, width, tile, z){
    super(x, y, tile);
    this.zPosition = z;
  }
  calculateScore(move){
    console.log('You scored some points')
  }

  moveTile(fromZ,fromX,fromY,toX,toY,toZ){
    // logic to move tile to different positions
  }

  removeTile(x, y, z){
    // logic to remove tile from board whenever an opposing player crosses it
  }
}
```

Example - Good Style
***
```
/*
If it looks like a duck, quakes like a duck but needs a battery. You probably have the wrong abstraction
*/
class ThreeDBoard {
  
  constructor(height, width, tile, z){\
    this.zPosition = z;
    this.height = height;
    this.width = width;
    this.tile = tile;
  }

  calculateScore(move){
    console.log('You scored some points')
  }

  moveTile(fromZ,fromX,fromY,toX,toY,toZ){
    // logic to move tile to different positions
  }

  removeTile(x, y, z){
    // logic to remove tile from board whenever an opposing player crosses it
  }
}
```
**I - Interface segregation principle**
------------------
This principle states that no client(classes, objects) should be forced to depend on methods it does not use. Though javascript does not offer a separate construct for representing interfaces, thereby making it impossible to force objects to depend on certain objects. A violation of this rule could also lead to violation is for example LSP.

Example
***
```
/*
Looking at this implementation, though rectangle objects cannot be forced to always implement all it's properties but having another rectangle which implements area and those not implement draw means that the two objects cannot be substituted in both geometryApplication and drawingApplication
*/
var rectangle = {
  length: 8,
  width: 2,
  area: function() { 
      return this.length * this.width
  },
  draw: function() { 
      // code to draw a triangle
  }
};

var geometryApplication = {
    getLargestRectangle: function(rectangles) { 
        var largestArea = 0;
        var largest;
        rectangles.forEach(rectangle=>{
          if(rectangle.area() > largestArea){
            largest = rectangle:
          }
        })
        return largest
    }
};

var drawingApplication = {
    drawRectangles: function(rectangles) {
       /* code */
    }
};
```
**D - Dependency inversion principle**
------------------
This principle states that high-level modules should not depend on low-level modules.  Both should depend on abstractions. Similarly abstractions should not depend upon details.  Details should depend upon abstractions. This renders high-level modules highly reusable and ensures that important parts of an application or framework aren’t affected when the low level components need to change.
