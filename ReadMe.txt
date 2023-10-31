Article: Top 60 C# Code Snippets For Every Developer
https://maherz.medium.com/top-60-c-code-snippets-for-every-developer-cf651018c222

Hey there! Today, I have something special to share with you — a compilation of 60 C# code snippets that I’ve found incredibly helpful in my own work.
In this article, we’re not just going to look at how these snippets solve everyday programming problems, but we’re also going to understand why they work the way they do. This is about building a deeper understanding, not just a quick copy-paste job.
These snippets are for you if you’ve been working with C# and have ever found yourself stuck on a problem, not sure how to tackle it efficiently. They’re also for you if you’re relatively new to C# and are trying to understand how to use the language more effectively.
Alright, enough talk. Let’s jump in and start exploring these code snippets together. I hope you find them as useful as I have.
Before we continue, in the provided examples I tried to add a touch of humour and list some of the use cases. Hopefully that’ll keep you entertained as well, as at least I, have always remembered the fun things easier :) Lets get started!
10 Complex All Type Snippets
1. Binary Search
public int BinarySearch(int[] arr, int target)
{
   int left = 0;
   int right = arr.Length - 1;
   while (left <= right)
   {
       int mid = left + (right - left) / 2;
       if (arr[mid] == target)
           return mid;
       if (arr[mid] < target)
           left = mid + 1;
       else
           right = mid - 1;
   }
   return -1;
}
Think of this code as the Sherlock Holmes of searching methods. You know, instead of wasting your time rummaging around looking for a particular item, wouldn’t it be nice if you could just cut to the chase? That’s precisely what Binary Search does — it saves your time (and sanity) by dividing and conquering!
Use Cases:
Searching for a specific user in a sorted list of users
Looking for a particular book in a sorted library database
2. Bubble Sort
public void BubbleSort(int[] arr)
{
   int len = arr.Length;
   for (int i = 0; i < len - 1; i++)
       for (int j = 0; j < len - i - 1; j++)
           if (arr[j] > arr[j + 1])
           {
               int temp = arr[j];
               arr[j] = arr[j + 1];
               arr[j + 1] = temp;
           }
}
Just like how you sometimes throw all your clothes in the air and then arrange them (come on, we all do that, right?), Bubble Sort shuffles around the numbers in an array until they’re in perfect order. Although it’s not the quickest sort around, it’s definitely a fun one to watch.
Use Cases:
Sorting leaderboard scores in ascending order
Organizing a list of products by their prices
3. Depth-First Search (DFS) on Graph
public void DFS(int v, bool[] visited, List<int>[] adj)
{
   visited[v] = true;
   Console.Write(v + " ");
   foreach (int neighbour in adj[v])
   {
       if (!visited[neighbour])
           DFS(neighbour, visited, adj);
   }
}
DFS is like that friend who just has to explore every nook and cranny when you go hiking together. It ventures as deep as it can into a path before it even considers trying a new one. Use it when you need a thorough, comprehensive search through all nodes of a graph.
Use Cases:
Pathfinding in a maze
Analyzing network connections
4. Fibonacci Series
public void PrintFibonacci(int n)
{
   int a = 0, b = 1, c;
   for(int i = 0; i < n; i++)
   {
       Console.Write(a + " ");
       c = a + b;
       a = b;
       b = c;
   }
}
Feeling in the mood for some numerical elegance? The Fibonacci series is like the symphony of numbers, each number a harmonious blend of its two predecessors. This snippet helps you generate a Fibonacci series of ’n’ terms.
Use Cases:
To solve problems related to recursive sequences in math
In algorithms related to search and sorting, or even cryptography
5. Factorial Calculation
public int Factorial(int n)
{
   if (n == 0)
       return 1;
   else
       return n * Factorial(n - 1);
}
Remember when you thought you could eat an infinite number of cookies and then realised you probably couldn’t get past 10? Well, factorials are kind of like that — they involve multiplying all positive integers up to a certain number, and they get big fast! Use this snippet when you need to compute a factorial.
Use Cases:
In calculating combinations and permutations for statistics
Used in certain search and query optimization algorithms
6. Matrix Multiplication
public int[,] MultiplyMatrix(int[,] a, int[,] b)
{
   int[,] result = new int[a.GetLength(0),b.GetLength(1)];
   for (int i = 0; i < result.GetLength(0); i++)
   {
       for (int j = 0; j < result.GetLength(1); j++)
       {
           result[i, j] = 0;
           for (int k = 0; k < a.GetLength(1); k++) // or k<b.GetLength(0)
               result[i, j] += a[i, k] * b[k, j];
       }
   }
   return result;
}
Matrix multiplication is like a party where every row from the first matrix gets to mingle with every column from the second matrix. And the result? A brand new matrix with elements created from the sum of multiplied pairs. So, when you want your matrices to have a party, this snippet will be your DJ!
Use Cases:
In computer graphics to transform a 3D object into a different scale or position
In solving system of linear equations in numerical methods
7. Palindrome Checker
public bool IsPalindrome(string str)
{
   str = str.ToLower();
   int i = 0, j = str.Length - 1;
   while (i < j)
   {
       if (str[i++] != str[j--])
           return false;
   }
   return true;
}
If you’re not sure whether a word or phrase is a secret palindrome, this function has got your back.
Use Cases:
Checking if a word is a palindrome for a word game or puzzle
Verifying the symmetry of DNA sequences in bioinformatics
8. Sieve of Eratosthenes (Finding all prime numbers up to n)
public List<int> SieveOfEratosthenes(int n)
{
   bool[] prime = new bool[n + 1];
   for (int i = 0; i <= n; i++)
       prime[i] = true;


   for (int p = 2; p * p <= n; p++)
   {
       if (prime[p] == true)
       {
           for (int i = p * p; i <= n; i += p)
           {
               prime[i] = false;
           }
       }
   }


   List<int> primeNumbers = new List<int>();


   for (int i = 2; i <= n; i++)
   {
       if (prime[i])
       {
           primeNumbers.Add(i);
       }
   }


   return primeNumbers;
}
The Sieve of Eratosthenes is an ancient (but gold) algorithm to fish out all primes up to a given number ’n’. It’s like a sieve sifting out the composite numbers, leaving only primes behind.
Use Cases:
Generating prime numbers for cryptographic applications
Using in number theory and mathematical problems
9. QuickSort Algorithm
public void QuickSort(int[] arr, int low, int high)
{
   if (low < high)
   {
       int pi = Partition(arr, low, high);
       QuickSort(arr, low, pi - 1);
       QuickSort(arr, pi + 1, high);
   }
}


int Partition(int[] arr, int low, int high)
{
   int pivot = arr[high];
   int i = (low - 1);
   for (int j = low; j <= high - 1; j++)
   {
       if (arr[j] < pivot)
       {
           i++;
           Swap(arr, i, j);
       }
   }
   Swap(arr, i + 1, high);
   return (i + 1);
}


void Swap(int[] arr, int a, int b)
{
   int temp = arr[a];
   arr[a] = arr[b];
   arr[b] = temp;
}
QuickSort, as its name suggests, is a fast and efficient sorting algorithm. It picks a pivot element, and then partitions the array around this pivot.
Use Cases:
Sorting data in software applications where time complexity matters
In select algorithms where the selection is done based on some condition
10. Finding Length of Linked List (Iteratively)
public int GetLength(ListNode head)
{
   int count = 0;
   ListNode current = head;
   while (current != null)
   {
       count++;
       current = current.next;
   }
   return count;
}
This function walks through the linked list just like you would pace back and forth, impatiently waiting for your caffeine fix, and counts the number of nodes.
Use Cases:
Determining the size of a dynamically built data structure
Evaluating the length of a linked list to solve various data manipulation problems
10 Dictionary Snippets
1. Populate a Dictionary using Linq
string[] fruits = { "apple", "banana", "cherry" };
var fruitsDictionary = fruits.Select((fruit, index) => new { fruit, index })
                            .ToDictionary(x => x.fruit, x => x.index);
We’re all about efficiency, and Linq can be a wonderful tool to help us populate a dictionary in a single statement. In this snippet, I'm taking an array of fruits and turning it into a dictionary, using the fruit name as a key and the index as a value.
Use Cases:
Quickly transforming a list of objects into a lookup table
Converting arrays into dictionaries for easier access
2. Creating a Nested Dictionary
Dictionary<string, Dictionary<string, int>> nestedDictionary =
   new Dictionary<string, Dictionary<string, int>>();
