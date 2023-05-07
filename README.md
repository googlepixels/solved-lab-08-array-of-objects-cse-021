Download Link: https://assignmentchef.com/product/solved-lab-08-array-of-objects-cse-021
<br>
<span style="font-size: 2.61792em; letter-spacing: -1px;">Overview</span>

We will see the power of Object-Oriented Programming (OOP) when we want to create a program that behaves similar to what we have done before (code reuse). This lab will not be limited to just 3 specialty cheeses but any amount set by the user. Luckily, this does not change anything for the Cheese class, and we just have to create a shop that contains an array of items to sell, which we will call ShopArr.




<strong>Before you get started</strong>, read chapters 7.10, 7.11, and 7.12. Answer the Assessment questions as you encounter them in the next section. The prompts for answering assessment questions are placed immediately following the material to which the listed questions relate.

<h1>Getting Started</h1>

After following the import instructions in the assignment page, you should have a Java project in Eclipse titled Lab 21_8. This PDF document is included in the project in the <strong>doc</strong> directory. The Java files you will use in this lab are in the <strong>src</strong> directory.




Copy over RunShop.java and Cheese.java from the previous lab. Your program must produce an output matching the sample runs given below.

<h1>Part 1: Modify RunShop.java (version 2)</h1>

In the original RunShop.java (from previous lab), we are creating an instance of Shop class named shop. Then we call the method run() of this shop object. Now we no longer have an object or class called Shop and instead, we will be using ShopArr. Import RunShop.java from the previous lab to do this step.




[Answer assessment question 1]




Make the change in RunShop.java file which will allow you to run the newest cheese shop. (same as answer to Q1)

<h1>Part 2: Fill-in ShopArr.java</h1>

Everywhere you see comment to “Fill in Code” is where you need to add code to make this program behave correctly. If it says “Fix Code” you need to change existing code. In most places a sample is provided to help you get started. The program currently runs but the behavior is obviously incorrect.




Here is a simpler version of intro() as reference




public static void intro(String[] names, double[]prices, int[] amounts) {

// Special 3 Cheeses  if (names.length &gt; 0) {   names[0] = ” Humboldt Fog”;   prices[0] = 25.00;

}

if (names.length &gt; 1) {   names[1] = “Red Hawk “;

prices[1] = 40.50;

}

if (names.length &gt; 2) {   names[2] = “Teleme”;

prices[2] = 17.25;

}   Random ranGen = new Random(100);

System.out.println(“We sell ” + names.length + ” kinds of Cheese”);  if (names.length &gt; 0)

System.out.println(names[0] + “: $” + prices[0] + ” per pound”);  if (names.length &gt; 1)

System.out.println(names[1] + “: $” + prices[1] + ” per pound”);  if (names.length &gt; 2)

System.out.println(names[2] + “: $” + prices[2] + ” per pound”);

for (int i = 3; i &lt; names.length; i++) {   names[i] = “Cheese Type ” + (char)(‘A’+i);   prices[i] = ranGen.nextInt(1000)/100.0;

amounts[i] = 0;

System.out.println(names[i] + “: $” + prices[i] + ” per pound”);

}

}




We must now split this method into two methods for this lab: init() and intro(). The reason is because we want to repeat intro() if needed, but creating objects using init() needs to be done only once. So all the println statements will be moved to intro(). Now take a look at ShopArr.java and the init() method in it. We see the code is very similar but the variables have changed. The very first thing we do is create the array of Cheese pointers since we are given the argument max.




// Create max number of Cheese pointers cheese = new Cheese[max];




Then you will see the code to handle Humboldt Fog cheese:




if (max &gt; 0) {

cheese[0] = new Cheese();  cheese[0].setName(“Humboldt Fog”);

cheese[0].setPrice(25.00);

}




Instead of names.length, we now use max in this code.




[Answer assessment question 2]




Also, instead of using three different arrays (names, prices and amounts), we now have only 1 array of cheeses. So the code is changed to use cheese[0] which points to the first Cheese object in the array. If we want to change the name then we use a mutator setName, which exists inside the Cheese object

