---
layout: post
title: LeetCode 20. 有效的括号
gh-repo: youcoding98/youcoding98.github.io
gh-badge: [star, fork, follow]
tags: [leetcode]
---

###  题目  

####  1. 题解之进栈出栈法：
  遇到开括号，我们只需将其推到栈上即可。这意味着我们将稍后处理它，让我们简单地转到前面的 子表达式。   
  遇到一个闭括号，那么我们检查栈顶的元素。如果栈顶的元素是一个 相同类型的 左括号，那么我们将它从栈中弹出并继续处理。否则，这意味着表达式无效
####  1.解题思路


```java
class ValidParentheses20 {
    private HashMap<Character,Character> mappings;

    public ValidParentheses20()
    {
        this.mappings = new HashMap<Character, Character>();
        this.mappings.put(')','(');
        this.mappings.put('}','{');
        this.mappings.put(']','[');
    }
    public boolean isValid(String s)
    {
        Stack<Character> stack = new Stack<Character>();

        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);

            if (this.mappings.containsKey(c))
            {
                char topElement = stack.isEmpty() ? '#' : stack.pop();

                if (topElement != this.mappings.get(c))
                {
                    return false;
                }


            }else {
                stack.push(c);
            }
        }

        return stack.isEmpty();

    }
}

```

####  2. 题解之消消乐法

####  2.解题思路
对于字符串的掌握真的让人佩服

```java

class Solution {
    public boolean isValid(String s) {
        
        while (s.contains("{}")||s.contains("[]")|| s.contains("()")){

            if(s.contains("{}")) s=s.replace("{}","");
            if(s.contains("()")) s=s.replace("()","");
            if(s.contains("[]")) s=s.replace("[]","");
            
        }

        return s.isEmpty();
    }
}

```

#### LeetCode 精选题解


### 补充知识
#### Map用法 Map<key,value>映射


```

```
