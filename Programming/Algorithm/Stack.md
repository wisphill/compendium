# Stock span problem

Số ngày liên tiếp trước đó mà giá ≤ giá hôm nay
Maintain a wall, no need to for for each step
[100, 80, 60, 70, 60, 75, 85]
100: [0] span 1
80: [0, 1] span 1
60: [0, 1, 2] span 1
70: [0, 1, 3] span = 3 - 1
60: [0, 1, 3, 4] span = 1
75: [0, 1, 5] span = 5 - 1
85: [0] span = 6 - 0
=> 1, 1, 1, 2, 1, 4, 6

// False, maintain 2 stacks
// Valid Parentheses với wildcard
The Sample: S = "((\*\*)) )))"
LeftStack: []
StarStack: []

// Simplify Path (Unix path)
"/a/./b/../../c/" → "/c"
[a]
[a]
[a, b]
[a]
[]
[c] => /c

// Evaluate Reverse Polish Notation (RPN)

```bash
["2","1","+","3","*"] → 9
Number stack: [2]
Number stack: [2, 1]
Number stack: [3] + plus and push
Number stack: [3, 3]
Number stack: [9] + multiply and push
```

Remove K Digits

"1432219", k=3 → "1219"
[1] k = 3
[1, 4] k = 3
3: [1, 3] k = 2
2: [1, 2] k = 1
2: [1, 2, 2] k = 1
1: [1, 2, 1] k = 0
9: [1, 2, 1, 9]
"1439219", k=3 → "1219"
[1] k = 3
[1, 4] k = 3
[1, 3] k = 2
[1, 3, 9] k = 2
[1, 3, 2] k = 1
[1, 2] k = 0 -> "1219"

Daily Temperatures
How many days to wait until the next warmer day?
Stack để lưu trữ các câu hỏi chưa có lời đáp (những ngày đang chờ ấm lên)
[73,74,75,71,69,72,76,73]