(cheese[0]), that we access using the “.” operator. We instantiate Humboldt Fog using default constructor with 0 arguments followed by invoking two mutators. Red Hawk is instantiated with a 1-argument constructor followed by invoking only one mutator. And finally, Teleme uses a 2-argument constructor, so no mutator calls are necessary. Note that you must use the corresponding accessor method calls in other parts of the code to get to the value of the variables set by the mutators.




[Answer assessment questions 3, 4 and 5]




Now you will need to implement the for-loop in init(). The original loop is as follows:




for (int i = 3; i &lt; names.length; i++) {  names[i] = “Cheese Type ” + (char)(‘A’ + i);  prices[i] = ranGen.nextInt(1000)/100.0;  amounts[i] = 0;

}




You must figure out the transformations needed in the for-loop to work with a single cheese array instead of 3 arrays, as shown by the code already inside init(). You can assume the amount is already set to 0 for each cheese so the loop doesn’t need to set it again to 0.




[Answer assessment question 6]




We have also implemented the basic version of ShopArr constructor which just invokes init method with a fixed number, 10. You must fill-in the 1-argument constructor which will invoke init using the max parameter instead.




[Answer assessment question 7]




Now implement intro(Scanner), itemizedList(), calcSubTotal() and discountSpecials() so they work for an array of cheese pointer. The methods printSubTotals() and printFinalTotal() should be identical to Lab 07.




[Answer assessment questions 8 and 9]

<h1>Part 3: Modify RunShop.java (version 3)</h1>

Now notice that there are two constructors for ShopArr available and version 2 of RunShop (from Part 1) is only calling the default constructor with no arguments. So, the program will always create 10 cheeses to sell. We will need to make use of the second constructor which takes an argument max and sets the amount of cheeses to sell.




Modify RunShop so it asks the following question to the user and then pass the number user enters to the ShopArr constructor. So the program now starts as follows:




Enter the number of Cheeses for shop setup: 12

We sell 12 types of Cheese (in 0.5 lb packages)




Everything should work as it did before, now you can just change the number of cheese from 10 to any amount you want (including 0 but not negatives).




[Answer assessment question 10]

<strong> </strong>

<h1>Part 4: (Assessment) Logic Check and Level of Understanding</h1>

Create a Word document or text file named Part4 that contains answers to the following:

<ul>

 <li>What are the minimal changes required to instantiate ShopArr and invoke run() on it?</li>

 <li>We can also use a &lt;something&gt;.length instead of max. What is the valid &lt;something&gt; to use in java?</li>

 <li>How can we tell which instantiation (new Cheese) corresponds to which constructor definition inside the Cheese class?</li>

 <li>How can we identify a mutator method call?</li>

 <li>What would be the result if we added this line right after Teleme is created: cheese[2].setName(“Wrong Name”); ?</li>

 <li>Why is the init() method both private and void?</li>

 <li>What are the distinguishing features of constructor methods? (i.e., How do we tell them apart from other methods?)</li>

 <li>How can we figure out the number of required iterations for each loop?</li>

 <li>Should we pass in Cheese array pointer (cheese[]) as arguments into calcSubTotal or itemizedList? (Why or why not)</li>

 <li>What value will be printed by RunShop for “Ran with Cheese Total”? (fixed number or a formula)</li>

</ul>




<strong>Sample Runs (user input shown in </strong><strong>green</strong><strong>, with each run separated by a dashed-line): </strong>




