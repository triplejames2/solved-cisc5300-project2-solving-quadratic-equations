Download Link: https://assignmentchef.com/product/solved-cisc5300-project2-solving-quadratic-equations
<br>



Programming Project #2

Write a program that prompts the user to enter the coefficients of a quadratic polynomial <em>ax</em><sup>2 </sup>+ <em>bx </em>+ <em>c</em>. It should then solve the polynomial equation

<em>ax</em><sup>2 </sup>+ <em>bx </em>+ <em>c </em>= 0.

You should use the quadratic formula to solve this equation; if you don’t remember it, you’ll find it later on in this handout.

Assuming that this is a genuine quadratic equation (i.e., the leading coefficient <em>a </em>is nonzero), there are three possible situations:

<ul>

 <li>Two distinct real solution, such as for the equation <em>x</em><sup>2</sup>− 3<em>x </em>+ 2 = 0, which has the solutions <em>x </em>= 1 and <em>x </em>= 2.</li>

 <li>Only one real root<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a> as in the case <em>x</em><sup>2 </sup>− 2<em>x </em>+ 1 = 0, which has the solution <em>x </em>= 1.</li>

 <li>No real roots, as with <em>x</em><sup>2 </sup>+ 1 = 0.</li>

</ul>

You can distinguish between these by checking the discriminant <em>b</em><sup>2 </sup>− 4<em>ac</em>.

Of course, you can’t control the input your users are giving you, which means that <em>a </em>= 0 is a possibility; in this case the quadratic equation has now degenerated to a linear equation. So your code should handle the case <em>a </em>= 0. Note that when <em>a </em>= 0, we have two subcases:

<ul>

 <li>When <em>b </em>, 0, the equation <em>bx </em>+ <em>c </em>= 0 can be solved for <em>x</em>. For example, 2<em>x </em>+ 5 = 0 has the solution <em>x </em>= −2.5.</li>

 <li>When <em>b </em>= 0, you’re now left with something of the form <em>c </em>= 0 to “solve”. For example, 1 = 0 is a contradiction, whereas 0 = 0 is an identity.</li>

</ul>

A few considerations:

<ol>

 <li>You are to do this using only the techniques found in Chapters 1 through 4 of the text.</li>

 <li>You should do this project, in a subdirectory proj2 of your ˜/private/programming-c++ directory. See the Project 1 handout for further discussion, and adjust accordingly.</li>

 <li>I am providing you with the following goodies, to help you get started.

  <ul>

   <li>An executable version of this program for you to try out, named proj2-agw.</li>

   <li>A “stub version” of the C++-code, named proj2-stub.cc. I’ll also explain this further on.</li>

  </ul></li>

</ol>

You should copy these files into your working directory, via the cp command. Assuming that you’re logged into one of our machines (i.e., on erdos or a lab machine) and that the working directory described in (2) above is your current directory, the command

