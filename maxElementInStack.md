# Tracking current Maximum Element in a Stack

Given a Stack, keep track of the maximum value in it. The maximum value may be the top element of the stack, but once a new element is pushed or an element is pop from the stack, the maximum element will be now from the rest of the elements.

*REQUIREMENT:* Push, Pop, Max should all be constant time

## Method 1 (Brute Force)
**Time Complexity:** O(n)
**Space** O(1)

## Method 2 (2 Stacks)
```
    1.) Create an auxiliary stack, say ‘trackStack’ to keep the track of maximum element
    2.) Push the first element to both mainStack and the trackStack.
    3.) Now from the second element, push the element to the main stack. Compare the element with the top element of the track stack, if the current element is greater than top of trackStack then push the current element to trackStack otherwise push the top element of trackStack again into it.
    4.)If we pop an element from the main stack, then pop an element from the trackStack as well.
    5.)Now to compute the maximum of the main stack at any point, we can simply print the top element of Track stack.
```

## Python Implementation
```
class StackWithMax: 
    def __init__(self): 
          
        # main stack  
        self.mainStack = []  
      
        # tack to keep track of 
        # max element  
        self.trackStack = [] 
  
    def push(self, x): 
        self.mainStack.append(x)  
        if (len(self.mainStack) == 1): 
            self.trackStack.append(x)  
            return
  
        # If current element is greater than  
        # the top element of track stack,  
        # append the current element to track  
        # stack otherwise append the element  
        # at top of track stack again into it.  
        if (x > self.trackStack[-1]):  
            self.trackStack.append(x)  
        else: 
            self.trackStack.append(self.trackStack[-1]) 
  
    def getMax(self): 
        return self.trackStack[-1] 
  
    def pop(self): 
        self.mainStack.pop()  
        self.trackStack.pop() 
 ```
 
