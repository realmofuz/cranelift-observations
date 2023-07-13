# Construction
This is a quick overview on how systems with the `Module` trait seem to work & allow you to start making Functions.


## Function
`Function` is a `struct`. It has just one field you should pay attention to, `name`. `name` is a `UserFuncName` type, this just means you have to assign it two integer values for it's name - one for the namespace, one for the index. For example, `(5, 2)` makes it the second function in the fifth namespace. You can assign the `name` & `signature` on creation with `Function::with_name_signature`.

### Signature
A `Signature` is what it says on the tin - it's a signature for the function. For example, here's a Rust function signature:
```rs
fn my_function(a: i32, b: i32) -> i64 
```
This is a header that describes the parameters & return type of the function. Here's what the same signature looks like in `CLIF` representation.
```clif
function %my_function(v0: i32, v1: i32) -> i32 windows_fastcall
```
You'll notice this is very similar to the Rust header - this is because they share similar integer types.

## Context
`Context` is a `struct`. It stores information associated with a `Function` you create. You usually won't have to worry about the inner data of `Context`. However, a useful function to keep in mind is `Context::verify`. This allows you to verify that your `Function` & it's `Context` is valid & possible to lower down to machine code. However, this doesn't mean that your code may run into bugs - it simply means that it's possible to do so.

## Module
This trait allows you to combine functions and data, and link them together. To construct a function with a `Module`:
1. first you must build the `Function` in the first place. 
2. Next, use `Module::declare_function(...)` to grab the Function ID (`FuncID` type). 
3. Finally, define it with `Module::define_function(...)`, with the first parameter being the `FuncId` you got from Step 2, and the second being the `Context`.