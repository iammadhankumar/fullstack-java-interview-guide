# Angular Interview Questions

#### 1. What is angular ?
Angular is a framework for building web applications. It helps developers create dynamic, interactive websites by providing tools and features to manage the front-end.
It handles the user input, displaying data and connecting to the backend services.

#### 2. What is typescript ?
TypeScript is a programming language that builds on JavaScript by adding types. It allows you to define the data types of variables, functions, and properties.</br>
Features of type script : Static Typing, Optional Typing , Interfaces and Classes, Type interference.

#### 3. how to create angular application ?
To create an Angular application, you follow these steps:</br>

Install Node.js: First, you need Node.js installed on your computer, as Angular depends on it.</br>
Install Angular CLI: Run npm install -g @angular/cli in your terminal. This installs Angular’s command-line tool, which helps you create and manage Angular projects.</br>
Create a New Project: Use the command ng new my-app to create a new Angular project called "my-app". Angular CLI sets up everything for you.</br>
Run the Application: Go into your project folder with cd my-app and then run ng serve. Your app will start, and you can view it in a web browser at http://localhost:4200. 

#### 4. How to call backend api in angular ?
Import HttpClient: First, you need to import HttpClient from @angular/common/http in your service or component. This allows Angular to send HTTP requests.


#### 5. What is directives in angular ?
Directives in Angular are special markers for HTML elements. It has three types.</br>
Component Directives: Component directives are custom tags created in Angular applications. ex. <app-header> </br>
Structural Directives: It is used for adding and removing the elements. Ex @ngIf, @ngFor, @ngSwitch. </br>
Attribute Directives :These change the appearance or behavior of an element. Ex ngClass, ngStyle.

#### 6. What is data binding in angular ?
Data binding in Angular is used to communicate between the HTML (view) and the component class (logic).</br>
Interpolation: {{ expression }} — Displays data from the component in the HTML. For example, {{ user.name }} shows the user's name.</br>
Property Binding: [property]="expression" — Sets HTML element properties. For example, [src]="imageUrl" sets the src attribute of an <img> tag.</br>
Event Binding: (event)="method()" — Listens for events and calls a method in the component. For example, (click)="onClick()" calls onClick() when the element is clicked.</br>
Two-Way Binding: [(ngModel)]="property" — Binds data in both directions. Changes in the input field update the component, and changes in the component update the input field. For example, [(ngModel)]="user.name" keeps the input field and user.name in sync.
