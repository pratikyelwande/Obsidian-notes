==Fibonacci sequence== is a series of numbers where each number is the sum of the two before it. It starts like this:

- **0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...**
```
#include<stdio.h>
int main(){
    int a=0,b=1,c,n;
    
    printf("Enter Your No");
    scanf("%d",&n);
    for(int i=1;i<=n;i++){
        printf("%d ",a);
        c=a+b;
        a=b;
        b=c;
    }
}
```

#### ==Reverse String-==
```
function Reverse(str) {  
    var a= str.split("");  
    console.log(a);  
    var b= a.reverse();  
    console.log(b)  
    var c= b.join();  
    console.log(c)  
}  
Reverse("hello");
// o/p- olleh
```

### ==Palindrome== - 
a string, number, or sequence that reads the same backward as forward, ignoring spaces, punctuation, and capitalization. For example, "madam", "121"

```
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Enter a string:");
        string input = Console.ReadLine();

        // Reverse the string
        string reversed = "";
        for (int i = input.Length - 1; i >= 0; i--)
        {
            reversed += input[i];
        }

        // Check if the original and reversed strings are the same
        if (input.ToLower() == reversed.ToLower())
        {
            Console.WriteLine($"\"{input}\" is a palindrome.");
        }
        else
        {
            Console.WriteLine($"\"{input}\" is not a palindrome.");
        }
    }
}

```