<table width="671">

 <tbody>

  <tr>

   <td width="671">——————————————————————————-SAMPLE RUN 11   Enter the number of Cheeses for shop setup: 02   We sell 0 kinds of Cheese (in 0.5 lb packages)345  Display the itemized list? (1 for yes): 1 6  No items were purchased.78   Original Sub Total:     $0.009   Specials…10  None      -$0.011  New Sub Total:    $0.0012  Additional 0% Discount:       -$0.013  Final Total:      $0.001415 Do you wish to redo your whole order? (1 for yes): 01617  Thanks for coming!18  Ran with Cheese Total: 0——————————————————————————-SAMPLE RUN 21   Enter the number of Cheeses for shop setup: 12   We sell 1 kinds of Cheese (in 0.5 lb packages)3   Humboldt Fog: $25.0 per pound45  Enter the amount of Humboldt Fog in lb: 167         Display the itemized list? (1 for yes): 18         1.0 lb of Humboldt Fog @ $25.00 = $25.00 910  Original Sub Total:     $25.0011  Specials…12  Humboldt Fog (Buy 1 Get 1 Free): -$12.5013  New Sub Total:    $12.5014  Additional 0% Discount:       -$0.015  Final Total:      $12.501617 Do you wish to redo your whole order? (1 for yes): 11819  We sell 1 kinds of Cheese (in 0.5 lb packages)20  Humboldt Fog: $25.0 per pound2122 Enter the amount of Humboldt Fog in lb: 02324 Display the itemized list? (1 for yes): 1 25 No items were purchased.2627  Original Sub Total:     $0.0028  Specials…29  None      -$0.030  New Sub Total:    $0.0031  Additional 0% Discount:       -$0.032  Final Total:      $0.003334 Do you wish to redo your whole order? (1 for yes): 03536 Thanks for coming!</td>

  </tr>

 </tbody>

</table>




