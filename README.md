# TypeScript-note


(1)   What is TypeScript?
(ans) TypeScript (TS) is a programming language built on top of JavaScript that adds static typing and other development features to JavaScript.

	In simple words, TypeScript is JavaScript with extra features that help you write cleaner, safer, and more maintainable code.
	It was developed by Microsoft.
	Why do we need TypeScript-> We need TypeScript because it helps us catch errors during development by checking data types.
	JavaScript allows a variable to hold different types of values, while TypeScript helps us define and maintain expected types.
	
(2) JavaScript vs TypeScript
	Feature		JavaScript		TypeScript
	Typing		Dynamic			Static 	(optional)
	Error detection	Mostly runtime		Compile-time + runtime
	Interfaces	No			Yes
	Type safety	Less			More
	Learning curve	Easy			Slightly harder
	Browser support	Directly supported	Compiles to JavaScript


(3) DataType
	(1) number → Numbers
	(2) string → Text
	(3) boolean → True / False
	(4) any → Any value without type safety
	(5) unknown → Any value with type checking
	(6) void → No return value
	(7) never → Never returns normally
	(8) array → Multiple values
	(9) object → Key-value pairs
	(10)tuple → Fixed types and positions
	(11)enum → Named constants
	(12)union → Multiple allowed types

(4) What is tsconfig.json in TypeScript?
(ans)	tsconfig.json is a configuration file that tells the TypeScript compiler (tsc) how to compile and check your TypeScript code.
	In simple words:
	Imagine you have a TypeScript project with 100 files. The TypeScript compiler needs to know:
	- Which files should it compile?
	- Where should it save the compiled JavaScript files?
	- Which JavaScript version should it generate?
	- How strictly should it check your code?
	- Should it allow certain types of errors?
	All these instructions are defined in tsconfig.json.

	"tsconfig.json is the configuration file of a TypeScript project. It tells the TypeScript compiler which files to compile,
	which JavaScript version to target, where to generate output files, and which type-checking rules to apply. 
	It helps maintain consistent compiler settings across the entire project."

(5) How to create tsconfig.json?
	npx tsc --init

(6) TypeScript Compiler (tsc)
(ans)	The TypeScript Compiler (tsc) is a tool that converts TypeScript code (.ts) into JavaScript code (.js).
	It also checks your TypeScript code for type-related errors before generating JavaScript.
	In simple words:
	You write TypeScript → tsc checks and compiles it → JavaScript is generated.
	Browsers and Node.js execute JavaScript, not TypeScript directly.

(7) Type Inference in TypeScript
(ans)	Type Inference is a feature in TypeScript that automatically detects the data type of a variable based on the value assigned to it.
	In simple words, you don't always need to explicitly write the data type. TypeScript can understand the type automatically.

	Without Type Inference (Explicit Typing):
	let username: string = "Krishna";
	let age: number = 22;
	let isDeveloper: boolean = true;
	//Here, we explicitly define the data types.
	

	With Type Inference (Implicit Typing):
	let username = "Krishna";
	let age = 22;
	let isDeveloper = true;
	//Here, TypeScript automatically identifies:

	Interview definition: Type Inference is a TypeScript feature that automatically determines the type of a variable, 
	function return value, or expression based on the available information, without requiring explicit type annotations.

(8)Type Annotations in TypeScript
(ans)	Type Annotations are used to explicitly specify the data type of a variable, function parameter, function return value, or object property in TypeScript.
	In simple words, Type Annotations tell TypeScript what type of data a variable should accept.
	We use a colon (:) to define a type.

	let username: string = "Krishna";

(9)Basic data types
	(1)string : let variableName: string = "value";
	(2)number : let variableName: number = value;
	(3)boolean : let variableName: boolean = true;
	(4)null: null represents the intentional absence of a value.
		In simple words, when you want to indicate that a variable currently has no value, you can assign null to it.
		For example:
		- A user has no profile picture.
		- An employee has no manager assigned.
		- An API response has no data.
		- A selected item has been cleared.

		let name: string | null = "Krishna";
		name = null;       // Allowed
		name = "Krishna";  // Allowed;
	
(5)undefined : undefined represents a variable that has been declared but has not been assigned a value.
		In simple words, when a variable exists but doesn't have an assigned value, its value is usually undefined.
		For example:
		- A variable is declared but no value is assigned.
		- An object property does not exist.
		- A function does not return anything explicitly.
		- An API response is missing an optional field.

		let age : string |undefined  ;
		console.log(age) //output undefined 

		"undefined is a primitive value that indicates a variable has not been assigned a value or a property is missing. 
		In TypeScript, with strictNullChecks enabled, we need to explicitly include undefined in a variable's type if we want it to accept undefined."

