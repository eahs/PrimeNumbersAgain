# Prime Numbers Again

Complete a .NET 10 console application that finds the **nth prime number**. A prime is an integer greater than 1 whose only positive divisors are 1 and itself. The sequence begins 2, 3, 5, 7, 11, 13, ... so the first prime is 2 and the sixth prime is 13.

Start by finding the first 1,000 primes correctly, then improve your approach to handle much larger positions. The challenge is to explain why your algorithm works and reduce how much work it does as the input grows.

## Your task

Implement `FindNthPrime(int n)` in `PrimeNumbersAgain/PrimeNumbersAgain/Program.cs`. Its current `return 0;` is a placeholder for your solution. Use a one-based position: valid assignment inputs are **1 through 1,999,999**. The input is the position in the sequence, not an upper bound on the prime's value.

The starter code already prompts for an integer, times the call to your method, and prints the result and a time check. It does not currently validate whether the integer is within the assignment's range.

To pass, return the correct prime for the requested position within **3,000 milliseconds (3 seconds)**, the current `MaxAllowableTime` in the starter code. The timer measures the search, excluding user input, and displays elapsed milliseconds with three decimal places. A fast but incorrect result does not satisfy the assignment; the printed time check only evaluates speed.

## Run and check your work

Install the .NET 10 SDK, then run this command from the repository root:

```sh
dotnet run --project PrimeNumbersAgain/PrimeNumbersAgain/PrimeNumbersAgain.csproj --configuration Release
```

Check small, known answers before testing larger inputs:

| Input (`n`) | Expected prime |
| ---: | ---: |
| 1 | 2 |
| 2 | 3 |
| 6 | 13 |
| 1,000 | 7,919 |

Use the same inputs and Release configuration when comparing versions. Run each version several times, since timings vary with machine load and runtime warm-up.

## Optimizations to consider

- **Stop when you find a divisor.** One divisor other than 1 and the candidate itself is enough to prove that a candidate is composite; there is no need to continue testing it.
- **Limit trial division to the square root.** A composite number must have a factor at or below its square root. Think about why checking larger divisors cannot reveal a new factor pair.
- **Skip even numbers after handling 2.** Every larger even number is composite. Consider both the candidates you generate and the divisors you test.
- **Reuse primes you have already found.** For trial division, composite divisors are redundant. Consider storing earlier primes and testing only those up to the candidate's square root, balancing extra memory against fewer divisions.
- **Skip multiples of other small primes.** After handling 2 and 3, every remaining prime has the form `6k - 1` or `6k + 1`. These forms narrow the candidates but do not guarantee primality.

Try one change at a time, verify the answers again, and compare timings. Be prepared to explain which unnecessary operations each change removes.