<table width="671">

 <tbody>

  <tr>

   <td width="671">37 Ran with Cheese Total: 1——————————————————————————-SAMPLE RUN 31   Enter the number of Cheeses for shop setup: 42   We sell 4 kinds of Cheese (in 0.5 lb packages)3   Humboldt Fog: $25.0 per pound4   Red Hawk: $40.5 per pound5   Teleme: $17.25 per pound6   Cheese Type D: $9.15 per pound78         Enter the amount of Humboldt Fog in lb: 4.59         Enter the amount of Red Hawk in lb: 4.510       Enter the amount of Teleme in lb: -311       Invalid input. Enter a value &gt;= 0: 1.712       Invalid input. Enter a value that’s multiple of 0.5: -413       Invalid input. Enter a value &gt;= 0: 1.914       Invalid input. Enter a value that’s multiple of 0.5: 1.5 15 Enter the amount of Cheese Type D in lb: 10 1617       Display the itemized list? (1 for yes): 118       4.5 lb of Humboldt Fog @ $25.00 = $112.5019       4.5 lb of Red Hawk @ $40.50 = $182.2520       1.5 lb of Teleme @ $17.25 = $25.8821       10.0 lb of Cheese Type D @ $9.15 = $91.50 2223  Original Sub Total:     $412.1324  Specials…25  Humboldt Fog (Buy 1 Get 1 Free): -$50.0026  Red Hawk (Buy 2 Get 1 Free): -$60.7527  New Sub Total:    $301.3828  Additional 15% Discount:      -$75.3429  Final Total:      $226.033031 Do you wish to redo your whole order? (1 for yes): 03233  Thanks for coming!34  Ran with Cheese Total: 4——————————————————————————-SAMPLE RUN 41         Enter the number of Cheeses for shop setup: 122         We sell 12 kinds of Cheese (in 0.5 lb packages)3         Humboldt Fog: $25.0 per pound4         Red Hawk: $40.5 per pound5         Teleme: $17.25 per pound6         Cheese Type D: $9.15 per pound 7  Cheese Type E: $2.5 per pound8   Cheese Type F: $8.74 per pound9   Cheese Type G: $9.88 per pound10  Cheese Type H: $2.91 per pound11  Cheese Type I: $6.66 per pound12  Cheese Type J: $0.36 per pound13  Cheese Type K: $2.88 per pound14  Cheese Type L: $7.23 per pound1516  Enter the amount of Humboldt Fog in lb: 1.517  Enter the amount of Red Hawk in lb: 2.218  Invalid input. Enter a value that’s multiple of 0.5: 2.519  Enter the amount of Teleme in lb: 020  Enter the amount of Cheese Type D in lb: 021  Enter the amount of Cheese Type E in lb: 022  Enter the amount of Cheese Type F in lb: 023  Enter the amount of Cheese Type G in lb: 824  Enter the amount of Cheese Type H in lb: 10</td>

  </tr>

  <tr>

   <td width="671">25       Enter the amount of Cheese Type I in lb: 026       Enter the amount of Cheese Type J in lb: 027       Enter the amount of Cheese Type K in lb: 028       Enter the amount of Cheese Type L in lb: 0 2930       Display the itemized list? (1 for yes): 131       1.5 lb of Humboldt Fog @ $25.00 = $37.5032       2.5 lb of Red Hawk @ $40.50 = $101.2533       8.0 lb of Cheese Type G @ $9.88 = $79.0434       10.0 lb of Cheese Type H @ $2.91 = $29.10 3536  Original Sub Total:     $246.8937  Specials…38  Humboldt Fog (Buy 1 Get 1 Free): -$12.5039  Red Hawk (Buy 2 Get 1 Free): -$20.2540  New Sub Total:    $214.1441  Additional 10% Discount:      -$21.4142  Final Total:      $192.734344 Do you wish to redo your whole order? (1 for yes): 14546  We sell 12 kinds of Cheese (in 0.5 lb packages)47  Humboldt Fog: $25.0 per pound48  Red Hawk: $40.5 per pound49  Teleme: $17.25 per pound50  Cheese Type D: $9.15 per pound51  Cheese Type E: $2.5 per pound52  Cheese Type F: $8.74 per pound53  Cheese Type G: $9.88 per pound54  Cheese Type H: $2.91 per pound55  Cheese Type I: $6.66 per pound56  Cheese Type J: $0.36 per pound57  Cheese Type K: $2.88 per pound58  Cheese Type L: $7.23 per pound5960       Enter the amount of Humboldt Fog in lb: 061       Enter the amount of Red Hawk in lb: 062       Enter the amount of Teleme in lb: 1263       Enter the amount of Cheese Type D in lb: 064       Enter the amount of Cheese Type E in lb: 165       Enter the amount of Cheese Type F in lb: 266       Enter the amount of Cheese Type G in lb: 367       Enter the amount of Cheese Type H in lb: 068       Enter the amount of Cheese Type I in lb: 069       Enter the amount of Cheese Type J in lb: 570       Enter the amount of Cheese Type K in lb: 071       Enter the amount of Cheese Type L in lb: -372       Invalid input. Enter a value &gt;= 0: 1.173       Invalid input. Enter a value that’s multiple of 0.5: 4 7475 Display the itemized list? (1 for yes): 0 7677  Original Sub Total:     $287.3478  Specials…79  None      -$0.080  New Sub Total:    $287.3481  Additional 15% Discount:      -$71.8482  Final Total:      $215.518384 Do you wish to redo your whole order? (1 for yes): 0</td>

  </tr>

 </tbody>

</table>




<ul>

 <li>Thanks for coming!</li>

 <li>Ran with Cheese Total: 12</li>

</ul>




<strong> </strong>

<h1>Specification Compliance</h1>

The following are some additional instructions to make sure your project complies with specifications:

<ol>

 <li>Your program must produce an output that <strong>exactly resembles the Sample Output shown above, including identical wording of prompts, spacing, input locations, etc</strong>.</li>

 <li>Your program must ensure the following:

  <ol>

   <li>Your program should not display items that are not bought (amount is 0) when listing them out [cf.</li>

  </ol></li>

</ol>

Sample Run 4, Lines 31-34]. If no items are purchased, then a special message is displayed [cf. Sample Run 2, Line 35].

<ol>

 <li>If no discounts are applied, a special message is displayed [cf. Sample Run 4, Line 79].</li>

</ol>

<ol start="3">

 <li>Your program must check for invalid inputs when entering the amounts [cf. Sample Run 3, Lines 8-15].</li>

 <li>Before you submit, in Eclipse, type CTRL-A (to select everything) followed by a CTRL-I (to fix indentation) on each of your java programs. In MacOS the corresponding keystrokes are Cmd-A followed by Cmd-I.</li>

</ol>

<strong> </strong>