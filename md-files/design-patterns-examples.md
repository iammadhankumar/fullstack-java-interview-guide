## Design Patterns in Java

### 1. Singleton Pattern :
The Singleton pattern ensures that a class has only one instance, and it provides a way to access that single instance globally. It prevents multiple objects of that class from being created.</br></br>
<b>Key Points:</b>
* <b>Single instance:</b> Only one object of the class is created.
* <b>Global access:</b> The same instance can be accessed anywhere in the code.
```java
public class Singleton {
    // Step 1: Create a private static instance
    private static Singleton instance;

    // Step 2: Make the constructor private so it can't be called from outside
    private Singleton() {}

    // Step 3: Provide a public method to get the single instance
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```
### 2. Factory Pattern :
The Factory Pattern is a way to create objects without specifying the exact class. Instead, it provides a general method for creating objects, and specific subclasses decide which type to create.
```java
// Step 1: Define the Shape interface with a method to draw shapes
interface Shape {
    void draw();
}

// Step 2: Implement the Circle class that draws a circle
class Circle implements Shape {
    public void draw() {
        System.out.println("Drawing a circle");
    }
}

// Step 3: Implement the Square class that draws a square
class Square implements Shape {
    public void draw() {
        System.out.println("Drawing a square");
    }
}

// Step 4: Create a ShapeFactory class to generate Shape objects
class ShapeFactory {
    // Method to get the shape based on the input type
    public Shape getShape(String type) {
        // Check if the requested shape is a circle
        if (type.equalsIgnoreCase("circle")) {
            return new Circle(); // Return a new Circle object
        } 
        // Check if the requested shape is a square
        else if (type.equalsIgnoreCase("square")) {
            return new Square(); // Return a new Square object
        }
        // If the shape type is not recognized, return null
        return null;
    }
}

// Step 5: Main class to test the Factory Pattern
public class Main {
    public static void main(String[] args) {
        // Create an instance of ShapeFactory
        ShapeFactory factory = new ShapeFactory();

        // Request a Circle shape from the factory
        Shape circle = factory.getShape("circle");
        circle.draw(); // Call the draw method to draw the circle

        // Request a Square shape from the factory
        Shape square = factory.getShape("square");
        square.draw(); // Call the draw method to draw the square
    }
}
```
### 3. Abstract Factory Pattern :
The Abstract Factory Pattern is a way to create groups of related objects without needing to specify the exact classes of those objects.
```java
// Step 1: Define the Button interface with a click method
interface Button {
    void click(); // Method to be implemented by different button types
}

// Step 2: Implement the MacButton class that represents a button in a Mac GUI
class MacButton implements Button {
    public void click() {
        System.out.println("Mac button clicked"); // Action performed when the Mac button is clicked
    }
}

// Step 3: Implement the WindowsButton class that represents a button in a Windows GUI
class WindowsButton implements Button {
    public void click() {
        System.out.println("Windows button clicked"); // Action performed when the Windows button is clicked
    }
}

// Step 4: Define the GUIFactory interface with a method to create buttons
interface GUIFactory {
    Button createButton(); // Method to create buttons of different types
}

// Step 5: Create the MacFactory class that implements GUIFactory to produce Mac buttons
class MacFactory implements GUIFactory {
    public Button createButton() {
        return new MacButton(); // Return a new instance of MacButton
    }
}

// Step 6: Create the WindowsFactory class that implements GUIFactory to produce Windows buttons
class WindowsFactory implements GUIFactory {
    public Button createButton() {
        return new WindowsButton(); // Return a new instance of WindowsButton
    }
}

// Step 7: Main class to demonstrate the Abstract Factory Pattern
public class Main {
    public static void main(String[] args) {
        // Create a variable for GUIFactory
        GUIFactory factory;

        // Set the factory based on the operating system (Mac or Windows)
        String os = "Mac"; // Change this to "Windows" to use WindowsFactory

        if (os.equalsIgnoreCase("Mac")) {
            factory = new MacFactory(); // Use MacFactory for Mac buttons
        } else {
            factory = new WindowsFactory(); // Use WindowsFactory for Windows buttons
        }

        // Create a button using the factory
        Button button = factory.createButton(); // Create a button using the factory
        button.click(); // Call the click method on the created button
    }
}
```
### 4. Builder Pattern :
The Builder Pattern is a way to create complex objects step by step without having to specify the exact details of how they are built. This allows for different versions of the same object to be created using the same process.
```java
// Step 1: Define the Pizza class that represents a pizza with various ingredients
class Pizza {
    private String dough = "";   // Variable to hold the type of dough
    private String sauce = "";   // Variable to hold the type of sauce
    private String topping = "";  // Variable to hold the type of topping

    // Step 2: Create a static Builder class inside Pizza
    public static class Builder {
        private String dough = "";   // Variable for dough in the builder
        private String sauce = "";   // Variable for sauce in the builder
        private String topping = "";  // Variable for topping in the builder

        // Method to set the dough type and return the Builder
        public Builder dough(String dough) {
            this.dough = dough; // Set the dough type
            return this;        // Return the Builder for method chaining
        }

        // Method to set the sauce type and return the Builder
        public Builder sauce(String sauce) {
            this.sauce = sauce; // Set the sauce type
            return this;        // Return the Builder for method chaining
        }

        // Method to set the topping type and return the Builder
        public Builder topping(String topping) {
            this.topping = topping; // Set the topping type
            return this;            // Return the Builder for method chaining
        }

        // Method to build and return the final Pizza object
        public Pizza build() {
            Pizza pizza = new Pizza(); // Create a new Pizza instance
            pizza.dough = this.dough;  // Set the dough type for the Pizza
            pizza.sauce = this.sauce;  // Set the sauce type for the Pizza
            pizza.topping = this.topping; // Set the topping for the Pizza
            return pizza;              // Return the constructed Pizza
        }
    }

    // Optional: Method to display the pizza details
    @Override
    public String toString() {
        return "Pizza with " + dough + " dough, " + sauce + " sauce, and " + topping + " topping.";
    }
}

// Step 3: Main class to demonstrate the Builder Pattern
public class Main {
    public static void main(String[] args) {
        // Create a Margherita Pizza using the Builder
        Pizza margherita = new Pizza.Builder()
                .dough("Thin Crust")
                .sauce("Tomato Sauce")
                .topping("Mozzarella Cheese")
                .build();
        
        // Print details of the Margherita Pizza
        System.out.println(margherita);

        // Create a Pepperoni Pizza using the Builder
        Pizza pepperoni = new Pizza.Builder()
                .dough("Thick Crust")
                .sauce("BBQ Sauce")
                .topping("Pepperoni")
                .build();
        
        // Print details of the Pepperoni Pizza
        System.out.println(pepperoni);
    }
}
```
### 5. Prototype Pattern
Creates new objects by copying an existing object, known as a prototype.
```java
// Step 1: Define the Shape class that implements Cloneable
class Shape implements Cloneable {
    public String type; // Variable to hold the type of shape

    // Method to clone the shape object
    public Shape clone() throws CloneNotSupportedException {
        return (Shape) super.clone(); // Call the clone method from Object and cast it to Shape
    }
}

// Step 2: Define Circle class that extends Shape
class Circle extends Shape {
    public Circle() {
        this.type = "Circle"; // Set the type to Circle
    }
}

// Step 3: Define Square class that extends Shape
class Square extends Shape {
    public Square() {
        this.type = "Square"; // Set the type to Square
    }
}

// Step 4: Main class to demonstrate the Prototype Pattern
public class Main {
    public static void main(String[] args) {
        try {
            // Create a Circle object
            Shape circle = new Circle();
            System.out.println("Original: " + circle.type); // Print the type of the original Circle

            // Clone the Circle object
            Shape clonedCircle = circle.clone();
            System.out.println("Cloned: " + clonedCircle.type); // Print the type of the cloned Circle

            // Create a Square object
            Shape square = new Square();
            System.out.println("Original: " + square.type); // Print the type of the original Square

            // Clone the Square object
            Shape clonedSquare = square.clone();
            System.out.println("Cloned: " + clonedSquare.type); // Print the type of the cloned Square

        } catch (CloneNotSupportedException e) {
            e.printStackTrace(); // Handle the exception if cloning is not supported
        }
    }
}
```