nestedDictionary["Fruits"] = new Dictionary<string, int> { { "Apple", 1 }, { "Banana", 2 } };
Nested dictionaries are like inception for data structures: a dictionary within a dictionary. These are great when you have complex data to store, and you need to maintain a relationship between different entities.
Use Cases:
Storing complex relationships between entities
Representing multi-level categories in a product list
3. Using ConcurrentDictionary for Thread-Safe Operations
ConcurrentDictionary<string, int> concurrentDictionary = new ConcurrentDictionary<string, int>();
concurrentDictionary.TryAdd("Apple", 1);
concurrentDictionary.TryUpdate("Apple", 2, 1);
It ensures thread-safe operations when you need to add or update entries concurrently. It's like having a traffic controller in a busy intersection.
Use Cases:
Implementing multi-threaded operations involving dictionary
Updating a shared resource in parallel computing scenarios
4. Sorting a Dictionary by Key using Linq
Dictionary<string, int> fruits = new Dictionary<string, int> { { "Apple", 1 }, { "Banana", 2 }, { "Cherry", 3 } };
var sortedDictionary = fruits.OrderBy(x => x.Key).ToDictionary(x => x.Key, x => x.Value);
Sometimes, sorting a dictionary by key can be a handy feature, especially when you want to display entries in a certain order. With Linq, you can easily achieve this, making your dictionary a well-ordered collection.
Use Cases:
Sorting dictionary entries for display purposes
Preparing data for algorithms that require sorted input
5. Dictionary as a Simple Cache
public class SimpleCache<TKey, TValue>
{
   private Dictionary<TKey, TValue> cache = new Dictionary<TKey, TValue>();
   public TValue Get(TKey key, Func<TKey, TValue> valueFactory)
   {
       if (!cache.TryGetValue(key, out TValue value))
       {
           value = valueFactory(key);
           cache[key] = value;
       }
       return value;
   }
}
I find this particularly cool. Using a dictionary, you can build a simple cache to avoid costly computations or network calls. You call Get with a key and a factory function. If the key isn't in the dictionary, it uses the function to create the value, adds it to the dictionary, and then returns it.
Use Cases:
Avoiding duplicate calculations in computational algorithms
Caching frequently used data from a database or API
6. Using Dictionary<TKey, TValue>.ValueCollection
Dictionary<string, int> fruits = new Dictionary<string, int> { { "Apple", 1 }, { "Banana", 2 } };
Dictionary<string, int>.ValueCollection fruitValues = fruits.Values;
Many people forget that dictionary values can be accessed directly as a collection using the Values property. This can be handy when you only need to work with the values in a dictionary, not the keys.
Use Cases:
Summing up all values in a dictionary
Finding the minimum or maximum value in a dictionary
7. Using AsParallel for Parallel Operations
Dictionary<string, int> largeDictionary = ... // Large dictionary
var modifiedDictionary = largeDictionary.AsParallel().Select(kvp => new { kvp.Key, Value = kvp.Value * 2 }).ToDictionary(x => x.Key, x => x.Value);
The AsParallel method in LINQ provides a way to perform operations in parallel, which can lead to significant performance improvements when dealing with large dictionaries. Please note that you should use it judiciously, as it may not provide benefits for smaller dictionaries and can even decrease performance due to the overhead of parallelism.
Use Cases:
Performing time-consuming operations on large dictionaries
Applying a function to each value in the dictionary for data transformation
8. Using Dictionary<TKey, TValue>.KeyCollection
Dictionary<string, int> fruits = new Dictionary<string, int> { { "Apple", 1 }, { "Banana", 2 } };
Dictionary<string, int>.KeyCollection fruitKeys = fruits.Keys;
Similar to the ValueCollection we discussed earlier, KeyCollection gives you direct access to the keys in a dictionary. It's a great way to iterate over the keys without worrying about the values.
Use Cases:
Checking if a certain key exists in the dictionary
Iterating over all keys for data analysis
9. Using HashSet<T> to Remove Duplicates
Dictionary<string, int> fruitsWithDuplicates = new Dictionary<string, int> { { "Apple", 1 }, { "Apple", 1 }, { "Banana", 2 } };
Dictionary<string, int> fruitsWithoutDuplicates = new HashSet<string>(fruitsWithDuplicates.Keys).ToDictionary(x => x, x => fruitsWithDuplicates[x]);
A HashSet<T> is an often overlooked but powerful tool to remove duplicates from a collection. When combined with a dictionary, it can be used to remove duplicate keys and create a new dictionary.
Use Cases:
Removing duplicates from a user-input dictionary
Cleaning up data during pre-processing
10. Using SortedDictionary<TKey, TValue> for Automatic Sorting
SortedDictionary<string, int> sortedFruits = new SortedDictionary<string, int> { { "Apple", 1 }, { "Banana", 2 } };
A SortedDictionary<TKey, TValue> automatically sorts the keys in a dictionary. It can be beneficial when you constantly need your data to be in a sorted state. Note, however, that the sorting process can introduce a performance cost.
Use Cases:
Implementing a priority queue
Maintaining sorted data for binary search operations
10 Threading Snippets
1. The Task.Run Shortcut
Task.Run(() =>
{
   // Long running operation...
});
Task.Run is a handy shortcut to spin off a background task. It's the equivalent of creating a new Task and then calling Start(), but with less code. Who doesn't love brevity?
Use Cases:
Starting a new operation that doesn’t require immediate attention
Doing heavy computations without blocking the main thread
2. Cancellation Tokens
CancellationTokenSource cts = new CancellationTokenSource();
Task.Run(() =>
{
   // Check the cancellation token regularly
   while (!cts.Token.IsCancellationRequested)
   {
       // Do some work...
   }
}, cts.Token);


// Cancel the task
cts.Cancel();
Cancellation tokens allow you to elegantly stop a task mid-flight. It’s like having a friendly tap on the shoulder to tell your task it’s time to stop.
Use Cases:
Stopping a background operation when exiting the application
Cancelling a long-running operation when it’s no longer needed
3. Safe Updates with Interlocked.Increment
int counter = 0;
Parallel.For(0, 10000, i => Interlocked.Increment(ref counter));
The Interlocked class provides atomic operations for variables shared by multiple threads. Interlocked.Increment is a way to safely increment a counter in a multi-threaded environment. It ensures your count doesn't miss a beat.
Use Cases:
Updating shared counters in multi-threaded scenarios
Making sure thread-based race conditions don’t cause incorrect results
4. Synchronization with Mutex
Mutex mutex = new Mutex();
mutex.WaitOne();
try
{
   // Do some work...
}
finally
{
   mutex.ReleaseMutex();
}
Mutexes are like traffic lights for threads. They ensure that only one thread can access a piece of code at a time, preventing unpleasant surprises.
Use Cases:
Protecting critical sections of code from simultaneous access
Synchronizing operations across multiple threads
5. Using BlockingCollection<T> for Thread-Safe Data Handling
BlockingCollection<int> data = new BlockingCollection<int>();
Task.Run(() =>
{
   while (!data.IsCompleted)
   {
       int item;
       if (data.TryTake(out item))
       {
           // Process item...
       }
   }
});
BlockingCollection<T> provides a thread-safe way to handle data across multiple threads. It's like having a secure vault for your shared data.
Use Cases:
Implementing producer-consumer scenarios
Safely exchanging data between multiple threads
6. Task Continuations with ContinueWith
Task<int> t = Task.Run(() => 42);
t.ContinueWith((antecedent) => Console.WriteLine(antecedent.Result));
Task continuations allow you to specify what should happen when a task completes. It’s like setting up a row of dominoes where one triggers the next.
Use Cases:
Performing an operation when a task completes
Creating a chain of dependent tasks
7. Exception Handling in Tasks
Task task = Task.Run(() => { throw new Exception("Oops!"); });
try
{
   task.Wait();
}
catch (AggregateException ex)
{
   Console.WriteLine(ex.InnerExceptions[0].Message);  // Prints "Oops!"
}
If exceptions in tasks were not handled correctly, they could bring your entire application down. With this hack, you can handle exceptions in tasks gracefully, just like you handle a glass of champagne.
Use Cases:
Catching and handling exceptions thrown in tasks
Making your application resilient to errors in background tasks
8. Thread-local Storage with ThreadLocal<T>
ThreadLocal<int> threadLocal = new ThreadLocal<int>(() => 42);
Console.WriteLine(threadLocal.Value);  // Prints 42
ThreadLocal<T> allows you to define data that is unique to each thread. It's like giving each thread its own private storage locker.
Use Cases:
Implementing thread-specific data for performance optimization
Storing state that should not be shared across threads
9. Using SemaphoreSlim for Limiting Concurrency
SemaphoreSlim semaphore = new SemaphoreSlim(2);  // Limit to 2 threads
Task.Run(() =>
{
   semaphore.Wait();
   try
   {
       // Do some work...
   }
   finally
   {
       semaphore.Release();
   }
});
Semaphores are great for controlling access to a resource that has a limited capacity. It’s like a bouncer at a nightclub, controlling how many threads can enter.
Use Cases:
Limiting the number of threads that can access a resource
Preventing resource exhaustion by limiting concurrency
10. Manual Reset Events for Cross-thread Synchronization
ManualResetEvent mre = new ManualResetEvent(false);
Task.Run(() =>
{
   // Wait for the event to be set
   mre.WaitOne();
   // Do some work...
});
// Set the event
mre.Set();
Manual reset events are a great tool for synchronizing operations across multiple threads. It’s like a starting gun at a race, signaling to all threads to start their operation.
Use Cases:
Synchronizing start times across multiple threads
Waiting for a certain condition to be met in another thread
10 Collections Snippets
1. Read-Only Collections
List<string> myList = new List<string> {"A", "B", "C"};
ReadOnlyCollection<string> myReadOnlyList = myList.AsReadOnly();
You can create read-only collections with the AsReadOnly method. This ensures that the collection won't be accidentally modified, which can be crucial when dealing with important data. Like a priceless artifact in a museum, it's look but don't touch!
Use Cases:
When you want to share a collection but don’t want it to be modified
To prevent unwanted side effects in your code
2. Implicitly Typed Arrays
var array = new[] { "A", "B", "C" };
You can create implicitly typed arrays with the new[] keyword. This saves typing and keeps your code clean and simple. It's like the dishwasher of array creation!
Use Cases:
When you want to create an array inline
When the type of the array is obvious from the context
3. Queue and Stack
Queue<int> queue = new Queue<int>();
queue.Enqueue(1);
queue.Enqueue(2);
int first = queue.Dequeue();


Stack<int> stack = new Stack<int>();
stack.Push(1);
stack.Push(2);
int last = stack.Pop();
The Queue and Stack classes provide efficient ways to work with ordered collections. Queues follow a "First-In-First-Out" (FIFO) policy and stacks follow a "Last-In-First-Out" (LIFO) policy. These are great for modeling real-world situations like a queue at a ticket booth or a stack of plates.
Use Cases:
When you need to implement a FIFO or LIFO policy
Modeling real-world situations
4. HashSet for Fast Lookup
HashSet<string> hashSet = new HashSet<string> { "A", "B", "C" };
bool containsA = hashSet.Contains("A");  // True
A HashSet is a collection that provides fast lookup for whether a specific element exists. It's like the Google of collections, just much faster!
Use Cases:
When you need to check whether a collection contains an element frequently
Removing duplicates from a collection
5. LINQ Queries
List<int> list = new List<int> { 1, 2, 3, 4, 5 };
IEnumerable<int> evenNumbers = list.Where(x => x % 2 == 0);
LINQ provides a powerful and declarative way to query collections. With just a single line of code, you can filter, sort, transform, and much more. It’s like having a personal assistant for your collections!
Use Cases:
When you need to perform complex operations on a collection
To filter or sort a collection
6. Observable Collections
ObservableCollection<string> collection = new ObservableCollection<string>();
collection.CollectionChanged += (s, e) => { /* Handle change */ };
collection.Add("A");
Observable collections allow you to easily react to changes in the collection. It’s like getting notifications whenever someone posts a new cat video!
Use Cases:
When you need to update the UI based on changes in a collection
To log changes to a collection
7. Concurrent Collections
ConcurrentDictionary<int, string> concurrentDictionary = new ConcurrentDictionary<int, string>();
The System.Collections.Concurrent namespace provides several collections that are safe to use from multiple threads. This saves you from having to deal with locks and other synchronization primitives. It's like a pre-packaged, hassle-free multi-threading solution!
Use Cases:
When you need to access a collection from multiple threads
To avoid manual synchronization
8. The IComparer<T> and IEqualityComparer<T> Interfaces
class MyComparer : IComparer<int>
{
   public int Compare(int x, int y)
   {
       // Reverse order
       return y.CompareTo(x);
   }
}


List<int> list = new List<int> { 1, 2, 3, 4, 5 };
list.Sort(new MyComparer());
The IComparer<T> and IEqualityComparer<T> interfaces allow you to customize how elements are compared and whether they're considered equal. It's like deciding your own rules for a game!
Use Cases:
When you need to sort a collection in a specific way
To compare elements based on a specific criterion
9. Grouping Elements with GroupBy
List<int> list = new List<int> { 1, 2, 3, 4, 5 };
var groups = list.GroupBy(x => x % 2 == 0 ? "Even" : "Odd");
The GroupBy method allows you to group elements based on a specific criterion. It's like organizing your sock drawer by color and size!
Use Cases:
When you need to group elements based on a specific criterion
To perform operations on each group separately
10. The Any and All Methods
List<int> list = new List<int> { 1, 2, 3, 4, 5 };
bool anyEven = list.Any(x => x % 2 == 0);  // True
bool allPositive = list.All(x => x > 0);  // True
The Any and All methods provide a declarative way to check whether any or all elements in a collection satisfy a condition. It's like quickly checking whether there's any chocolate left in the box or if all the apples in a basket are ripe!
Use Cases:
When you need to check whether any or all elements satisfy a condition
To avoid having to write loops manually
10 Delegates and Events Snippets
1. Multicast Delegates
Action<int> action1 = x => Console.WriteLine($"Action 1: {x}");
Action<int> action2 = x => Console.WriteLine($"Action 2: {x}");


