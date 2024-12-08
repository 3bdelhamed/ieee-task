# ieee-task
- What is the best time complexity that can be achieved to count the number of occurrences of a given subsequence in a given array,
  (A subsequence of an array is the array resulted from removing any number of elements (possibly zero) from the original array)

from description, a subsequence does not need to be contiguous  
arr [1,2,3,4,1,3] , sub = [1 ,3] → number of occurrences is {3} in indexes is
[ [0,2] , [0,5] ,[4,5] ]
Algorithm

```
x , y = sub
countOfX = 0 , total = 0
loop (array)
    if element == x
        countOfX++
    else if element == y
        total += countOfX
total is number of occurrences of [x, y]
```

time complexity is o(n)

**Solve the same question assuming the subsequence can have any length.**
Array: [1, 2, 3, 4, 1, 2, 3]
Subsequence: [1, 2, 3]
count number of occurrences is 4
[0, 1, 2]
[0, 4, 6]
[0, 5, 6]
[4, 5, 6]

```
    n = length of arr
    m = length of subseq

    # Initialize DP table with dimensions (n+1) x (m+1)
    # dp[i][j] represents the number of ways to match first j elements of subseq in first i elements of arr
    create a 2D list dp with dimensions (n+1) x (m+1), initialized to 0

    # Base case: An empty subsequence can always be matched in any prefix of arr
    for i = 0 to n:
        dp[i][0] = 1  # There's exactly 1 way to match an empty subsequence

    # Fill the DP table
    for i = 1 to n:
        for j = 1 to m:
            if arr[i-1] == subseq[j-1]:
                # Case 1: Include the current element in the subsequence
                dp[i][j] = dp[i-1][j-1] + dp[i-1][j]
            else:
                # Case 2: Exclude the current element
                dp[i][j] = dp[i-1][j]

    # The answer is the number of ways to match the entire subsequence in the entire array → dp[n][m]

 time O(N.M)

```

- Explain method overloading in terms of an E-commerce OOP application.

method overloading for applying discounts

```
    Method 1: Apply a percentage discount
    public double applyDiscount(double percentage) {
        return price * (1 - percentage / 100);
    }

     Method 2: Apply a fixed amount discount
    public double applyDiscount(double amount, boolean isFixedDiscount) {
        return isFixedDiscount ? price - amount : price;
    }

     Method 3: Conditional discount based on quantity
    public double applyDiscount(int quantity, double discountRate) {
        return quantity > 10 ? price * (1 - discountRate / 100) : price;
    }

    double percentageDiscount = basicProduct.applyDiscount(10); // 10% off
    double fixedDiscount = basicProduct.applyDiscount(100, true); // $100 off
    double quantityDiscount = basicProduct.applyDiscount(15, 20); // 20% off for orders > 10
```
---

- **JavaScript can run scripts on the client-side. Can we use it to directly interact with the database system? Explain your answer**
  No, client-side JavaScript cannot directly interact with a database system due to security risks and browser restrictions. Instead, it sends HTTP requests to a server, which then interacts with the database and returns the results. This ensures security and proper data handling.
- **What is the difference between Authentication and Authorization?**
  Authentication verifies the identity of a user or service, and Authorization determines their access rights.

- **HTTP protocol is stateless, how do web servers overcome this to manage the request’s state?**
  while HTTP itself does not maintain state, these mechanisms (cookies, sessions, URL parameters, local storage, and hidden form fields) allow web applications to simulate a stateful experience. By leveraging these methods, developers can create applications that feel interactive and personalized, despite the underlying stateless nature of the HTTP protocol.

---
- **Explain (in Arabic) the difference between LEFT JOIN and INNER JOIN.**
INNER JOIN : هيديك جدول مشترك مبين جدولين علي كوندشن معين
LEFT JOIN  : هيديك جدول يشمل كل الصفوف الجدول الايسر و كمان الي الصفوف الي متطابقة مع اليمين

- **You have a posts table in a blog website database. You need to implement a simple search functionality that looks for the given search query inside the title and the content of the post and returns the post if the query is present. The search functionality should be case insensitive. Order the posts according to the number of views descendingly. Write the SQL query that can be used to achieve this functionality.**

```
SELECT *
FROM posts
WHERE LOWER(title) LIKE LOWER('%search_query%')
   OR LOWER(content) LIKE LOWER('%search_query%')
ORDER BY views DESC;
```
