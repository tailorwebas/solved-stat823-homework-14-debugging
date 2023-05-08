Download Link: https://assignmentchef.com/product/solved-stat823-homework-14-debugging
<br>
Using RMarkdown in RStudio, complete the following questions. Launch RStudio and open a new RMarkdown file and save it on your working directory as a name.Rmd file. At the end of the activity, knit your document to pdf generated from RMarkdown+Knitr and submit your homework on the Blackboard.

<h1>Q1</h1>

In order to calculate <em>f</em>(<em>x</em>) = <em>e<sup>−x</sup></em><sup>2</sup>

A function called <strong>calculate.exp() </strong>was defined below. However, this function is buggy.

<table width="632">

 <tbody>

  <tr>

   <td width="632">calculate.exp &lt;- <strong>function</strong>(my.number){exp.num &lt;- (<strong>–</strong>my.number) <strong>^ </strong>2 result &lt;- <strong>exp</strong>(exp.num) <strong>return</strong>(result)} <strong>calculate.exp</strong>(1)</td>

  </tr>

 </tbody>

</table>

## [1] 2.718282

After looking at the result when input equals of 1, we believe the <strong>calculate.exp(1) </strong>does not produce the correct reuslt.

(a). Modify this function by adding one line of code. After modification, when this function is being called, it prints the value of <strong>exp.num</strong>.

(b). Call the modified function with input value equals to 1.

(c). Add one line of code after the function is being defined, so that next time the <strong>calculate.exp() </strong>function is being called, the function enters into debug mode.

(d). Describe the difference between <strong>debug() </strong>and <strong>debugonce()</strong>. No code is required to answer this subquestion.

(e). Insert a <strong>browser() </strong>function in the middle of your <strong>calculate.exp()</strong>. So that a browser window opens after <strong>exp.num </strong>was calculated.

(f). Describe an equivlent alternative to do this using RStudio debugging tools.

<h1>Q2</h1>

Suppose we were asked to generate a function to run simulations with steps below:

Step 1: Sample 10 values from a normal distribution with <strong>mean = mu </strong>and <strong>SD = 1</strong>.

Step 2: Calculate the sample mean of the 10 values being simulated.

Step 3: Repeat 100,000 times and save sample means.

<table width="632">

 <tbody>

  <tr>

   <td width="632">my.simulation &lt;- <strong>function</strong>(mu){ <em># initiate an empty value </em>mean.vec &lt;- NA <strong>for </strong>(i <strong>in </strong>1<strong>:</strong>100000){ <em># Step 1 </em>simu.data &lt;- <strong>rnorm</strong>(n = 10, mean = mu, sd = 1)<em># Step 2</em>mean.simu &lt;- <strong>mean</strong>(simu.data)<em># Step 3</em>mean.vec &lt;- <strong>c</strong>(mean.vec, mean.simu)}result &lt;- <strong>mean</strong>(mean.vec) <strong>return</strong>(result)}<em># print the time it takes to execute the function </em><strong>system.time</strong>(<strong>print</strong>(<strong>my.simulation</strong>(10)))</td>

  </tr>

 </tbody>

</table>

## [1] NA

##        user system elapsed ## 19.596 9.845 29.519

We called this function by using <strong>mu = 10 </strong>as input, we got an NA value as a result and it took about 30 seconds to get this result.

(a). Modify this function by reduce the number of iterations so that it returns the same NA result with same <strong>mu = 10 </strong>as input but takes shorter time to run.

(b). Debug the function. After your debug, call the function with <strong>mu = 10 </strong>and print the result. Your result should be a numberic number close to 10.

<h1>Q3</h1>

Suppose that we are interested in finding runs of k consecutive TRUE values in a vector <strong>x </strong>that contains TRUE/FALSE. Below is a buggy version of a get.runs() function.

<table width="632">

 <tbody>

  <tr>

   <td width="632">get.runs &lt;- <strong>function</strong>(x, k){n &lt;- <strong>length</strong>(x) runs &lt;- NULL <strong>for </strong>(i <strong>in </strong>1<strong>:</strong>(n<strong>–</strong>k)){ <strong>if</strong>(<strong>all</strong>(x[i<strong>:</strong>(i<strong>+</strong>k-1)] <strong>== </strong>TRUE)){runs &lt;- <strong>c</strong>(runs, i)} <strong>return</strong>(runs)}</td>

  </tr>

 </tbody>

</table>

(a). If you copy and paste the buggy version of this function and try to run it, you will get a <strong>“Error: Incomplete expression:”</strong>. Fix this error. (Hint: by adding matching parentheses, brackets, braces)

(b). By looking at a input vector <strong>x = c(TRUE, FALSE, FALSE, TRUE, TRUE, TRUE, FALSE, TRUE, TRUE) </strong>we see there are three places where we can find <strong>k = 2 </strong>TRUEs, they are at 4,5,8. However, after you fixed the error in part (a). this function returns a vector of <strong>c(4,5) </strong>instead of <strong>c(4,5,8)</strong>. By using different debugging tools, find out where the bug is and fix the bug. Show your bug free function and execute the below code so that you get a result of vector <strong>c(4,5,8)</strong>.

<table width="632">

 <tbody>

  <tr>

   <td width="632"><em># this function below should return a vector # of (4,5,8) because there are a run of two TRUEs # in those indices.</em><strong>get.runs</strong>(<strong>c</strong>(TRUE, FALSE, FALSE, TRUE, TRUE, TRUE, FALSE, TRUE, TRUE), 2)</td>

  </tr>

 </tbody>

</table>

## [1] 4 5