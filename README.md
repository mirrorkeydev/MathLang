# MathLang: Programming Language Fundamentals Project
A stack-based language that performs basic mathematic/logic operations.

## Team Members
Name			 | ONID Username
:---------------:|:--------------:
Melanie Gutzmann | gutzmanm
Cole Swanson     | swanscol
Hannah Vaughan   | vaughanh

## Language Introduction
Our language, named _MathLang_, is a stack-based language with a stack that can have integers, doubles, booleans, tuples, commands, and functions as its values. These values can be pushed onto the stack, and mathematical operations can be performed on the integer, boolean, and tuple values in the stack. Conditional logic allows for differing series of commands to be executed with if/else branching; while loops allow for looping to occur on values on the stack, and tuples can be both constructed and deconstructed to provide invertability. A "Mathlude" contains functions that perform less common mathematical operations, such as `factorial`, `percent`, and `summation`.

## Usage
### Setup Instructions
_MathLang_ is intended to be run from GHCi, so the _Lang_ module must be loaded to run programs in the language.

### Good Program Examples and their Outputs
#### Example 1: Convert Integers to Digits
This program deconstructs an integer into its digits. The digits are then pushed back onto the stack as individual integers.
```haskell
-- Prebuilt example:
run int2digit_example i2d_functions
>>> Expected Output: Just [I 2,I 3,I 5,I 2,I 3,I 4]

-- Custom argument:
prog int2digit_example [I 2837] i2d_functions
>>> Expected Output: Just [I 2,I 8,I 3,I 7]

-- Full program:
prog [Call "preprocessing", S (While Less [Call "deconstruct"]), Push (F "cleanup"), CallStackFunc] [I 2837] [  ("preprocessing", [E Dup, Push (I 0)]), ("deconstruct", [E Dup, Push (I 10), E Mod, Swap, Push (I 10), Swap, E Div, E Dup, Push (I 0)]), ("cleanup", [Pop])]
>>> Expected Output: Just [I 2,I 8,I 3,I 7]
```

#### Example 2: TBA

#### Further Examples
Further examples of programs written in our language can be found in our "Mathlude". This standard library contains functions that allow users of our language to perform mathmatical calculations. Users can call functions such as `factorial`, `summation`, and `percent`. These functions are automatically included in the list of accessible functions when programs are run using the `run` keyword.

```haskell
run [Push (I 6), Call "factorial"] []
>>> Expected Output: Just [I 720]
```


### Bad Program Examples and their Outputs
```haskell
expr Add [I 1,B True,I 2]
>>> Expected Output: Nothing
```

```haskell
expr Mul [B False,I 1,I 2]
>>> Expected Output: Nothing
```

```haskell
expr Div [I 5,I 0,I 1]
>>> Expected Output: Nothing
```

```haskell
expr Div [I 5,B True,I 1]
>>> Expected Output: Nothing
```

```haskell
expr Equ [B True,T (B False) (B True)]
>>> Expected Output: Nothing
```

```haskell
expr (If [Push (I 5)] [Push (B False)]) [T (B True) (I 1)]
>>> Expected Output: Nothing
```

```haskell
stmt (While Equ [Push (I 5),E Add]) [B True,I 4]
>>> Expected Output: Nothing
```

```haskell
prog [E Add,E Equ] []
>>> Expected Output: Nothing
```
