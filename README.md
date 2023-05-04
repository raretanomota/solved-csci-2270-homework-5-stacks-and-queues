Download Link: https://assignmentchef.com/product/solved-csci-2270-homework-5-stacks-and-queues
<br>
<h1></h1>

Stacks and Queues are both data structures that can be implemented using either an array or a linked list. You will gain practice with each of these in the following two mini-projects. The first is to build a simple calculator using a linked list stack and the second is to simulate a

multi-process producer-consumer problem using a circular array based queue.

RPN calculator

During the ‘70s and ‘80s, Hewlett-Packard used the so-called Reverse Polish Notation (RPN) in all their calculators. The notation refers to the way that binary operations are processed. Rather than the standard infix notation “1 + 1”, RPN, or postfix notation, is written “1 1 +”. While it may look backward at first, it is actually less ambiguous to write operations this way and it lends itself to an elegant implementation with a stack. As numbers (operands) are entered to the calculator, they are pushed onto a stack. When an operator, e.g. “+”, is entered, the top two elements on the stack are popped, added, and the result is pushed back to the stack. Note that you can load the stack with more than two operands; for example, entering the following sequence of inputs “1.5, 2, 4, +, +” will add 4+2, push the result, 6, to the stack, then add 6+1.5, and push 7.5 to the stack.




<table width="309">

 <tbody>

  <tr>

   <td width="95"><strong>Instruction </strong></td>

   <td width="214"><strong>Stack </strong></td>

  </tr>

  <tr>

   <td width="95">#&gt; 1.5</td>

   <td width="214"> </td>

  </tr>

  <tr>

   <td width="95">#&gt; 2</td>

   <td width="214"> </td>

  </tr>

  <tr>

   <td width="95">#&gt; 4</td>

   <td width="214"> </td>

  </tr>

  <tr>

   <td width="95">#&gt; +</td>

   <td width="214"> </td>

  </tr>

  <tr>

   <td width="95">#&gt; +</td>

   <td width="214"> </td>

  </tr>

 </tbody>

</table>




Similarly, the input sequence “2,3,4, *, 3, +, +” performs the product 4*3, then the sum 3+12, then the sum 15+2 and the resulting stack will have one item: 17.

<table width="311">

 <tbody>

  <tr>

   <td width="94"><strong>Instruction </strong></td>

   <td width="217"><strong>Stack </strong></td>

  </tr>

  <tr>

   <td width="94">#&gt; 2</td>

   <td width="217"> </td>

  </tr>

  <tr>

   <td width="94">#&gt; 3</td>

   <td width="217"> </td>

  </tr>

  <tr>

   <td width="94">#&gt; 4</td>

   <td width="217"> </td>

  </tr>

  <tr>

   <td width="94">#&gt; *</td>

   <td width="217"> </td>

  </tr>

  <tr>

   <td width="94">#&gt; 3</td>

   <td width="217"> </td>

  </tr>

  <tr>

   <td width="94">#&gt; +</td>

   <td width="217"> </td>

  </tr>

  <tr>

   <td width="94">#&gt; +</td>

   <td width="217"> </td>

  </tr>

 </tbody>

</table>




<h1>Producer-consumer problem</h1>

In parallel computing, the producer-consumer problem describes a simple synchronization task involving two processes; a producer, which generates data, and a consumer, which processes data. The problem is that they may work at different speeds, causing one process to wait for the other which is very inefficient. We can solve this problem by creating a data buffer in the form of a queue. When the producer generates some data it pushes it to the queue. The consumer dequeues data and processes it as it comes in. You will simulate this interaction (without parallelism of course) using a circular queue.

<h1>Starter Code on Moodle</h1>

<strong> </strong>

Do not modify the provided header files. You are provided with skeletons of your driver programs (​<em>RPNCalculatorDriver.cpp, ProducerConsumerDriver.cpp</em>​) which you need to complete and submit on Moodle. Write one corresponding C++ file for each header file that implements all of the class methods (a few of the getter functions are defined already, so you don’t have to implement them). The names of these files are below:




