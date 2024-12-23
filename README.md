# Frontend Interview Questions

## Table of Contents
- [CSS Questions](#css-questions)
- [JavaScript Questions](#javascript-questions)
- [Angular Questions](#angular-questions)

## CSS Questions

### 1. in a short summary can you explain How is border-box different from content-box?
**Answer:** Here's a simple explanation of border-box vs content-box:

**content-box (default)**
- Width and height only include content
- Padding and border are added extra to the specified width/height
- Final element size = width + padding + border

**border-box:**
- Width and height include content, padding, and border
- Padding and border are included within the specified width/height
- Final element size = specified width (no additions)

**Quick example:**
```
.content-box {
    width: 100px;
    padding: 10px;
    /* Total width = 120px (100 + 10 + 10) */
}

.border-box {
    width: 100px;
    padding: 10px;
    /* Total width = 100px */
}
```

### 2. margin line VS margin block?
**Answer**
- **margin-inline:** Controls horizontal margins (left and right)
- **margin-block:** Controls vertical margins (top and bottom)

### 3. what is the flex-shrink and flex-grow?
**Answer**
- **flex-shrink:**
  - Controls how items shrink when space is limited
  - Default value is 1 (will shrink)
- **flex-shrink:**
  - Controls how items grow when extra space is available
  - Default value is 0 (won't grow)

**Key difference:**
- flex-grow: handles extra space
- flex-shrink: handles insufficient space

## JavaScript Questions

### 1. What is hoisting in JavaScript?
**Answer:** Hoisting is JavaScript's default behavior of moving declarations to the top of their scope during compilation, before code execution. Here's what happens:

- Function declarations are fully hoisted (both declaration and definition)
- Variables declared with 'var' are hoisted but initialized as undefined
- let and const declarations are hoisted but not initialized (temporal dead zone)

Example:
```javascript
console.log(x); // undefined
console.log(getName); // function definition
console.log(y); // ReferenceError

var x = 5;
function getName() { return "John"; }
let y = 10;
```

### 2. Explain the difference between `let`, `const`, and `var`
**Answer:** 
- `var`: Function-scoped or globally-scoped, can be redeclared and updated
- `let`: Block-scoped, can be updated but not redeclared
- `const`: Block-scoped, cannot be updated or redeclared

### 3. What is closure in JavaScript?
**Answer:** A closure is a function that has access to variables in its outer (enclosing) scope, even after the outer function has returned. It forms a "closure" over the data, preserving access to it.

**Simple example:**
```
function makeAdder(x) {
    return function(y) {
        return x + y;  // 'x' is preserved in closure
    }
}

const add5 = makeAdder(5);
console.log(add5(3)); // 8
```

### 4. Explain event bubbling and event capturing
**Answer:** 
- Event Bubbling: Events propagate from the target element up through its ancestors
- Event Capturing: Events propagate from the root element down to the target element

### 5. What is the difference between `==` and `===`?
**Answer:** 
- `==` performs type coercion before comparison
- `===` compares both value and type without coercion

### 6. What is a single page application(SPA)?
**Answer:** A Single Page Application (SPA) is a web application that loads a single HTML page and dynamically updates content as users interact with it, without requiring full page reloads. Instead of loading entire new pages, SPAs use JavaScript to fetch data and update specific parts of the page, creating a smoother, more app-like experience.

### 7. What is the difference between synchronous and asynchronous code?
**Answer:** 
- Synchronous code: Executes line by line, blocking further execution until current operation completes
- Asynchronous code: Allows multiple operations to happen simultaneously, doesn't block execution

### 8. What is the event loop in JavaScript?
**Answer:** The event loop is a component of the JavaScript engine that manages the execution of code, collecting and processing events, and executing queued sub-tasks.
**Another declaration:** The Event Loop is a core mechanism in JavaScript that handles asynchronous operations

### 9. Explain Promise in JavaScript?
**Answer:** A Promise is an object representing the eventual completion (or failure) of an asynchronous operation. It has three states:
- Pending: Initial state, neither fulfilled nor rejected
- Fulfilled: Operation completed successfully
- Rejected: Operation failed

### 10. Explain the concept of prototypal inheritance?
**Answer:** Prototypal inheritance is a method by which an object can inherit properties and methods from another object. In JavaScript, each object has a private property called `[[Prototype]]` that links to another object called its prototype. This creates a prototype chain that is used for property lookup.

### 11. What is type of in javascript ? What is the difference between type of and instance of?
**Answer:** `typeof` and `instanceof` are both operators used for type checking in JavaScript, but they serve different purposes:

**typeof:**
- Returns a string indicating the primitive type of a value
- Works with primitive data types (string, number, boolean, etc.)
- Example:
```javascript
typeof "hello" // "string"
typeof 42      // "number"
typeof true    // "boolean"
typeof undefined // "undefined"
typeof null    // "object" (this is a known JavaScript quirk)
```

**instanceof:**
- Tests if an object is an instance of a specific class/constructor
- Checks the prototype chain
- Only works with objects, not primitives
- Example:
```javascript
let arr = [];
let date = new Date();

arr instanceof Array  // true
date instanceof Date  // true
"hello" instanceof String // false (primitive string)
new String("hello") instanceof String // true (String object)
```

### 12. What are the differences between cookie, local storage and session storage?
**Answer:** Here are the key differences between these web storage options:

**Cookies:**
- Small data (4KB limit)
- Sent with every HTTP request
- Can set expiration date
- Accessible server-side and client-side
- Can be secured with httpOnly flag

**Local Storage:**
- Larger storage (5-10MB)
- Data persists until explicitly cleared
- Not sent with requests
- Only accessible client-side
- Persists across browser sessions

**Session Storage:**
- Similar to Local Storage (5-10MB)
- Data only persists for current session
- Cleared when browser tab closes
- Only accessible client-side
- Separate storage per tab

**Code Examples:**
```javascript
// Cookies
document.cookie = "username=John Doe; expires=Thu, 18 Dec 2023 12:00:00 UTC";

// Local Storage
localStorage.setItem("username", "John Doe");
let user = localStorage.getItem("username");

// Session Storage
sessionStorage.setItem("username", "John Doe");
let tempUser = sessionStorage.getItem("username");
```

### 13. how I can make the object can't edit on it?
**Answer:** Here are several ways to make an object immutable (prevent editing) in JavaScript:

- **Object.freeze():**
```
const user = {
    name: "John",
    age: 30
};
Object.freeze(user);
user.name = "Mike"; // Won't work
```
- **Object.seal():**
```
const user = {
    name: "John",
    age: 30
};
Object.seal(user);
// Can modify existing properties
user.name = "Mike"; // Works
// But can't add new properties
user.city = "NY"; // Won't work
```
- **const (only prevents reassignment):**
```
const user = {
    name: "John"
};
// Can't reassign user
user = {}; // Error
// But can modify properties
user.name = "Mike"; // Works
```
- **readonly in TypeScript:**
```
interface User {
    readonly name: string;
    readonly age: number;
}
```

### 13. arrow function VS regular function?
**Answer** Here are the key differences between arrow functions and regular functions:
- 'this' binding:
```
// Regular function - 'this' changes based on context
function regularFunc() {
    this.value = 1;
    setTimeout(function() {
        this.value++; // 'this' is window/undefined
    }, 1000);
}

// Arrow function - 'this' is lexically bound
function arrowFunc() {
    this.value = 1;
    setTimeout(() => {
        this.value++; // 'this' refers to arrowFunc's this
    }, 1000);
}
```
- Arguments object:
```
// Regular function has arguments object
function regular() {
    console.log(arguments); // [1, 2, 3]
}

// Arrow function doesn't have arguments
const arrow = () => {
    console.log(arguments); // ReferenceError
}
```
- Constructor:
```
// Regular function can be constructor
function Regular() {
    this.name = "John";
}
new Regular(); // Works

// Arrow function cannot be constructor
const Arrow = () => {
    this.name = "John";
}
new Arrow(); // TypeError
```
- Syntax
```
// Regular function
function add(a, b) {
    return a + b;
}

// Arrow function (shorter syntax)
const add = (a, b) => a + b;
```

**Main differences summary:**
- Arrow functions have no their own 'this'
- Can't use arrow functions as constructors
- No arguments object in arrow functions
- Arrow functions provide shorter syntax

### 14. what is the Event Loop!
**Answer** The Event Loop is a core mechanism in JavaScript that handles asynchronous operations.

### 15. what is microservices in frontend?
**Answer** Microservices in frontend (also called micro-frontends) is an architectural style where a frontend application is divided into smaller, independent applications.

### 16. what is the docker image?
**Answer** A Docker image is a lightweight, standalone package that contains everything needed to run an application.

### 17. How promise.all work?
**Answer** Promise.all() executes multiple promises in parallel and waits for all to complete:
```
// Basic usage
Promise.all([
    fetch('/users'),
    fetch('/products'),
    fetch('/orders')
])
.then(([users, products, orders]) => {
    // All promises resolved
})
.catch(error => {
    // If any promise fails
});

// Real example
const userPromises = [
    Promise.resolve({ id: 1, name: 'John' }),
    Promise.resolve({ id: 2, name: 'Jane' }),
    new Promise((resolve) => setTimeout(() => {
        resolve({ id: 3, name: 'Mike' })
    }, 1000))
];

Promise.all(userPromises)
    .then(users => console.log(users))
    .catch(error => console.error(error));
```
**Key points:**
- Returns array of results in same order
- Fails if any promise fails
- All promises execute simultaneously
- Waits for longest promise to complete
- Returns single rejected promise if any fails

**Use cases:**
- Multiple API calls
- Parallel data loading
- Batch operations
- Dependencies that can load in parallel

### 18. What the result 0.1+0.2 === 0.3?
**Answer** The result of 0.1 + 0.2 === 0.3 is false in JavaScript.
**Here's why:**
```
console.log(0.1 + 0.2); // 0.30000000000000004
console.log(0.1 + 0.2 === 0.3); // false
```

### 19. What type of null?
**Answer** In JavaScript, when you check the type of null using the typeof operator:
```
console.log(typeof null); // "object"
```
This is actually a known bug in JavaScript that has persisted since the language's creation. Even though null is a primitive value:
1. It represents the intentional absence of any object value
2. It's one of JavaScript's primitive values
3. Despite being primitive, typeof null returns "object"

### 20. What is lexical scoping?
**Answer** Lexical scoping means that the scope of a variable is determined by its location within the source code. Variables can access their own scope and any variables in any outer/enclosing scopes.
**Here's a simple example:**
```
const globalVar = "I'm global";

function outerFunction() {
    const outerVar = "I'm from outer";
    
    function innerFunction() {
        const innerVar = "I'm from inner";
        console.log(innerVar);     // Can access own scope
        console.log(outerVar);     // Can access outer scope
        console.log(globalVar);    // Can access global scope
    }
    
    innerFunction();
    console.log(innerVar);  // Error: can't access inner scope
}
```
**Important points:**
- Inner scopes can access outer scopes
- Outer scopes cannot access inner scopes
- Scope is determined at write time, not run time
- This is fundamental to how closures work

**Common use in closures:**
```
function createCounter() {
    let count = 0;  // Lexically scoped variable
    
    return function() {
        return ++count;  // Has access to count due to lexical scope
    }
}

const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```
This is why inner functions maintain access to their outer scope's variables, even after the outer function has finished executing.

### 21. What is callback function?
**Answer** A callback function is a function passed as an argument to another function, which is then executed at a later time. Here's a clear explanation:
**Real-world examples:**

- Event Handlers:
```
button.addEventListener('click', function() {
    console.log("Button clicked");
});
```
- Asynchronous Operations:
```
// Reading file with callback
fs.readFile('file.txt', (error, data) => {
    if (error) {
        console.error('Error:', error);
        return;
    }
    console.log('Data:', data);
});
```
- Array Methods:
```
const numbers = [1, 2, 3];
numbers.forEach(num => console.log(num));
numbers.map(num => num * 2);
```

**Common Issue - Callback Hell:**
```
getData(function(a) {
    getMoreData(a, function(b) {
        getMoreData(b, function(c) {
            getMoreData(c, function(d) {
                // Callback hell!
            });
        });
    });
});
```
**Solution:** Use Promises or async/await to avoid callback hell.

### 22. Determine the output of the following Javascript code. for(var hack=0; hack< 6; hack++) { setTimeout(() => console.log(hack), 0); }?

**Answer** The output will be:
```
6
6
6
6
6
6
```
**Here's why:**
- The loop creates 6 timeouts using var hack
- var is function-scoped, not block-scoped
- By the time the timeouts execute, the loop has completed
- At completion, hack equals 6
- All callbacks reference the same variable hack
- So they all print 6

To get 0,1,2,3,4,5 instead, you could:
- Use let instead of var:
```
for(let hack=0; hack<6; hack++) {
    setTimeout(() => console.log(hack), 0);
}
```
- Or use an IIFE to create a new scope:
```
for(var hack=0; hack<6; hack++) {
    ((num) => {
        setTimeout(() => console.log(num), 0);
    })(hack);
}
```
The issue occurs because of var's scoping behavior and the asynchronous nature of setTimeout.

##

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

### 5. what is the wild card router in angular?
**Answer:** A wildcard route in Angular (denoted by '**') is a special route that handles any URL that doesn't match any other defined routes. It's typically used for 404 error pages or handling unknown routes.

**Quick example:**
```
const routes: Routes = [
    { path: 'home', component: HomeComponent },
    { path: 'about', component: AboutComponent },
    // Wildcard route - must be last
    { path: '**', component: PageNotFoundComponent }
];
```

### 6. what is the Signals angular?
**Answer:** Signals in Angular (introduced in Angular 16) are a new reactivity primitive that provide more efficient and fine-grained reactivity compared to traditional change detection.

**Quick example:**
```
// Create a signal
const count = signal(0);

// Read value
console.log(count()); // 0

// Update value
count.set(1);

// Update based on previous
count.update(value => value + 1);

// Computed signal
const doubled = computed(() => count() * 2);

// Effect
effect(() => {
  console.log(`Count is: ${count()}`);
});
```
**Key benefits**
- Better performance than traditional change detection
- More predictable data flow
- Fine-grained updates
- Less memory usage
- Simpler dependency tracking

**Common use cases:**
- Managing component state
- Handling reactive data updates
- Creating computed values
- Side effects management

### 7. what the different between Observable VS Subject VS BehaviorSubject?
**Answer:** Here's a quick comparison of Observable, Subject, and BehaviorSubject in RxJS:

**Observable:**
- Unicast (one-to-one)
- Can't emit values from outside
- Lazy (executes only when subscribed)
**Example**
```
const observable = new Observable(subscriber => {
    subscriber.next(1);
});
```

**Subject:**
- Multicast (one-to-many)
- Can emit values using next()
- No initial value
- Only emits new values to subscribers
**Example**
```
const subject = new Subject();
subject.next('New data');
```

**BehaviorSubject**
- Multicast like Subject
- Requires initial value
- New subscribers get the last emitted value
- Always has current value state
**Example**
```
const behaviorSubject = new BehaviorSubject('Initial value');
behaviorSubject.next('New value');
// New subscriber will immediately receive 'New value'
```

**Key Difference:**
- Observable: Simple data stream
- Subject: Like an event emitter
- BehaviorSubject: Like a state container with current value

### 8. what the angular design pattern?
- Component Design Patterns:
```
// Smart Component
@Component({
  selector: 'user-container'
})
export class UserContainer {
  users$ = this.service.getUsers();
  onUserUpdate(user) { /* handle logic */ }
}

// Dumb Component
@Component({
  selector: 'user-list'
})
export class UserList {
  @Input() users: User[];
  @Output() userUpdate = new EventEmitter();
}
```
- Singleton Services Pattern:
```
@Injectable({
  providedIn: 'root'
})
export class UserService {
  // Shared across app
}
```
- Observer Pattern:
```
// Using Observables
users$ = this.http.get<User[]>('/api/users');
this.users$.subscribe(users => /* handle data */);
```
- Module Pattern:
```
@NgModule({
  imports: [CommonModule],
  declarations: [UserComponent],
  exports: [UserComponent]
})
export class UserModule { }
```
- Dependency Injection:
```
constructor(
  private userService: UserService,
  private authService: AuthService
) { }
```
- Repository Pattern:
```
@Injectable()
export class UserRepository {
  private apiUrl = '/api/users';
  getUsers() { return this.http.get(this.apiUrl); }
}
```
**Common additional patterns:**
- Facade Pattern (simplifying complex subsystems)
- Strategy Pattern (interchangeable algorithms)
- Factory Pattern (creating objects)
- Mediator Pattern (component communication)

### 9. what is the uses ngDestory?
**Answer** NgOnDestroy is a lifecycle hook in Angular that's called right before a component is destroyed.
**Benefits**
- Prevent memory leaks
- Clean up subscriptions
- Remove event listeners
- Clear intervals/timeouts
- Clean up any manual DOM changes

### 10.what is the uses ngDoCheck?
**Answer**  NgDoCheck is a lifecycle hook in Angular that's called during every change detection run.
**Key uses:**
- Implement custom change detection
- Track changes Angular doesn't catch
- Deep object comparisons
- Performance monitoring
**Warning:**
- Runs very frequently
- Can impact performance
- Use sparingly
- Prefer OnChanges for simple input changes

### 11.what is the bootstrap in angular?
**Answer** Bootstrap in Angular refers to two things:
1. Initial Application Bootstrap:
```
// main.ts - Starting point of Angular app
bootstrapApplication(AppComponent, {
  providers: [...]
}); 

// Or traditional way
platformBrowserDynamic()
  .bootstrapModule(AppModule);
```
2. Angular Module Bootstrap:
```
@NgModule({
  declarations: [...],
  imports: [...],
  providers: [...],
  bootstrap: [AppComponent] // Component to start with
})
export class AppModule { }
```
**Key points:**

- Initializes the application
- Sets up dependency injection
- Creates the root component
- Starts change detection
- Renders initial view

**Different ways:**

- Standalone bootstrap (newer, recommended)
- NgModule-based bootstrap (traditional)
- Server-side bootstrap (for SSR)

### 12. How to modify a specific component when using a shared service across multiple components?
**Question:** If I have three components and I add a service to the providers in the module that contains all the components, and I inject this service into every component, how can I make a change specific to one component?

**Answer** Here's how to override a service for a specific component while keeping the module-level service for others:
```
// Shared service in module
@NgModule({
  providers: [UserService]  // Module level service
})
export class UserModule { }

// Override for specific component
@Component({
  selector: 'specific-component',
  providers: [  // Component level service
    {
      provide: UserService,
      useClass: SpecificUserService  // Override with different implementation
    }
  ]
})
export class SpecificComponent { }
```
**Another approach using useFactory:**
```
@Component({
  providers: [
    {
      provide: UserService,
      useFactory: () => {
        return new UserService('specific config');
      }
    }
  ]
})
```
**Key points:**
- Component-level providers override module-level providers
- Only affects this component and its children
- Other components still use module-level service
- Can use useClass, useFactory, or useValue

### 13.what is dependency injection?
**Answer** Dependency Injection (DI) is a design pattern where components receive their dependencies from an external source rather than creating them internally.
**Injection Levels:**
```
// 1. Root level (singleton)
@Injectable({
    providedIn: 'root'
})

// 2. Module level
@NgModule({
    providers: [UserService]
})

// 3. Component level
@Component({
    providers: [UserService]  // New instance for this component
})
```
### 14.promise VS observable!
**Answer:** Here's a detailed comparison between Promises and Observables:

| Feature | Promise | Observable |
|---------|---------|------------|
| Values | Single value only | Multiple values over time |
| Execution | Eager (executes immediately) | Lazy (only when subscribed) |
| Cancellation | Not cancellable | Cancellable via unsubscribe |
| Operators | No built-in operators | Rich set of operators (map, filter, etc.) |
| Error Handling | Single catch block | Multiple error handlers possible |
| Async/Sync | Always async | Can be either sync or async |

**Best use cases:**
- Promises: Single async operations (API calls)
- Observables: Event streams, real-time data, multiple values

### 15.what is the zones!
**Answer:** Zones in Angular are provide a mechanism to intercept the scheduling and calling of asynchronous operations.

### 16.what is the change detection!
**Answer** Change detection is the process through which Angular checks to see whether your application state has changed, and if any DOM needs to be updated.

### 17. what is the interceptor in angular?
**Answer** An Interceptor in Angular is a service that allows you to intercept and modify HTTP requests and responses in your application. It acts as a middleware between your application and the server.

### 18. what is the CI/CD in github
**Answer** CI/CD (Continuous Integration/Continuous Deployment) in GitHub is automated through GitHub Actions.