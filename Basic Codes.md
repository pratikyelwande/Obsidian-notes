Fibonacci sequence is a series of numbers where each number is the sum of the two before it. It starts like this:

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



 