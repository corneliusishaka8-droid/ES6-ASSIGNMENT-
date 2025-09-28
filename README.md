# ES6-ASSIGNMENT-
Course assignment 
// ======================================================
// ES6 Assignment — All Concepts in One File
// Name: Ishaka Cornelius
// Matric Number: 24/2497
// ======================================================


// ======================= 1. CLASSES ===================
class Person {
  #id;
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.#id = Math.floor(Math.random() * 10000);
  }

  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  }

  set fullName(value) {
    const [first, ...rest] = value.split(" ");
    this.firstName = first;
    this.lastName = rest.join(" ");
  }

  get id() { return this.#id; }

  static isPerson(obj) { return obj instanceof Person; }
}

class Student extends Person {
  constructor(firstName, lastName, level) {
    super(firstName, lastName);
    this.level = level;
  }
  describe = () => `${this.fullName} (Level: ${this.level})`;
}

const bob = new Student("Bob", "Okoro", "200");
console.log("=== CLASSES ===");
console.log(bob.describe(), "| isPerson?", Person.isPerson(bob));


// ================ 2. ARROW FUNCTIONS ==================
const square = x => x * x;
const sum = (a, b) => a + b;
const toUpper = s => s.toUpperCase();

console.log("\n=== ARROW FUNCTIONS ===");
console.log("square(5):", square(5));
console.log("sum(2,3):", sum(2, 3));
console.log("toUpper('hello'):", toUpper("hello"));

const counter = {
  value: 0,
  start() {
    const tick = () => { this.value++; };
    tick(); tick();
  }
};
counter.start();
console.log("Counter value:", counter.value);


// ================== 3. VARIABLES ======================
var a = 1;
let b = 2;
const c = 3;
console.log("\n=== VARIABLES ===");
console.log("a,b,c:", a, b, c);

{
  let inside = "inside block";
  var leaks = "I leak outside (var)";
  console.log(inside);
}
console.log("var leaks:", leaks);

const user = { name: "Zainab" };
user.name = "Zee";
console.log("Mutated const object:", user);


// ============== 4. ARRAY METHODS ======================
const nums = [5, 2, 9, 1, 5, 6];

console.log("\n=== ARRAY METHODS ===");
console.log("Squares:", nums.map(n => n * n));
console.log("Evens:", nums.filter(n => n % 2 === 0));
console.log("Sum:", nums.reduce((acc, n) => acc + n, 0));
console.log("First > 5:", nums.find(n => n > 5));
console.log("Has negatives?", nums.some(n => n < 0));
console.log("All positive?", nums.every(n => n >= 0));
console.log("Sorted:", [...nums].sort((x, y) => x - y));


// ============= 5. DESTRUCTURING =======================
console.log("\n=== DESTRUCTURING ===");
const rgb = [255, 165, 0];
const [r, g, b2] = rgb;
console.log("RGB:", r, g, b2);

const [first, , third = "default"] = ["A"];
console.log("First:", first, "| Third (default):", third);

const person = { name: "Ngozi", city: "Lagos", age: 21 };
const { name, city, age } = person;
console.log("Name:", name, "| City:", city, "| Age:", age);

const { name: n, ...rest } = person;
console.log("n:", n, "| rest:", rest);


// ============== 6. MODULES (SIMULATED) ================
// Normally these would be separate .mjs files.
// Here, we simulate imports/exports inline.

console.log("\n=== MODULES (SIMULATED) ===");

const math = {
  add: (a, b) => a + b,
  mul: (a, b) => a * b,
};
function titleCase(str) {
  return str
    .toLowerCase()
    .split(" ")
    .map(w => w.charAt(0).toUpperCase() + w.slice(1))
    .join(" ");
}

console.log("add(2,3):", math.add(2,3));
console.log("mul(4,5):", math.mul(4,5));
console.log("titleCase:", titleCase("hello from lagos"));


// ============ 7. TERNARY OPERATORS ====================
console.log("\n=== TERNARY OPERATORS ===");
const score = 72;
const grade = score >= 70 ? "A" : score >= 60 ? "B" : "C";
console.log("Score:", score, "| Grade:", grade);

const isLoggedIn = false;
const btnText = isLoggedIn ? "Logout" : "Login";
console.log("Button text:", btnText);


// ============ 8. SPREAD OPERATORS =====================
console.log("\n=== SPREAD OPERATORS ===");
const arr1 = [1,2,3];
const arr2 = [...arr1, 4, 5];
console.log("arr1:", arr1, "| arr2:", arr2);

const user2 = { id: 1, name: "Amaka" };
const updated = { ...user2, role: "admin" };
console.log("Updated user:", updated);

const defaults = { theme: "light", sidebar: true };
const settings = { sidebar: false };
const finalConfig = { ...defaults, ...settings };
console.log("Final config:", finalConfig);
