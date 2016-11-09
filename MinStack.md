### Min Stack
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

* 设计一个实现push,pop,top, getMin(在常量时间检索最小元素)的栈
	* push(x) -- Push element x onto stack.
	* pop() -- Removes the element on top of the stack.
	* top() -- Get the top element.
	* getMin() -- Retrieve the minimum element in the stack.
	
``` java
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> Returns -3.
minStack.pop();
minStack.top();      --> Returns 0.
minStack.getMin();   --> Returns -2.
```
* 思路：利用Java 的Stack类实现，设置int类型的min，用来更新最小数
``` java
public class MinStack {

    /** initialize your data structure here. */
    public MinStack() {
        
    }
    Stack<Integer> stack = new Stack<>();
    int min = Integer.MAX_VALUE;
    
    public void push(int x) {
        if(x<=min){
            stack.push(min);
            min = x;
        }
        stack.push(x);
    }
    
    public void pop() {
        if(stack.peek()==min){
            stack.pop();
            min = stack.pop();
        }else{
            stack.pop();
        }
    }
    /**
    public void pop() {
       if(stack.pop() ==min) {
          min =stack.pop();
          }
     }
    */
    
    public int top() {
        return stack.peek();
    }
    
    public int getMin() {
        return min;
    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(x);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */    
```
* 下面这个方法是根据LinkedList的push()操作是有序的特性，一个list存放元素，如果push的x小于现有最小元素的值，则需要更新
``` java
public class MinStack {
   public MinStack() {}
   LinkedList<Integer> s = new LinkedList<>(); //存放元素的list
   LinkedList<Integer> m = new LinkedList<>(); //存放最小值的list
   public void push(int x) {
      if(m.isEmpty()) {
          m.add(x);
        }else if(x<=m.get(m.size()-1)) {
            m.add(x);
        }
        s.add(x);
     }
     public void pop() {
        if(s.size()<1) return;
        if(top() == m.get(m.size()-1)) {
            m.remove(m.size()-1);
          }
          s.remove(s.size()-1);
      }
      public int top() {
        if(s.size() <1) {
           return 0;
         }
         return s.get(s.size()-1);
      }
      public int getMin() {
          return m.get(m.size() -1);
       }
 }         
```
* 简洁的Python写法，列表嵌套存储最小的值
``` python
class MinStack(object):

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.stack = []
        

    def push(self, x):
        """
        :type x: int
        :rtype: void
        """
        self.stack.append((x,min(self.getMin(), x)))
        
        

    def pop(self):
        """
        :rtype: void
        """
        self.stack.pop()
        

    def top(self):
        """
        :rtype: int
        """
        return self.stack[-1][0]

    def getMin(self):
        """
        :rtype: int
        """
        if self.stack:
            return self.stack[-1][-1]
        return sys.maxint
        


# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(x)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```

