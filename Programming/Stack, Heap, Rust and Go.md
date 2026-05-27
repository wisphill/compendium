---
layout: post
description: Some notes about the references feature of the Rust, Slack, Heap, Rust
---
#stack #memory #rust #go #garbage_collector
```table-of-contents
```
# Stack memory
- In RAM
- It's stack, the memory allocation's auto cleaned after the function exits
- Limited by OS (2Mb, 8Mb) - can check by using `ulimit -s`
- Created per functions for e.g
- Stack is a block with a fixed size in the RAM, when it's deleted, it's considered as no longer used, and can be assigned to another allocation.

# Heap memory
- In RAM
- It's free space, the program must to find a free space to allocate the memory, so it costs management time
- Data on the heap exists only if there's no longer a pointer to that.
- GC have to scan whole HEAP to find out which is no longer used
- Fragmentation - there are some "holes" after GC, sometimes, it's too small to fill new objects with the medium size.

# Comparison

|          | Stack                   | Heap                                            |
| -------- | ----------------------- | ----------------------------------------------- |
| Size     | Max 2Mb based on OS     | Free space                                      |
| Clean up | LIFO, by moving pointer | By GC, can create small holes, create fragments |

# Golang
- Utilize Heap by managing it, by assigning their own stacks on the physical Heap memory, and using the Stack mechanism to cleanup
- Only use Stack when booting up the program or running the CGO (with C)
- GC: Tricolor Mark-and-Sweep algorithm
- Allow the GC to run at the same time with their goroutines. Go uses `Write Barrier`, it's script that will be run whenever there is a change of pointer on the Heap, the white object in the Tricolor Mark-and-Sweep algorithm will be marked as gray to avoid wrong deletion.
# Rust
- Owner for each value in program with strict rules
- Similar as C++, it follows the specifications of memory
- At a specific time, there is one owner of a value, if the owner is out of scope, the value will be dropped.
```
{
	// "hello" được cấp phát trên Heap, 's' nằm trên Stack trỏ tới nó
    let s = String::from("hello"); 
} // 's' ra khỏi scope, Rust tự động gọi hàm `drop`, bộ nhớ Heap của "hello" được giải phóng.
```
- No need GC, Rust adds code to cleanup at the coding time.
- Prevent double cleanup HEAP by `move` mechanism. When the function ends, only s2 will be dropped
```
let s1 = String::from("hello");
let s2 = s1; // Giá trị đã "move" sang s2. s1 không còn giá trị, bạn không thể dùng s1 nữa.
```
- Borrowing uses Immutable Reference (`&T`), so the original variable does not loose the ownership
```
fn main() {
    let s1 = String::from("hello"); // s1 sở hữu "hello"

    let len = tinh_do_dai(&s1); // s1 cho mượn địa chỉ thông qua &s1

    println!("Giá trị của s1 vẫn còn: {}", s1); // Vẫn dùng được s1 ở đây!
}

fn tinh_do_dai(s: &String) -> usize { // s chỉ là người mượn
    s.len() 
} // s ra khỏi phạm vi ở đây, nhưng vì nó chỉ mượn nên "hello" không bị xóa.
```
- Borrowing use Mutable Reference (&mut T), allow reference and editing but only one can edit at a time to prevent the data racing.

## Ownership rules
1. Each value in Rust has an owner
2. Each value has `only one` owner at a time
3. If the owner goes out of scope, so the value will be dropped and free in the memory.

## Move data assignee
Let's take an example
```rust
let x = String::from("mom");
let y = x;
print("{:?}", x); // throw error because of borrowing of moved value `x`, the ownership has been changed
```
1. The string value `mom` has a dynamic size and be stored in the HEAP memory and its ownership is `x` variable
2. The assignee is changed to y and now y is the new ownership and it has a pointer point to the value `mom`
So we call this as the value of `x` has been moved