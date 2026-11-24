# JOBSHEET 11 - 2-Dimensional Arrays

**Student Identity:**
* **Name:** Datu Ayu Fitria Ceasa
* **NIM:** 264107020087
* **Class / Present number:** 1I / 06

---

## 1: OBJECTIVES

1. Declare, instantiate, and initialize 2-dimensional arrays in Java. 
2. Access and fill elements of a 2-dimensional array using row and column indices. 
3. Process 2-dimensional arrays with nested loops, using both for and foreach. 
4. Create 2-dimensional arrays whose rows have different lengths (*jagged arrays*).
5. Compute row averages and column averages in a real case study.

---

## 3: Lab Exercises

### 3.1. Experiment 1: Declaration, Initialization, and Displaying a 2-Dimensional Array 
#### 3.1.1 Java Code
```java
public class cinema06 {
    public static void main(String[] args) {
        String[][] audience = new String[4][2];

        audience[0][0] = "Amin"; 
        audience[0][1] = "Bena"; 
        audience[1][0] = "Candra"; 
        audience[1][1] = "Dela"; 
        audience[2][0] = "Eka"; 
        audience[2][1] = "Farhan"; 
        audience[3][0] = "Gisel"; 
        audience[3][1] = "Hana";

        System.out.printf("%s \t %s\n", audience[0][0], audience[0][1]);
        System.out.printf("%s \t %s\n", audience[1][0], audience[1][1]); 
        System.out.printf("%s \t %s\n", audience[2][0], audience[2][1]); 
        System.out.printf("%s \t %s\n", audience[3][0], audience[3][1]); 
        
    }
}
```

#### 3.1.2 Screenshot Output

![Example Image of Experiment 1 Output](/numberarray.png)

#### 3.1.3 Questions
* **Question 1:** Must the elements of an array be filled in order, starting from index 0? Explain!
   * **Answer:** The program will not compile if numbers is still an int[] and you assign 5.0 or 7.5. Those are double literals, and Java does not automatically narrow them to integers because that could lose the fractional part. The other values, 12867 and 2000000, are valid int values. If you need to keep the decimal values, declare the array as double[]; Java will convert the integer values to doubles as well.
* **Question 2:** Temporarily comment out the line audience[3][1] = "Hana";, then compile and run again. 
What is printed for row 4 now? Explain using the default values of arrays.   
  * **Answer:**
   
* **Question 3:** Restore the line you commented out in Question 2. Why is it important to fill every element before the array is displayed? 
  * **Answer:**
   
    
* **Question 4:** Add the following code after Step 4. Explain the purpose of audience.length and audience[0].length!
```
System.out.println(audience.length);
System.out.println(audience[0].length); 
System.out.println(audience[1].length); 
System.out.println(audience[2].length); 
System.out.println(audience[3].length);
```  
  * **Answer:** The array has four elements, with valid indexes 0 through 3. The loop runs for i = 0, 1, 2, and 3, printing those values. When i becomes 4, numbers[4] is out of bounds, so Java throws an ArrayIndexOutOfBoundsException. The foreach loop and Arrays.toString() are not reached.
    
* **Question 5:** Do audience[0].length, audience[1].length, audience[2].length, and audience[3].length have the same value? Why?  
 * **Answer:**
    
-Indexed for loop: Gives access to the index and value. Use it when you need the position, want to update array elements, or need to control which indexes are processed.
    
-Foreach loop: Processes each value without managing indexes. Use it when you simply need to read or process every element.

-Arrays.toString(numbers): Prints the whole array in a compact format, such as [5, 13, -7, 17]. Use it for quick display or debugging when you do not need custom formatting per element.

* **Question 6:** Modify the code in Question 4 to display the length of every row using a for loop. Compile, run, and observe the result.
```
System.out.println(audience.length); 
for (int i = 0; i < audience.length; i++) { 
System.out.println("Length of row " + (i + 1) + ": " + 
audience[i].length); 
} 
```
 * **Answer:**
   
* **Question 7:** Modify the code in Question 5 to display the length of every row using a foreach loop. Compile, run, and observe the result.
```
System.out.println(audience.length); 
for (String[] rowAudience : audience) { 
System.out.println("Row length: " + rowAudience.length); 
} 
```
  * **Answer:** 
 
* **Question 8:** Add code to display the names in row 3 (index 2) using a for loop. Compile, run, and observe the result. 
```
System.out.println("Audience in row 3: "); 
for (int i = 0; i < audience[2].length; i++) { 
System.out.println(audience[2][i]); 
} 
```
  * **Answer:**
    
* **Question 9:** Modify the code in Question 8 to use a foreach loop. Compile, run, and observe the result.
```
System.out.println("Audience in row 3: "); 
for (String name : audience[2]) { 
System.out.println(name); 
}
```
  * **Answer:**
 