(6)any : any is a data type that allows a variable to store values of any data type without generating type errors.

		let data: any = "Krishna";
		console.log(data);


		let data: any = "Krishna";
		data = 22;              // Allowed
		data = true;            // Allowed
		data = [10, 20, 30];    // Allowed
		data = { name: "Krishna" }; // Allowed
		data = null;            // Allowed
		data = undefined;       // Allowed
		console.log(data);


		Why should we avoid any? 
		let username: any = "Krishna";
		console.log(username.toUpperCase());
		console.log(username.toFixed(2));

		The first statement works because strings have toUpperCase().
		But the second statement causes a runtime error because strings don't have toFixed().
		Problem: TypeScript doesn't catch this mistake because the variable is declared as any.
		
		"any is a special TypeScript type that allows a variable to hold values of any data type. 
		It disables most type checking for that variable, so TypeScript cannot catch many type-related errors. 
		Therefore, it should be avoided when possible."

(7)unknown : unknown is a data type that allows you to store values of any data type, but requires you to check the type before performing operations on that value.
		In simple words:
		unknown accepts any value, but TypeScript doesn't allow you to use that value until you verify its data type.
		It is a safer alternative to any.


		let data: unknown = "Krishna";
		if (typeof data === "string") {
		    console.log(data.toUpperCase());
		}

		Difference between any and unknown
		This is a very important interview question.
		any					unknown
		Accepts any value			Accepts any value
		No meaningful type safety		Type safety is maintained
		Allows operations without checking	Requires type checking before operations
		Less safe				More safe


		"unknown is a special TypeScript type that can hold values of any data type. 
		Unlike any, it does not allow us to perform operations directly on the value without first checking or narrowing its type.	
		It provides better type safety and is useful when handling dynamic or external data."

(8)Void : void is used to indicate that a function does not return a meaningful value.

		function greet(): void {
		    console.log("Hello Krishna");
		}
		greet();


		function displayUser(name: string): void {
		    console.log(`Welcome ${name}`);
		}
		displayUser("Krishna");  //output Welcome Krishna


		"void is a TypeScript type primarily used as a function return type. It indicates that a function does not return a meaningful value. 
		It is commonly used with functions that perform actions such as logging messages, updating data, or handling events."


(9)never : never represents a value that never occurs.
		In simple words, never is used when a function never completes normally or when a variable cannot have any possible value.
		It is commonly used in:
		- Functions that always throw errors.
		- Functions that never stop executing.
		- Exhaustive type checking.
		- Handling impossible conditions in TypeScript.

		function throwError(): never {
		    throw new Error("Something went wrong!");
		}
		throwError();

	(10)object:object is used to store multiple values in key-value pairs.

		let user: {
		  name: string;
		  age: number;
		  email: string;
		  isActive: boolean;
		} = {
		  name: "Krishna",
		  age: 23,
		  email: "krishna@example.com",
		  isActive: true
		};
		
		Optional Properties (?):  Sometimes an object property is not required. Use ? to make a property optional.
		Object Using type (Recommended) : Instead of writing the object structure repeatedly, you can create a reusable type.

		type User = {
		  id: number;
		  name: string;
		  email: string;
		  age?: number;
		};

		let user1: User = {
		  id: 1,
		  name: "Krishna",
		  email: "krishna@example.com"
		};

		let user2: User = {
		  id: 2,
		  name: "Rahul",
		  email: "rahul@example.com",
		  age: 25
		};


		Object Using interface :You can also define object structures using an interface.
		interface User {
		  id: number;
		  name: string;
		  email: string;
		}

		const user: User = {
		  id: 1,
		  name: "Krishna",
		  email: "krishna@example.com"
		};



(10) Array 
(11) Tuples
	A Tuple is a special type of array in TypeScript where you define the type of each element at a specific position.
	In a normal array, all elements usually have the same type. In a tuple, different positions can have different types.
	
	let user: [number, string, boolean] = [101, "Krishna", true];

	Tuple with Optional Elements
	let user: [number, string, boolean?];
	user = [101, "Krishna"];
	user = [102, "Rahul", true];
	
	Named Tuples
	let user: [id: number, name: string, isActive: boolean] = [101,"Krishna", true];

	Readonly Tuple
	let user: readonly [number, string] = [101, "Krishna"];
	console.log(user[0]); // Valid
	user[0] = 102; // Error
	user.push(103); // Error