cp ˜agw/class/programming-c++/share/proj2/* .

will do this. The dot is part of the command; it means “current working directory”. Once you’ve copied it over, <em>please </em>try it out, so you can see what I consider to be good input/output behavior, not to mention how I handle various strange data values (as mentioned above).

<ol start="4">

 <li>Of course, you’ll need to compute the square root of the discriminant. The standard library has afunction sqrt() that will be pretty helpful here. Its prototype (which you get for free) is double sqrt(double x);</li>

</ol>

The return value of sqrt(blah) is (not surprisingly) the square root of blah, assuing that blah is non-negative.<a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a>

<ol start="5">

 <li>As you know by now, it’s a good idea to let a function carry out a well-encapsulated subtask. Whendone carefully, this can shorten the main() function; my main() is only 21 lines long. I used two subsidiary functions:

  <ul>

   <li>The function having prototype void solve_linear(double b, double c);</li>

  </ul></li>

</ol>

solves a linear equation <em>bx </em>+ <em>c </em>= 0, distinguishing between the cases <em>b </em>, 0 and <em>b </em>= 0. Please make sure that this function does not divide by zero! For the record, my version was 14 lines long.

<ul>

 <li>The function having prototype void solve_quadratic(double a, double b, double c);</li>

</ul>

solves a genuine quadratic equation <em>ax</em><sup>2 </sup>+ <em>bx </em>+ <em>c </em>= 0, “genuine” meaning that <em>a </em>, 0. Mine was 21 lines long. This function should not take the square root of a negative number. Also, note that since the discriminant is zero for a repeated root, the quadratic formula can be used without the square root of the discriminant.

The main reason for using functions here (other than simply getting practice) is that each function (including the main() function) is small enough to understand easily; in particular, each function takes up less than a screenful of space.

At this point, we can talk about proj2-stub.cc. This file

<ul>

 <li>takes care of the overall logic flow,</li>

 <li>declares the two functions mentioned above, and</li>

 <li>gives “stub” implementations of these functions, i.e., minimal implementations for the program to compile.</li>

</ul>

Your first step will be to make a copy of proj2-stub.cc, which you’ll call proj2.cc. For fun, you should compile this file “as is,” and see if you understand why it works the way it does, in its limited way. If you now fill in the blanks (which means implementing the input section and completing the implementation of the two functions mentioned above), you’ll now have a working program.

Big hint: Do one thing at a time. First, take care of the input phase (this should be pretty easy). Run the program, to make sure that this piece works right. Now, implement one of the two functions, after which you should run the program and test that the program works right so far. Finally, implement the other function, and do yet more testing.

<ol start="6">

 <li>Here is a good collection of sample data to use.</li>

</ol>

<table width="0">

 <tbody>

  <tr>

   <td width="24"><em>a</em></td>

   <td width="29"><em>b</em></td>

   <td width="23"><em>c</em></td>

   <td width="114">Equation</td>

   <td width="204">Explanation</td>

  </tr>

  <tr>

   <td width="24">1</td>

   <td width="29">-3</td>

   <td width="23">2</td>

   <td width="114"><em>x</em><sup>2 </sup>− 3<em>x </em>+ 2 = 0</td>

   <td width="204">Two real roots (<em>x </em>= 1 and <em>x </em>= 2)</td>

  </tr>

  <tr>

   <td width="24">2</td>

   <td width="29">-6</td>

   <td width="23">4</td>

   <td width="114">2<em>x</em><sup>2 </sup>− 6<em>x </em>+ 4 = 0</td>

   <td width="204">Two real roots (<em>x </em>= 1 and <em>x </em>= 2)</td>

  </tr>

  <tr>

   <td width="24">1</td>

   <td width="29">-2</td>

   <td width="23">1</td>

   <td width="114"><em>x</em><sup>2 </sup>− 2<em>x </em>+ 1 = 0</td>

   <td width="204">One double root (<em>x </em>= 1)</td>

  </tr>

  <tr>

   <td width="24">1</td>

   <td width="29">-2</td>

   <td width="23">4</td>

   <td width="114"><em>x</em><sup>2 </sup>− 2<em>x </em>+ 4 = 0</td>

   <td width="204">No real roots</td>

  </tr>

  <tr>

   <td width="24">0</td>

   <td width="29">2</td>

   <td width="23">4</td>

   <td width="114">2<em>x </em>+ 4 = 0</td>

   <td width="204">Linear equation, root <em>x </em>= −2</td>

  </tr>

  <tr>

   <td width="24">0</td>

   <td width="29">0</td>

   <td width="23">0</td>

   <td width="114">0 = 0</td>

   <td width="204">An identity</td>

  </tr>

  <tr>

   <td width="24">0</td>

   <td width="29">0</td>

   <td width="23">1</td>

   <td width="114">1 = 0</td>

   <td width="204">A contradiction</td>

  </tr>

 </tbody>

</table>

<ol start="7">

 <li>Use the photo program so you can have something to turn in. <em>Don’t do this until the program is working! </em>The commands you should issue are as follows:</li>

</ol>

photo cat proj2.cc g++ -std=c++17 -o proj2 proj2.cc proj2 proj2 proj2 proj2 proj2 proj2 proj2 exit

You’ll be running proj2 once for each test dataset. Once again, see the Project 1 handout if you’re still unclear about photo.

Good luck!

Here is a listing of proj2-stub.cc:

/**********************************************************************




*

**********************************************************************/

#include &lt;bjarne/std_lib_facilities.h&gt;

// function declarations void solve_linear(double b, double c); void solve_quadratic(double a, double b, double c);

int main()

{

// input the coefficients of the polynomial

double a, b, c;                                                                  // coefficients of the polynomial

// figure out the rest yourself!!

// handle degenerate case (linear equation) and quit if (a == 0) // linear equation, not quadratic solve_linear(b, c);

else // genuine quadratic equation … forge ahead

solve_quadratic(a, b, c);

}

// solve the linear equation b*x + c == 0 void solve_linear(double b, double c)

{ cout &lt;&lt; “Trying to solve linear equation ” &lt;&lt; b &lt;&lt; “*x + ” &lt;&lt; c &lt;&lt; ” == 0
”;

// figure out the rest yourself!

}

// use classical quadratic formula to solve a genuine quadratic equation

// a*xˆ2 + b*x + c ==0, with a != 0

void solve_quadratic(double a, double b, double c)

{ cout &lt;&lt; “Trying to solve the quadratic equation ” &lt;&lt; a &lt;&lt; “*x*x + ” &lt;&lt; b &lt;&lt; “*x + ” &lt;&lt; c &lt;&lt; ” == 0
”;

// figure out the rest yourself!

}

<a href="#_ftnref1" name="_ftn1">[1]</a> More precisely, it’s a repeated real root of multiplicity two.

<a href="#_ftnref2" name="_ftn2">[2]</a> More honestly, the sqrt() function doesn’t really return the exact square root of its argument, but an approximation to same. But it’s a <em>very </em>good approximation.