Action<int> combined = action1 + action2;
combined(5);  // Executes both actions
You can combine multiple delegates into a single multicast delegate. It’s like inviting all your friends to the same party!
Use Cases:
When you want to notify multiple listeners
To simplify code that executes multiple callbacks
2. Weak Event Pattern
public class WeakEventHandler<TEventArgs>
{
   private readonly WeakReference _targetReference;
   private readonly MethodInfo _method;


   public WeakEventHandler(EventHandler<TEventArgs> eventHandler)
   {
       _targetReference = new WeakReference(eventHandler.Target);
       _method = eventHandler.Method;
   }


   public void Invoke(object sender, TEventArgs e)
   {
       if (_targetReference.IsAlive)
           _method.Invoke(_targetReference.Target, new object[] { sender, e });
   }
}
The weak event pattern allows listeners to be garbage collected even if the source of the event is still alive. It’s like leaving the party without anyone noticing!
Use Cases:
When you want to avoid memory leaks in long-lived objects
To ensure that short-lived listeners do not prolong the life of the listener
3. Generic Delegates
public delegate TResult MyFunc<T1, T2, TResult>(T1 arg1, T2 arg2);
You can define generic delegates that work with any type. It’s like a Swiss Army knife for delegate types!
Use Cases:
When you need a delegate that works with different types
To write more reusable and type-safe code
4. Events with Custom EventArgs
public class MyEventArgs : EventArgs
{
   public string Message { get; set; }
}


public class MyClass
{
   public event EventHandler<MyEventArgs> MyEvent;
   protected virtual void OnMyEvent(string message)
   {
       MyEvent?.Invoke(this, new MyEventArgs { Message = message });
   }
}
You can define custom EventArgs to provide more information about an event. It's like sending a detailed report instead of a brief notification!
Use Cases:
When you need to provide additional information with an event
To create more expressive and informative events
5. Covariance and Contravariance in Delegates
Func<object> objectFunc = () => new object();
Func<string> stringFunc = objectFunc;  // Covariance


Action<string> stringAction = str => Console.WriteLine(str);
Action<object> objectAction = stringAction;  // Contravariance
Covariance and contravariance allow you to assign delegates in a way that preserves type compatibility. It’s like fitting square pegs into round holes, but in a type-safe manner!
Use Cases:
When you need to assign delegates to each other
To create more flexible and reusable delegate code
6. Anonymous Delegates
Func<int, int> square = delegate(int x) { return x * x; };
You can define delegates anonymously without having to declare a separate method. It’s like creating a pop-up store instead of a permanent shop!
Use Cases:
When you want to define a delegate inline
To keep delegate code close to where it’s used
7. Asynchronous Delegates
Func<int, int> slowFunc = x => { Thread.Sleep(1000); return x * x; };
IAsyncResult asyncResult = slowFunc.BeginInvoke(5, null, null);
// Do other work...
int result = slowFunc.EndInvoke(asyncResult);  // Waits for the result
You can execute delegates asynchronously with the BeginInvoke and EndInvoke methods. It's like sending a letter instead of making a phone call!
Use Cases:
When you need to execute long-running operations
To keep your UI responsive
8. Delegates as Instance Variables
class MyClass
{
   private Func<int, int> _myFunc = x => x * x;
   public void SetFunc(Func<int, int> func)
   {
       _myFunc = func;
   }
   public int Compute(int x)
   {
       return _myFunc(x);
   }
}
You can use delegates as instance variables to create highly customizable classes. It’s like changing the engine of a car while it’s running!
Use Cases:
When you need to customize the behavior of a class
To create flexible and extensible classes
9. The EventHandler<T> Delegate
public class MyClass
{
   public event EventHandler<string> MyEvent;
   protected virtual void OnMyEvent(string value)
   {
       MyEvent?.Invoke(this, value);
   }
}
The EventHandler<T> delegate provides a standard way to declare events. It's like a universally accepted handshake for events!
Use Cases:
When you need to declare an event
To ensure that your events are compatible with .NET conventions
10. Delegates for Expressions
Func<int, bool> isEven = x => x % 2 == 0;
List<int> numbers = Enumerable.Range(0, 10).ToList();
List<int> evenNumbers = numbers.Where(isEven).ToList();
Delegates are a great way to encapsulate expressions and pass them around. It’s like carrying a portable math equation in your pocket!
Use Cases:
When you need to pass around complex expressions
To make your code more expressive and flexible
10 Exception Handling Snippets
1. Try-Catch-Finally Statement
try
{
   // Potentially dangerous code here...
}
catch (SpecificException ex)
{
   // Handle a specific exception
}
catch
{
   // Handle any other exceptions
}
finally
{
   // Cleanup code that always executes
}
The classic try-catch-finally statement. It’s like a safety net that catches any unexpected trapeze artist falls!
Use Cases:
When executing code that may throw exceptions
To ensure cleanup code always runs
2. Throwing New Exceptions
catch (Exception ex)
{
   throw new MyException("Something bad happened", ex);
}
Re-throwing exceptions with additional information. It’s like returning a defected product but with a complaint letter attached!
Use Cases:
When you need to add additional information to an exception
To create a detailed exception history
3. Filtering Exceptions
catch (Exception ex) when (ex.Message.Contains("specific"))
{
   // Handle the exception
}
Filtering exceptions based on conditions. It’s like a bouncer for exceptions that only lets certain ones in!
Use Cases:
When you only want to handle certain exceptions
To create more readable and efficient exception handling code
4. Inner Exceptions
catch (Exception ex)
{
   Console.WriteLine(ex.InnerException);
}
Accessing the inner exceptions of an exception. It’s like peeling an onion to reveal its layers!
Use Cases:
When you need to uncover the underlying cause of an exception
To display or log more detailed exception information
5. AggregateException
try
{
   // Parallel or async code that throws multiple exceptions...
}
catch (AggregateException ae)
{
   ae.Handle(ex =>
   {
       // Handle each exception
       return true;
   });
}
Handling multiple exceptions thrown from parallel or async code. It’s like catching a swarm of bees with one net!
Use Cases:
When executing parallel or async code that may throw multiple exceptions
To handle each exception individually
6. Non-Catching Exception Handler
try
{
   // Dangerous code...
}
catch (Exception ex) when (LogException(ex))
{
}


bool LogException(Exception ex)
{
   // Log the exception and return false
   return false;
}
Logging exceptions without catching them. It’s like a CCTV camera that observes everything but doesn’t intervene!
Use Cases:
When you need to log exceptions but allow them to propagate
To monitor exceptions in your code
7. The ExceptionDispatchInfo Class
ExceptionDispatchInfo capturedException;


try
{
   // Dangerous code...
}
catch (Exception ex)
{
   capturedException = ExceptionDispatchInfo.Capture(ex);
}
// Later...
capturedException?.Throw();
Capturing and re-throwing exceptions while preserving the original stack trace. It’s like a time capsule for exceptions!
Use Cases:
When you need to throw exceptions across threads or async methods
To preserve the original stack trace of an exception
8. Custom Exceptions
public class MyException : Exception
{
   public MyException(string message) : base(message) { }
   public MyException(string message, Exception inner) : base(message, inner) { }
}
Creating custom exceptions for specific error scenarios. It’s like creating a wanted poster for a specific outlaw!
Use Cases:
When you need to represent specific error conditions in your code
To create more expressive and detailed exceptions
9. Checking an Exception’s Source
catch (Exception ex)
{
   if (ex.Source == "MyAssembly")
   {
       // Handle the exception
   }
}
Checking the source of an exception. It’s like tracing the origin of a phone call!
Use Cases:
When you need to handle exceptions from specific sources
To differentiate between exceptions from different assemblies or classes
10. The OnException Method in MVC
public class MyController : Controller
{
   protected override void OnException(ExceptionContext filterContext)
   {
       // Handle exceptions for the entire controller
   }
}
Handling exceptions for an entire MVC controller. It’s like a safety inspector for a building!
Use Cases:
When you want to handle all exceptions in a MVC controller
To centralize exception handling code in a MVC application
Mastering C# is a journey, not a sprint. So, take your time. Come back, revisit, practice. And remember, I’m here to help you navigate this complex maze. So, keep this page handy and drop by anytime for a refresher or to dive deeper into the world of C#.
https://maherz.medium.com/top-60-c-code-snippets-for-every-developer-cf651018c222

https://maherz.medium.com/c-12-the-features-that-are-turning-heads-257d01a61b3f
Article: C# 12: The Features That Are Turning Heads
CSharp Features, .NET, Microsoft
C# 12, introduced in the latest Visual Studio previews and .NET 8 preview SDK it’s making waves in the developer community.
C# keeps getting better with each version, and this one’s no exception.
It’s packed with new tools that make our coding life easier and more fun. If you’re a C# fan like me, you’re going to love exploring all the new stuff.
Let’s jump in and see what it’s all about!
Primary Constructors
Primary constructors are a game-changer for object initialization. Instead of declaring properties and then a constructor separately, developers can now do both simultaneously.
public class Person(string name, int age)
{
   public string Name { get; } = name;
   public int Age { get; } = age;
}
This feature shines especially for classes intended to be immutable. It reduces boilerplate code, making the codebase cleaner and more readable. For developers, this means faster coding with fewer errors.
Optional Parameters in Lambda Expressions
Lambda expressions have always been a powerful tool in C#. With the introduction of optional parameters, their versatility has been enhanced.
Func<int, int, int> add = (x, y = 5) => x + y;
Console.WriteLine(add(10));  // Outputs 15
This feature reduces the need for multiple overloads, leading to cleaner and more maintainable code. It’s especially useful when working with delegates or events, providing flexibility in function signatures.
Alias Any Type
The expanded capabilities of the using alias directive in C# 12 bring a new level of flexibility and clarity to the code. By allowing developers to create semantic aliases for more complex types, the code becomes more readable and maintainable.
Here’s an example:
// This would not compile in versions before C# 12
using Person = (string Name, int Age);
using Matrix = double[,];
In essence, the ability to alias any type in C# 12 is not just a syntactic sugar but a feature that can significantly improve code quality, readability, and maintainability.
Inline Arrays
Inline arrays are a significant performance booster. They allow for the creation of fixed-size arrays within structs, providing performance characteristics similar to unsafe fixed-size buffers.
[System.Runtime.CompilerServices.InlineArray(10)]
public struct Buffer
{
   private int _element0;
   // ... other elements ...
}
While many developers might not declare their own inline arrays, they’ll benefit from them when used in runtime APIs.
This feature is a step forward in optimizing high-performance applications, especially in scenarios where memory management and speed are crucial.
Collection Expressions
Collection expressions simplify the creation of collections. The new syntax is concise, making the code cleaner.
// Create an array:
int[] a = [1, 2, 3, 4, 5];
// Using the spread operator:
int[] b = [..a, 6, 7, 8];
The spread operator, in particular, is a powerful addition, allowing developers to merge collections effortlessly.
This feature is a boon for developers working with data manipulation, making tasks like merging datasets or spreading data across functions more intuitive.
Default Lambda Parameters
The ability to define default values for lambda expression parameters brings them on par with regular methods.
// Define a lambda with a default parameter
Func<string, string, string> greet = (name, greeting = "Hello") => $"{greeting}, {name}!";


