## 20. Valid Parentheses
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.

```
Example 1:

Input: s = "()"
Output: true
Example 2:

Input: s = "()[]{}"
Output: true
Example 3:

Input: s = "(]"
Output: false
Example 4:

Input: s = "([)]"
Output: false
Example 5:

Input: s = "{[]}"
Output: true
```

```Java

/*
    Using Stack:
    1. Initialize a stack S.
    2. Process each bracket of the expression one at a time.
    3. If we encounter an opening bracket, we simply push it onto the stack. This means we will process it later, let us simply     move onto the sub-expression ahead.
    4. If we encounter a closing bracket, then we check the element on top of the stack. If the element at the top of the stack     is an opening bracket of the same type, then we pop it off the stack and continue processing. Else, this implies an         invalid expression.
    5. In the end, if we are left with a stack still having elements, then this implies an invalid expression.
*/
class Solution {
    public boolean isValid(String s) {
        
        // Map<K, v>
        HashMap<Character, Character> map = new HashMap<Character, Character>();
        map.put(')', '(');
        map.put('}', '{');
        map.put(']', '[');
        
        
        Stack<Character> stack = new Stack<>();
        
        for(int i =0; i< s.length(); i++){
            char c = s.charAt(i);
            
            //if the current is opening bracket
            if( !map.containsKey(c)){
                stack.push(c);
            }

            //else if the current value is closing bracket
            else{
                //get the top element of the stack
                char topE = stack.empty() ? '@' : stack.pop();
                
                //if the map for this bracket doesnt match this element, return false
                if(topE != map.get(c))
                    return false;
            }
        }
        return stack.isEmpty();
    }
}
```