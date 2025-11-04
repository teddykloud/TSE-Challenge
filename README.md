TSE C# Coding Challenge
This repository contains my solution for the Technical Support Engineer C# coding challenge.

The solution is a C# static class, KeypadPhoneConverter, that correctly converts T9-style keypad input into a human-readable string.

Solution Design
My approach was to build a simple, efficient, and robust state machine.

Core Logic: The method iterates through the input string character by character. It uses a StringBuilder (currentPresses) to buffer consecutive, identical key presses.

Committing: This buffer is "committed" (i.e., processed and converted to a letter) whenever a "commit trigger" is encountered:

A different button is pressed.

A pause (' ') is detected.

A backspace ('*') is detected.

The send ('#') key is hit.

Performance: I used StringBuilder for all string creation, avoiding inefficient string + string concatenation in a loop. The keypad map is a static readonly Dictionary for O(1) (constant time) lookups.

Readability: A local Action helper function (processBuffer) is used to contain the buffer-commit logic, adhering to the DRY (Don't Repeat Yourself) principle and keeping the main loop clean.

Robustness: The solution gracefully handles null and empty inputs. It also includes a final check after the loop to process any trailing key presses, making it stable even if the input string does not end with the '#' (send) key.

How to Run & Test
This solution is structured as a .NET 10 Solution (.sln) containing a class library (OldPhonePadSolution) and a corresponding xUnit test project (OldPhonePadTests).

The test project contains a comprehensive suite of tests, including all examples from the prompt plus numerous edge cases.

To run the tests:

Clone this repository.

Navigate to the test project directory: cd IronSoftware-TSE-Challenge/KeypadPhoneTests

Run the tests: dotnet test

You will see a "Test Run Successful" message confirming the solution's correctness.

Note on Example 4
The fourth example in the prompt, OldPhonePad("8 88777444666*664#") => ?????, appears to contain a typo. Based on a literal interpretation of the rules, the correct output is "TURING". My solution correctly implements these rules, and the test case [InlineData("8 88777444666*664#", "TURING")] confirms this behavior.# TSE-Challenge
Solution for the C# Coding Challenge for the Technical Support Engineer role.
