# Chapter 3

## Variables and mutability

By default variables are immutable.
You still have the option to make your variables mutable.

You can make them mutable by adding mut in front of the variable name.

`fn main() { let mut x = 5; println!("The value of x is: {x}"); x = 6; println!("The value of x is: {x}"); }`

That works fine.

## Constants

Constants are values that are bound to a name and are not allowed to change, but there are a few differences between constants and variables.
You aren’t allowed to use mut with constants.
You must always annotate the type.
You need to user upeercase with underscores.

Constants can be declared in any scope, including the global scope, which makes them useful for values that many parts of code need to know about.

Constants may be set only to a constant expression, not the result of a value that could only be computed at runtime.

Constants are valid for the entire time a program runs, within the scope they were declared in.

## Shadowing

You can declare a new variable with the same name as a previous variable. The second variable is what the compiler will see when you use the name of the variable.

`
fn main() {
let x = 5;

    let x = x + 1;

    {
        let x = x * 2;
        println!("The value of x in the inner scope is: {x}");
    }

    println!("The value of x is: {x}");

}
`

`$ cargo run Compiling variables v0.1.0 (file:///projects/variables) Finished dev [unoptimized + debuginfo] target(s) in 0.31s Running`target/debug/variables`
The value of x in the inner scope is: 12
The value of x is: 6

`

Shadowing is different from marking a variable as mut, because we’ll get a compile-time error if we accidentally try to reassign to this variable without using the let keyword.

The other difference between mut and shadowing is that because we’re effectively creating a new variable when we use the let keyword again, we can change the type of the value but reuse the same name.

Example:
`fn main() { let mut spaces = " "; spaces = spaces.len(); }`
Error

`fn main() { let spaces = " "; let spaces = spaces.len(); }`
Works

Link: https://doc.rust-lang.org/book/ch03-02-data-types.html

## Data Types
