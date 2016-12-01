### Implement Queue using Stacks
Implement the following operations of a queue using stacks.

push(x) -- Push element x to the back of queue. //将元素x添加到队列后面
pop() -- Removes the element from in front of queue. //从队列前面删除元素
peek() -- Get the front element. //获取队列最前面的元素
empty() -- Return whether the queue is empty. //返回队列是否为空

You must use only standard operations of a stack -- which means only push to top, peek/pop from top, size, and is empty operations are valid.
Depending on your language, stack may not be supported natively. You may simulate a stack by using a list or deque (double-ended queue), as long as you use only standard operations of a stack.
You may assume that all operations are valid (for example, no pop or peek operations will be called on an empty queue).

* 使用一个辅助栈作为栈的元素的反转
``` java
class MyQueue {
    Stack<Integer> s1 = new Stack<>();
    Stack<Integer> s2 = new Stack<>();
    //Push element x to the back of queue.
    public void push(int x) {
         while(!s1.isEmpty()) {
             s2.push(s1.pop());
          }
         s1.push(x);
         while(!s2.isEmpty()) {
             s1.push(s2.pop());
         }
      }
      //Removes the element from in front of queue.
      public void pop() {
          s1.pop();
       }
       public int peek() {
           return s1.peek();
        }
        //Return whether the queue is empty.
        public boolean empty() {
            return s1.isEmpty();
         }
   }
```
``` python
class Queue(object):
    def __init__(self):
        """
        initialize your data structure here.
        """
        self.temp=[]
        

    def push(self, x):
        """
        :type x: int
        :rtype: nothing
        """
        self.temp.append(x)
        

    def pop(self):
        """
        :rtype: nothing
        """
        self.temp.remove(self.temp[0]) if len(self.temp)!=0 else None
        

    def peek(self):
        """
        :rtype: int
        """
        return self.temp[0] if len(self.temp)!=0 else None
        

    def empty(self):
        """
        :rtype: bool
        """
        return True if len(self.temp)==0 and self.temp is not None else False
```