// Call the lambda without the second parameter
Console.WriteLine(greet("Alice"));  // Outputs: Hello, Alice!


// Call the lambda with both parameters
Console.WriteLine(greet("Bob", "Hi"));  // Outputs: Hi, Bob!
This feature streamlines the use of lambdas, especially in scenarios where certain parameters often have common default values. It’s a step towards making lambdas more flexible and reducing the need for multiple lambda variants.
Interceptors (Experimental)
Interceptors, though still experimental, show promise. They allow methods to substitute calls at compile time, providing a mechanism to modify existing code, especially in source generators.
While the full potential of this feature is yet to be realized, it opens doors for innovative compile-time code manipulations.
Potential Future Applications
Code Optimization: Interceptors can be used to replace method calls with more optimized versions at compile time, especially in scenarios where performance is crucial. For instance, during the development phase, a method might have additional logging or debugging code. An interceptor could replace this method with a leaner, production-ready version during the build process for a release.
Feature Flagging: Interceptors can be instrumental in implementing feature flags. Depending on the build configuration or environment, certain features or methods can be toggled on or off by redirecting method calls to alternative implementations.
Mocking and Testing: In unit testing, it’s common to mock certain methods to isolate the code being tested. Interceptors can provide a more integrated way to substitute real method calls with mock implementations at compile time.
Aspect-Oriented Programming (AOP): AOP is a programming paradigm that focuses on separating cross-cutting concerns from the main business logic. Interceptors can be used to inject behaviors (like logging, caching, or security checks) into methods without altering their actual implementation.
Source Generators: With the introduction of source generators in C#, which allow code to be generated at compile time, interceptors can play a pivotal role in modifying or enhancing the generated code. For instance, a source generator might create a basic implementation of a method, and an interceptor could then replace or augment that implementation based on certain criteria.
C# 12 is like a breath of fresh air for all of us who love coding.
It’s packed with cool new tools that make our work smoother and faster.
Honestly, it’s hard not to get excited about all these upgrades. For us coders, diving into these new features means our code gets neater and runs even better.
Thank you for reading!
Additionally
Speaking of C# and its incredible capabilities, I’d like to share a little secret with you.
When it comes to hosting my C# APIs, I rely on Time4VPS. Their service is top-notch, and I’ve had a seamless experience with them.
If you’re looking for a reliable hosting service for your projects, I highly recommend giving them a try. And hey, since I use them too, you know they’ve got the stamp of approval from a fellow developer!
https://maherz.medium.com/c-12-the-features-that-are-turning-heads-257d01a61b3f

Article: 10 Mind-Blowing C# Hacks
https://maherz.medium.com/10-mind-blowing-c-hacks-95fa629cfcef

Hey there! As a passionate C# developer myself, I’ve always been on the lookout for ways to level up my coding skills. I’m excited to share with you some mind-blowing hacks and insights that have helped me become a better programmer.
So, grab a cup of coffee, and join me!
1. Using Caller Information Attributes for Better Debugging and Logging
Caller information attributes allow you to obtain information about the caller of a method, which can be useful for debugging and logging purposes.
public void Log(string message, [CallerMemberName] string memberName = "", [CallerFilePath] string filePath = "", [CallerLineNumber] int lineNumber = 0)
{
   Console.WriteLine($"[{memberName}({lineNumber}) in {filePath}]: {message}");
}
In the example above, the ‘Log()’ method uses caller information attributes to automatically include the caller’s member name, file path, and line number in the log message. This makes it easier to trace log messages back to their source without having to manually include this information.
I hope I caught your attention. Before we continue, here’s one interesting fact about C# .NET you might not have known about.
The C# compiler (Roslyn) and runtime (CoreCLR) are open-source projects, allowing developers to contribute and influence the language’s direction. This open-source approach has led to increased community involvement and a faster pace of innovation for the language.
GitHub - dotnet/core: Home repository for .NET Core
You can't perform that action at this time. You signed in with another tab or window. You signed out in another tab or…
github.com
Alright, let’s continue with the hacks!
2. Memory-efficient Collections with Span<T>
Span<T> is a memory-efficient collection introduced in C# 7.2 that allows you to work with contiguous blocks of memory without creating new arrays or causing unnecessary heap allocations. It can be used to create “slices” of existing arrays or other memory segments without copying data.
public static void ProcessLargeArray(byte[] largeArray)
{
   const int chunkSize = 1024;
   for (int i = 0; i < largeArray.Length; i += chunkSize)
   {
       int length = Math.Min(chunkSize, largeArray.Length - i);
       Span<byte> chunk = largeArray.AsSpan(i, length);
       ProcessChunk(chunk);
   }
}


public static void ProcessChunk(Span<byte> chunk)
{
   // Process the chunk of data without creating a new array
   for (int i = 0; i < chunk.Length; i++)
   {
       chunk[i] *= 2;
   }
}
How it works and why it’s useful:
In the example above, the ProcessLargeArray method processes a large byte array by dividing it into smaller chunks. Instead of creating new arrays for each chunk, which would lead to increased memory usage and garbage collection overhead, the method uses Span<byte> to create a "view" into the original array for each chunk.
The AsSpan extension method is used to create a Span<byte> from the original array, starting at the current index (i) and having the desired length (length). The resulting Span<byte> can be used just like an array, but it doesn't cause any additional memory allocations.
The ProcessChunk method demonstrates how you can work with a Span<byte> to manipulate the data it points to. In this case, it doubles the value of each byte in the chunk.
Using Span<T> can help you write more memory-efficient and performant code by reducing the number of heap allocations and unnecessary data copying, especially when working with large data sets or in performance-critical scenarios.
3. Using Discards to Ignore Unneeded Values
Discards are used to ignore values that are not needed in a particular context, making the code more concise and easier to understand.
(int min, _) = GetMinMax(numbers);
Console.WriteLine($"Minimum: {min}");
In the example above, the ‘_’ discard is used to ignore the ‘max’ value returned by the ‘GetMinMax()’ method. This makes it clear that the maximum value is not needed or used in this context.
Discards in out parameters
if (int.TryParse("123", out _))
{
   Console.WriteLine("The input is a valid integer.");
}
Discards can be used with ‘out’ parameters when you don’t need the actual value, making the code more concise and easier to read.
Discards in pattern matching
if (shape is Circle _)
{
   Console.WriteLine("The shape is a circle.");
}
Discards can be used in pattern matching when you only need to test the type and don’t need the actual value, simplifying the code.
4. Pipelines for High-Performance Stream Processing
Pipelines is a high-performance stream processing library in .NET designed for efficient handling of large data streams with low-latency requirements. The System.IO.Pipelines namespace provides abstractions for reading and writing data in a streaming fashion, while minimizing memory allocations and copying.
public static async Task ProcessStreamAsync(Stream stream)
{
   var pipe = new Pipe();
   var writeTask = FillPipeAsync(stream, pipe.Writer);
   var readTask = ReadPipeAsync(pipe.Reader);


   await Task.WhenAll(writeTask, readTask);
}


private static async Task FillPipeAsync(Stream stream, PipeWriter writer)
{
   const int minimumBufferSize = 512;


   while (true)
   {
       var memory = writer.GetMemory(minimumBufferSize);
       int bytesRead = await stream.ReadAsync(memory);


       if (bytesRead == 0)
       {
           break;
       }


       writer.Advance(bytesRead);


       var result = await writer.FlushAsync();


       if (result.IsCompleted)
       {
           break;
       }
   }


   writer.Complete();
}


private static async Task ReadPipeAsync(PipeReader reader)
{
   while (true)
   {
       var result = await reader.ReadAsync();
       var buffer = result.Buffer;


       foreach (var segment in buffer)
       {
           // Process the data in the segment
           Console.WriteLine($"Read {segment.Length} bytes");
       }


       reader.AdvanceTo(buffer.End);


       if (result.IsCompleted)
       {
           break;
       }
   }


   reader.Complete();
}


public static async Task UsePipelinesAsync()
{
   using var stream = new MemoryStream(Encoding.UTF8.GetBytes("Hello, Pipelines!"));
   await ProcessStreamAsync(stream);
}
How it works and why it’s useful:
In the example above, the ProcessStreamAsync method demonstrates how to use the Pipe class to process data from a Stream object. The method creates a new Pipe instance and starts two tasks: one for writing data to the pipe (FillPipeAsync) and one for reading data from the pipe (ReadPipeAsync). The Task.WhenAll method is used to await the completion of both tasks.
The FillPipeAsync method reads data from the input Stream and writes it to the PipeWriter. It does this in a loop, getting memory from the PipeWriter, reading data from the stream into the memory, and advancing the writer. The PipeWriter.FlushAsync method is called to signal that data is available for reading, and the loop continues until the stream is exhausted or the pipe is completed.
The ReadPipeAsync method reads data from the PipeReader and processes it in a loop. It awaits the PipeReader.ReadAsync method, which returns a ReadResult containing a ReadOnlySequence<byte> buffer. The buffer is processed in segments, and the PipeReader.AdvanceTo method is called to signal that the data has been consumed. The loop continues until the pipe is completed.
Using Pipelines for stream processing can provide significant performance benefits, especially in scenarios where low-latency processing and minimal memory allocations are required. The library’s abstractions and design make it easier to handle complex streaming scenarios, such as network communication or file I/O, with efficient resource management and optimal performance.
5. Conditional Weak Table for Metadata Association
Conditional Weak Table allows you to associate metadata with objects without modifying their original structure. It uses weak references, so it doesn’t prevent the garbage collector from collecting the objects when they’re no longer in use.
public class Person
{
   public string Name { get; set; }
}


public static class PersonMetadata
{
   private static readonly ConditionalWeakTable<Person, Dictionary<string, object>> MetadataTable = new();


   public static void SetMetadata(Person person, string key, object value)
   {
       var metadata = MetadataTable.GetOrCreateValue(person);
       metadata[key] = value;
   }


   public static object GetMetadata(Person person, string key)
   {
       if (MetadataTable.TryGetValue(person, out var metadata) && metadata.TryGetValue(key, out var value))
       {
           return value;
       }


