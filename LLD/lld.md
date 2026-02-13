# LLD Design Patterns in JavaScript

This guide explains commonly used **Design Patterns in Low-Level Design (LLD)** interviews with:

- ✅ When to use
- ✅ JavaScript code example
- ✅ Real-world interview use case

---

# 1️⃣ Singleton Pattern

## ✅ When to Use

- When only **one instance** should exist in the system.
- Shared resources like:
  - Database connection
  - Logger
  - Configuration manager
  - Cache
  - Main system object (ParkingLot, ElevatorSystem)

---

## 🔥 Example: Logger

```js
class Logger {
  constructor() {
    if (Logger.instance) {
      return Logger.instance;
    }
    Logger.instance = this;
  }

  log(message) {
    console.log(`[LOG]: ${message}`);
  }
}

const logger1 = new Logger();
const logger2 = new Logger();

console.log(logger1 === logger2); // true
```

### 🧠 Interview Use Case
- Parking Lot system → Only one ParkingLot instance
- Central logging service

---

# 2️⃣ Factory Pattern

## ✅ When to Use

- Object creation depends on input
- Creation logic is complex
- Want to hide object creation logic
- Avoid using `new` everywhere

---

## 🔥 Example: Vehicle Factory

```js
class Car {
  drive() {
    console.log("Driving Car");
  }
}

class Bike {
  drive() {
    console.log("Driving Bike");
  }
}

class VehicleFactory {
  static createVehicle(type) {
    if (type === "car") return new Car();
    if (type === "bike") return new Bike();
    throw new Error("Invalid vehicle type");
  }
}

const vehicle = VehicleFactory.createVehicle("car");
vehicle.drive();
```

### 🧠 Interview Use Case
- Ticket types (Silver, Gold, Platinum)
- Different vehicle types
- Different user roles

---

# 3️⃣ Observer Pattern

## ✅ When to Use

- One-to-many dependency
- When state changes should notify multiple subscribers
- Event-driven systems

---

## 🔥 Example: Notification System

```js
class Subject {
  constructor() {
    this.observers = [];
  }

  subscribe(observer) {
    this.observers.push(observer);
  }

  notify(data) {
    this.observers.forEach(observer => observer.update(data));
  }
}

class User {
  constructor(name) {
    this.name = name;
  }

  update(data) {
    console.log(`${this.name} received: ${data}`);
  }
}

const subject = new Subject();
const user1 = new User("Aman");
const user2 = new User("Rahul");

subject.subscribe(user1);
subject.subscribe(user2);

subject.notify("New movie released!");
```

### 🧠 Interview Use Case
- Order status updates
- Stock price system
- Elevator status notifications
- Push notification system

---

# 4️⃣ Strategy Pattern

## ✅ When to Use

- Multiple algorithms available
- Need to switch behavior at runtime
- Avoid large if-else blocks
- Future extension expected

---

## 🔥 Example: Payment Strategy

```js
class CreditCardPayment {
  pay(amount) {
    console.log(`Paid ${amount} using Credit Card`);
  }
}

class UpiPayment {
  pay(amount) {
    console.log(`Paid ${amount} using UPI`);
  }
}

class PaymentContext {
  constructor(strategy) {
    this.strategy = strategy;
  }

  setStrategy(strategy) {
    this.strategy = strategy;
  }

  pay(amount) {
    this.strategy.pay(amount);
  }
}

const payment = new PaymentContext(new CreditCardPayment());
payment.pay(1000);

payment.setStrategy(new UpiPayment());
payment.pay(500);
```

### 🧠 Interview Use Case
- Parking fee calculation
- Lift selection algorithm
- Discount calculation
- Different pricing logic

---

# 5️⃣ Decorator Pattern

## ✅ When to Use

- Add functionality dynamically
- Avoid subclass explosion
- Extend behavior without modifying base class

---

## 🔥 Example: Coffee Customization

```js
class Coffee {
  cost() {
    return 100;
  }
}

class MilkDecorator {
  constructor(coffee) {
    this.coffee = coffee;
  }

  cost() {
    return this.coffee.cost() + 20;
  }
}

class SugarDecorator {
  constructor(coffee) {
    this.coffee = coffee;
  }

  cost() {
    return this.coffee.cost() + 10;
  }
}

let coffee = new Coffee();
coffee = new MilkDecorator(coffee);
coffee = new SugarDecorator(coffee);

console.log(coffee.cost()); // 130
```

### 🧠 Interview Use Case
- Add extra services to booking
- Subscription add-ons
- Middleware in API

---

# 6️⃣ Builder Pattern

## ✅ When to Use

- Object has many optional parameters
- Avoid long constructors
- Step-by-step object creation

---

## 🔥 Example: User Builder

```js
class User {
  constructor(builder) {
    this.name = builder.name;
    this.age = builder.age;
    this.phone = builder.phone;
  }
}

class UserBuilder {
  setName(name) {
    this.name = name;
    return this;
  }

  setAge(age) {
    this.age = age;
    return this;
  }

  setPhone(phone) {
    this.phone = phone;
    return this;
  }

  build() {
    return new User(this);
  }
}

const user = new UserBuilder()
  .setName("Aman")
  .setAge(25)
  .setPhone("9999999999")
  .build();

console.log(user);
```

### 🧠 Interview Use Case
- Booking object
- Order creation
- Elevator request object
- Complex configuration object

---

# 🎯 Most Asked Patterns in LLD Interviews

For SDE-II roles:

1. Singleton
2. Factory
3. Strategy
4. Observer
5. Builder

---

# 🚀 How Interviewers Indirectly Hint Patterns

They won’t say:

> "Use Strategy pattern"

Instead they say:

- "We may add new payment types in future"
- "Fee calculation logic may change"
- "Different algorithms may be added"

👉 That means use **Strategy Pattern**

---

# 🏆 Common LLD Systems Where These Patterns Are Used

- Parking Lot System
- Elevator System
- Ticket Booking System
- Food Delivery System
- Splitwise
- Ride Sharing

---

# 📌 Final Tip

In most real LLD interviews:

- Use **Singleton** → Main system
- Use **Factory** → Object creation
- Use **Strategy** → Business logic
- Use **Observer** → Notifications
- Use **Builder** → Complex objects

---

⭐ Master these 5 patterns and you are 80% ready for LLD interviews.
