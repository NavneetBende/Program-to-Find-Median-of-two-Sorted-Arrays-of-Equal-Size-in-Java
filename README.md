Median of two sorted arrays of equal size in Java
Here, in this page we will discuss the program to find median of two sorted arrays of equal size in Java programming language. We are given with two arrays say arr1[] and arr2[] of the same size say n . We need to find the median after merging these arrays.

Median of two sorted arrays of equal size in Java
Method Discussed :
Method 1 : Linear Approach
Method 2 : By comparing the medians of two arrays
Let’s discuss them one by one in brief,

Method 1:
The given arrays are sorted, so merge the sorted arrays in an efficient way.
Keep the count of elements inserted in the output array or printed form.
So when the elements in the output array are half the original size of the given array print the element as a median element.
Method 1 : Code in Java
Run
class Main
{
    static int getMedian(int ar1[], int ar2[], int n)
    {  
        int i = 0; 
        int j = 0;
        int count;
        int m1 = -1, m2 = -1;
      
        for (count = 0; count <= n; count++)
        {
            if (i == n)
            {
                m1 = m2;
                m2 = ar2[0];
                break;
            }
      
            else if (j == n)
            {
                m1 = m2;
                m2 = ar1[0];
                break;
            }
            
            if (ar1[i] <= ar2[j])
            {  
                m1 = m2; 
                m2 = ar1[i];
                i++;
            }
            else
            {
                m1 = m2; 
                m2 = ar2[j];
                j++;
            }
        }
      
        return (m1 + m2)/2;
    }
      
    public static void main (String[] args)
    {
        int ar1[] = {1, 12, 15, 26, 38};
        int ar2[] = {2, 13, 17, 30, 45};
      
        int n1 = ar1.length;
        int n2 = ar2.length;
        if (n1 == n2)
            System.out.println("Median is " +getMedian(ar1, ar2, n1));
        else
            System.out.println("arrays are of unequal size");
    }   
}
Output :
Median is 16
Related Pages
Given an array which consists of only 0, 1 and 2

Move all the negative elements to one side of the array

Find the Union and Intersection of the two sorted arrays

Find Largest sum contiguous Subarray

Minimize the maximum difference between heights 

Method 2:
This method works by first getting medians of the two sorted arrays and then comparing them.

Method 2 : Code in Java
Run
import java.util.*;
class Main {
 
    static int getMedian(
        int[] a, int[] b, int startA,
        int startB, int endA, int endB)
    {
        if (endA - startA == 1) {
            return (Math.max(a[startA], b[startB]) + Math.min(a[endA], b[endB]))/ 2;
        }
        
        int m1 = median(a, startA, endA);
 
        int m2 = median(b, startB, endB);
 
        if (m1 == m2) {
            return m1;
        }
 
        else if (m1 < m2) {
            return getMedian(
                a, b, (endA + startA + 1) / 2,
                startB, endA,
                (endB + startB + 1) / 2);
        }
 
        else {
            return getMedian(
                a, b, startA,
                (endB + startB + 1) / 2,
                (endA + startA + 1) / 2, endB);
        }
    }
 
    static int median( int[] arr, int start, int end)
    {
        int n = end - start + 1;
        if (n % 2 == 0) {
            return ( arr[start + (n / 2)]+ arr[start + (n / 2 - 1)])/ 2;
        }
        else {
            return arr[start + n / 2];
        }
    }
 
    public static void main(String[] args)
    {
        int ar1[] = { 1, 2, 3, 6 };
        int ar2[] = { 4, 6, 8, 10 };
        int n1 = ar1.length;
        int n2 = ar2.length;
        if (n1 != n2) {
            System.out.println("Doesn't work for arrays of unequal size");
        }
        else if (n1 == 0) {
            System.out.println("Arrays are empty.");
        }
        else if (n1 == 1) {
            System.out.println((ar1[0] + ar2[0]) / 2);
        }
        else {
            System.out.println("Median is " + getMedian(ar1, ar2, 0, 0,ar1.length - 1, ar2.length - 1));
        }
    }
}
Output :
Median is 5