       return null;
   }
}
How it works and why it’s useful:
In the example above, the Person class has no built-in support for metadata. The PersonMetadata static class uses a ConditionalWeakTable to associate metadata with Person instances without modifying the original class. This approach is useful when you want to store additional information with objects without altering their structure or creating strong references that could prevent garbage collection.
The SetMetadata and GetMetadata methods in the PersonMetadata class allow you to store and retrieve metadata for Person objects. The metadata is stored in a dictionary, which is then associated with the object using the ConditionalWeakTable. The table holds weak references to the objects, so when the object is no longer in use and eligible for garbage collection, the associated metadata will also be collected.
6. Advanced Reflection Techniques with Expression Trees
Expression trees are a powerful feature in C# that enables you to represent code as data structures, which can be manipulated and compiled at runtime. This can be useful for advanced reflection scenarios, such as generating dynamic methods or optimizing performance-critical code paths.
public static Func<T, object> GeneratePropertyGetter<T>(string propertyName)
{
   var parameter = Expression.Parameter(typeof(T), "obj");
   var property = Expression.Property(parameter, propertyName);
   var conversion = Expression.Convert(property, typeof(object));
   var lambda = Expression.Lambda<Func<T, object>>(conversion, parameter);


   return lambda.Compile();
}


public class Person
{
   public string Name { get; set; }
   public int Age { get; set; }
}


public static void UseExpressionTree()
{
   var person = new Person { Name = "John Doe", Age = 30 };


   var nameGetter = GeneratePropertyGetter<Person>("Name");
   var ageGetter = GeneratePropertyGetter<Person>("Age");


   Console.WriteLine($"Name: {nameGetter(person)}, Age: {ageGetter(person)}");
}
How it works and why it’s useful:
In the example above, the GeneratePropertyGetter<T> method demonstrates how to use expression trees to generate a property getter for a given class and property name. The method takes a type parameter T and a string representing the property name, then constructs an expression tree that represents accessing the property on an instance of T and returning its value.
The expression tree is constructed using the Expression class methods, such as Expression.Parameter, Expression.Property, and Expression.Lambda. Once the expression tree is complete, the Compile method is called to generate a Func<T, object> delegate that can be used to invoke the property getter at runtime.
In the UseExpressionTree method, the GeneratePropertyGetter method is used to create property getters for the Name and Age properties of the Person class. These property getters are then used to retrieve the property values from a Person object.
Using expression trees for advanced reflection techniques can provide several benefits, such as improved performance, flexibility, and the ability to generate and compile code at runtime. However, keep in mind that expression trees can be more complex and harder to debug than traditional reflection techniques, so use them judiciously and only when necessary.
7. Simplifying Multithreading with Channels
Channels are a synchronization primitive introduced in .NET Core 3.0 that simplify multithreading by providing a way for threads to communicate and exchange data in a thread-safe manner. They can be used to implement the producer-consumer pattern, allowing you to decouple the producing and consuming of data.
public static async Task ProcessDataAsync()
{
   var channel = Channel.CreateUnbounded<int>();


   var producer = Task.Run(async () =>
   {
       for (int i = 1; i <= 10; i++)
       {
           Console.WriteLine($"Produced: {i}");
           await channel.Writer.WriteAsync(i);
           await Task.Delay(1000);
       }
       channel.Writer.Complete();
   });


   var consumer = Task.Run(async () =>
   {
       await foreach (var item in channel.Reader.ReadAllAsync())
       {
           Console.WriteLine($"Consumed: {item}");
       }
   });


   await Task.WhenAll(producer, consumer);
}
How it works and why it’s useful:
In the example above, the ProcessDataAsync method demonstrates a simple producer-consumer scenario using a channel. The channel variable is an unbounded channel, meaning it can store an unlimited number of items.
The producer task generates data (integers from 1 to 10) and writes it to the channel using the WriteAsync method. The consumer task reads the data from the channel using the ReadAllAsync method and processes it. In this case, it just prints the consumed data to the console.
The producer and consumer tasks run concurrently, allowing the consumer to process data as soon as it becomes available. The Channel class ensures that the data exchange is thread-safe, making it easier to write multithreaded code without worrying about locks or other synchronization mechanisms.
Channels can be used in various scenarios, such as data processing pipelines, parallelizing workloads, or implementing communication between components in a multithreaded application. They provide an easy-to-use and efficient way to manage concurrency and data exchange between threads.
8. Dynamic Code Compilation with Roslyn
Dynamic code compilation with Roslyn allows you to compile and execute C# code at runtime. This can be useful for scripting, plugins, or situations where the code needs to be generated or modified on-the-fly.
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CSharp;
using System.Reflection;


public static async Task ExecuteDynamicCodeAsync(string code)
{
   string sourceCode = $@"
using System;


namespace DynamicCode
{{
   public class Runner
   {{
       public static void Run()
       {{
           {code}
       }}
   }}
}}";


   var syntaxTree = CSharpSyntaxTree.ParseText(sourceCode);
   var references = new List<MetadataReference>
   {
       MetadataReference.CreateFromFile(typeof(object).GetTypeInfo().Assembly.Location),
   };


   var compilation = CSharpCompilation.Create("DynamicCode")
       .WithOptions(new CSharpCompilationOptions(OutputKind.DynamicallyLinkedLibrary))
       .AddReferences(references)
       .AddSyntaxTrees(syntaxTree);


   using var ms = new MemoryStream();
   var result = compilation.Emit(ms);


   if (!result.Success)
   {
       Console.WriteLine("Compilation failed");
       return;
   }


   ms.Seek(0, SeekOrigin.Begin);
   var assembly = Assembly.Load(ms.ToArray());
   var type = assembly.GetType("DynamicCode.Runner");
   var method = type.GetMethod("Run", BindingFlags.Static | BindingFlags.Public);
   method.Invoke(null, null);
}


await ExecuteDynamicCodeAsync("Console.WriteLine(\"Hello from dynamic code!\");");
How it works and why it’s useful:
In the example above, the ExecuteDynamicCodeAsync method demonstrates how to compile and execute a piece of C# code at runtime using the Roslyn compiler. The input code parameter is embedded into a simple class definition that is placed in the sourceCode variable.
The Roslyn CSharpSyntaxTree.ParseText method is used to parse the source code into a syntax tree, which is then added to a new CSharpCompilation object. The necessary assembly references are also added to the compilation object, including the reference to the System namespace.
The Emit method compiles the code into a dynamically linked library (DLL) and writes the output to a MemoryStream. If the compilation is successful, the resulting assembly is loaded into the current application domain using Assembly.Load. The Runner class and its Run method are then obtained via reflection, and the method is invoked, executing the dynamic code.
This technique allows you to build flexible and extensible applications that can dynamically compile and execute C# code at runtime. However, be cautious with the security implications, as executing arbitrary code can introduce security risks if not handled properly.
9. Converting Anonymous Types to Dynamic for Flexible Data Manipulation
Converting anonymous types to dynamic objects can provide more flexibility when manipulating data. Anonymous types are read-only and strongly-typed, which can be limiting when you want to modify or extend the data. By converting an anonymous type to a dynamic ExpandoObject, you gain the ability to add, remove, or modify properties at runtime.
public static dynamic ToDynamic(object anonymousObject)
{
   var dynamicObject = new ExpandoObject() as IDictionary<string, object>;
   var properties = TypeDescriptor.GetProperties(anonymousObject);


   foreach (PropertyDescriptor property in properties)
   {
       dynamicObject.Add(property.Name, property.GetValue(anonymousObject));
   }


   return dynamicObject;
}


public static void ManipulateData()
{
   var anonymousData = new { Name = "John", Age = 30 };
   dynamic dynamicData = ToDynamic(anonymousData);


   Console.WriteLine($"Name: {dynamicData.Name}, Age: {dynamicData.Age}");


   dynamicData.Age = 35;
   dynamicData.City = "New York";


   Console.WriteLine($"Name: {dynamicData.Name}, Age: {dynamicData.Age}, City: {dynamicData.City}");
}
How it works and why it’s useful:
In the example above, the ToDynamic method takes an anonymous object as input and converts it into a dynamic ExpandoObject. It does this by iterating through the properties of the anonymous object using TypeDescriptor.GetProperties and adding them to the ExpandoObject using an IDictionary<string, object> interface.
The ManipulateData method demonstrates how to use the ToDynamic method to convert an anonymous object into a dynamic object. The anonymousData variable holds an anonymous object with Name and Age properties. After converting it to a dynamic object with ToDynamic, you can access and modify its properties directly, as well as add new properties like City.
Converting anonymous types to dynamic objects can be useful when you need more flexibility with your data structures, especially when dealing with dynamically generated data or when the schema is not known at compile time. However, keep in mind that using dynamic objects can come at the cost of losing compile-time type checking and potential performance overhead.
10. Creating a Simple Object Pool for Reusable Resources
An object pool is a design pattern that helps to reuse objects that are expensive to create, such as database connections or large memory buffers. By creating a pool of pre-allocated objects and reusing them when needed, you can improve the performance of your application and reduce the overhead associated with creating and destroying objects.
public class ObjectPool<T> where T : new()
{
   private readonly ConcurrentBag<T> _objects;
   private readonly Func<T> _objectGenerator;


   public ObjectPool(Func<T> objectGenerator = null)
   {
       _objectGenerator = objectGenerator ?? (() => new T());
       _objects = new ConcurrentBag<T>();
   }


   public T GetObject()
   {
       if (_objects.TryTake(out T item))
       {
           return item;
       }


       return _objectGenerator();
   }


   public void ReturnObject(T item)
   {
       _objects.Add(item);
   }
}


public class ExpensiveResource
{
   public int Value { get; set; }
}


public static void UseObjectPool()
{
   var pool = new ObjectPool<ExpensiveResource>();


   var resource = pool.GetObject();
   resource.Value = 42;


   Console.WriteLine($"Resource value: {resource.Value}");


   pool.ReturnObject(resource);
}
How it works and why it’s useful:
In the example above, the ObjectPool<T> class is a generic implementation of an object pool. It uses a ConcurrentBag<T> to store the pooled objects and a Func<T> delegate to create new objects when needed. The GetObject method retrieves an object from the pool if available or creates a new one if the pool is empty. The ReturnObject method returns an object to the pool when it's no longer needed.
The ExpensiveResource class represents a hypothetical resource that is expensive to create. In the UseObjectPool method, an instance of ObjectPool<ExpensiveResource> is created, and an ExpensiveResource object is retrieved from the pool using the GetObject method. After manipulating the object's properties, the ReturnObject method is called to return the object to the pool for future reuse.
Using an object pool can improve your application’s performance and reduce memory usage by minimizing the number of object allocations and deallocations. This is particularly useful in high-performance or resource-constrained environments where object creation and garbage collection can be significant bottlenecks. However, keep in mind that object pooling adds complexity to your code and may not be suitable for all scenarios.
🔗 Connect with me!
🚀 Give me a clap and follow for more articles!
🌟 Facebook — Stay updated with my latest content!

https://maherz.medium.com/10-mind-blowing-c-hacks-95fa629cfcef


A

