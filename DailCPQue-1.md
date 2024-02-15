# DailyCPQues-1

Hello everyone!! Hope you guys have tried to attempt all the 5 questions that we have prepared for you. This is the solutions for the questions. I will be providing comments where ever needed inorder to help you guys understand the code better as well as understand different ways people accept input as well as other minor things that makes your life when programming better!

Also we would suggest all people who code in C to make the switch to C++ and also
learn the different data structures and functions in STL.[Here is the STL Link](https://www.geeksforgeeks.org/cpp-stl-cheat-sheet/)
I  would suggest simply getting familiar with the tools that the vector structure has to offer
and then the rest comes simply from just practice!

# Q1) Airplanes

```
// This line allows us to import alot of useful headers such as stdio as well
//  the ability to use multiple useful data structures as well as functions
//  which will be very useful for your DSA endavour
#include <bits/stdc++.h>

// The line below will allow us to write things like std::cout simply as cout
using namespace std;

int main()
{

    // There are a total of 10 planes available daily
    // X-Capacity of Planes, Y- Number of people will to book a ticket,Z- Cost of the ticket
    // We need to find the maximum amount of money the airlines will make

    // Take in the input
    int x, y, z;
    cin >> x;
    cin >> y;
    cin >> z;
    
    int amount;
    
    // Check if Y is less than or equal total capacity i.e. 10*X>=Y
    if (10 * x >= y)
    {
        amount = y * z;
    }
    else
    {
        // Since we only have 10*x seats to offer that is the maximum seats we can sell
        amount = 10 * x * z;
    }

    // Print the output
    cout << amount;
}

```

# Q2) Make them 1
 
 ```
#include <bits/stdc++.h>
using namespace std;

int main()
{   
    // Taking in the input
    int n;
    cin >> n;
    string s;
    cin >> s;

    // Initializing pointers to the beginning and end of the string 
    int l = 0, r = n - 1;

    // The reason why I am using a while loop with the condition where l<r
    // is becaue when the left pointer becomes greater than right pointer 
    // it simply means that all the characters in the string is 1 and hence we 
    // will simply return 0 when this happens
    while (l < r)
    {
        
        // If both pointers are at a '0' then break the loop
        if (s[l] == '0' && s[r] == '0')
        {
            break;
        }
        // Increment left pointer on seeing a '1'
        if (s[l] == '1')
        {
            l++;
        }
        // Decrement right pointer on seeing a '1'
        if (s[r] == '1')
        {
            r--;
        }
    }

    //Here we have what we call a ternary operator
    //Sounds very fancy but it is a very simple tool
    // Lets break the function down
    // x?y:z        Here let x be a condition if x 
    //              is satisfied then we return y else we return z
    // Simple right!!
    // So if l>r then we know that all the characters are  '1' hence 
    // we need not perform the operation at all on any segment of characters
    // else we will need to perform the operation on r-l-1 characters
    // if the r-l-1 is still confusing try manually taking down a few examples
    // and check whether it holds or not so that it will make sense
    
    cout <<(l>r?0:r-l+1)<<endl;
    return 0;
}

 ```

# Q3) NITT-PRIME
```
#include <bits/stdc++.h>
using namespace std;

int main()
{   
    int n;
    cin>>n;
    
    // Let us initialize the count to 2 as every number n 
    // atleast has the positive divisors {1,n}
    int count=2;

    // The reason we set our limit of i to sqrt(n) is because
    // it is more efficient than setting the limit to any other 
    // uper bound as the highest divisor of any number is sqrt(n) itself
    // By highest here i mean lets take an example of 64
    //Divisors of 64 are {1,2,4,8,16,32,64}
    // although we know that sqrt(64)=8 clearly we can see that if we 
    // have a divisor 2 then it has to be paired with 32 ({2,32}) inorder to be 
    // equal to 64 so it comes as a pair. 8 is paired up with 8 it self but ({8,8})
    //  since its  the same number we only mention it once, hence we only need to check 
    // all the divisors till sqrt(n) after sqrt(n) all divisors are basically
    // the reverse of the divisor pairs (going along with the example we already know
    // that {2,32} exists so why recalculate {32,2}).
    
    for(int i=2;i<=sqrt(n);i++){
        if(n%i==0){
            count++;
        }
        if(count>3){
            break;
        }
    }

    // If count is equal to 3 and only 3 then we have a correct answer
    // else it is not
    if(count==3){
        cout<<"YES";
    }
    else{
        cout<<"NO";
    }
    
}
```

# Q4) Beatiful Permutation 1
```
#include <bits/stdc++.h>
using namespace std;

int main()
{   
    int n;
    cin>>n;
    
    // This question has more to do with ones mathematical ability
    // rather than their coding ability. The aim of the question is
    // to see if you can prove that there always exists a beautiful
    // premutation after a certain valueo of n
    // Eg if we take the values  2 and 3 we can say that it is impossible
    // to do so. But for all values above 3 we can form a beautiful permutation
    // by simply placing the even numbers in increasing order first and then
    // the odd numbers in increasing order in the second half of the list
    // You cant do odd first then even as a generalised case(take the case of 4).
    // Then the set will be {1,3,2,4} which isnt beautiful
    // On this realization the question becomes simple :)   


    // Clearly 1 is also a valid solution as nothing is adjacent to it to begin with
    if(n == 1) {
        cout << "1";
    }

    // for {2,3} case
    else if(n < 4) {
        cout << "NO SOLUTION";
    }
    // for all other cases print the even first then the odd
    else {
        for(int i=2; i<=n; i+=2) {
            cout << i << " ";
        }
        for(int i=1; i<=n; i+=2) {
            cout << i << " ";
        }
    }


}
```

# Q5) Magic Number 33
```
#include <bits/stdc++.h>
using namespace std;

int main()
{   

    // Whats stopping us from taking the input as a string :)

    string n;
    cin>>n;
    
    // Lets think of how to proceed with this question
    // Lets start reading the string from right to left
    // If there is a 1 then there is no issues we can move
    // on to the next character on the left
    // If there is a 4 then either the character to the left
    // must be a 1 or the character to the left is a 4 as well as
    // its left character is a 1 (i.e if there is a 4 to its left
    // there should be a 1 or 14)

    int pointer = n.size()-1; // Gives us the size of the string

    // This is a clever way of writing while(size!=0) as since 
    // we have a condition in the brackets it will continue the 
    // loop if the condition is true i.e not 0, if it is a 0
    // then the condition will out put false and then break the loop!!
    
    while(pointer!=-1){
        if(n[pointer]=='1'){
            pointer--;         // Decrements by 1
        }
        else if(n[pointer]=='4'){
            
            // We first check if there are enough characters to the left of
            // 4 to access hence we hav pointer-2>=0 and pointer-1>=0
            // otherwise we will get an error as we will be accessing
            // values outside the allocated memory for the string

            if(pointer-2>=0 && n[pointer-1]=='4' && n[pointer-2]=='1'){
                pointer-=3;      // Decrements by 3
            }
            else if(pointer-1>=0 && n[pointer-1]=='1'){
                pointer-=2;      // Decrements by 2
            }

            // If it doesnt satisfy te above conditions then it clearly 
            // is not a number as per the given definitions
            else{
                break;
            }
        }
        // If the number we start checking with isnt a 1 then it also
        // is clearly not a valid magic number
        else{
            break;
        }
    }

    // If the pointer finishes going through the entire string then the pointer
    // will finally land at pointer=-1 so if it is at -1 then our answer is yes
    // other wise it clearly broke out of the loop before it was supposed to 
    // so it is not a valid magic number
    cout<<(pointer==-1?"YES":"NO");


}
```
