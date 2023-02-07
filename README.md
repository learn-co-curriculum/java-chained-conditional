# Chained Conditional Statements

## Learning Goals

- Continue learning about conditionals.
- Introduce chained conditional statements.

## Introduction

In the previous lesson we introduced the `if-else` statement. In this lesson, we
will continue expanding on the topic of conditionals but introducing a chain of
conditional statements.

Let's look at the `else if` statement.

## Else If Statements

An `if` statement can also be followed by an `else if` statement. When an
`else if` statement follows an `if`, the `else if` allows us to specify
another condition whenever the conditional clause of the `if` statement is
not true. It is similar to an `else` in that it is not required to follow
an `if` statement but differs in that it has another conditional clause
attached to it. Let's alter our code to this:

```java
import java.util.InputMismatchException;
import java.util.Scanner;

public class GradeExample {
    public static void main (String[] args) {
        Scanner scanner = new Scanner(System.in);

        try {
            // Prompt the user to enter a numeric grade from 0 to 100
            System.out.println("Enter a numeric grade from 0 - 100:");
            int grade = scanner.nextInt();

            // A passing grade is a 70 or higher
            if (grade > 70) {
                System.out.println("Congrats! You passed!");
            } else if (grade == 70) {
                System.out.println("Whew! You just passed!");
            } else {
                System.out.println("Oops! Better luck next time!");
            }

        } catch (InputMismatchException exception) {
            System.out.println("Invalid input");
        }
    }
}
```

Notice we switched the relational operator in the `if` statement's conditional
clause from `>=` to `>` and then added the `else-if` statement with the
conditional clause of `grade == 70`. So now, if the user enters 70, we would
expect the program to execute the `else-if` block.

If we were to create a flowchart of this control flow, it would look like this:

![chained-conditional-flowchart](https://curriculum-content.s3.amazonaws.com/java-mod-1/chained-conditional/chained-conditional-flowchart.png)

If we run the program in the debugger, notice that when we step-over the
breakpoint at the `if` statement, the next line of execution this time is
`else if (grade == 70)`:

![next-line-else-if-statement](https://curriculum-content.s3.amazonaws.com/java-mod-1/if-statement/intellij-debugger-else-if-statement-breakpoint.PNG)

Java will then look at the conditional clause, `grade == 70`. As we can see, the
`grade` variable is storing the value 70; therefore, `70 == 70` will evaluate to
`true`. Let's continue to step-over in the debugger:

![execute-else-if-block](https://curriculum-content.s3.amazonaws.com/java-mod-1/if-statement/intellij-debugger-else-if-block-executed.PNG)

As we can see, the code then falls into the `else-if` block. If we continue
to step-over, we will then see that the program skips over the `else` block.
This is because a conditional clause had been satisfied by either the `if`
statement's clause or any other `else-if` conditional clauses prior.

When we resume the program, the output in the console will look like this:

```text
Enter a numeric grade from 0 - 100:
70
Whew! You just passed!
```

Note: We can have as many `else-if` statements within an `if/else-if/else` block
of code. Consider this example:

```java
if (grade >= 90) {
    System.out.println("Wow! You got an A!");
} else if (grade >= 80) {
    System.out.println("You got a B!");
} else if (grade >= 70) {
    System.out.println("Congrats! You passed!");
} else {
    System.out.println("Oops! Better luck next time!");
}
```

Take note of the way the conditional clauses are ordered within the `if` and
`else-if` statements. If the user enters a grade of 90 or higher, the program
will execute the statements within the `if` block and **only** the `if` block.
The program will then skip over the `else-if` and `else` statements. If the user
enters a grade between 89 and 80, then the second `else-if` block will then be
executed. If the user enters a grade between 79 and 70, then the third `else-if`
block will be executed. Finally, if the grade is 69 or less, then the `else`
block will be executed.

You may follow along with this by either using the IntelliJ debugger, as we have
throughout this lesson, or you can use the browser-based Java visualizer
[here](https://pythontutor.com/java.html#code=public%20class%20GradeExample%20%7B%0A%20%20%20%20public%20static%20void%20main%28String%5B%5D%20args%29%20%7B%0A%20%20%20%20%20%20%0A%20%20%20%20%20%20//%20Change%20this%20hardcoded%20value%20and%20watch%20the%20code%20be%20executed%0A%20%20%20%20%20%20int%20grade%20%3D%2090%3B%0A%20%20%20%20%20%20%0A%20%20%20%20%20%20if%20%28grade%20%3E%3D%2090%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20System.out.println%28%22Wow!%20You%20got%20an%20A!%22%29%3B%0A%20%20%20%20%20%20%7D%20else%20if%20%28grade%20%3E%3D%2080%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20System.out.println%28%22You%20got%20a%20B!%22%29%3B%0A%20%20%20%20%20%20%7D%20else%20if%20%28grade%20%3E%3D%2070%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20System.out.println%28%22Congrats!%20You%20passed!%22%29%3B%0A%20%20%20%20%20%20%7D%20else%20%7B%0A%20%20%20%20%20%20%20%20%20%20System.out.println%28%22Oops!%20Better%20luck%20next%20time!%22%29%3B%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%7D&cumulative=false&heapPrimitives=nevernest&mode=edit&origin=opt-frontend.js&py=java&rawInputLstJSON=%5B%5D&textReferences=false)
to see the flow of how this program is executed.

## Conclusion

The `else if` statement creates a chain of conditional clauses that we can refer
to as a chained conditional statement. As mentioned, it is not a requirement for
an `else if` to exist, but if we do have an `else if`, then it must be chained
with an `if` statement first.
