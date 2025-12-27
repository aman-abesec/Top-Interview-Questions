# SOLID Principles in JavaScript (Practical & Real-World Examples)

This repository explains the **SOLID principles** using **real-world JavaScript use cases**, detailed explanations, and guidance on **when and where to apply each principle**. These examples are suitable for **Node.js backends, frontend applications (React/Vue), and large-scale JS systems**.

---

## 📌 Why SOLID Matters in JavaScript

JavaScript applications often grow quickly and become hard to maintain. Applying SOLID principles helps:

* Reduce bugs when features change
* Improve code readability for teams
* Make testing easier
* Avoid tightly coupled code
* Scale applications safely

---

## 1️⃣ Single Responsibility Principle (SRP)

> **A module or class should have only one responsibility and one reason to change.**

### 🧠 When to Use SRP

* When a file grows too large
* When one change breaks unrelated features
* When testing becomes difficult

### ❌ Bad Example (Multiple Responsibilities)

```js
class OrderService {
  createOrder(order) {
    console.log('Order created');
  }

  saveToDatabase(order) {
    console.log('Saving order to DB');
  }

  sendEmail(order) {
    console.log('Sending confirmation email');
  }
}
```

**Why this is bad:**

* Business logic, database logic, and notification logic are mixed
* Any change affects the same class

### ✅ Good Example (Separated Responsibilities)

```js
class OrderService {
  createOrder(order) {
    console.log('Order created');
  }
}

class OrderRepository {
  save(order) {
    console.log('Saving order to DB');
  }
}

class EmailService {
  send(order) {
    console.log('Sending confirmation email');
  }
}
```

✔ Each class has **one job**
✔ Easier to test and maintain

---

## 2️⃣ Open/Closed Principle (OCP)

> **Code should be open for extension but closed for modification.**

### 🧠 When to Use OCP

* Pricing rules
* Payment methods
* Feature flags
* Adapters / plugins

### ❌ Bad Example (Conditional Explosion)

```js
function calculateShipping(type, price) {
  if (type === 'standard') return price + 50;
  if (type === 'express') return price + 100;
}
```

**Problem:**

* Every new type requires modifying this function

### ✅ Good Example (Strategy Pattern)

```js
class ShippingStrategy {
  calculate(price) {
    return price;
  }
}

class StandardShipping extends ShippingStrategy {
  calculate(price) {
    return price + 50;
  }
}

class ExpressShipping extends ShippingStrategy {
  calculate(price) {
    return price + 100;
  }
}

function calculateShipping(strategy, price) {
  return strategy.calculate(price);
}
```

✔ Add new shipping methods without touching existing code

---

## 3️⃣ Liskov Substitution Principle (LSP)

> **Subtypes must be usable in place of their parent types without breaking behavior.**

### 🧠 When to Use LSP

* Inheritance hierarchies
* Framework extensions
* Polymorphic behavior

### ❌ Bad Example (Unexpected Behavior)

```js
class Payment {
  pay(amount) {
    console.log(`Paid ${amount}`);
  }
}

class FreePayment extends Payment {
  pay() {
    throw new Error('No payment required');
  }
}
```

**Problem:**

* Code expecting `Payment` breaks

### ✅ Good Example (Behavior Preserved)

```js
class Payment {
  pay(amount) {}
}

class CardPayment extends Payment {
  pay(amount) {
    console.log(`Paid ${amount} via card`);
  }
}

class FreePayment extends Payment {
  pay() {
    console.log('No payment required');
  }
}
```

✔ All subclasses respect parent expectations

---

## 4️⃣ Interface Segregation Principle (ISP)

> **Do not force classes to depend on methods they do not use.**

### 🧠 When to Use ISP

* Large interfaces
* Microservices
* Device or capability-based APIs

### ❌ Bad Example (Fat Interface)

```js
class Worker {
  work() {}
  eat() {}
  sleep() {}
}
```

### ✅ Good Example (Focused Interfaces)

```js
class Workable {
  work() {}
}

class Eatable {
  eat() {}
}

class HumanWorker extends Workable {
  work() {}
  eat() {}
}

class RobotWorker extends Workable {
  work() {}
}
```

✔ Classes only implement what they need

---

## 5️⃣ Dependency Inversion Principle (DIP)

> **High-level modules should depend on abstractions, not concrete implementations.**

### 🧠 When to Use DIP

* Swappable services
* External APIs
* Database layers
* Testing & mocking

### ❌ Bad Example (Tight Coupling)

```js
class MongoDB {
  connect() {
    console.log('MongoDB connected');
  }
}

class App {
  constructor() {
    this.db = new MongoDB();
  }
}
```

### ✅ Good Example (Dependency Injection)

```js
class Database {
  connect() {}
}

class MongoDB extends Database {
  connect() {
    console.log('MongoDB connected');
  }
}

class App {
  constructor(database) {
    this.db = database;
  }
}

const app = new App(new MongoDB());
```

✔ Easy to replace DB or mock in tests

---

## 🧪 Where SOLID Is Used in Real Projects

* **Node.js**: Services, repositories, controllers
* **React**: Hooks, services, UI logic separation
* **Microservices**: Clean boundaries
* **SDKs / Libraries**: Stable public APIs

---

## 📂 Recommended Project Structure

```
src/
 ├── services/
 ├── repositories/
 ├── strategies/
 ├── interfaces/
 └── app.js
```

---

## 📘 References

* Clean Architecture – Robert C. Martin
* Refactoring Guru

---

## 🧑‍💻 Author

**Aman Singh**

⭐ If this helped you, consider starring the repo!
