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
#include <stdio.h>
#include <string.h>

void reverseString(char str[]) {
    int length = strlen(str);
    char temp;

    // Using a for loop to reverse the string in place
    for (int start = 0, end = length - 1; start < end; start++, end--) {
        temp = str[start];
        str[start] = str[end];
        str[end] = temp;
    }
}

int main() {
    char str[100];

    printf("Enter a string: ");
    scanf("%s", str);

    reverseString(str);
    printf("Reversed string: %s\n", str);

    return 0;
}
```

### ==Palindrome== - 
a string, number, or sequence that reads the same backward as forward, ignoring spaces, punctuation, and capitalization. For example, "madam", "121"

```
#include <stdio.h>
#include <string.h>

int isPalindrome(char str[]) {
    int length = strlen(str);

    // Check characters from both ends using a for loop
    for (int start = 0, end = length - 1; start < end; start++, end--) {
        if (str[start] != str[end]) {
            return 0; // Not a palindrome
        }
    }
    return 1; // It's a palindrome
}

int main() {
    char str[100];

    printf("Enter a string: ");
    scanf("%s", str);

    if (isPalindrome(str)) {
        printf("The string '%s' is a palindrome.\n", str);
    } else {
        printf("The string '%s' is not a palindrome.\n", str);
    }

    return 0;
}

```

## ==Second Highest Number==
```
def find_second_highest(numbers):
    unique_numbers = list(set(numbers))  # Remove duplicates
    unique_numbers.sort()  # Sort the unique numbers in ascending order
    return unique_numbers[-2] if len(unique_numbers) > 1 else None  # Return the second-highest or None if not applicable

nums = [1, 2, 3, 4, 5, 6]
print(find_second_highest(nums))  # Output: 5
```

## ==Prime or not==
```
def isprime(num):
    if num <=1:
        return False;
    for i in range(2,num):
        if num % i==0:
            return False;
        return True;

print(isprime(7))
```

## ==Even Odd==
```
def even(n):
	if(n%2==0){
	print("even)
	}
	else:
	print("odd")
```

## ==Armstrong Number==
```
#include <stdio.h>
#include <math.h>

int main() {
    int num, sum = 0, temp, remainder, digits = 0;

    // Take input from the user
    printf("Enter a number: ");
    scanf("%d", &num);

    temp = num;

    // Count the number of digits in the number
    for (temp; temp != 0; temp /= 10) {
        digits++;  // increment digits count
    }

    
    temp = num;  // Restore the original number to temp for iteration

    // Calculate the sum of each digit raised to the power of the number of digits
    for (temp; temp != 0; temp /= 10) {
        remainder = temp % 10;
        sum += pow(remainder, digits);  // raise the digit to the power of 'digits'
    }

    // Check if the sum is equal to the original number
    if (sum == num) {
        printf("%d is an Armstrong number.\n", num);
    } else {
        printf("%d is not an Armstrong number.\n", num);
    }

    return 0;
}

```

## ==Factorial==
```
def fact(n):
    if n==0 or n==1:
        return 1
    return n *fact(n-1)
print(fact(5))
```
## ==list occurance==
```
def cnt(lst):
    occ = {}  # Use a dictionary to store occurrences
    for i in lst:
        if i in occ:
            occ[i] += 1  # Increment the count if the item exists
        else:
            occ[i] = 1  # Initialize the count if the item doesn't exist
    return occ

# Example usage
lst = [1, 1, 2, 3, 4, 5, 5, 5, 5, 5]
print(cnt(lst))
2
```
## ==Vowel in string==
```
vo=['a','e','i','o','u']
word="pratik"
count=0;
for i in word:
    if i in vo:
        count+=1
print(count)
```