Polymorphism — a concept that may seem daunting to many new programmers. What exactly is polymorphism? If you’re familiar with Greek, you might know that “poly” means many and “morph” means forms. So, in the simplest terms, polymorphism allows an object to take on many forms.
It’s funny how our journey through life often circles back to the beginning, isn’t it? The same can be said for our understanding and mastery of any subject. The more we learn, the more we realize the significance of the fundamental principles that underpin everything else. Today, I find myself reflecting on the basics of C# programming, specifically on one of the most fundamental yet powerful concepts in object-oriented programming: polymorphism.
Article: Back to Basics: C# Polymorphism
https://maherz.medium.com/back-to-basics-c-polymorphism-242a1e5d7288
Basics of Object-Oriented Programming
In the world of programming, especially in C#, polymorphism is a fundamental concept of Object-Oriented Programming (OOP). Let’s understand this step-by-step.
Classes and Objects in C#
We all know real-world objects like cars, dogs, or people, right? In OOP, these real-world objects are translated into ‘classes’ which define the properties (or ‘attributes’) and behaviors (or ‘methods’) that an object can have. The real instances of these classes are known as ‘objects’.
In C#, a class is a blueprint for an object, and an object is an instance of a class. Let’s break this down with some examples.
Defining a Class in C#
Here’s an example of a simple class named Car:
public class Car
{
   // Properties of the Car class
   public string Make { get; set; }
   public string Model { get; set; }
   public string Color { get; set; }


   // Method of the Car class
   public void Drive()
   {
       Console.WriteLine("The car is driving.");
   }
}
In this example, Car is a class that has three properties (Make, Model, and Color) and one method (Drive).
Creating an Object in C#
An object is an instance of a class. To create an object of the Car class, you can do the following:
Car myCar = new Car();
In this example, myCar is an object of the Car class.
Inheritance in C#
Inheritance is a fundamental principle in object-oriented programming. It allows you to create new classes that reuse, extend, and modify behavior defined in other classes. The class whose members are inherited is called the base class, and the class that inherits those members is called the derived class.
Base Class in C#
Let’s start by defining a base class Animal. This class has properties like Name and Age, and a method Eat:
public class Animal
{
   public string Name { get; set; }
   public int Age { get; set; }


   public void Eat()
   {
       Console.WriteLine($"{Name} is eating.");
   }
}
Derived Class in C#
Now, we can create a derived class Dog that inherits from the Animal class and has an additional method Bark:
public class Dog : Animal
{
   public void Bark()
   {
       Console.WriteLine($"{Name} is barking.");
   }
}
The : operator is used to inherit the Dog class from the Animal class.
Using Inheritance in C#
You can now create an object of the Dog class and access both the methods from the base Animal class and the derived Dog class:
Dog myDog = new Dog();
myDog.Name = "Buddy";
myDog.Age = 5;
myDog.Eat();
myDog.Bark();
This will output:
Buddy is eating.
Buddy is barking.
In this example, myDog is an object of the Dog class. Even though we didn't define the Eat method or the Name property in the Dog class, we can use them because the Dog class inherits from the Animal class.
Polymorphism in C#
In C#, Polymorphism is divided into two types: static and dynamic. Both of these have their unique characteristics and uses.
Static Polymorphism
Method Overloading in C#
Static polymorphism, also known as compile-time polymorphism, involves method overloading. This is where multiple methods have the same name but different parameters.
Method overloading involves creating multiple methods with the same name but different parameters:
public class Calculator
{
   public int Add(int a, int b)
   {
       return a + b;
   }


   public int Add(int a, int b, int c)
   {
       return a + b + c;
   }
}
In this example, the Calculator class has two methods named Add. One adds two integers, and the other adds three integers.
Dynamic Polymorphism
Method Overriding in C#
Dynamic polymorphism, or run-time polymorphism, involves method overriding. This is where a method in a derived class has the same name and parameters as a method in its base class.
Method overriding involves a base class method being overridden in a derived class:
public class Animal
{
   public virtual void MakeSound()
   {
       Console.WriteLine("The animal makes a sound");
   }
}


public class Dog : Animal
{
   public override void MakeSound()
   {
       Console.WriteLine("The dog barks");
   }
}
In this example, the Animal class has a method MakeSound that is marked as virtual, which means it can be overridden in a derived class. The Dog class is derived from Animal and overrides the MakeSound method.
To see the polymorphism in action, you can do:
Animal myAnimal = new Animal();
Animal myDog = new Dog();
myAnimal.MakeSound(); // Outputs: "The animal makes a sound"
myDog.MakeSound();    // Outputs: "The dog barks"
In this example, myAnimal and myDog are both objects of type Animal. However, myDog is actually an instance of the Dog class. This is why it uses the MakeSound method defined in Dog rather than the one in Animal.
Benefits of Polymorphism in C#
Polymorphism is an integral part of OOP in C# for many reasons. It increases code reusability, enhances program structure, and boosts code readability and maintainability.
Common Mistakes with Polymorphism in C#
Like any programming concept, it’s easy to make mistakes with polymorphism if you’re not careful. From forgetting to declare virtual methods to improperly using base classes, the pitfalls are endless. But don’t worry, with practice comes perfection.
1. Don’t override a method without the virtual keyword in the base class. If a method in the base class is not marked as virtual, attempting to override it in a derived class will result in a compile-time error.
public class Animal
{
   public void MakeSound()
   {
       Console.WriteLine("The animal makes a sound");
   }
}


public class Dog : Animal
{
   public override void MakeSound()  // This will cause a compile-time error
   {
       Console.WriteLine("The dog barks");
   }
}
2. Remember to override keyword when intending to override a method. If you're trying to override a method but forget to include the override keyword, C# will treat it as a new method, and polymorphism won't work as intended.
public class Animal
{
   public virtual void MakeSound()
   {
       Console.WriteLine("The animal makes a sound");
   }
}


public class Dog : Animal
{
   public void MakeSound()  // Should be marked as 'override' to correctly override the base method
   {
       Console.WriteLine("The dog barks");
   }
}
3. Don’t attempt to override a sealed method. If a method in the base class is marked as sealed, it cannot be overridden in a derived class. Trying to do so will result in a compile-time error.
public class Animal
{
   public virtual void MakeSound()
   {
       Console.WriteLine("The animal makes a sound");
   }
}


public sealed class Dog : Animal
{
   public override void MakeSound()  // This will cause a compile-time error as Dog class is sealed
   {
       Console.WriteLine("The dog barks");
   }
}
4. Remember to call the base class’ method in the derived class if needed. If you override a method and still want to include the functionality of the base class’ method, you should call it using base.MethodName(). If you forget to do this, the base method's functionality won't be included
public class Animal
{
   public virtual void Eat()
   {
       Console.WriteLine("The animal is eating");
   }
}


public class Dog : Animal
{
   public override void Eat()
   {
       // The base.Eat() is missing here, so "The animal is eating" won't be printed
       Console.WriteLine("The dog is eating a bone");
   }
}
Polymorphism is one of the core pillars of OOP and an essential skill in C#. Through understanding and applying this concept, you can write more efficient, clean, and flexible code.
FAQs about C# Polymorphism
What is the main difference between static and dynamic polymorphism? Static polymorphism is determined at compile-time, whereas dynamic polymorphism is determined at run-time.
How is polymorphism used in real-world programming? Polymorphism is used in scenarios like user interface design, database handling, or game development, to name a few.
What are the benefits of using polymorphism in C#? Polymorphism increases code reusability, enhances program structure, and boosts code readability and maintainability.
What are some common mistakes made with polymorphism? Common mistakes include forgetting to declare virtual methods and improperly using base classes.
Thank you for reading!

https://maherz.medium.com/back-to-basics-c-polymorphism-242a1e5d7288

Article: C# Back to Basics
https://code-maze.com/csharp-back-to-basics/
https://maherz.medium.com/back-to-basics-c-polymorphism-242a1e5d7288
https://www.c-sharpcorner.com/article/back-to-basics-how-and-why-learning-c-sharp-programming-language/
https://dailydotnettips.com/net-c-back-to-basics-series/


