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
### 6. Adapter Pattern :
The Adapter Pattern in Java is like a translator. It allows two classes with different interfaces to work together by using an adapter class. The adapter converts one interface into another so that classes can communicate without changing their original code.
```java
// Step 1: Define the MediaPlayer interface
interface MediaPlayer {
    void play(String audioType); // Method to play media based on its type
}

// Step 2: Implement the MediaPlayer interface in Mp3Player
class Mp3Player implements MediaPlayer {
    // Mp3Player can only play mp3 files
    public void play(String audioType) {
        System.out.println("Playing mp3"); // Print message when playing mp3
    }
}

// Step 3: Define the Mp4Player class with its own play method
class Mp4Player {
    // Mp4Player has its own method to play mp4 files
    public void playMp4() {
        System.out.println("Playing mp4"); // Print message when playing mp4
    }
}

// Step 4: Create the MediaAdapter to make Mp4Player work with MediaPlayer
class MediaAdapter implements MediaPlayer {
    Mp4Player mp4Player; // Reference to the Mp4Player

    // Constructor initializes Mp4Player object
    public MediaAdapter() {
        mp4Player = new Mp4Player(); // Create an instance of Mp4Player
    }

    // Implement the play method from MediaPlayer interface
    public void play(String audioType) {
        // Check if the audio type is mp4
        if ("mp4".equals(audioType)) {
            mp4Player.playMp4(); // Call Mp4Player's play method for mp4 files
        }
    }
}

// Step 5: Use the adapter in the client code
public class Main {
    public static void main(String[] args) {
        // Create an Mp3Player object
        MediaPlayer mp3Player = new Mp3Player();
        mp3Player.play("mp3"); // Play an mp3 file

        // Create a MediaAdapter object for playing mp4 files
        MediaPlayer mp4Adapter = new MediaAdapter();
        mp4Adapter.play("mp4"); // Play an mp4 file using the adapter
    }
}
```

