# Classes: Kristen and the Valedictorian Problem (C++)

**Submitted by:**  
Abu Bakar Siddik  
ID: IT25052  
Session: 2024-2025  

**Supervised by:**  
Dr. Ziaur Rahman  
Associate Professor  
Department of ICT, MBSTU  

---

A HackerRank C++ practice problem on **classes and objects**.

## Problem Description

A class defines a blueprint for an object. We use the same syntax to declare objects of a class as we use to declare variables of other basic types. For example:

```cpp
Box box1;          // Declares variable box1 of type Box
Box box2;          // Declares variable box2 of type Box
```

Kristen is a contender for valedictorian of her high school. She wants to know how many students (if any) have scored higher than her in the exams given during this semester.

Create a class named `Student` with the following specifications:

- An instance variable named `scores` to hold a student's exam scores.
- A `void input()` function that reads integers and saves them to `scores`.
- An `int calculateTotalScore()` function that returns the sum of the student's scores.

## Input Format

Most of the input is handled for you by the locked code in the editor.

In the `void Student::input()` function, you must read scores from stdin and save them to your instance variable.

The first line contains `n`, the number of students in Kristen's class. The subsequent lines contain each student's exam grades for this semester (5 scores each).

## Output Format

In the `int Student::calculateTotalScore()` function, you must return the student's total grade (the sum of the values in `scores`).

The locked code in the editor will determine how many scores are larger than Kristen's and print that number to the console.

## Sample

**Input**

```
3
30 40 45 10 10
40 40 40 10 10
50 20 30 10 10
```

**Output**

```
1
```

**Explanation:** Kristen (first student) has a total of 135. The second student scores 140 (higher), the third scores 120 (lower), so only 1 student beats her.

## Solution

```cpp
#include <iostream>
using namespace std;

class Student {
private:
    int scores[5];

public:
    void input() {
        for (int i = 0; i < 5; i++) {
            cin >> scores[i];
        }
    }

    int calculateTotalScore() {
        int sum = 0;

        for (int i = 0; i < 5; i++) {
            sum += scores[i];
        }

        return sum;
    }
};

int main() {
    int n;
    cin >> n;

    Student students[1000];
    int total[1000];

    for (int i = 0; i < n; i++) {
        students[i].input();
        total[i] = students[i].calculateTotalScore();
    }

    int kristen = total[0];
    int count = 0;

    for (int i = 1; i < n; i++) {
        if (total[i] > kristen) {
            count++;
        }
    }

    cout << count << endl;

    return 0;
}
```

## Results

### Sample test case passed

<img src="images/result.png" alt="Sample test case result" width="600">

### Leaderboard

<img src="images/leaderboard.png" alt="Leaderboard" width="600">

## Concepts Practiced

- Class definition and instance variables
- Member functions (`input`, `calculateTotalScore`)
- Reading from stdin with `cin`
