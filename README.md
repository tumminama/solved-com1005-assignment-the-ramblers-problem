Download Link: https://assignmentchef.com/product/solved-com1005-assignment-the-ramblers-problem
<br>
The problem is to work out the best walking route from a start point to a goal point, given a terrain map for the walking area. A terrain map specifies the height of each point in the area. Figures 1 shows an example of a realistic terrain map.

Figure 1: A realistic Terrain Map

A more simple terrain map is shown in Figure 2.

For a rambler, the best route is the one which involves the least climbing.

Figure 2: A simple Terrain Map. White is highest, black is lowest. This map is saved in tmc.pgm

<h1>Representing Terrain Maps</h1>

We’ll store our terrain maps in Portable Grey Map (pgm<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>) format.

In this format each cell is represented by an int from 0 to 255.

You can view and edit pgm files using irfanviewer – free download here: <a href="http://www.irfanview.com/">http://www. </a><a href="http://www.irfanview.com/">irfanview.com</a> or just a normal text editor as it is in fact just a normal text file. In Figure 3 you can see a screenshot of the content of the tmc.pgm.

Figure 3: This is the content of the file tmc.pgm when viewed in a terminal window.

A pgm file contains a header followed by a matrix with the actual data. Figure 4 shows the header information. Figure 5 shows the x- and y-axis definitions.

<h1>Code</h1>

Code for handling the terrain maps is in the code folder within the assignment folder.

Figure 4: Header information in the pgm file.

Figure 5: PGM data matrix with <em>x </em>and <em>y </em>orientation.

You are provided with the file tmc.pgm and a java class TerrainMap whose constructor is given the filename of a pgm image and reads its contents, i.e.,

<table width="633">

 <tbody>

  <tr>

   <td width="633">// defining a new terrain mapTerrainMap tm = new TerrainMap(“tmc.pgm”);</td>

  </tr>

 </tbody>

</table>

1

2

TerrainMap has the following accessors:

<table width="633">

 <tbody>

  <tr>

   <td width="633">// accessors public int[][] getTmap() { return tmap;};public int getWidth() { return width;};public int getDepth() { return depth;};public int getHeight() { return height;};</td>

  </tr>

 </tbody>

</table>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

<h1>Rambler’s costs</h1>

The Rambler steps one pixel at a time North, South, East or West (not diagonally). An upward step is more costly. The local cost <em>c</em>(<em>y,x,y</em>′<em>,x</em>′) of a step from (<em>y,x</em>) to (<em>y</em>′<em>,x</em>′) is:

<table>

 <tbody>

  <tr>

   <td>{</td>

  </tr>

 </tbody>

</table>

1                                                      if <em>h</em>(<em>y</em><sup>′</sup><em>,x</em><sup>′</sup>) ≤ <em>h</em>(<em>y,x</em>)

<em>c</em>(<em>y,x,y</em><sup>′</sup><em>,x</em><sup>′</sup>) =(1)

1+ |<em>h</em>(<em>y</em><sup>′</sup><em>,x</em><sup>′</sup>) − <em>h</em>(<em>y,x</em>)|         otherwise.

where <em>h</em>(<em>y,x</em>) is the height in the terrain map at point (<em>y,x</em>). NOTE, that <em>y </em>is written before <em>x</em>!

Figure 6: Illustration of a lowest cost route found from a start point (car park at (7,0)) and point at (5,8).

<h1>What you must do</h1>

Using the Java code provided for the assignment do the following <strong>four tasks</strong>:

<strong>Task 0: </strong>Set up a GitHub (or similar) repository for keeping versions of your code as you develop your solution. Make sure to push updates regularly. The purpose of using a git repository is twofold: i) to develop good habits and practice around version control; ii) in case of a suspicion of unfair means, you have clear evidence that code was developed along the way by yourself. You must add the url of your github repository to your LATEX report (I’ve added a nifty little footnote to the title where this info can go).

<strong>Task 1: Implement branch-and-bound for the Rambler’s problem </strong>Working with search4 code and following the procedure of taking a set of general classes and making a specific solution for a particular problem, implement branch-and-bound search for the Rambler’s problems. You will need to define a class RamblersState and a class RamblersSearch. Look at the corresponding classes for Map Traversal (week3) for guidance. You will also need a class for running the tests. Call this RunRamblersBB.

<strong>Task 2: Assess the efficiency of branch-and-bound </strong>Try out a number of start and end points on the tmc map and assess the efficiency of branch-and-bound in this domain. You may also create other Terrain Maps of your own, or make use of diablo.pgm in the Rambler’s folder which is a terrain map of Mt Diablo in California. Tip: that map is a lot bigger, so if your code takes a long time to run, consider editing the map down.

<strong>Task 3: Implement A* search for the Rambler’s problem </strong>Working from the search4 code, implement A* search for the Rambler’s problem. Remember that for A* you need (under)estimates of the remaining cost to the goal. Experiment with different choices for this heuristics, for example:

<ol>

 <li>the Manhattan Distance between the current pixel and the goal (<em>p </em>+ <em>q</em>).</li>

 <li>the Euclidean distance</li>

 <li>the height difference</li>

 <li>combinations of these</li>

</ol>

You may also devise other ways of combining the estimates. You will also need a class for running the tests. Call this RunRamblersAstart.

<strong>Task 4: Compare the efficiency of branch-and-bound and A* </strong>Perform experiments to test the hypothesis that A* is more efficient than branch-and-bound and that the efficiency gain is better for more accurate heuristics.

<strong>Task 5: Produce a report </strong>Your experimental report should describe your implementations and your results. Your report should include at the very least:

<ul>

 <li>Description of your branch-and-bound and A* search implementations.</li>

 <li>Presentation of results obtained when testing the efficiency of these two approaches.</li>

 <li>A comparison of the results – can you verify your hypothesis?</li>

</ul>

A LATEX report template is provided, with compulsory sections specified. You may add more sections if you wish: include in your report what you think is interesting.

<strong>Note 1: </strong><em>you <strong>must </strong>use the L</em><em>ATEX template provided for your report. However, you will not be marked on your ability to use L</em><em>ATEX to format your report (i.e., there are no extra marks for making it look fancy!). That being said, L</em><em>ATEX is an essential piece of software for communicating research and results in engineering and science, so we want you to get experience using it early on.</em>

<strong>Note 2: </strong><em>you should not have to make any changes to the Java code provided except to control the amount of printout during a search and perhaps to modify what a successful search returns. It’s a good idea to revisit the week 3 lab class for a reminder of how you worked with branch-and-bound and A* searches.</em>


