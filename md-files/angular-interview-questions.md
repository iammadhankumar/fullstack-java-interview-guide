# Angular Interview Questions

#### 1. What is angular ?
Angular is a framework for building web applications. It helps developers create dynamic, interactive websites by providing tools and features to manage the front-end.
It handles the user input, displaying data and connecting to the backend services.

#### 2. What is typescript ?
* `TypeScript` is a programming language that builds on JavaScript by adding som addition features. It allows you to define the data types of variables, functions, and properties.</br>
* Features of typescript : Static Typing, Optional Typing , Interfaces and Classes, Type interference.

#### 3. how to create angular application ?
To create an Angular application, you follow these steps:</br>

* <b>Install Node.js:</b> First step is to install node js in the system if not</br>
* <b>Install Angular CLI:</b> To install the angular cli, we can use the command `npm install -g @angular/cli` to create and run the angular application. This tool will help you create and manage Angular applications.</br>
* <b>Create Angular Application:</b> To create  angular application by using the command `ng new my-project`.</br>
* <b>Run Application:</b> To run the angular application, we can the command `ng serve` and the application will be accessible in your browser at http://localhost:4200 by default.

#### 4. How to call backend api in angular ?
* First step is to import `HttpClientModule` in the main module file.</br>
* Inject the HttpClient into the constructor in service class</br>
* Use HttpClient methods like get, post, put, etc., in the service to make API requests.</br>
* In the component class, Using Subscribe method to call the service class api request and handle exceptions to return the response.

#### 5. What is directives in angular ?
Directives in Angular are classes that allows to add and modify the behavior to html elements. </br>

* <b>Component Directives:</b> Component directives in angular that encapsulates HTML, component class, styles into a single unit. A component directive in Angular is used to create reusable UI elements with custom HTML tags and encapsulated logic and styles. </br>
* <b>Structural Directives:</b> Structural directives in Angular used for adding, removing, or manipulating structure of DOM (Document Object Model) elements.</br> 
  `*ngIf` : Adds or removes an element based on a condition.</br>
   `*ngFor` : Iterating over an element, create a new instance of element.</br>
  `*ngSwitch`: Adds or removes elements based on a switch expression. </br>
* <b>Attribute Directives:</b> Attributes directives in angular used to change the appreances of existing DOM elements by changing its styles or classes. </br>
   `ngClass` : adds or removes CSS classes based on an expression.</br>
   `ngStyle` : Dynamically sets inline styles for an element.</br>
   `ngModel` : Enables two way data binding.

#### 6. What is data binding in angular ?
Data binding in Angular is a mechanism is used to communicate between HTML template (view) and the component class (logic).</br>
* <b>Interpolation:</b> Using double curly braces to display data from the component in the HTML.</br>
  For example, `{{ user.name }}` shows the user's name.</br>
* <b>Property Binding:</b> Using square brackets to display data from the component in the HTML.</br>
  For example, `<img [src]="imageUrl" [alt]="imageAlt">` sets image source.</br>
* <b>Event Binding:</b> Event binding in Angular is a way to handle clickable events such as from submissions.</br>
  For Example, `<element (event)="handlerMethod()"></element>` Event binding uses parentheses ( ) around the event name.</br>
* <b>Two-Way Binding:</b> Two-way data binding in Angular allows for the synchronization of data between the component and the template. This means that changes 
  made in the component are reflected in the template, and vice versa.</br>
  For Example, </br>
 `<input [(ngModel)]="username" placeholder="Enter your username">`</br>
  `<p>Your username is: {{ username }}</p>`</br>
  Binds data in both directions.

 #### 7. What is Doument Object model (DOM) in angular ?
The Document Object Model (DOM) in Angular is a way of representing and interacting with the HTML structure of a webpage. It represents all the HTML tags and their relationships on a webpage.

#### 8. What is routing in angular ?
Routing in angular is used to navigate the one web page to another without requiring full page reload.</br>
* We can set up routing in the app routing module file. We can define a routes as an array of objects which contains the path and component name</br>
* To use routing in other components, we can import the RouterModule in the app routing module and export it to other components.
  
#### 9. What is decorators in angular ?
Decorators are special markers of the classes and its members. They allow you to modify the behavior of a class or its members without directly modifying their source code.</br>
Types of decorators :</br>
* <b>Class Decorators:</b></br>
  @Component: The most common decorator, used to define Angular components. It provides metadata such as the component's selector, template, styles.</br>
  @NgModule: Used to define Angular modules, which group components, directives, pipes, and services.</br>
  @Injectable: Marks a class as an injectable service, allowing it to be used in dependency injection.</br></br>

* <b>Property Decorators:</b></br>
@Input: Marks a property as an input, allowing data to be passed into the component from its parent.</br>
@Output: Marks a property as an output, allowing the component to emit events to its parent.</br></br>

* <b>Method Decorators:</b></br>
@HostListener: Binds a method to a DOM event on the host element of a component or directive.</br>
@HostBinding: Binds a property of a component or directive to a property of its host element.