* **Question 10:** Modify the code in Question 9 to display the audience of every row. Use String.join(), compile, run, and observe the result.
```
for (int i = 0; i < audience.length; i++) { 
System.out.println("Audience in row " + (i + 1) + ": " + String.join(", ", 
audience[i])); 
}
```
  * **Answer:**
    
* **Question 11:**  In your opinion, what are the advantages and disadvantages of a foreach loop compared to a for loop? 
  * **Answer:**
 
* **Question 12:** What is the maximum row index of the array audience? Where does this value come from? 
  * **Answer:**
 
* **Question 13:** What is the maximum column index of the array audience? Is it the same for every row? 
  * **Answer:**
 
* **Question 14:** What does String.join() do? Explain the parameters it receives. 
  * **Answer:**
---

### 3.2. Experiment 2: Scanner and Loops for Input and Output of a 2-Dimensional Array
#### 3.2.1 Java Code
```java
import java.util.Scanner;

public class CinemaWithScanner06 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int row, col;
        String name, choice; 
        String[][] audience = new String[4][2];

        while (true) { 
            System.out.print("Enter name: "); 
            name = sc.nextLine(); 
            System.out.print("Enter row: "); 
            row = sc.nextInt(); 
            System.out.print("Enter column: "); 
            col = sc.nextInt(); 
            sc.nextLine(); 

            audience[row - 1][col - 1] = name; 

            System.out.print("Add another audience member? (y/n): "); 
            choice = sc.nextLine(); 

            if (choice.equalsIgnoreCase("n")) { 
                break; 
            } 
        }   
    }
}

```
![Example Image of Experiment 2 Output](/scorearray.png)



#### 3.2.3 Questions
* **Question 1:** Must the elements of an array be filled from Scanner in order, starting from index 0? explain! 
  * **Answer:**
    The syntax if (score < 0 || score > 100) { System.out.println("Invalid score. Please enter a valid score!"); continue; } means: if the score is less than 0 or greater than 100, it is invalid, so the program prints an error message and immediately skips the rest of the current loop iteration using continue. Its purpose is to prevent 
* **Question 2:** Modify the program so that it shows the following menu:
```
1. Enter audience data 
2. Show the audience list 
3. Exit
```
  * **Answer:**
    The i++ statement is written at the end of the while loop so that each time a valid student score is entered and processed, the counter increases by 1. This keeps track of how many students have already been handled and ensures the loop eventually stops when i reaches studentCount. If i++ were written at the beginning of the loop, the loop would skip the first student because i would increase before checking or processing the score, causing the program to count incorrectly and possibly stop too early.
* **Question 3:** Modify the program to handle a row or column number that does not exist (for example row 7 or column 0).   
  * **Answer:**
    If the number of students entered is 19, the while loop will run 19 times, because the loop condition is while (i < studentCount), so it repeats until i reaches 19. Each valid student input increases i by 1, and the loop stops when i becomes 19.
* **Question 4:** In menu 1, display a warning if the chosen seat is already taken by another audience member, then ask for the row and column again.

Hint: A seat is taken when audience[row - 1][col - 1] != null. The range must also be 
checked against audience.length for rows, and audience[row - 1].length for columns.


  * **Answer:**
    ![](/modifiedcode.png)

* **Question 5:** In menu 2, if a seat is empty (null), display *** instead of null. 
  * **Answer:**
 

### 3.3. Experiment 3: 2-Dimensional Array with Rows of Different Lengths

#### 3.3.1 Java Code
```java
import java.util.Arrays;

public class numbers06 {
    public static void main(String[] args) {
        int[][] myNumbers = new int[3][]; 
        myNumbers[0] = new int[5]; 
        myNumbers[1] = new int[3]; 
        myNumbers[2] = new int[1]; 

        for (int i = 0; i < myNumbers.length; i++) { 
            System.out.println(Arrays.toString(myNumbers[i])); 
        }
    }
}
```

#### 3.3.2 Screenshot Output

![Example Image of Experiment 3 Output](/average.png)

#### 3.3.3 Questions
* **Question 1:** What does Arrays.toString() do? 
  * **Answer:** The loop runs once. A do-while loop executes its body before checking the condition. Since the first name is “cancel,” the break statement exits the loop during that first execution.
* **Question 2:** In Code 16, Arrays.toString() is called on myNumbers[i]. Change the call to Arrays.toString(myNumbers), then compile and run the program. What is displayed? Explain.   
  * **Answer:** The loop’s condition is while (true), which is always true. In practice, the loop stops when the customer enters “cancel” and the break statement runs.
* **Question 3:** Also run System.out.println(Arrays.deepToString(myNumbers));. Compare the result with Code 16. Why is deepToString() needed for a 2-dimensional array?  
  * **Answer:** true makes the loop repeat indefinitely unless it is exited another way, such as with the break statement.
