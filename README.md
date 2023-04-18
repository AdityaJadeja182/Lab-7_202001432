
<p align="center">
    <img  src="https://user-images.githubusercontent.com/100967786/232732898-7362dc01-01a3-4088-9432-fadbef53c397.png">
</p>

## Name: Aditya Jadeja

## Student ID: 202001432

## Lab-7 : Black-box and White-box Testing

## Date : 18-04-2023



---

# Section A

Consider a program for determining the previous date. Its input is triple of day, month and year with the
following ranges 1 <= month <= 12, 1 <= day <= 31, 1900 <= year <= 2015.The possible output dates would be
previous date or invalid date. Design the equivalence class test cases?

**Equivalence classes patition:**

For Day(D):
    
| Equivalence class | Range | Status
| ----------------- | ----- | ------
| E1 | 1 <= D <= 31 | Valid
| E2 | D < 1 | Invalid
| E3 | D > 31 | Invalid

For Month(M):
    
| Equivalence class | Range | Status
| ----------------- | ----- | ------
| E4 | 1 <= M <= 12 | Valid
| E5 | M < 1  | Invalid
| E6 | M > 12 | Invalid

For Year(Y):
    
| Equivalence class | Range | Status
| ----------------- | ----- | ------
| E7 | 1900 <= Y <= 2015 | Valid
| E8 | Y < 1900 | Invalid
| E9 | Y > 2015 | Invalid

**Test Cases: For Boundary Value Analysis (DD/MM/YYYY)**
| Test Case ID |(DD/MM/YYYY)| Expected Output |
| -------------|-----------------|-----------------|
|1 |01/01/2000| 31/12/1999
|2 |01/01/2010 |31/12/2009
|3 |31/02/2000 |Invalid
|4 |30/02/2001 |Invalid
|5 |01/01/1901 |31/12/1900
|6 |31/12/2003 |30/12/2003
|7 |31/12/1899 |Invalid
|8 |31/13/2025 |Invalid
|9 |32/12/2000 |Invalid
|10|18/05/2045 |Invalid

### P1. The function linearSearch searches for a value v in an array of integers a. If v appears in the array a, then the function returns the first index i, such that a[i] == v; otherwise, -1 is returned.

--> Test-case for this program is as follows.

| Test Case | Expected Output | Test-acse type
| --------- | --------------- | --------------
| a=[1,2,3,4,5],v=2 | 1 | Equivalence Partitioning
| a=[2,4,6],v=3 | -1 | Equivalence Partitioning
| a=[3,2,4,1],v=4 | 2 | Equivalence Partitioning
| a=[2,1,7,8],v=4 | -1 | Equivalence Partitioning
| a=[],v=5| -1 | Boundary Case Analysis
| a=[1,2,3] | 0 | Boundary Case Analysis
| a=[2,3,4] | 2 | Boundary Case Analysis
| a=[2,c,3] | 2 | Equivalence Partitioning
| a=[2,4,5] | a | Equivalence Partitioning

--> Test-case compilation in eclipse using Junit:

**P1.java**

    public class P1
    {
        public int linearSearch(int v, int a[])
        {
            int i = 0;
            while (i < a.length)
            {
                if (a[i] == v)
                    return(i);
                i++;
            }
            return (-1);
        }
    }
    
**P1Test.java:**

    import static org.junit.Assert.*;
    import org.junit.Test;

    public class P1Test {

        P1 newclass=new P1();
        @Test
        public void elementexist() {
            int[] arr = {1,2,3,4,5};
            int expected = 1;
            int v = 2;
            assertEquals(newclass.linearSearch(v, arr), expected);
        }
        @Test
        public void elementnotexist() {
            int[] arr = {2,4,6};
            int expected = -1;
            int v = 8;
            assertEquals(newclass.linearSearch(v, arr), expected);
        }
        @Test
        public void emptyarray() {
            int[] arr = {};
            int expected = -1;
            int v = 5;
            assertEquals(newclass.linearSearch(v, arr), expected);
        }
        @Test
        public void elementatstart() {
            int[] arr = {1,2,3};
            int expected = 0;
            int v = 1;
            assertEquals(newclass.linearSearch(v, arr), expected);
        }
        @Test
        public void elementatLast() {
            int[] arr = {2,3,4};
            int expected = 2;
            int v = 4;
            assertEquals(newclass.linearSearch(v, arr), expected);
        }
    }
