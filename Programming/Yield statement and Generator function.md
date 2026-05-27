---
description: All about the generator functions
layout: post
---
### Use cases
- Reduce the memory usage
- Looping and iterate the file and each lines without overloading or f**k up the memory
- Handle and coupled with asynchronization jobs.

```python
def square_calculator():
	i = 0
	while i < 10:
		yield i * i
		i++

if name == '__main__':
	for i in square_calculator():
		print(result)
```

- The generator function can exit and re-enter the context with binding variables. So it's known as lazy-evaluation, call when needed. `square_calculator()` here is similar with an iterator and be called when the loop trigger it each time. The returned variable in the previous call in the memory storage can be released without waiting to return as an array like a normal function.

The generator function is already supported in so many languages such as Python, Javascript or Java as well.


### Yield in Python
Generator functions in the python can be created via the `yield` statement. In another way, it can be created via the generator expressions as well, as known as `generator comprehension`
For e.g
```python
csv_gen = (row for row in open(file_name))
```


### Advanced generator methods in Python
- `yield` in Python can be used like a expression, rather than a statement. 
```python
i = (yield num)
```
It looks like `i` takes the value that is yielded, and we can use this to manipulate the yielded value. We can use the `.send()` a value back to the generator.

```python
gen = call_a_generator_func()
for gen_returned_value in pal_gen:
    print(gen_returned_value) # print the yield value
    gen.send(gen_returned_value + 9) # modify the yield response
```


Here is an example where we manipulate the i value after triggering the generator function then modifying the response and add a condition to check None (based on the passed value `gen_returned_value + 1`)
```python
def call_a_generator_func():  
    num = 0  
    while True:  
        if num < 99:  
            i = (yield num)  
            if i is not None: # handle the response of yield statement  
                num = i  
  
            num += 1  
  
if __name__ == '__main__':  
    gen = call_a_generator_func()  
    for gen_returned_value in gen:  
        print(gen_returned_value)  # print the yield value  
        gen.send(gen_returned_value + 1)  # modify the yield response and continue the loop  
    print("Here we can call it as the Python coroutine")
```
- In Python, `throw()` allows the main flow to throw an exception with the generator function
- Also `.close()` to close the generator iteration.