* **Question 4:** What is the default value of an array element of type int?
  * **Answer:**
* **Question 5:** Add the following code to display the length of each row. Compile and run it, then observe the result.
```
for (int i = 0; i < myNumbers.length; i++) { 
System.out.println("Length of row " + (i + 1) + ": " + 
myNumbers[i].length); 
} 
```
  * **Answer:**
* **Question 6:** The array myNumbers has a different length for each row. Can the length of an array be changed after it has been instantiated? Explain.
  * **Answer:**
* **Question 7:** After instantiation, run myNumbers[0] = new int[7];, then print myNumbers.length and myNumbers[0].length. Which value changes? Why? 
  * **Answer:**
  
### 3.4. Experiment 4: SIAKAD Case Study 

#### 3.4.1 Java Code
```java
public class scoreSearch06 {
    public static void main(String[] args) {
        int[] scores = {78, 65, 90, 55, 88, 72}; 
        int key = 90; 
        boolean found = false; 
        for (int i = 0; i < scores.length; i++) { 
            if (scores[i] == key) { 
                System.out.println("Score " + key + " was found at index " + i); 
                found = true; 
                break; 
            } 
        } 
        if (!found) { 
            System.out.println("Score " + key + " was not found."); 
        }
    }
}
```

#### Screenshot Output

![Example Image of Experiment 4 Output](/linear.png)


#### 3.4.2 Questions
* **Question 1:** What if the number of students and the number of courses change? Modify the SIAKAD program so that both numbers can be decided while the program runs.

Hint: use Scanner to read the two values, then create the array with new 
int[numStudents][numCourses]. Make sure every loop uses length, not a fixed number.   
  * **Answer:** The loop runs once. A do-while loop executes its body before checking the condition. Since the first name is “cancel,” the break statement exits the loop during that first execution.
* **Question 2:** In Code 20, the variable totalPerStudent is declared inside the outer loop. What happens if you move the declaration outside the loop? Explain with an example of scores. 
  * **Answer:** The loop’s condition is while (true), which is always true. In practice, the loop stops when the customer enters “cancel” and the break statement runs.
* **Question 3:** If some scores have not been entered yet (they hold the default value 0), how does this affect the average?   
  * **Answer:** true makes the loop repeat indefinitely unless it is exited another way, such as with the break statement.


---

## 4: Assignment 

Implement the flowchart of the survey exercise from the Programming Fundamentals (theory) 
slides in a Java program. The survey data consists of 10 respondents and 6 questions with 
answers from 1 to 5. The program must: 

      
• store the survey results in a 2-dimensional array; 

• display the average score for each respondent; 

• display the average score for each question; 

• display the overall average score.
      

### 4.1 Task 1 Code Implementation

```java
import java.util.Scanner;

public class task2dimentionalarray06 {
    private static final int NUM_RESPONDENTS = 10;
    private static final int NUM_QUESTIONS = 6;

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[][] surveyResults = new int[NUM_RESPONDENTS][NUM_QUESTIONS];
        int overallTotal = 0;

        for (int respondent = 0; respondent < NUM_RESPONDENTS; respondent++) {
            System.out.println("Enter answers for respondent " + (respondent + 1) + ":");

            for (int question = 0; question < NUM_QUESTIONS; question++) {
                int answer;
                do {
                    System.out.print("Question " + (question + 1) + " (1-5): ");
                    answer = sc.nextInt();
                    if (answer < 1 || answer > 5) {
                        System.out.println("Please enter a score from 1 to 5.");
                    }
                } while (answer < 1 || answer > 5);

                surveyResults[respondent][question] = answer;
                overallTotal += answer;
            }
        }

        System.out.println("\nAverage score for each respondent:");
        for (int respondent = 0; respondent < NUM_RESPONDENTS; respondent++) {
            int respondentTotal = 0;
            for (int question = 0; question < NUM_QUESTIONS; question++) {
                respondentTotal += surveyResults[respondent][question];
            }
            System.out.printf("Respondent %d: %.2f%n",
                    respondent + 1, (double) respondentTotal / NUM_QUESTIONS);
        }

        System.out.println("\nAverage score for each question:");
        for (int question = 0; question < NUM_QUESTIONS; question++) {
            int questionTotal = 0;
            for (int respondent = 0; respondent < NUM_RESPONDENTS; respondent++) {
                questionTotal += surveyResults[respondent][question];
            }
            System.out.printf("Question %d: %.2f%n",
                    question + 1, (double) questionTotal / NUM_RESPONDENTS);
        }

        System.out.printf("%nOverall average score: %.2f%n",
                (double) overallTotal / (NUM_RESPONDENTS * NUM_QUESTIONS));
    }
}

```
![](/managing.png)

---

## 4: Conclusion

These programs demonstrate how loops and conditional st