<ul>

 <li><em> Provided Starter Code: </em></li>

</ul>

○    RPN Calculator files

■    RPNCalculator.hpp (DO NOT MODIFY)

■    RPNCalculatorDriver.cpp (TODO #1)

○    Producer-Consumer files

■    ProducerConsumer.hpp (DO NOT MODIFY)

■    ProducerConsumerDriver.cpp (TODO #2) <strong><em>●      IMPORTANT: Files you need to create: </em></strong>○  RPNCalculator.cpp (TODO #3)

○    ProducerConsumer.cpp (TODO #4)

<h1>RPNCalculator Class</h1>

You will build an RPN calculator that can perform addition and multiplication on floating point numbers. This class utilizes the functionality of a linked list stack, which employs the following struct (included in ​<em>RPNCalculator.hpp</em>​)

<strong>struct</strong> ​ <strong>Operand</strong>​

<strong>{     </strong><strong>float</strong>​               ​<strong> number;     Operand* next; </strong>

<strong>}; </strong>




Implement the RPNCalculator class according to the following specifications

<h2>Operand* stackHead</h2>

<ul>

 <li>Points to the top of the stack (first node in the linked list). This is defined in the header file.</li>

</ul>

<strong>RPNCalculator() </strong>

<ul>

 <li>Constructor–set the ​<strong>stackHead </strong>​pointer to NULL</li>

</ul>

<strong>~RPNCalculator() </strong>

<ul>

 <li>Destructor–​<strong>pop</strong>​ everything off the stack and set ​<strong>stackHead </strong>​to NULL.</li>

</ul>

<strong>bool isEmpty() </strong>

<ul>

 <li>Returns true if the stack is empty (i.e. ​<strong>stackHead </strong>​is NULL), false otherwise</li>

</ul>

<strong>void push(float </strong>​<strong>number)</strong>​

<ul>

 <li>Insert a new node with ​<strong>number</strong>​ ​onto the top of the stack (beginning of linked list)</li>

</ul>

<h2>void pop()</h2>

➔ If the stack is empty, print ​<em>“Stack empty, cannot pop an item.” </em>​and return. Otherwise delete the top most item from the stack

<h2>Operand* peek()</h2>

➔ If the stack is empty, print​<em> “Stack empty, cannot peek.” </em>​and return NULL.​ ​Otherwise, return a pointer to the top of the stack

<h2>bool compute(std::string ​symbol​)</h2>

<ul>

 <li>Perform the arithmetic operation <strong>symbol</strong>​ ,​ ​ which will be either “+” or “*”, on the top 2​   numbers in the stack. The return value indicates whether the operation was carried out successfully</li>

 <li>If ​<strong>symbol </strong>​is not “+” or “*”, print ​<em>“err: invalid operation” </em>​and return false</li>

 <li>Store the floats from the top two elements in the stack in local variables and ​<strong>pop </strong>​</li>

</ul>

◆ Before getting each element, make sure that the stack is not empty. If it is empty, print ​<em>“err: not enough operands”</em>​ and return false

◆ If you pop the first element, and notice that the list is empty prior to getting the next element, print the error message, push the first element back to the stack (use push function), and return false

<ul>

 <li>Perform the arithmetic operation ​<strong>symbol</strong>​ ​on those two elements and push the result to the stack</li>

</ul>




<h2>**​Important</h2>

<ul>

 <li>use NULL, and not nullptr.</li>

 <li>make sure the prompt “#&gt; ” (without a newline at the end of prompt) is printed at every input of float or an operand.</li>

 <li>Only ‘=’ marks the end of expression. Till the end of expression is reached, the code is expected to: consume input, print error message if any, ignore the said erroneous input, and continue onto the next available input.</li>

</ul>




<h1>RPNCalculator main driver file</h1>

<ul>

 <li>Create a stack by instantiating an RPNCalculator object</li>

 <li>Prompt the user to enter the operators and operands using the print statement​<em>, “Enter the operators and operands (‘+’, ‘*’) in a postfix format”</em></li>

 <li>Read user inputs ​<em>(Tip: use getline for all inputs)</em>​ until ​<strong>“=”</strong>​ is entered. If the input is a number (<strong>isNumber</strong>​ function provided in starter code) then push it onto the stack, else,​ call the ​<strong><em>compute</em></strong>​ function on the input ➔ When your program reads ​<strong>“=”</strong>​:</li>

</ul>

◆ If the stack is empty print <em>“No operands: Nothing to evaluate” </em>​ ​and return

◆ If the expression is invalid print ​<em>“Invalid expression” </em>​and return. An expression is considered valid if there is exactly one item left on the stack. <em>(</em>​ <em>Hint: pop the last item and check if the stack is empty)</em>

◆ Otherwise, print the result of the expression (for floating numbers limit the precision to 4 decimals)




<h2>Below are some sample outputs</h2>

<strong><u>SAMPLE OUTPUT 1</u></strong>

<strong>Enter the operators and operands (‘+’, ‘*’) in a postfix format </strong>

<strong>#&gt; </strong>​<strong>2.5 </strong>

<strong>#&gt; </strong>​<strong>3 </strong>

<strong>#&gt; </strong>​<strong>+ </strong>

<strong>#&gt; </strong>​<strong>2.4 </strong>

<table width="624">

 <tbody>

  <tr>

   <td width="624"><strong>#&gt; </strong>​<strong>* </strong><strong>#&gt; </strong>​<strong>=</strong><strong>13.2</strong></td>

  </tr>

  <tr>

   <td width="624"><strong><u>SAMPLE OUTPUT 2</u></strong><strong>Enter the operators and operands (‘+’, ‘*’) in a postfix format </strong><strong>#&gt; </strong>​<strong>15 </strong><strong>#&gt; </strong>​<strong>25 </strong><strong>#&gt; </strong>​<strong>* </strong><strong>#&gt; </strong>​<strong>30 </strong><strong>#&gt; </strong>​<strong>=</strong><strong>Invalid expression </strong></td>

  </tr>

 </tbody>

</table>

<h1>ProducerConsumer Class</h1>

**Beware of edge cases that arise from the array being circular**

In this class you will build a queue using the circular array implementation. Implement the methods of ​<strong>ProducerConsumer</strong>​ according to the following specifications.




<h2>std::string queue[​SIZE​]</h2>

<ul>

 <li>A circular queue of strings in the form of an array. ​<strong>SIZE </strong>​is initialized to a default value of 20 in ​<em>hpp</em></li>

</ul>

<strong>int queueFront </strong>

<ul>

 <li>Index in the array that keeps track of the front item</li>

</ul>

<h2>int queueEnd</h2>

<ul>

 <li>Index in the array that keeps track of the first available empty space (in case the queue is full, queueEnd points to queuFront).</li>

</ul>

<strong>ProducerConsumer() </strong>

<ul>

 <li>Constructor–Set ​<strong>queueFront </strong>​and ​<strong>queueEnd </strong>​to 0</li>

</ul>

<strong>bool isEmpty() </strong>

<ul>

 <li>Return true if the queue is empty, false otherwise</li>

</ul>

<strong>bool isFull() </strong>

<ul>

 <li>Return true if the queue is full, false otherwise</li>

</ul>

<h2>void enqueue(std::string ​item​)</h2>

➔ If the queue is not full, then add the​<strong> item</strong>​ to the end of the queue and modify <strong>queueFront </strong>​and/or ​<strong>queueEnd </strong>​if appropriate, else print “​<em>Queue full, cannot add new item”</em>

<h2>void dequeue()</h2>

<ul>

 <li>Remove the first item from the queue if the queue is not empty and modify ​<strong>queueFront </strong>and/or ​<strong>queueEnd </strong>​if appropriate. Otherwise print ​<em>“Queue empty, cannot dequeue an item” </em></li>

</ul>

<strong>int queueSize() </strong>

<ul>

 <li>Return the number of items in the queue.</li>

</ul>

<h2>std::string peek()</h2>

➔ If the queue is empty then print “​<em>Queue empty, cannot peek</em>​” and return an empty string.

Otherwise, return the first item in the queue.

<h1>ProducerConsumer main driver file</h1>

Your program will start by displaying a menu by calling the ​<strong>menu() </strong>​function which is included in the provided skeleton code. The user will select an option from the menu to decide upon what the program will do, after which the menu will be displayed again. Below are the specifics of the menu




<h2>Option 1: Producer (Produce items into the queue) – ​This is an enqueue operation</h2>

<ul>

 <li>This option prompts the user to enter the number of items being produced using the below print statement</li>

</ul>

cout &lt;&lt; ​”Enter the number of items to be produced:”​ &lt;&lt; endl;




<ul>

 <li>Then prompt the user to enter each item using the below print statement</li>

</ul>

cout &lt;&lt; ​”Item”​ &lt;&lt; &lt;ITEM_NO&gt; &lt;&lt; ​”:”​ &lt;&lt; endl;




<ul>

 <li>Produce (​<strong><em>enqueue</em></strong>​) all the items into the queue</li>

</ul>




<h2>Option 2: Consumer (Consume items from the queue) – This is a dequeue operation​</h2>

<ul>

 <li>This option prompts the user to enter the number of items being consumed using the below print statement</li>

</ul>

cout &lt;&lt; ​”Enter the number of items to be consumed:”​ &lt;&lt; endl;




<ul>

 <li>Consume (​<strong><em>dequeue</em></strong>​) items from the queue. If the number of items to be consumed is greater than the total number of items in the queue, then consume (​<strong><em>dequeue</em></strong>​) all the available items in the queue and notify the user with a below statement</li>

</ul>

cout&lt;&lt;​ “No more items to consume from queue” ​&lt;&lt; endl;

This message should never be printed more than once.

<ul>

 <li>For each item consumed, print the following</li>

</ul>

cout &lt;&lt; “Consumed: “​ &lt;&lt; item &lt;&lt; endl;”​

where <strong>item </strong>​ is the string you are dequeuing.​










<h2>Option 3: Return the queue size and exit</h2>

<ul>

 <li>This option prompts the user to return the number of items in the queue using the below print statement, before exiting the program.</li>

</ul>

cout &lt;&lt; “Number of items in the queue:” &lt;item_count&gt;​ ;​




<h2>Below is a sample output</h2>

<strong>*—————————————-* </strong>

<strong>Choose an option: </strong>

<ol>

 <li><strong>Producer (Produce items into the queue) </strong></li>

 <li><strong>Consumer (Consume items from the queue) 3. Return the queue size and exit </strong></li>

</ol>

<strong>*—————————————-* </strong>

<strong>1 </strong>

<strong>Enter the number of items to be produced: </strong>

<strong>3 </strong>

<strong>Item1 </strong>

<strong>Honey </strong>

<strong>Item2 </strong>

<strong>Bread </strong>

<strong>Item3 </strong>

<strong>Butter </strong>

<strong>*—————————————-* </strong>

<strong>Choose an option: </strong>

<ol>

 <li><strong>Producer (Produce items into the queue) </strong></li>

 <li><strong>Consumer (Consume items from the queue) 3. Return the queue size and exit </strong></li>

</ol>

<strong>*—————————————-* </strong>

<strong>2 </strong>

<strong>Enter the number of items to be consumed: </strong>

<strong>2 </strong>

<strong>Consumed: Honey </strong>

<strong>Consumed: Bread </strong>

<strong>*—————————————-* </strong>

<strong>Choose an option: </strong>




<h1><em>Instructor: Maciej Zagrodzki, Christopher Godley</em></h1>




<ol>

 <li><strong>Producer (Produce items into the queue) </strong></li>

 <li><strong>Consumer (Consume items from the queue) 3. Return the queue size and exit </strong></li>

</ol>

<strong>*—————————————-* </strong>

<strong>3 </strong>

<strong>Number of items in the queue:1 </strong>

<strong> </strong>


