 # 0x244 - Functions

- Instructions that need to be used several times can be grouped into reusable functions
- Arguments (variables) can be passed into functions

  `Function Turn(variable_direction)`
  `{`
    `Activate the variable_direction blinker;`
    `Slow down;`
    `Check for oncoming traffic;`
    `while(there is oncoming traffic)`
    `{`
        `Stop;`
        `Watch for oncoming traffic;`
    `}`
    `Turn the steering wheel to the variable_direction;`
    `while(turn is not complete)`
    `{`
        `if(speed < 5 mph)`
            `Accelerate;`
    `}`
    `Turn the steering wheel back to the original position;`
    `Turn off the variable_direction blinker;`
`}`


- By default, functions return a value to the caller
- In C keywords are declared by the data type of the variable they are returning
- This function returns an integer
  `int factorial(int x)`
  `{`
    `int i;`
    `for(i=1; i < x; i++)`
        `x *= i;`
    `return x;`
   `}`
  
  - In C, the complier needs to know about functions before it can use them
    - This can be done by 
      - Writing the function before you use it
      - Using a function prototype
        - Function prototypes tell the compiler to expect a function with a specific name
        - Function prototypes are typically located at the beginning of the program
        - The complier only cares about the function name, return data type, and the data type of any arguments
        - Example
          - `int factorial(int);`
