
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

**Junit Testing Code** <br/>
```
package tests;

import static org.junit.Assert.*;

import org.junit.Test;

public class TestFunctions {
    @Test
    public void testNonLeapYear() {
        assertEquals("29/02/2004", UnitTest.findPreviousDate("01/03/2004"));
        assertEquals("28/02/2007", UnitTest.findPreviousDate("01/03/2007"));
        assertEquals("INVALID", UnitTest.findPreviousDate("29/02/2007"));
        assertEquals("INVALID", UnitTest.findPreviousDate("30/02/2004"));
    }
    @Test
    public void testNonLeapYear() {
        assertEquals("31/12/1899", UnitTest.findPreviousDate("01/01/1900"));
        assertEquals("30/12/2015", UnitTest.findPreviousDate("31/12/2015"));
        assertEquals("INVALID", UnitTest.findPreviousDate("31/12/1899"));
        assertEquals("INVALID", UnitTest.findPreviousDate("31/13/1900"));
        assertEquals("INVALID", UnitTest.findPreviousDate("32/12/1900"));
        assertEquals("17/05/2001", UnitTest.findPreviousDate("18/05/2001"));
    }
}
```
**Junit Testing Output** <br/>

![image](https://user-images.githubusercontent.com/77292724/231760083-ab16aa08-3513-4051-a6c4-4cccacaa49b0.png)

### P1: LinearSearch Problem

| Tester Action and Input Data    | Expected Outcome | Test Case Type           |
| ------------------------------- | ---------------- | ------------------------ |
| arr=[-3,4,-1,1,1,13,5], v = 1   | 3                | Equivalence Partitioning (first ocurrance)|
| arr=[-3,4,-1,-1,0,13,5], v = 2 | -1                | Equivalence Partitioning (not found)|
| arr=[-3,4,-1,-1,0,13,5], v = -3 | 0                | Boundary Value Analysis  |
| arr=[3,4,1,1,0,13,5], v = 5    | 6               | Boundary Value Analysis  |
| arr=[7], v = 7 | 0 | Boundary Value Analysis |
| arr=[3,4,1,-1,0,13,5], v = -1    | 3               | Boundary Value Analysis  |
| arr=[], v = 5 | -1 | Boundary Value Analysis |
| NULL, v = 5 | -1 | Boundary Value Analysis|

**Junit Testing Code** <br/>
``` 
package tests;

import static org.junit.Assert.*;

import org.junit.Test;

public class TestFunctions {
    @Test
    public void testLinearSearch() {
        int[] a1 = {-3,4,-1,1,1,13,5};
        int v1 = 1;
        assertEquals(3,  UnitTest.linearSearch(v1, a1));
        
        int[] a2 = {-3,4,-1,-1,0,13,5};
        int v2 = 2;
        assertEquals(-1, UnitTest.linearSearch(v2, a2));
        
        int[] a3 = {};
        int v3 = 5;
        assertEquals(-1, UnitTest.linearSearch(v3, a3));
        
        int[] a4 = {7};
        int v4 = 7;
        assertEquals(0, UnitTest.linearSearch(v4, a4));
    }
}
```

**Junit Testing Output** <br/>

![image](https://user-images.githubusercontent.com/77292724/231767489-bc9ee281-63a7-4084-af25-e6ad8e27d7ec.png)

### P2: CountItem Problem
| Tester Action and Input Data                   | Expected Outcome | Test Case Type           |
| ---------------------------------------------- | ---------------- | ------------------------ |
| arr=[1,1,2,4,6,1,4,32,1,5,76,2,1], v = 1       | 5                | Equivalence Partitioning |
| arr=[1,2,3,4,5,6,7], v = 0                     | 0                | Equivalence Partitioning  |
| arr=[1,-1,2,4,-6,6,-4,-32,1,5,-76,2,-1], v = 6 | 1                | Boundary Value Analysis  |
| arr=[6,6,6], v = 6                | 3                | Boundary Value Analysis  |
| arr=[6,6,6], v = -6                | 0                | Boundary Value Analysis  |
| arr=[], v = 5 | 0 | Boundary Value Analysis |
| NULL, v = 5 | 0 | Boundary Value Analysis |

**Junit Testing Code** <br/>
``` 
package tests;

import static org.junit.Assert.*;

import org.junit.Test;

public class TestFunctions {

    @Test
    public void testCountItem() {
        int[] a1 = {1,1,2,4,6,1,4,32,1,5,76,2,1};
        int v1 = 1;
        assertEquals(5, UnitTest.countItem(v1, a1));
        
        int[] a2 = {1,2,3,4,5,6,7};
        int v2 = 0;
        assertEquals(0, UnitTest.countItem(v2, a2));
        
        int[] a3 = {6,6,6};
        int v3 = 6;
        assertEquals(3, UnitTest.countItem(v3, a3));
        
        int[] a4 = {};
        int v4 = 5;
        assertEquals(0, UnitTest.countItem(v4, a4));
    }
}
```

**Junit Testing Output** <br/>

![image](https://user-images.githubusercontent.com/77292724/231772483-637297a5-e007-41e3-bce9-fdca42f75c10.png)

### P3: BinarySearch Problem

| Tester Action and Input Data | Expected Outcome | Test Case Type           |
| ---------------------------- | ---------------- | ------------------------ |
| arr=[0,1,2,3,4,5,6,7], v = 6 | 6                | Equivalence Partitioning |
| arr=[-100,-90,-80,10,100],v = -90| 1 | Equivalence Partitioning |
| arr=[0,1,2,4], v = 5         | -1               | Equivalence Partitioning |
| arr=[0,1,2,3,7], v = 7       | 4                | Boundary Value Analysis |
| arr=[0,2,4,5,7], v = 0       | 0                | Boundary Value Analysis  |
| arr=[0,2,4,5,7], v = 4       | 2                | Boundary Value Analysis  |
| arr=[4], v = 4       | 0                | Boundary Value Analysis  |
| arr=[0,2], v = 2       | 1                | Boundary Value Analysis  |
| arr=[], v = 5                | -1               | Boundary Value Analysis  |
| NULL, v = 5 | -1 | Boundary Value Analysis |

**Junit Testing Code** <br/>
```
package tests;

import static org.junit.Assert.*;

import org.junit.Test;

public class TestFunctions {

    @Test
    public void testBinarySearch() {
        int[] a1 = {0,1,2,3,4,5,6,7};
        int v1 = 6;
        assertEquals(6, UnitTest.binarySearch(v1, a1));
        
        int[] a2 = {-100,-90,-80,100,1000};
        int v2 = -90;
        assertEquals(1, UnitTest.binarySearch(v2, a2));
        
        int[] a3 = {0,1,2,4};
        int v3 = 5;
        assertEquals(-1, UnitTest.binarySearch(v3, a3));
        
        int[] a4 = {4};
        int v4 = 4;
        assertEquals(0, UnitTest.binarySearch(v4, a4));
        
        int[] a5 = {};
        int v5 = 5;
        assertEquals(-1, UnitTest.binarySearch(v5, a5));
        
        int[] a6 = {0,3};
        int v6 = 3;
        assertEquals(1, UnitTest.binarySearch(v6, a6));
    }
}
```
**Junit Testing Output** <br/>

![image](https://user-images.githubusercontent.com/77292724/231779493-081afec2-4ac0-4401-891d-1e334991dc7f.png)

### P4: Triangle Problem

| Tester Action and Input Data | Expected Outcome | Test Case Type           |
| ---------------------------- | ---------------- | ------------------------ |
| a = 0, b = 0, c = 0          | INVALID          | Boundary Condition       |
| a = 0, b = 5, c = 0          | INVALID          | Boundary Condition       |
| a = 9, b = 8, c = 0          | INVALID          | Boundary Condition       |
| a = 9, b = 8, c = 100        | INVALID          | Equivalance Partitioning |
| a = -8, b = -8, c = -8       | INVALID          | Boundary Condition       |
| a = 10, b = 10, c = 10       | EQUILATERAL      | Equivalence Partitioning |
| a = 100, b = 100, c = 100    | EQUILATERAL      | Equivalence Partitioning |
| a = 10, b = 10, c = 12       | ISOSCELES        | Equivalence Partitioning |
| a = 12, b = 10, c = 10       | ISOSCELES        | Equivalence Partitioning |
| a = 150, b = 100, c = 150    | ISOSCELES        | Equivalence Partitioning |
| a = 5, b = 6, c = 10         | SCALENE          | Boundary Condition       |

**Junit Testing Code** <br/>
```
package tests;

import static org.junit.Assert.*;

import org.junit.Test;

public class TestFunctions {

    @Test
    public void testTriangleInvalid() {
        assertEquals(3, UnitTest.triangle(0, 0, 0));
        assertEquals(3, UnitTest.triangle(9, 8, 100));
        assertEquals(3, UnitTest.triangle(-8, -8, -8));
    }
    
    @Test
    public void testTriangleEquilateral() {
        assertEquals(0, UnitTest.triangle(10, 10, 10));
    }
    
    @Test
    public void testTriangleIsosceles() {
        assertEquals(1, UnitTest.triangle(10, 10, 12));
        assertEquals(1, UnitTest.triangle(12, 10, 10));
        assertEquals(1, UnitTest.triangle(150, 100, 150));
    }
    
    @Test
    public void testTriangleScalene() {
        assertEquals(2, UnitTest.triangle(5, 6, 10));
    }
}
```
**Junit Testing Output** <br/>

![image](https://user-images.githubusercontent.com/77292724/231783233-2e58f5e7-e5ae-4f2c-8d73-97f0fb98d002.png)

### P5: Prefix Problem

| Tester Action and Input Data | Expected Outcome | Test Case Type           |
| ---------------------------- | ---------------- | ------------------------ |
| s1="", s2=""                 | true             | Boundary Condition       |
| s1="hell", s2="hello"        | true             | Equivalence Partitioning |
| s1="hell", s2="hell"         | true             | Boundary Condition       |
| s1="", s2="hell"             | true             | Boundary Condition       |
| s1="hello", s2="hell"        | false            | Equivalence Partitioning |
| s1="he ll", s2="hell"        | false            | Boundary Condition       |
| s1=" hell", s2="hello"       | false            | Boundary Condition       |

**Junit Testing Code** <br/>
```
package tests;

import static org.junit.Assert.*;

import org.junit.Test;

public class TestFunctions {

    @Test
    public void testPrefix() {
        assertTrue(UnitTest.prefix("", ""));
        assertTrue(UnitTest.prefix("hell", "hello"));
        assertTrue(UnitTest.prefix("hell", "hell"));
        assertTrue(UnitTest.prefix("", "hell"));
        assertFalse(UnitTest.prefix("hello", "hell"));
        assertFalse(UnitTest.prefix("he ll", "hell"));
    }
}
```
**Junit Testing Output** <br/>

![image](https://user-images.githubusercontent.com/77292724/231787027-d44b327a-823c-4f82-b059-4a83a37e180e.png)

### P6: Assumes the problem domain of P4 with A, B, and C as floating values instead of integers

**A. Equivalence classes for the system**

The possible equivalence classes and their corresponding conditions are as follows:

| Equivalence Class    | Neccessary Condition                                  |
| -------------------- | ----------------------------------------------------- |
| Invalid Triangle     | A > B+C or B > A+C or C > A+B                         |
| Scalene Triangle     | A != B and B != C and C != A                          |
| Isoceles Triangle    | either A == B or B == C or A == C                     |
| Equilateral Triangle | A == B and B == C                                     |
| Right-angle Triangle | A^2 + B^2 = C^2 or A^2 = B^2 + C^2 or B^2 + A^2 = C^2 |

**B. Test Cases for Equivalence Classes**

Following are list of test cases each belonging to one of the defined Equivalence class

| Test Case | Condition           | Expected Outcome     |
| --------- | ------------------- | -------------------- |
| 1         | A = 7, B = 7, C = 7 | Equilateral Triangle |
| 2         | A = 5, B = 12, C = 13 | Right-angle Triangle |
| 3         | A = 4, B = 4, C = 3 | Isosceles Triangle   |
| 4         | A = 4, B = 6, C = 7 | Scalene Triangle     |
| 5         | A = 1, B = 2, C = 3 | Invalid Triangle     |

**C. Boundary Condition A + B > C (scalene triangle)**

Below is the list of possible corner cases looking like scalene triangle but are not

| Test Case | Condition                 | Expected Outcome |
| --------- | ------------------------- | ---------------- |
| 1         | A = 2, B = 1, C = 5       | Invalid Triangle |
| 2         | A = 1, B = 2, C = 4       | Invalid Triangle |
| 3         | A = 2, B = 2, C = 5       | Invalid Triangle |
| 4         | A = 0.1, B = 0.2, C = 0.3 | Invalid Triangle |
| 5         | A = 1, B = 2, C = 2.5     | Scalene Triangle |

**D. Boundary Condition A = C (isosceles triangle)**

Below is the list of possible corner cases looking like isosceles triangle but are not

| Test Case | Condition                   | Expected Outcome   |
| --------- | --------------------------- | ------------------ |
| 1         | A = -4, B = 3, C = -4       | Invalid Triangle   |
| 2         | A = 1, B = 2, C = 1         | Invalid Triangle   |
| 3         | A = 1, B = 4, C = 1         | Invalid Triangle   |
| 4         | A = 0.1, B = 0.4, C = 0.1   | Invalid Triangle   |
| 5         | A = 0.15, B = 0.25, C = 0.15 | Isosceles Triangle |

**E. Boundary Condition A = B = C (equilateral triangle)**

Below is the list of possible corner cases looking like isosceles triangle but are not

| Test Case | Condition                 | Expected Outcome     |
| --------- | ------------------------- | -------------------- |
| 1         | A = -3, B = -3, C = -3    | Invalid Triangle     |
| 2         | A = 0, B = 0, C = 0       | Invalid Triangle     |
| 3         | A = 7, B = 7, C = 7    | Equilateral Triangle |
| 4         | A = 0.2, B = 0.2, C = 0.2 | Equilateral Triangle |

**F. Boundary Condition $A^2$ + $B^2$ = $C^2$ (right-angle triangle)**

Below is the list of possible corner cases looking like right-angle triangle but are not

| Test Case | Condition                    | Expected Outcome      |
| --------- | ---------------------------- | --------------------- |
| 1         | A = 5, B = 12, C = 13          | Right Angled Triangle |
| 2         | A = -4, B = -3, C = 5        | Invalid Triangle      |
| 3         | A = -1, B = -1.414, C = 1.73 | Invalid Triangle      |
| 3         | A = 1, B = 1.414, C = 1.73   | Right Angled Triangle |

**G. Non-triangle Case**

Below is the list of possible Invalid Triangle cases

| Test Case | Condition                    | Expected Outcome |
| --------- | ---------------------------- | ---------------- |
| 1         | A = 3, B = 4, C = 9          | Invalid Triangle |
| 2         | A = -4, B = -2, C = 5        | Invalid Triangle |
| 3         | A = -1, B = -1, C = -1 | Invalid Triangle |
| 4         | A = 111, B = 1.414, C = 9.73 | Invalid Triangle |
| 5         | A = 1, B = 53, C = 9.73      | Invalid Triangle |
| 6         | A = 1, B = 1.414, C = -9.73  | Invalid Triangle |
| 7         | A = 0, B = 0, C = 0          | Invalid Triangle |

**H. Non-positive Input**

Below is the list of possible Invalid Triangle cases

| Test Case | Condition        | Expected Outcome |
| --------- | ---------------- | ---------------- |
| 1         | a=-1, b=2, c=1   | Invalid Triangle |
| 2         | a=-4, b=-5, c=-7 | Invalid Triangle |
| 3         | a=1, b=-5, c=7  | Invalid Triangle |

---

# Section B

### 1. The control flow graph for the given problem is as follows

![image](https://user-images.githubusercontent.com/100967786/232775937-78a8ff77-d3fd-4c2c-8056-89a5d32dde52.png)
### 2. Criteria specific test case for flow graph

**(a) Statement coverage test set:** In this all the statements in code should be covered
<br/>
| Test Number | Test Case |
|-------------|-----------|
| 1 | p is empty array |
| 2 | p has one point object |
| 3 | p has two points object with different y component |
| 4 | p has two points object with different x component |
| 5 | p has three or more point object with different y component |

**(b) Branch Coverage test set:** In this all branch are taken atleast once
<br/>

| Test Number | Test Case |
|-------------|-----------|
| 1 | p is empty array |
| 2 | p has one point object |
| 3 | p has two points object with different y component |
| 4 | p has two points object with different x component |
| 5 | p has three or more point object with different y component |
| 6 | p has three or more point object with same y component |
| 7 | p has three or more point object with all same x component |
| 8 | p has three or more point object with all different x component |
| 9 | p has three or more point object with some same and some different x component |

**(c) Basic condition coverage test set:** Each boolean expression has been evaluated to both true and false

| Test Number | Test Case |
|-------------|-----------|
| 1 | p is empty array |
| 2 | p has one point object |
| 3 | p has two points object with different y component |
| 4 | p has two points object with different x component |
| 5 | p has three or more point object with different y component |
| 6 | p has three or more point object with same y component |
| 7 | p has three or more point object with all same x component |
| 8 | p has three or more point object with all different x component |
| 9 | p has three or more point object with some same and some different x component |
| 10 | p has three or more point object with some same and some different y component |
| 11 | p has three or more point object with all different y component |
| 12 | p has three or more point object with all same y component |