**Output**:

   ![image](https://user-images.githubusercontent.com/75557009/231734563-1d88224e-295a-4cc2-833c-891e410185f5.png)

### P2.The function countItem returns the number of times a value v appears in an array of integers a.

--> Test-case for this program is as follows.

| Test Case | Expected Output | Test-acse type
| --------- | --------------- | --------------
| a=[1,2,2,3,4,2,5,6,7,8,2,2],v=2 | 5 | Equivalence Partitioning
| a=[2,4,6,8,10],v=3 | 0 | Equivalence Partitioning
| a=[],v=5| 0 | Boundary Case Analysis
| a=[1,1,1,1],v=1 | 4 |Boundary Case Analysis
| a=[2147483647,0,-1,-2,2147483647],v=2147483647 | 2 | Boundary Case Analysis

**P2.java**:

    public class P2
    {
        public int countItem(int v, int a[])
        {
            int count = 0;
            for (int i = 0; i < a.length; i++)
            {
                if (a[i] == v)
                    count++;

            }
            return (count);
        }
    }
 
**P2Test.java**:

    import static org.junit.Assert.*;

    import org.junit.Test;

    public class P2Test {

        P2 newclass=new P2();
        @Test
        public void elementexist() {
            int[] arr = {1,2,2,3,4,2,5,6,7,8,2,2};
            int expected = 5;
            int v = 2;
            assertEquals(newclass.countItem(v, arr), expected);
        }
        @Test
        public void elementnotexist() {
            int[] arr = {2,4,6,8,10};
            int expected = 0;
            int v = 3;
            assertEquals(newclass.countItem(v, arr), expected);
        }
        @Test
        public void emptyarray() {
            int[] arr = {};
            int expected = 0;
            int v = 5;
            assertEquals(newclass.countItem(v, arr), expected);
        }
        @Test
        public void allequal() {
            int[] arr = {1,1,1,1};
            int expected = 4;
            int v = 1;
            assertEquals(newclass.countItem(v, arr), expected);
        }
        @Test
        public void MaxintElement(){
            int[] arr = {2147483647,0,-1,-2,2147483647};
            int expected = 2;
            int v = 2147483647;
            assertEquals(newclass.countItem(v, arr), expected);
        }

    }
**Output**:

![image](https://user-images.githubusercontent.com/75557009/231737171-f8faa307-274d-4249-af34-c9f02cf6e6a8.png)

### P3. The function binarySearch searches for a value v in an ordered array of integers a. If v appears in the array a, then the function returns an index i, such that a[i] == v; otherwise, -1 is returned.

--> Test-case for this program is as follows.

| Test Case | Expected Output | Test-acse type
| --------- | --------------- | --------------
| a=[1,2,3,4,5],v=2 | 1 | Equivalence Partitioning
| a=[2,4,6],v=3 | -1 | Equivalence Partitioning
| a=[],v=5| -1 | Boundary Case Analysis
| a=[1,2,3] | 0 | Boundary Case Analysis
| a=[2,3,4] | 2 | Boundary Case Analysis
| a=[2,c,3] | 2 | Equivalence Partitioning
| a=[2,4,5] | a | Equivalence Partitioning

**P3.java**:

    public class P3
    {
        public int binarySearch(int v, int a[])
        {
            int lo,mid,hi;
            lo = 0;
            hi = a.length-1;
            while (lo <= hi)
            {
                mid = (lo+hi)/2;
                if (v == a[mid])
                    return (mid);
                else if (v < a[mid])
                    hi = mid-1;
                else
                    lo = mid+1;

            }
            return(-1);
        }
    }

**P3Test.java**:

    import static org.junit.Assert.*;

    import org.junit.Test;

    public class P3Test {

        P3 newclass=new P3();
        @Test
        public void elementexist() {
            int[] arr = {1,2,3,4,5};
            int expected = 1;
            int v = 2;
            assertEquals(newclass.binarySearch(v, arr), expected);
        }
        @Test
        public void elementnotexist() {
            int[] arr = {2,4,6};
            int expected = -1;
            int v = 8;
            assertEquals(newclass.binarySearch(v, arr), expected);
        }
        @Test
        public void emptyarray() {
            int[] arr = {};
            int expected = -1;
            int v = 5;
            assertEquals(newclass.binarySearch(v, arr), expected);
        }
        @Test
        public void elementatstart() {
            int[] arr = {1,2,3};
            int expected = 0;
            int v = 1;
            assertEquals(newclass.binarySearch(v, arr), expected);
        }
        @Test
        public void elementatLast() {
            int[] arr = {2,3,4};
            int expected = 2;
            int v = 4;
            assertEquals(newclass.binarySearch(v, arr), expected);
        }

    }
    
**Output**:

![image](https://user-images.githubusercontent.com/75557009/231739214-4824c42f-3593-4294-b867-90181d4a0a5d.png)

### P4. The following problem has been adapted from The Art of Software Testing, by G. Myers (1979). Thefunction triangle takes three integer parameters that are interpreted as the lengths of the sides of atriangle. It returns whether the triangle is equilateral (three lengths equal), isosceles (two lengths equal),scalene (no lengths equal), or invalid (impossible lengths).

--> Test-case for this program is as follows.

| Test Case | Expected Output | Test-acse type
| --------- | --------------- | --------------
| A=0,B=0,C=0 | Invalid Triangle | Boundary Case Analysis
| A=0,B=5,C=0 | Invalid Triangle | Boundary Case Analysis
| A=2,B=5,C=7 | Invalid Triangle | Equivalence Partitioning
| A=-1,B=-1,C=-1 | Invalid Triangle | Boundary Case Analysis
| A=1,B=1,C=1 | Equilateral Triangle | Equivalence Partitioning
| A=2,B=2,C=1 | Isoscels Triangle | Equivalence Partitioning
| A=2,B=1,C=2 | Isoscels Triangle | Equivalence Partitioning
| A=3,B=3,C=3 | Equilateral Triangle | Equivalence Partitioning
| A=5,B=12,C=13 | Scalene Triangle | Boundary Case Analysis

**P4.java**:

    public class P4
    {
        final int EQUILATERAL = 0;
        final int ISOSCELES = 1;
        final int SCALENE = 2;
        final int INVALID = 3;
        public int triangle(int a, int b, int c)
        {
            if (a >= b+c || b >= a+c || c >= a+b)
                return(INVALID);
            if (a == b && b == c)
                return(EQUILATERAL);
            if (a == b || a == c || b == c)
                return(ISOSCELES);
            return(SCALENE);

        }
    }

**P4Test.java**:

    import static org.junit.Assert.*;

    import org.junit.Test;

    public class P4Test {

        P4 newclass=new P4();
        @Test
        public void invalid1() {
            int a=0,b=0,c=0;
            int expected=newclass.INVALID;
            assertEquals(newclass.triangle(a, b,c),expected);
        }
        @Test
        public void invalid2() {
            int a=0,b=5,c=0;
            int expected=newclass.INVALID;
            assertEquals(newclass.triangle(a, b,c),expected);
        }
        @Test
        public void invalid3() {
            int a=-1,b=-1,c=-1;
            int expected=newclass.INVALID;
            assertEquals(newclass.triangle(a, b,c),expected);
        }
        @Test
        public void equilateral1() {
            int a=1,b=1,c=1;
            int expected=newclass.EQUILATERAL;
            assertEquals(newclass.triangle(a, b,c),expected);
        }
        @Test
        public void Isoscels1() {
            int a=2,b=2,c=1;
            int expected=newclass.ISOSCELES;
            assertEquals(newclass.triangle(a, b,c),expected);
        }
        @Test
        public void Isoscels2() {
            int a=2,b=1,c=2;
            int expected=newclass.ISOSCELES;
            assertEquals(newclass.triangle(a, b,c),expected);
        }
        @Test
        public void scalene1() {
            int a=5,b=12,c=13;
            int expected=newclass.SCALENE;
            assertEquals(newclass.triangle(a, b,c),expected);
        }
    }

**Output**:

![image](https://user-images.githubusercontent.com/75557009/231743262-41789966-3ec5-4b03-8256-a97aeb56d828.png)

### P5. The function prefix (String s1, String s2) returns whether or not the string s1 is a prefix of string s2 (you may assume that neither s1 nor s2 is null).

--> Test-case for this program is as follows.

| Test Case | Expected Output | Test-acse type
| --------- | --------------- | --------------
| s1="",s2="" | True | Boundary Case Analysis
| s1="Man",s2="Manan" | True | Equivalence Partitioning
| s1="Manan",s2="Manan" | True | Boundary Case Analysis
| s1="Mand",s2="Manan" | False | Equivalence Partitioning
| s1="",s2="Manan" | True | Boundary Case Analysis
| s1="M a",s2="Manan" | False | Boundary Case Analysis
| s1="ma",s2="Manan" | False | Boundary Case Analysis
| s1="Truth",s2="Tbcd" | False | Equivalence Partitioning
| s1="Manan",s2="" | False | Boundary Case Analysis

**P5.java**:

    public class P5
    {
        public static boolean prefix(String s1, String s2)
        {
            if (s1.length() > s2.length())
            {
                return false;
            }
            for (int i = 0; i < s1.length(); i++)
            {	
                if (s1.charAt(i) != s2.charAt(i))
                {
                    return false;
                }
            }
            return true;
        }
    }

**P5Test.java**:

    import static org.junit.Assert.*;

    import org.junit.Test;

    public class P5Test {

        P5 newclass=new P5();
        @Test
        public void test1() {
            String s1="";
            String s2="";
            assertTrue(newclass.prefix(s1, s2));
        }
        @Test
        public void test2() {
            String s1="Man";
            String s2="Manan";
            assertTrue(newclass.prefix(s1, s2));
        }
        @Test
        public void test3() {
            String s1="Manan";
            String s2="Manan";
            assertTrue(newclass.prefix(s1, s2));
        }
        @Test
        public void test4() {
            String s1="Mand";
            String s2="Manan";
            assertFalse(newclass.prefix(s1, s2));
        }
        @Test
        public void test5() {
            String s1="";
            String s2="Manan";
            assertTrue(newclass.prefix(s1, s2));
        }
        @Test
        public void test6() {
            String s1="M a";
            String s2="Manan";
            assertFalse(newclass.prefix(s1, s2));
        }
        @Test
        public void test7() {
            String s1="ma";
            String s2="Manan";
            assertFalse(newclass.prefix(s1, s2));
        }
        @Test
        public void test8() {
            String s1="Manan";
            String s2="";
            assertFalse(newclass.prefix(s1, s2));
        }
    }

**Output**:

![image](https://user-images.githubusercontent.com/75557009/231746366-0e61c10f-dfcd-43bd-8526-90b1e913e989.png)


### P6. In this program we consider program given in P4 but value can be float rather than integers

#### a) Equivalence Classes for program:

| Equivalence Class | Condition
| ----------------- | ---------
| E1:Invalid Inputs | A<=0 or B<=0 or C<=0
| E2:Invalid Triangle | A+B<C or B+C<A or A+C<B
| E3:Scalene Triangle | A!=B and B!=C and A!=C
| E4:Equilateral Triangle | A==B and B==C
| E5:Isoscels Triangle | A==B or B==C or A==C
| E6:Right-Angel Triangle | A^2=B^2+C^2 or B^2=A^2+C^2 or C^2=A^2+B^2
                                                
#### b) Test-cases for Equivalence classes:
                                                
| Test Case | Input Data | Expected Output | Equivalence class covered
| --------- | ---------- | --------------- | ---------------------
| 1 | A=7,B=7,C=7 | Equilateral Triangle | E4
| 2 | A=5,B=12,C=13 | Right-Angle Triangle | E6
| 3 | A=5,B=5,C=4 | Isoscels Triangle | E5
| 4 | A=4,B=5,C=7 | Scalene Triangle | E3
| 5 | A=1,B=2,C=3 | Invalid Triangle | E2
| 6 | A=-1,B=-2,C=3 | Invalid Triangle | E1

#### c) Boundary condition A + B > C(Scalene Triangle):
    
--> We have to check for three boundary condition where A+B<C and A+B>C and A+B==C
     
| Test Case | Input Data | Expected Output
| --------- | ---------- | --------------
| 1 | A=2,B=3,C=5 | Invalid Triangle
| 2 | A=2,B=3,C=6 | Scalene Triangle
| 3 | A=1,B=2,C=3 | Invalid Triangle

--> Here In 1st and 3rd test case we would think that it is Scalene Triangle but it is Invalid Triangles.

#### d) Boundary condition A = C(Isoscels Triangle):

--> We have to check for two boundary condition A=C and A!=C
    
| Test Case | Input Data | Expected Output
| --------- | ---------- | ---------------
| 1 | A=-1,B=2,C=-1 | Invalid Triangle
| 2 | A=1,B=2,C=1 | Invalid Triangle
| 3 | A=1,B=3,C=1 | Isoscels Triangle
| 4 | A=0.2,B=0.5,C=0.2 | Isoscels Triangle
    
--> Here In 1st and 2nd test-case we think that it is Isoscels Triangle but it is not.
                                                
 #### e) Boundary condition A = B = C (Equilateral Traingle):
    
 | Test Case | Input Data | Expected Output
 | --------- | ---------- | ---------------
 | 1 | A=-1,B=-1,C=-1 | Invalid Traingle
 | 2 | A=0,B=0,C=0 | Invalid Triangle
 | 3 | A=3,B=3,C=3 | Equilateral Triangle
 | 4 | A=0.2,B=0.2,C=0.2 | Equilateral Triangle
 
 #### f) Boundary condition $ A^2 + B^2 = C^2 $(Right-Angeled Triangle):
 
 | Test Case | Input Data | Expected Output
 | --------- | ---------- | ---------------
 | 1 | A=-3,B=-4,C=5 | Invalid Traingle
 | 2 | A=3,B=4,C=5 | Invalid Traingle
 | 3 | A=1,B=1,C=2 | Invalid Traingle
 | 4 | A=5,B=12,C=13 | Right-Angeled Traingle
    
 #### g) Non-Traingle Case :
    
 | Test Case | Input Data | Expected Output
 | --------- | ---------- | --------------
 | 1 | A=0.1, B=0.2, C=0.3 | Invalid Triangle
 | 2 | A=1,B=1,C=2 | Invalid Triangle
 | 3 | A=1.2,B=1.2,C=2.4 | Invalid Traingle
 | 4 | A=0,B=0,C=0 | Invalid Traingle
 
 #### h) Non-positive Inputs: 
    
 | Test Case | Input Data | Expected Output
 | ---------- | --------- | ------------
 | 1 | A=-1,B=-2,C=-3 | Invalid Triangle
 | 2 | A=-0.2,B=-0.2,C=-3.6 | Invalid Triangle
 | 3 | A=-1,B=-1,C=-2 | Invalid Triangle
 | 4 | A=-2,B=-2,C=-2 | Invalid Triangle
 
    
 # Section B
  
The code below is part of a method in the ConvexHull class in the VMAP system. The following is a small
fragment of a method in the ConvexHull class. For the purposes of this exercise you do not need to know the
intended function of the method. The parameter p is a Vector of Point objects, p.size() is the size of the
vector p, (p.get(i)).x is the x component of the ith point appearing in p, similarly for (p.get(i)).y. This exercise is
concerned with structural testing of code and so the focus is on creating test sets that satisfy some particular
coverage criterion.

1. Convert the Java code comprising the beginning of the doGraham method into a control flow graph(CFG).
    
    ![image](https://user-images.githubusercontent.com/75557009/231730370-c1898df9-d977-44a5-8eac-a6bf131824ff.png)

2. Construct test sets for your flow graph that are adequate for the following criteria:
    a. Statement Coverage.
    b. Branch Coverage.
    c. Basic Condition Coverage.

a. Statement Coverage:
    
| Test Case | Condition | Input
| --------- | ------ | ------
| 1 | Empty Vector | p=[] 
| 2 | Vector with one point | p=[(1,1)]
| 3 | Vector with two points with same y co-ordinate | p=[(1,1),(2,1)]
| 4 | Vector with two points with different y co-ordinate | p=[(1,1),(1,2)]
| 5 | Vector with three Points | p=[(1,1),(2,2),(3,3)]   

b. Branch Coverage:
    
| Test Case | Condition | Input
| --------- | --------- | ---
| 1 | Empty Vector | p=[]
| 2 | Vector with one point | p=[(2,2)]
| 3 | Vector with two points having same y co-ordinate | p=[(1,1),(2,1)]
| 4 | Vector with two points having different y co-ordinate | p=[(1,1),(1,2)]
| 5 | Vector with three or more point with some have same y co-ordinate and some have same x co-ordinate | p=[(1,1),(1,2),(2,1),(3,2)]
| 6 | Vector with three or more point with different y co-ordinate and different x co-ordinate | p=[(1,1),(2,2),(3,3),(4,4)]

c. Basic condition Coverage:
    
| Test Case | Condition | Input
| --------- | ---------- | ------
| 1 | Empty Vector | p=[]
| 2 | Vector with one point | p=[(2,2)]
| 3 | Vector with two points having same y co-ordinate | p=[(1,1),(2,1)]
| 4 | Vector with two points having different y co-ordinate | p=[(1,1),(1,2)]
| 5 | Vector with three or more point with some have same y co-ordinate and some have same x co-ordinate | p=[(1,1),(1,2),(2,1),(3,2)]
| 6 | Vector with three or more point with different y co-ordinate and different x co-ordinate | p=[(1,1),(2,3),(3,2),(4,5)]
  