### 7. Bridge Pattern :
The Bridge Pattern separates an interface from its implementation, allowing changes to one without affecting the other. It uses interfaces and classes to connect without tight coupling, making the code flexible and easy to extend. This approach keeps the code organized and allows for more options.
```java
// Color interface
interface Color {
    void fill(); // Method to fill a shape with color
}

// Red color implementation
class Red implements Color {
    public void fill() {
        System.out.println("Filling with Red color");
    }
}

// Green color implementation
class Green implements Color {
    public void fill() {
        System.out.println("Filling with Green color");
    }
}

// Shape abstract class
abstract class Shape {
    protected Color color; // Reference to Color object

    protected Shape(Color color) { // Constructor to initialize Color
        this.color = color;
    }

    abstract void draw(); // Abstract method to draw the shape
}

// Circle shape implementation
class Circle extends Shape {
    public Circle(Color color) {
        super(color); // Initialize the Color in the parent class
    }

    public void draw() {
        System.out.print("Drawing Circle: ");
        color.fill(); // Use the Color to fill the Circle
    }
}

// Square shape implementation
class Square extends Shape {
    public Square(Color color) {
        super(color); // Initialize the Color in the parent class
    }

    public void draw() {
        System.out.print("Drawing Square: ");
        color.fill(); // Use the Color to fill the Square
    }
}

// Bridge pattern demo class
public class BridgePatternDemo {
    public static void main(String[] args) {
        // Create red and green color objects
        Color red = new Red();
        Color green = new Green();

        // Create circle and square objects with different colors
        Shape circle = new Circle(red);
        Shape square = new Square(green);

        // Draw the shapes
        circle.draw(); // Output: Drawing Circle: Filling with Red color
        square.draw(); // Output: Drawing Square: Filling with Green color
    }
}
```
### 8. Decorator Pattern :
The Decorator Pattern lets you add new features or behaviors to individual objects without changing the original object. It wraps the object in a new class that provides additional functionality.
```java
// Coffee interface defining methods for getting description and cost
interface Coffee {
    String getDescription(); // Method to get the coffee description
    double cost();           // Method to get the cost of the coffee
}

// SimpleCoffee class implementing the Coffee interface
class SimpleCoffee implements Coffee {
    // Returns the description of the simple coffee
    public String getDescription() {
        return "Simple Coffee";
    }

    // Returns the cost of the simple coffee
    public double cost() {
        return 2.0; // Base cost for simple coffee
    }
}

// MilkDecorator class implementing the Coffee interface
class MilkDecorator implements Coffee {
    private Coffee coffee; // Reference to a Coffee object

    // Constructor that takes a Coffee object to decorate
    public MilkDecorator(Coffee coffee) {
        this.coffee = coffee; // Assigns the passed Coffee object to the instance variable
    }

    // Returns the description of the coffee with milk added
    public String getDescription() {
        return coffee.getDescription() + ", Milk"; // Adds "Milk" to the existing description
    }

    // Returns the total cost including the cost of milk
    public double cost() {
        return coffee.cost() + 0.5; // Adds 0.5 for the milk to the existing cost
    }
}

// Main class to demonstrate the Decorator Pattern
public class Main {
    public static void main(String[] args) {
        // Create a simple coffee
        Coffee myCoffee = new SimpleCoffee();
        System.out.println(myCoffee.getDescription() + " $" + myCoffee.cost());

        // Add milk to the coffee using the MilkDecorator
        myCoffee = new MilkDecorator(myCoffee);
        System.out.println(myCoffee.getDescription() + " $" + myCoffee.cost());
    }
}
```
### 9. Facade Pattern :
Facade Pattern is a structural design pattern that provides a simplified (but limited) interface to a complex system of classes.
```java
// Class representing the CPU component of a computer
class CPU {
    void start() { 
        System.out.println("CPU started"); // Method to start the CPU
    }
}

// Class representing the Memory component of a computer
class Memory {
    void load() { 
        System.out.println("Memory loaded"); // Method to load the memory
    }
}

// Class representing the Hard Drive component of a computer
class HardDrive {
    void read() { 
        System.out.println("Hard Drive read"); // Method to read data from the hard drive
    }
}

// Facade class that simplifies interactions with the computer subsystem
class ComputerFacade {
    private CPU cpu;          // Reference to the CPU component
    private Memory memory;    // Reference to the Memory component
    private HardDrive hardDrive; // Reference to the Hard Drive component

    // Constructor initializes the components
    public ComputerFacade() {
        cpu = new CPU();                   // Create a new CPU instance
        memory = new Memory();             // Create a new Memory instance
        hardDrive = new HardDrive();       // Create a new Hard Drive instance
    }

    // Method to start the computer, which initiates all components
    public void start() {
        cpu.start();                       // Start the CPU
        memory.load();                     // Load the Memory
        hardDrive.read();                  // Read from the Hard Drive
    }
}
```
### 10. Flyweight Pattern :
Reduces memory consumption by sharing objects that are similar.
```java
import java.util.HashMap;
import java.util.Map;

// Flyweight class that holds shared state
class Flyweight {
    private String sharedState; // Shared state among Flyweight objects

    // Constructor to initialize shared state
    public Flyweight(String sharedState) {
        this.sharedState = sharedState;
    }

    // Method to perform an operation using both shared and unique states
    public void operation(String uniqueState) {
        System.out.println("Shared: " + sharedState + ", Unique: " + uniqueState);
    }
}

// FlyweightFactory class to manage Flyweight objects
class FlyweightFactory {
    private Map<String, Flyweight> flyweights = new HashMap<>(); // Map to store Flyweight objects

    // Method to get a Flyweight object based on a key
    public Flyweight getFlyweight(String key) {
        // If the Flyweight doesn't exist, create a new one and store it
        if (!flyweights.containsKey(key)) {
            flyweights.put(key, new Flyweight(key));
        }
        // Return the existing Flyweight object
        return flyweights.get(key);
    }
}

// Main class to demonstrate the Flyweight pattern
public class Main {
    public static void main(String[] args) {
        // Create a FlyweightFactory instance
        FlyweightFactory factory = new FlyweightFactory();

        // Get Flyweight objects with shared state
        Flyweight flyweight1 = factory.getFlyweight("State1");
        Flyweight flyweight2 = factory.getFlyweight("State2");
        Flyweight flyweight3 = factory.getFlyweight("State1"); // This will reuse the existing Flyweight

        // Perform operations with unique state for each Flyweight
        flyweight1.operation("Unique1");
        flyweight2.operation("Unique2");
        flyweight3.operation("Unique3"); // This uses the shared state "State1"

        // Show that flyweight1 and flyweight3 are the same instance
        System.out.println("flyweight1 and flyweight3 are the same: " + (flyweight1 == flyweight3));
    }
}
```
