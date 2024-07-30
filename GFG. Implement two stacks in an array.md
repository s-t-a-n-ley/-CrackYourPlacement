Your task is to implement  2 stacks in one array efficiently. You need to implement 4 methods.

twoStacks : Initialize the data structures and variables to be used to implement  2 stacks in one array.
push1 : pushes element into first stack.
push2 : pushes element into second stack.
pop1 : pops element from first stack and returns the popped element. If first stack is empty, it should return -1.
pop2 : pops element from second stack and returns the popped element. If second stack is empty, it should return -1.

Example 1:

Input:
push1(2)
push1(3)
push2(4)
pop1()
pop2()
pop2()
Output:
3 4 -1
Explanation:
push1(2) the stack1 will be {2}
push1(3) the stack1 will be {2,3}
push2(4) the stack2 will be {4}
pop1()   the poped element will be 3 from stack1 and stack1 will be {2}
pop2()   the poped element will be 4 from stack2 and now stack2 is empty
pop2()   the stack2 is now empty hence returned -1

**Solution**
```
class TwoStacks:
    def __init__(self, size):
        self.size = size
        self.arr = [0] * size
        self.top1 = -1       # Top of Stack 1
        self.top2 = size     # Top of Stack 2

    def push1(self, value):
        # Check if there is space available in the array for Stack 1
        if self.top1 < self.top2 - 1:
            self.top1 += 1
            self.arr[self.top1] = value
        else:
            raise OverflowError("Stack Overflow for Stack 1")

    def push2(self, value):
        # Check if there is space available in the array for Stack 2
        if self.top1 < self.top2 - 1:
            self.top2 -= 1
            self.arr[self.top2] = value
        else:
            raise OverflowError("Stack Overflow for Stack 2")

    def pop1(self):
        if self.top1 >= 0:
            value = self.arr[self.top1]
            self.top1 -= 1
            return value
        else:
            raise IndexError("Stack Underflow for Stack 1")

    def pop2(self):
        if self.top2 < self.size:
            value = self.arr[self.top2]
            self.top2 += 1
            return value
        else:
            raise IndexError("Stack Underflow for Stack 2")

    def is_empty1(self):
        return self.top1 == -1

    def is_empty2(self):
        return self.top2 == self.size

    def is_full(self):
        return self.top1 + 1 >= self.top2


```
