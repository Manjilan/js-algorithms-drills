# Data Structures: Stacks & Queues

Stacks and queues are two commonly used data structures.  You can read about them below or watch [this video](https://www.youtube.com/watch?v=6QS_Cup1YoI). All stack and queue operations mentioned (`push`, `pop`, `enqueue`, `dequeue`) take O(1) time.

## Stacks

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/29/Data_stack.svg/2000px-Data_stack.svg.png" width="400px" alt="stack image with push and pop">

Stacks as a data structure are a lot like stacks as a physical structure. Think of stacks of dishes or books – we can remove an item from the top of the stack (by `pop`ing), or add an item to the top of the stack (by `push`ing it). 

While we may be able to Jenga stacks of real world objects, the data structure only allows us to manipulate the top item of the stack.  Some stack implementations also allow us to `peek` at the value of the top item without actually `pop`ing it off of the stack.

Stacks are "Last In, First Out" (LIFO) -- the last item pushed on top of a stack will be the first thing popped off of the stack. Because elements within a stack do not have an index, you can only add to the top (`push`) and remove from the bottom (`pop`) of the stack. The `push` and `pop` operations both take O(1) - constant time. 

<img src="https://media.giphy.com/media/x5bZM4HAwr2mY/giphy.gif" alt="syrup on pancakes gif" width="400px">

### Thinking with Stacks

1. Draw a stack after each of the following operations:

  * PUSH 0
  * POP
  * PUSH 2
  * PUSH 4
  * PUSH 6
  * POP
  * PUSH 8

  <details><summary>click for answer</summary>
  
    ```
    * start     []
    * PUSH 0    [0]
    * POP       []
    * PUSH 2    [2]
    * PUSH 4    [2, 4]
    * PUSH 6    [2, 4, 6]
    * POP       [2, 4]
    * PUSH 8    [2, 4, 8]
    ```
    
  </details>

1. Stacks and queues are often implemented with linked lists. Think about how you'd use a linked list to make a stack.  Where would you put the "top" of the stack? How would you add something to the top the stack? How would you take something off?
 
 <details><summary>super stuck? click for an answer...</summary>
 > The "top" could be the head of the linked list. You could use `prepend` to `push` something onto the top. You could `delete` the list's head and return it to `pop`.
 </details>

1. It's also pretty natural to use arrays for stacks given the built-in methods we have access to in JavaScript.  So, let's think of arrays.  Where would you put the "top" of the stack? How would you add something to the top the stack? How would you take something off?

 <details><summary>super stuck? click for an answer...</summary>
 > The "top" could be the end of the array, and you could use array methods `push` and `pop`.  Thanks, JavaScript!
 </details>

1. **Stretch:** How would you implement a stack with a fixed-size array? [Why would you want to do this?](https://stackoverflow.com/questions/33725821/why-would-one-implement-a-stack-using-a-fixed-length-array-instead-of-a-variable)


## Queues


<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/52/Data_Queue.svg/2000px-Data_Queue.svg.png" width="400px" alt="queue image with enqueue and dequeue">


Queues as a data structure are a lot like queues as a physical structure. This makes more sense with British English, where *queue* means "a line" or "to line up". Think of an orderly line of customers waiting to order at a restaurant. We can remove a customer from the front of the queue when his/her turn comes (by `pop`ing, also known as `dequeue`ing), or add a customer to the back of the queue when he/she joins the line (by `push`ing or `enqueue`ing it). 

Again, while we may be able to "cut" in line in the real world, the queue data structure only allows us to add to the end of the stack or remove from the beginning. Like with stacks, some implementations of queues also allow us to `peek` at the value of the first item without `dequeue`ing it.

Queues are "First In, First Out" (FIFO) -- the first item enqueued will be the first to move all the way through the line and get dequeued. The `enqueue` and `dequeue` operations both take O(1) - constant time.  

<img src="http://www.rioleo.org/images/static/queuesafety.jpg" alt="stick figure demon eats person cutting in line -- from popcoaster.com" width="400px">

### Thinking with Queues

1.  Draw a queue after each of the following operations:

  * ENQUEUE 0
  * DEQUEUE
  * ENQUEUE 2
  * ENQUEUE 4
  * ENQUEUE 6
  * DEQUEUE
  * ENQUEUE 8

  <details><summary>click for answer...</summary>
  
    ```
    
    * start        []
    * ENQUEUE 0    [0]
    * DEQUEUE      []
    * ENQUEUE 2    [2]
    * ENQUEUE 4    [2, 4]
    * ENQUEUE 6    [2, 4, 6]
    * DEQUEUE      [4, 6]
    * ENQUEUE 8    [4, 6, 8]
    
    ```
    
  </details>



1. How would you implement a queue **with an array**? Where would you decide the front of the queue would be? How would you `enqueue` something to the end of the queue? How would you `dequeue` something from the front of the queue?

 <details><summary>super stuck? click for an answer...</summary>
 > The "front" could be the beginning of the array.  To enqueue, you'd use JavaScript's handy `push` array method. To dequeue, you could use JavaScript's `shift` method, which removes and returns the first element from an array.
 </details>
 

1. How would you implement a queue **with a linked list**? Where would you decide the front of the queue would be? How would you `enqueue` something to the end of the queue? How would you `dequeue` something from the front of the queue?

 <details><summary>super stuck? click for an answer...</summary>
 > You'd need to store the tail.  The "front" could be the head of the linked list. The "back" could be the tail.  You could enqueue by `append`ing to the tail.  You could dequeue by deleting and returning the head node. 
 </details>

1. **Stretch:** How would you implement a queue with a fixed-size array?



## Challenges

#### Design Decisions

Would you use a stack or a queue to...

1. ... print out a list of instructions that must be done in order?

1. ... allow a user to undo changes to a document, one by one?

1. ... let users create playlists and play back the songs?

1. ... display *only* the 10 most recent websites a user has visited, with the most recently visited at the top of the list


#### Stacks in the Wild

1. **The Call Stack**

 Most programming languages rely on something called the "call stack," especially for recursion. The call stack keeps track of function calls that are in the process of executing.  When a function is called, it's `push`ed onto the call stack. When the function returns, it's `pop`ed off of the stack.
 
 Here's a recursive `factorial` function:
 
 ```js
 function factorial(num){
   if (num > 1){
     return num * factorial(num-1);
   } else if (num === 1 || num === 0){
     return 1;
   } else {
     console.log("can't do factorial of this number!");
     return undefined;
   }
 }
 
 factorial(3);
 // => 6
 ```
 
 Write out the full call stack for `factorial(3)` at each step in the function's execution.

1. **Stretch:** Try out [this stack challenge](stacks-parenthesis-battle.md), an epic battle for correct code!

#### Queues in the Wild

1. **Message Queues**

 Queues are often used to create "buffers" that temporarily store data from one part of a program until another part of a program can process the data. This is common with asynchronous data transfer, or when there is a gap between how often data is sent and how often it can be processed.
 
A good real-life example would be a restaurant where its diners order food faster than its chefs can cook it.  
 
 How would a queue help the chef keep track of meals to make? What should the chef do when the queue is empty?

1. **Stretch:** Try out [this queue challenge](queues-pricing.md) to calculate the total price of a purchase. 