In
the world of software development, there’s a saying that goes, “Premature optimization is the root of all evil.” It’s a quote from the brilliant mind of Donald Knuth, and it’s something I’ve carried with me throughout my decade-long journey as a C# developer. But let’s be honest, while we shouldn’t let optimization take over our entire development process, we can’t completely ignore it either.
Now, after years of writing, debugging, and optimizing C# code, I want to share the top 10 performance optimization tips that have made a significant difference in my work. So let’s dive in!
This one took me quite a bit to write. FIrst, thank you for reading and I hope you will learn something new. I tried to write this to make it easier for beginners to understand, but as well for experienced developers to perhaps learn something new :)
Before we continue, I thought I’d share an interesting fact about C# you might not have heard about.
Did you know that C# and .NET framework were initially named differently? During its early development stages at Microsoft, C# was referred to as “Cool”, which stood for “C-like Object Oriented Language”. Likewise, the .NET framework was initially named “Next Generation Windows Services” (NGWS). The name changes occurred before their official release to the public.
Article: Top 10 Performance Optimization Tips for C# Developers
https://maherz.medium.com/top-10-performance-optimization-tips-for-c-developers-3b09d2385e54
1. Avoid Boxing and Unboxing
One of the key performance optimization tips for C# developers is to avoid unnecessary boxing and unboxing. Boxing and unboxing might seem like complex concepts, especially for beginners, but they’re actually quite simple to understand. Moreover, understanding these concepts is crucial to write efficient C# code.
What is Boxing and Unboxing?
Boxing is the process of converting a value type (int, char, etc.) to an object type or to any interface type implemented by this value type. When the common language runtime (CLR) boxes a value type, it wraps the value inside a System.Object instance and stores it on the heap. Here's an example:
int num = 123; 
object obj = num;  // Boxing
Unboxing, on the other hand, is the process of converting the object type back to the value type. This requires an explicit cast:
int num2 = (int)obj;  // Unboxing
Why Should We Avoid Boxing and Unboxing?
Boxing and unboxing operations take time because they involve system-level operations such as object creation and memory allocation. Boxing moves a value from stack to heap, which is slower. Unboxing involves type checking and copying a value from the heap to stack, which also slows down your code.
If your code has a lot of boxing and unboxing happening inside a loop, the performance hit could be significant.
How to Avoid Boxing and Unboxing?
The best way to avoid unnecessary boxing and unboxing is to minimize the use of the object data type. Instead, use generic collections like List<T> instead of ArrayList, which stores its elements as object.
Here’s an example:
List<int> numbers = new List<int>();
for(int i = 0; i < 10000; i++)
{
   numbers.Add(i); // No boxing
}
In contrast, using an ArrayList would cause boxing:
ArrayList numbers = new ArrayList();
for(int i = 0; i < 10000; i++)
{
   numbers.Add(i); // Boxing occurs here
}
In the first example, no boxing occurs because the List<int> is a collection of integers, so no conversion to object is needed. In the second example, boxing occurs because the ArrayList is a collection of object, so the integer i is boxed to an object before it is added to the ArrayList.
You can read more about boxing and unboxing in the official Microsoft Docs.
2. Use StringBuilder for String Concatenation
When dealing with multiple string concatenations, especially within loops, an important optimization tip for C# developers is to use the StringBuilder class instead of the + operator. Let's break down why this is important.
Understanding the Issue with String Concatenation
In C#, strings are immutable. This means that once a string is created, it cannot be changed. When we use the + operator to concatenate strings, the .NET runtime is actually creating a new string and disposing of the old one every time. This can lead to significant performance overhead, especially when dealing with large strings or performing numerous concatenations.
string result = "";
for(int i = 0; i < 10000; i++)
{
   result += i.ToString(); // Inefficient
}
In the code snippet above, each iteration of the loop creates a new string in memory. If the loop runs thousands of times, this can lead to a noticeable slowdown.
The StringBuilder Solution
To overcome the performance issues with string concatenation, .NET provides a StringBuilder class. The StringBuilder class allows you to manipulate strings without constantly creating and disposing of string instances.
StringBuilder sb = new StringBuilder();
for(int i = 0; i < 10000; i++)
{
   sb.Append(i.ToString()); // Efficient
}
string result = sb.ToString();
In this example, the StringBuilder efficiently handles the string concatenation inside the loop. When you're done appending, you can convert the StringBuilder back into a string using the ToString() method.
Why is StringBuilder More Efficient?
The StringBuilder class uses a mutable string buffer, meaning it reserves more memory than actually needed. When you append to a StringBuilder, it does not create a new string but instead adds to the existing buffer. If the buffer runs out of space, it automatically doubles its size, making room for more append operations. This results in fewer memory allocations and better performance.
You can read more about StringBuilder in the official Microsoft Docs.
3. Leverage C#’s Lazy Initialization
Lazy initialization is a programming technique that defers the creation of an object until the moment it’s needed. It can be a powerful tool for improving the performance of your C# applications, particularly when dealing with resources that are expensive to create or seldom used.
Understanding Lazy Initialization
Consider a scenario where you have an object that’s expensive to create, either in terms of memory, CPU usage, or I/O operations. If this object isn’t always used, or if its use is deferred until some condition is met, you might be wasting resources by creating it upfront. This is where lazy initialization comes in.
C# offers a built-in class called Lazy<T> that handles lazy initialization for you. Here's an example of how to use it:
Lazy<ExpensiveObject> lazyObject = new Lazy<ExpensiveObject>(() => new ExpensiveObject());
In the code above, ExpensiveObject will not be created when lazyObject is instantiated. Instead, ExpensiveObject will only be created the first time you access the Value property of lazyObject:
ExpensiveObject myObject = lazyObject.Value; // ExpensiveObject is created here
Why is Lazy Initialization Useful?
The key benefit of lazy initialization is that it enables you to defer the cost of creating an object until it’s actually needed. If it turns out that the object is never used, then you’ve saved the cost of creating it entirely.
In addition, Lazy<T> in C# is thread-safe by default. This means that if multiple threads access the Value property at the same time, Lazy<T> will ensure that only a single instance of ExpensiveObject is created.
However, be aware that lazy initialization is not always the best solution. If the object is likely to be used immediately after it’s declared, or if it’s used frequently throughout the lifetime of your application, then the overhead of lazy initialization may not be worth the benefits.
You can learn more about Lazy<T> and lazy initialization in the official Microsoft Docs.
4. Optimize Loops
One common area where performance optimization is essential is when dealing with loops. Loops are used in almost every piece of software, and they can easily become a bottleneck if not handled efficiently. Below are some strategies to optimize loops in C#.
Avoid Redundant Calculations
One common mistake is to perform calculations or method calls inside the loop that could be done once outside the loop. Here’s an example:
for (int i = 0; i < myList.Count; i++)
{
   // loop body
}
In this example, myList.Count is calculated on each iteration, which is unnecessary. You can optimize this by calculating the count once before the loop starts:
int count = myList.Count;
for (int i = 0; i < count; i++)
{
   // loop body
}
Use for Instead of foreach Where Applicable
foreach loops are very convenient, but they come with some overhead. If performance is critical, consider using a for loop instead, especially when iterating over arrays or List<T>. Here's an example:
foreach (var item in myList)
{
   // loop body
}
This can be optimized by using a for loop:
int count = myList.Count;
for (int i = 0; i < count; i++)
{
   string item = myList[i];
   // loop body
}
Be Careful with Collection Modifications
Modifying a collection while iterating over it can lead to unexpected behavior and even runtime errors. If you need to add or remove items from a collection inside a loop, consider copying the collection or using a different data structure that supports these operations better.
Profile and Measure
Lastly, remember that optimization decisions should be driven by actual data. Use profiling tools to identify bottlenecks and measure the impact of your changes. What works best can depend on many factors, including the size and nature of your data, the specific operations performed inside the loop, and more.
For more information about optimizing loops in C#, check out this Microsoft Docs guide.
Also, you might want to check profiling tools: Microsoft Profiling Tools
5. Use Async/Await for I/O Operations
Input/Output (I/O) operations, such as reading from or writing to a database or a file, are typically time-consuming tasks. They often involve waiting for some external process or device, which can block your application’s threads and significantly affect your application’s responsiveness and scalability. C# provides the async and await keywords that make it easy to write code that can do other things while waiting for these long-running I/O operations to complete.
A basic example of using async/await is when reading text from a file:
using System.IO;


public async Task<string> ReadTextFromFileAsync(string filePath)
{
   using (StreamReader reader = new StreamReader(filePath))
   {
       string fileText = await reader.ReadToEndAsync();
       return fileText;
   }
}
In this example, the ReadToEndAsync method returns a Task<string>, which represents the ongoing read operation. The await keyword yields control back to the caller of ReadTextFromFileAsync until the read operation completes, at which point execution resumes and the text read from the file is returned.
Now let’s look at a more complex example that involves making an HTTP request:
using System.Net.Http;


public async Task<string> FetchWebPageAsync(string url)
{
   HttpClient client = new HttpClient();
   string pageContent = await client.GetStringAsync(url);
   return pageContent;
}
In this example, the GetStringAsync method initiates an HTTP GET request to the specified URL and then yields control back to the caller of FetchWebPageAsync. When the HTTP response is received, execution resumes, and the content of the web page is returned.
However, I/O operations are not the only type of operations that can benefit from async/await. CPU-bound operations, such as complex calculations or processing large amounts of data, can also be made asynchronous to improve the responsiveness of your application. For instance, if you're developing a desktop application with a graphical user interface, performing a long-running calculation on the UI thread would make the application unresponsive. By making the operation asynchronous, you can keep the UI responsive while the calculation is being performed.
Here’s a complex example involving both CPU-bound and I/O-bound operations:
public async Task ProcessDataAsync(string filePath, string url)
{
   // I/O-bound operation: Read text from a file
   string fileText = await ReadTextFromFileAsync(filePath);


   // CPU-bound operation: Process the text
   string processedText = await Task.Run(() => ProcessText(fileText));


   // I/O-bound operation: Fetch a web page
   string pageContent = await FetchWebPageAsync(url);


   // CPU-bound operation: Compare the processed text with the web page content
   bool areEqual = await Task.Run(() => CompareTexts(processedText, pageContent));


   // Output the result
   Console.WriteLine($"The texts are {(areEqual ? "equal" : "not equal")}.");
}
This example demonstrates how you can use async/await to write code that performs both I/O-bound and CPU-bound operations without blocking the calling thread. Note that the Task.Run method is used to offload the CPU-bound operations to a thread pool thread.
6. Avoid Exceptions in Normal Program Flow
In C#, exceptions are meant for exceptional circumstances — things that you don’t expect to happen during the normal execution of your program. They are not meant to be used for regular control flow, because they impose a significant performance cost. When an exception is thrown, the runtime has to collect a lot of diagnostic information (like the stack trace) which can be quite expensive.
The first principle is to always check for errors before they happen. For instance, if you’re trying to open a file, first check if it exists:
using System.IO;


public void ProcessFile(string filePath)
{
   if (File.Exists(filePath))
   {
       // Process the file
   }
   else
   {
       Console.WriteLine($"File {filePath} does not exist.");
   }
}
In this example, we avoid the FileNotFoundException that would occur if we attempted to open a non-existent file. Instead, we check if the file exists before trying to open it.
Another common scenario is when parsing user input. Instead of catching a FormatException when trying to parse an invalid number, you can use the TryParse method:
public void ProcessInput(string input)
{
   int number;
   if (int.TryParse(input, out number))
   {
       // Process the number
   }
   else
   {
       Console.WriteLine($"'{input}' is not a valid number.");
   }
}
Here, int.TryParse attempts to parse the string as an integer. If the parse is successful, it returns true and assigns the parsed value to number. If the parse is unsuccessful, it returns false, allowing us to handle the error without an exception.
Now, let’s consider a more complex scenario where we have a series of operations that could potentially throw exceptions:
public void ProcessData(string filePath, string url)
{
   try
   {
       string fileText = File.ReadAllText(filePath);
       string webContent = new WebClient().DownloadString(url);


       // Further processing...
   }
   catch (Exception ex)
   {
       Console.WriteLine($"An error occurred: {ex.Message}");
   }
}
In this example, we have two operations that could potentially throw exceptions — reading text from a file and downloading a string from a URL. Instead of letting these exceptions propagate and potentially crash our application, we catch them and handle them gracefully.
However, we could improve this code by checking for potential errors beforehand:
public void ProcessData(string filePath, string url)
{
   if (!File.Exists(filePath))
   {
       Console.WriteLine($"File {filePath} does not exist.");
       return;
   }


   if (!Uri.IsWellFormedUriString(url, UriKind.Absolute))
   {
       Console.WriteLine($"'{url}' is not a valid URL.");
       return;
   }


   string fileText = File.ReadAllText(filePath);
   string webContent = new WebClient().DownloadString(url);


   // Further processing...
}
In this improved version, we first check if the file exists and if the URL is valid before attempting the potentially exception-throwing operations. This way, we avoid exceptions in the normal flow of our program, improving its performance and readability.
Please note, the aim of the provided example was to illustrate the principle of avoiding exceptions in normal program flow, and to emphasize that it’s generally more efficient to test for a condition that might cause an exception, rather than handling the exception itself.
7. Prefer ValueTypes Over ReferenceTypes
In C#, we have two main types of data types — ValueTypes and ReferenceTypes. Understanding the difference between these two types and knowing when to use each is key to writing efficient C# code.
ValueType vs ReferenceType
ValueTypes (such as int, double, bool, struct) are types that hold their data within their own memory allocation. When you copy a ValueType, you're creating a completely separate copy of the data. On the other hand, ReferenceTypes (like class, interface, delegate) hold a reference to the data's location in memory. If you copy a ReferenceType, both copies point to the same memory location.
Why Prefer ValueTypes?
There are several reasons to prefer ValueTypes over ReferenceTypes:
Memory Efficiency: ValueTypes are stored on the stack, which is more memory-efficient than the heap (where ReferenceTypes are stored). This means they have less impact on the garbage collector and can lead to a performance improvement.
Immutability: ValueTypes are immutable by default. When you change the value of a ValueType, you’re creating a new copy. This can make your code safer and easier to understand.
Example 1: Simple Use of ValueType vs ReferenceType
// ValueType example
int number1 = 10;
int number2 = number1; // Creates a new copy of number1
number2 = 20; // Changes to number2 do not affect number1
Console.WriteLine(number1); // Outputs: 10


