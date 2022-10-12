# 12 October 2022

## Problem Statement
Given a string w, integer array b,  character array x and an integer n. n is the size of array b and array x. Find a substring which has the sum of the ASCII values of its every character, as maximum. ASCII values of some characters are redefined.
Note: Uppercase & lowercase both will be present in the string w. Array b and Array x contain corresponding redefined ASCII values. For each i, 0<=ib[i] contain redefined ASCII value of character x[i].

## Example 1:

### Input:
W = abcde
N = 1
X[] = { 'c' }
B[] = { -1000 }
### Output:
de
### Explanation:
Substring "de" has the
maximum sum of ascii value,
including c decreases the sum value


## Example 2:

### Input:
W = dbfbsdbf 
N = 2
X[] = { 'b','s' }
B[] = { -100, 45  }
### Output:
dbfbsdbf

### Explanation:
Substring "dbfbsdbf" has the maximum
sum of ascii value.

## Your Task:
You don't need to read input or print anything. Your task is to complete the function maxSum() which takes string W, character array X, integer array B, integer N as length of array X and B as input parameters and returns the substring with the maximum sum of ascii value.
 

Expected Time Complexity: O(|W|)
Expected Auxiliary Space: O(1)


## Constraints:

1<=|W|<=100000
1<=|X|<=52
-1000<=Bi<=1000

Each character of W and A will be from a-z, A-Z.


## Solution
```
//{ Driver Code Starts
import java.io.*;
import java.util.*;

// } Driver Code Ends
class Solution{
    static String maxSum(String w,char x[],int b[], int n){
        
        HashMap<Character, Integer> map = new HashMap<>();
        
        for(int i=0; i<n; i++)
        {
            map.put(x[i], b[i]);
        }
        
        int sum = 0, max_sum = Integer.MIN_VALUE;
        
        int st = 0;
        
        int max_st=0, max_end=0;
        
        for(int i=0; i<w.length(); i++)
        {
            
            char ch = w.charAt(i);
            
            int value = (int) ch;
            
            if(map.containsKey(ch)) value = map.get(ch);
            
            if(sum<0)
            {
                st = i;
                sum = 0;
            }
            
            sum += value;
            
            
            if(sum>max_sum)
            {
                
                max_st = st;
                max_end = i;
                
                max_sum = sum;
            }
        }
        
        
        return w.substring(max_st, max_end+1);
        
        
    
}
}

//{ Driver Code Starts.
class GFG
{
    public static void main(String args[])throws IOException
    {
        BufferedReader read = new BufferedReader(new InputStreamReader(System.in));
        int t = Integer.parseInt(read.readLine());
        while(t-- > 0)
        {
            String w = read.readLine();
            int n = Integer.parseInt(read.readLine());
            String TE[] = read.readLine().trim().split(" ");
            char x[] = new char[n];
            for(int i = 0;i<n;i++)
            {
                x[i] = TE[i].charAt(0);
            }
            
            String TR[] = read.readLine().trim().split(" ");
            int b[] = new int[n];
            for(int i = 0;i<n;i++)
            {
                b[i] = Integer.parseInt(TR[i]);
            }
           
            Solution ob = new Solution();
            System.out.println(ob.maxSum(w,x,b,n));
        }
    }
}
// } Driver Code Ends
```
