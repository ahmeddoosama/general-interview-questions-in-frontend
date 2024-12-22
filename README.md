# Frontend Interview Questions

## Table of Contents
- [JavaScript Questions](#javascript-questions)
- [Angular Questions](#angular-questions)

## JavaScript Questions

### 1. What is hoisting in JavaScript?
**Answer:** Hoisting is JavaScript's default behavior of moving declarations to the top of their scope before code execution. This means that regardless of where variables and functions are declared, they are moved to the top of their scope. However, only the declarations are hoisted, not the initializations.

### 2. Explain the difference between `let`, `const`, and `var`
**Answer:** 
- `var`: Function-scoped or globally-scoped, can be redeclared and updated
- `let`: Block-scoped, can be updated but not redeclared
- `const`: Block-scoped, cannot be updated or redeclared

### 3. What is closure in JavaScript?
**Answer:** A closure is the combination of a function bundled together with references to its surrounding state (lexical environment). It gives you access to an outer function's scope from an inner function.

### 4. Explain event bubbling and event capturing
**Answer:** 
- Event Bubbling: Events propagate from the target element up through its ancestors
- Event Capturing: Events propagate from the root element down to the target element

### 5. What is the difference between `==` and `===`?
**Answer:** 
- `==` performs type coercion before comparison
- `===` compares both value and type without coercion

## Angular Questions

### 1. What is Angular and what are its main features?
**Answer:** Angular is a TypeScript-based open-source framework. Main features include:
- Component-based architecture
- Two-way data binding
- Dependency Injection
- Templates
- Routing
- Observables
- Forms (Template-driven and Reactive)

### 2. Explain the difference between constructor and ngOnInit
**Answer:**
- Constructor: Used to initialize class members and inject dependencies
- ngOnInit: Lifecycle hook used for any additional initialization after constructor

### 3. What is dependency injection in Angular?
**Answer:** Dependency Injection (DI) is a design pattern where dependencies are passed into an object instead of being created inside the object. Angular's DI framework provides dependencies to a class when it is instantiated.

### 4. What are Angular decorators?
**Answer:** Decorators are design patterns that allow you to mark a class or add metadata to class members. Common decorators include:
- @Component()
- @Injectable()
- @Input()
- @Output()
- @NgModule()

### 5. Explain Angular pipes and give examples
**Answer:** Pipes transform displayed values within a template. Built-in pipes include:
- DatePipe: {{ date | date:'short' }}
- UpperCasePipe: {{ text | uppercase }}
- LowerCasePipe: {{ text | lowercase }}
- CurrencyPipe: {{ price | currency:'USD' }}