// ReferenceType example
StringBuilder builder1 = new StringBuilder("Hello");
StringBuilder builder2 = builder1; // Copies the reference to builder1
builder2.Append(", World!"); // Changes to builder2 also affect builder1
Console.WriteLine(builder1); // Outputs: Hello, World!
In the example above, changing number2 doesn't affect number1 because integers are ValueTypes. However, appending to builder2 also changes builder1 because StringBuilder is a ReferenceType.
Example 2: Complex Use of ValueType vs ReferenceType
Consider you’re creating a large array of objects. Using a ValueType can significantly reduce the memory footprint.
// ReferenceType array
ClassPoint[] classPoints = new ClassPoint[1000000]; // Each element is a separate object on the heap


// ValueType array
StructPoint[] structPoints = new StructPoint[1000000]; // All elements are in a single, contiguous block of memory
In the example above, the StructPoint array is much more memory-efficient than the ClassPoint array. Each element in the ClassPoint array is a separate object on the heap, while all the elements in the StructPoint array are in a single, contiguous block of memory.
Remember, while ValueTypes often have performance benefits, they aren’t always the right choice. If you need to share data between different parts of your code, a ReferenceType might be more appropriate. It’s essential to understand the difference and make an informed decision based on the specific requirements of your program.
8. Cache Results of Expensive Computations
In programming, there are often times when you need to perform expensive computations — operations that take a significant amount of time or resources to complete. When such computations are part of a routine that gets called frequently, the performance impact can be substantial. However, if the result of the computation doesn’t change between calls, you can improve performance by storing (or “caching”) the result and reusing it in subsequent calls. This technique is often referred to as “memoization”.
The Basics of Caching
Here’s a simple example of caching in action. Suppose you have a function that calculates the nth Fibonacci number, which is a costly operation when n is large:
public static long CalculateFibonacci(int n)
{
   if (n <= 1)
       return n;
   else
       return CalculateFibonacci(n - 1) + CalculateFibonacci(n - 2);
}
Now, let’s add caching to this function to improve its performance:
private static Dictionary<int, long> cache = new Dictionary<int, long>();


public static long CalculateFibonacci(int n)
{
   if (n <= 1)
       return n;


   if (cache.ContainsKey(n))
       return cache[n];


   cache[n] = CalculateFibonacci(n - 1) + CalculateFibonacci(n - 2);
   return cache[n];
}
In the modified version of the function, we first check whether the result for the given n is already in the cache. If it is, we return the cached result. Otherwise, we calculate the result, store it in the cache, and then return it.
A More Complex Example
Let’s consider a more complex example. Suppose you have a web application that needs to display data from a database query. Running the query every time the data is needed can be a significant performance drain. By caching the results, you can avoid the expensive database call most of the time.
Here’s an example of how you might implement this in an ASP.NET Core application using the IMemoryCache interface, which provides a fast, in-memory cache:
public class DataService
{
   private readonly IMemoryCache _cache;
   private readonly DatabaseContext _db;


   public DataService(IMemoryCache cache, DatabaseContext db)
   {
       _cache = cache;
       _db = db;
   }


   public async Task<List<Data>> GetDataAsync()
   {
       const string cacheKey = "DataCacheKey";
      
       if (!_cache.TryGetValue(cacheKey, out List<Data> data))
       {
           data = await _db.Data.ToListAsync();


           var cacheEntryOptions = new MemoryCacheEntryOptions()
               .SetAbsoluteExpiration(TimeSpan.FromHours(1));


           _cache.Set(cacheKey, data, cacheEntryOptions);
       }


       return data;
   }
}
In this example, the GetDataAsync method first checks whether the data is already in the cache. If it's not, the method retrieves the data from the database, stores it in the cache with an expiration time of one hour, and then returns it.
Caching can greatly improve the performance of your applications, but it’s not without its pitfalls. Cache invalidation (deciding when to remove items from the cache) can be tricky to get right, and you also need to be mindful of not using too much memory by caching excessively. Nonetheless, used judiciously, caching can be one of the most effective ways to optimize your C# code.
9. Be Mindful of Capturing in Lambdas
Lambda expressions in C# are a powerful tool that allows you to define an anonymous function inline. However, when used carelessly, they can cause performance problems. One such situation is when a lambda expression captures (i.e., references) variables from the surrounding scope.
Understanding Variable Capture
Let’s start with a simple example. Consider the following method:
public static List<Action> CreateActions()
{
   List<Action> actions = new List<Action>();
   for (int i = 0; i < 10; i++)
   {
       actions.Add(() => Console.WriteLine(i));
   }
   return actions;
}
This code creates a list of actions, each of which writes the current value of i to the console. However, because of the way lambdas capture variables, all of the actions will actually write 10 (the value of i after the loop finishes), not the value of i at the time each action was created.
Avoiding Unintended Captures
To avoid this problem, you can create a new variable inside the loop and capture that instead:
public static List<Action> CreateActions()
{
   List<Action> actions = new List<Action>();
   for (int i = 0; i < 10; i++)
   {
       int loopVar = i;
       actions.Add(() => Console.WriteLine(loopVar));
   }
   return actions;
}
Now each action captures a different loopVar variable, so they each write the expected value.
Understanding Performance Implications
The performance implications of variable capture become more pronounced when the captured variables are large or when they’re referenced in a long-running lambda that prevents them from being garbage-collected.
For example, consider the following code:
public static void ProcessData(int[] largeArray)
{
   Action action = () => Console.WriteLine(largeArray.Length);
   // More code...
}
The action lambda captures the largeArray variable. If ProcessData is called with a large array and action is long-lived (e.g., if it's stored in a global variable or used as an event handler), largeArray won't be garbage-collected until action is.
To avoid this, you can limit the scope of the captured variables as much as possible and avoid capturing large objects. For example, you could modify the above code like this:
public static void ProcessData(int[] largeArray)
{
   int length = largeArray.Length;
   Action action = () => Console.WriteLine(length);
   // More code...
}
Now action only captures the length variable, which is much smaller than largeArray. This allows largeArray to be garbage-collected earlier, reducing memory usage.
10. Use the ‘in’ Keyword for Read-Only Reference Parameters
In C#, parameters can be passed to methods in one of two ways: by value or by reference. By default, value types (such as structs or ints) are passed by value, which means a copy of the value is made and the method receives that copy. Any modifications made to this copy inside the method do not affect the original value. However, this copying can be resource-intensive when dealing with large value types, potentially impacting performance.
C#’s ‘in’ keyword offers a solution to this potential inefficiency. The ‘in’ keyword allows you to pass parameters by reference, but without permitting the method to modify the parameter’s value. This approach allows you to avoid the cost of copying large value types, improving performance, while still preserving the immutability of the original value. When working with large structs, the ‘in’ keyword can be a powerful tool for enhancing your code’s efficiency.
Let’s look at some examples to illustrate this.
struct LargeStruct
{
   public double X, Y, Z, A, B, C, D, E, F, G;
}


void MyMethod(in LargeStruct largeStruct)
{
   // Do something with largeStruct
}
Now, you can call the method like this:
LargeStruct myStruct = new LargeStruct();
MyMethod(in myStruct);
By using the ‘in’ keyword, you can optimize the performance of your C# code when dealing with large structs. However, be aware that ‘in’ parameters have their own nuances and should be used judiciously. For example, passing a struct as an ‘in’ parameter can result in defensive copying if the struct’s methods are called within the method. Always measure the performance before and after applying such optimizations.
TLDR;
1. Avoid Boxing and Unboxing
Boxing and unboxing can be a heavy operation. Use them sparingly for better performance.
Common Pitfalls:
Misunderstanding the concept and inadvertently using boxing/unboxing.
Overuse in critical performance code paths.
Reference: Boxing and Unboxing (C# Programming Guide)
2. Use StringBuilder for String Concatenation
StringBuilder provides an efficient way to concatenate strings, especially in loops.
Common Pitfalls:
Using StringBuilder for single concatenation.
Using ‘+’ operator for multiple concatenations in loops.
Reference: StringBuilder Class in .NET
3. Leverage C#’s Lazy Initialization
Lazy initialization is a tactic where you delay the creation of an object, the calculation of a value, or some other expensive process until the first time it is needed.
Common Pitfalls:
Ignoring thread safety when using lazy initialization.
Overusing lazy initialization where immediate initialization is more suitable.
Reference: Lazy<T> Class in .NET
4. Optimize Loops
Make sure to optimize your loops, this can significantly increase your performance.
Common Pitfalls:
Not caching the count in for loops.
Not considering the order of complexity in nested loops.
Reference: For Loop — C# Reference
5. Use Async/Await for I/O Operations
Async/Await pattern can help to make your application more responsive and less likely to be unresponsive while it’s performing operations.
Common Pitfalls:
Using .Result or .Wait() instead of await.
Making every method async without need.
Reference: Asynchronous programming with async and await
6. Avoid Exceptions in Normal Program Flow
Exceptions are for exceptional cases, not for regular control flow. Avoid them where possible.
Common Pitfalls:
Using exceptions to control normal program flow.
Not using proper error checking before operations.
Reference: Exception Handling
7. Prefer ValueTypes Over ReferenceTypes
ValueTypes typically stay on the stack, making them more efficient. Use ValueTypes when possible.
Common Pitfalls:
Not considering the copy semantics of value types.
Using reference types where a value type is more appropriate.
Reference: Choosing Between Class and Struct
8. Cache Results of Expensive Computations
Don’t repeat expensive calculations if the result remains the same. Cache the results for better performance.
Common Pitfalls:
Not using caching for repeatable expensive computations.
2. Overusing caching leading to memory bloat or stale data.
Reference: Caching in .NET
9. Use the ‘in’ keyword for Read-Only Reference Parameters
The ‘in’ keyword allows passing reference types by reference, but without the possibility of modifying them. This helps with performance when dealing with large structs.
Common Pitfalls:
Using ‘in’ keyword when modification is needed.
Overusing ‘in’, leading to code that’s harder to understand.
Reference: in keyword — C# Reference
10. Be Mindful of Capturing in Lambdas
Summary: Captured variables in lambdas can lead to unforeseen consequences. Be mindful of them for better memory and performance efficiency.
Common Pitfalls:
Unintentional capturing of variables leading to larger-than-expected scopes.
Not understanding how closure works with lambdas.
Reference: Variable Scope in Lambda Expressions
I would appreciate your response on how you liked it, but as well what kind of articles you would like to see in the future.
https://maherz.medium.com/top-10-performance-optimization-tips-for-c-developers-3b09d2385e54
