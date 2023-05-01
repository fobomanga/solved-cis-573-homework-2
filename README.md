Download Link: https://assignmentchef.com/product/solved-cis-573-homework-2
<br>
<h1>Introduction</h1>

In this assignment, you are given an implementation of a simple Android app. The code mostly works correctly but admittedly is not very “good” in terms of quality: design, understandability, readability, changeability, etc. Your job is to refactor the code to make it better.




This assignment is more complicated than it sounds. Even if you are a good programmer and have Android experience, do not wait until the last minute, as it can take quite a bit of time to get your development environment set up and figure out what the code is doing before you can start changing it.




<h1>Specification</h1>

This section describes the specification of the app that you need to refactor. Note that except in one place, you are <em>not</em> changing the functionality of the app, just its internal quality! Please contact a member of the instruction staff if you feel it is necessary to change the app’s functionality.




The app is a game that lets the user try to solve the Traveling Salesman Problem (http://en.wikipedia.org/wiki/Travelling_salesman_problem).




When the app starts, it displays a welcome screen and lets the user choose the number of points/locations that they need to connect:

<img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/925.png?w=980&amp;ssl=1" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/925.png?w=980&amp;ssl=1" data-recalc-dims="1">

 </noscript>




After the user chooses the number of locations and clicks “Play,” the app changes orientation and displays a map of the Penn campus, with the selected number of locations randomly placed and displayed as red boxes:

<img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/516.png?w=980&amp;ssl=1" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/516.png?w=980&amp;ssl=1" data-recalc-dims="1">

 </noscript>




The user can attempt to “connect the dots” and solve the Traveling Salesman Problem by drawing lines between locations. As the user moves their finger across the screen, the “stroke” is represented in yellow. Note that a stroke will only be shown if its beginning is close to one of the map locations:

<img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/147.png?w=980&amp;ssl=1" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/147.png?w=980&amp;ssl=1" data-recalc-dims="1">

 </noscript>







If the user releases their finger near another map location, the yellow stroke line disappears and a red line segment is shown connecting the two locations.




<img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/587.png?w=980&amp;ssl=1" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/587.png?w=980&amp;ssl=1" data-recalc-dims="1">

 </noscript>

The user can continue to draw more strokes and line segments, and can connect points in any order (i.e., the endpoint of one line segment does not have to be the beginning of the next one that is drawn).




When the number of line segments equals the number of locations in the map, the app determines whether the line segments form a circuit. If not, an error message is displayed:




<img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/303.png?w=980&amp;ssl=1" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/303.png?w=980&amp;ssl=1" data-recalc-dims="1">

 </noscript>

In this case, the line segments do not form a circuit, so the user is prompted to clear all line segments using the options menu at the top right:




<img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/946-1.png?w=980&amp;ssl=1" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/946-1.png?w=980&amp;ssl=1" data-recalc-dims="1">

 </noscript>

If they select “Clear,” all line segments are removed. If they select “Undo,” only the last line segment is removed. If they select “Quit,” they go back to the welcome screen.




If the line segments form a circuit, the app determines whether this is the shortest path. If it is not, it shows a message indicating approximately how much longer the user’s path is compared to the shortest path:




<img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/266.png?w=980&amp;ssl=1" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/266.png?w=980&amp;ssl=1" data-recalc-dims="1">

 </noscript>

If the path created by the user is the shortest path, the app shows a congratulatory message:




<img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/371.png?w=980&amp;ssl=1" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/371.png?w=980&amp;ssl=1" data-recalc-dims="1">

 </noscript>

After the third attempt of solving the problem, the app shows the solution in yellow:




<img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/433.png?w=980&amp;ssl=1" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/433.png?w=980&amp;ssl=1" data-recalc-dims="1">

 </noscript>




<h1>Getting Started</h1>

Before you begin, make sure you have set up your Android development environment. The app you will refactor was compiled with API Level 22 and we recommend that you use at least API Level 15 (“Android 4.0.3”).




Your AVD should be a Nexus 5 with 1080×1920 resolution; the app may not render correctly on smaller displays but should be fine on AVDs with similar screen sizes.




Android Studio should be installed on the Windows and Linux machines in the Moore 100 and Moore 207 labs. If you use one of them, be sure to unselect the “Use Host GPU” option when creating the AVD. <em>Also be sure to back up your work, as your Android Studio project may not persist between login sessions! </em>




Be sure that you can build a simple “Hello, World” project and run it in your AVD.




Next, download the .zip file containing the Android Studio project for the app that you will refactor; you will find it in Canvas.




Creating a new Android project from an existing one can be a tricky proposition, particularly when using different versions of the API, but you should (hopefully) be able to do the following:

<ul>

 <li>Download the file and then unzip it somewhere locally on your computer</li>

 <li>In Android Studio, choose: <strong>File</strong> -&gt; <strong>New -&gt; Import Project…</strong>, then navigate to the directory where you unzipped the distribution.</li>

 <li>You should see the little Android Studio icon next to the directory name; that’s what Android Studio thinks is the root directory. Click on that name.</li>

 <li>Then click OK.</li>

</ul>




After a few seconds, Android Studio should figure out all of the dependencies and build your app, and your project should be ready to go. You may see a blank “No files are open” screen, but you can open up the file navigator by clicking on the vertical “Project” tab on the left side of the screen.




Launch the app in your AVD by clicking the “Run app” button (the green arrow) on the menu bar and make sure that you can play the game before proceeding. Be sure that you can reproduce all of the features described above.




If Android Studio reports that there are problems with the project (e.g. some dependencies missing from the build path), you may need to add some support libraries by following the instructions in the “Adding libraries with resources” section at http://developer.android.com/tools/support-library/setup.html




If you can’t figure out how to fix these problems, ask a member of the instruction staff for help or post a question on Piazza before looking elsewhere online.




If you’re having a lot of trouble importing the existing project, a simpler (though less graceful) solution may be to just create a new Android project from scratch. Then open up the Android view in the Project tool window and copy over the relevant files from the project you imported:

<ul>

 <li>Copy the four .java files from app/src/main/java/ in the distribution to app/java/ in Android Studio, and make sure they’re in the right package</li>

 <li>Copy campus.png and salesman.png from app/src/main/res/drawable/ to app/res/drawable/ in Android Studio</li>

 <li>Copy the two .xml files from app/src/main/res/layout/ to app/res/layout/ in Android Studio</li>

 <li>Copy the two .xml files from app/src/main/res/menu/ to app/res/menu/ in Android Studio</li>

 <li>Copy the four .xml files from app/src/main/res/values/ to app/res/values/ in Android Studio</li>

 <li>Copy app/src/main/AndroidManifest.xml to app/manifests in Android Studio</li>

</ul>




After you’ve done all that, choose Build -&gt; Make Project from the main menu and hopefully it will all work!




<em>Troubleshooting note (09/20/15): </em>if you are able to run the app in your AVD but don’t see an options menu in the top right corner of the “game play” screen, try modifying GameActivity so that it extends <strong>android.support.v7.app.ActionBarActivity</strong> instead of just Activity.




Once you’ve got the app installed and running, you’re ready to start refactoring!




<h1>Implementation</h1>

The app consists of these classes:

<strong> </strong>

<h2>MainActivity</h2>

This is the Activity class that represents the welcome screen described above. It contains an <em>onButtonClick</em> method to handle the “Play” button on that screen, and an <em>onItemSelected</em> method that is used with the Spinner.




<h2>GameActivity</h2>

This class is the Activity that represents the game play screen. It has an <em>onOptionsItemSelected</em> method that is called when the user chooses something from the options menu.

<strong> </strong>

<h2>GameView</h2>

This is the View that represents the graphics for playing the game. It has an <em>onDraw</em> method for drawing what should be on the screen, as well as an <em>onTouchEvent</em> method for handling user interaction. It also has a number of helper methods and fields for storing all of the game state.




<h2>ShortestPath</h2>

This contains a static <em>shortestPath</em> method which is a brute-force solution to the

TravelingSalesmanProblem (it tries all possible combinations… hey, I was lazy, okay?).







<strong>A few notes about the code…</strong>

<ul>

 <li>The comments in the code are mostly there to help you if you’re not already familiar with Android. Some of them may be superfluous and you can certainly remove them if they’re in your way, but the intent here is not to address how they affect internal quality.</li>

 <li>As discussed in class, you really should have some good unit tests handy when you do refactoring, to make sure you didn’t break anything. Unfortunately, Android testing is a bit tricky (as you’ll find out in Homework #3!) and we don’t want to complicate things further, so please be sure that the program still adheres to the above specification after each refactoring step.</li>

 <li>You may find small bugs in the code, particularly with regard to things that are not explicitly covered in the spec. Unless otherwise explicitly instructed, you are <em>not</em> expected to fix these small bugs, but if you are unsure, please ask a member of the instruction staff.</li>

 <li>Likewise, there are some inefficiencies in the code, not only in the brute-force TSP solution but also in the logic of the game itself, e.g. it could detect that the line segments don’t form a circuit a bit sooner than it does. You’re not expected to address any of these issues unless explicitly asked to do so.</li>

 <li>The speed and smoothness of drawing the lines on the screen may be affected by your virtual device. These are not “bugs” to be fixed in this assignment, though.</li>

</ul>










<h1>Refactoring Activities</h1>

Your goal in this assignment is to refactor the code in the Traveling Salesman game in order to improve its design and internal quality.




If you have a question about the specification or the intended behavior of the code, please ask the instructor immediately; relevant answers will be distributed to the entire class.

<strong> </strong>

<strong><em>NOTE</em>:</strong> it is recommended that you complete the refactoring steps in the order in which they are provided here. Although you will ultimately end up with the same final product anyway, the steps that are described here will help remove any redundant refactoring activities.







<h2>Step 1. Remove dependency between GameView and MainActivity</h2>

MainActivity has a static field called <em>numLocations</em> which is populated when the user chooses an option from the Spinner (in <em>onItemSelected</em>) and represents the number of locations to use in the TSP map. GameView then reads this field in its <em>init </em>method. This works but creates a dependency between GameView and MainActivity.




Refactor MainActivity, GameActivity, and GameView so that MainActivity passes the value to GameActivity when it launches it (hint: use the Intent object in <em>onButtonClick</em>), and then GameActivity passes it to GameView (hint: do this in <em>onCreate</em>; you’ll have to do this after you’ve called <em>setContentView</em>).




In the refactoring.xls spreadsheet that was provided as part of the Android Studio project

(in the root directory), indicate the line numbers in MainActivity, GameActivity, and GameView (cells C8, C9, and C10) where you implemented this refactoring step. Please be sure to use the line numbers of the code in your final submission!




Be sure to check that the app still runs correctly before proceeding to the next step! Even if the code compiles, that doesn’t mean the user will correctly be able to choose the number of locations in the map.




<strong> <img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/565.png?w=980&amp;ssl=1" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

  <noscript>

   <img decoding="async" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2018/03/565.png?w=980&amp;ssl=1" data-recalc-dims="1">

  </noscript></strong>

<h2>Step 2. Comment GameView.init method</h2>

The <em>init</em> method in GameView contains some slightly confusing code (starting with the declaration of the Set object). Add a meaningful comment to this code segment to summarize what it does.




Don’t just write “this creates a Set,” “this creates a Random,” “this is a for-loop,” etc. Write 1-2 sentences before that code segment that summarizes it so that the reader can know what it does without having to step through each line.




Then, copy/paste the comment that you wrote for this step into your refactoring spreadsheet in cell C12.







<h2>Step 3. Use the android.graphics.Point class</h2>

The GameView uses two separate ArrayLists (<em>xCoords</em> and <em>yCoords</em>) to track the x- and y-coordinates of the points in the stroke that the user is drawing on the screen.




In your refactoring spreadsheet, name <strong>two</strong> code smells (from the ones discussed in class) exhibited by GameView as a result of this implementation.




Then, modify the GameView class so that you use an ArrayList of <u>android.graphics.Point</u> objects to represent the points in the stroke instead of separate Lists to represent corresponding x- and y-coordinates.




Since this is a pretty significant change, make sure that the app still runs correctly before moving on!







<h2>Step 4. Extract a Stroke class</h2>

As a result of your refactoring from Step 3, the GameView class should now have an ArrayList of Points representing the current stroke. You’ll also note that the width and color to be used when drawing the stroke are set repeatedly in <em>onDraw</em>, and there is a boolean in GameView indicating whether the current stroke is valid (i.e., whether its first point was within 30 pixels of a location on the map).

<em> </em>

Use the “Extract Class” refactoring pattern to create a Stroke class that encapsulates these four fields. Create any necessary helper methods in the Stroke class and make changes to GameView as needed.




<em>Note! Doing this part well is trickier than it sounds! </em>Be careful about accidentally introducing other code smells as a result of your refactoring. It is not sufficient to simply create and use a new Stroke class to represent those four fields. You should aim to write “good” code and avoid the code smells we’ve discussed in class, particularly as they relate to how those four fields are used in GameView.




As above, since this is a big change that affects lots of code, be sure that the app still runs correctly before going to the next step.







<h2>Step 5. Extract a Segments class</h2>

The GameView class also has an ArrayList of Point arrays called <em>segments </em>representing all of the line segments that the user has drawn so far (each Point array contains the start and end Points of the segments).




This ArrayList is used in various methods in GameView, but is also used in the menu handler method (<em>onOptionItemSelected</em>) in GameActivity.




First, in cell C17 of your refactoring spreadsheet, identify the code smell exhibited by GameActivity with respect to the way it uses GameView’s <em>segments</em> ArrayList.




Then, use the “Extract Class” refactoring pattern to create a Segments class that represents the line segments that the user has drawn. Instead of using an ArrayList of Point arrays to represent the line segments, create a LineSegment class that holds the start- and endpoints of the line segment, or use the android.graphics.Path class.




Modify GameView and GameActivity to use this new class, and create new methods in the Segments class as necessary. As in Step 4, do not assume that creating a Segments class and getting your code to compile is sufficient for this part of the assignment! You need to ensure that other classes use it in a “good” way, avoiding the code smells we discussed in class. This may include adding methods besides just getters and setters (<em>hint, hint!</em>).







<h2>Step 6. Create “distance” method</h2>

There are numerous places throughout the code where the distance between two Points is calculated.




Extract a static method called “distance” that takes two Points and returns a double representing the Euclidean distance between them.




It is up to you to decide which class should host this method; in your refactoring spreadsheet, update the row for Step 6 to indicate which class holds this method, and then justify your decision.




Then, update cells C22-27 and indicate all of the places in your code where you invoke the “distance” method. Please use the line numbers from your final code submission.







<strong>Step 7. Extract method to detect circuit – and fix it! </strong>

The <em>onDraw</em> method in GameView contains a chunk of code that is used to determine whether the line segments the user has created form a circuit. It does this by checking that each Point appears in exactly two line segments (or, in graph-speak, that each vertex/node has an order of two).




First, move this code into the Segments class you created in Step 5 so that it can determine for itself whether its line segments form a circuit.




You may have already done this as part of Step 5. Great! So you’re done, right? Not so fast…




Unfortunately, there is a bug in this implementation. It is “necessary” for each Point to be involved in two lines in order to form a circuit, but it is not “sufficient.” For instance, in the example below, the user has formed two smaller circuits, and the program has not pointed out that this is incorrect. That is, the program should warn the user that they have not actually formed a single circuit including all points in the map.










Fix this bug so that the method only indicates that a circuit has been formed only if there is a <strong>single</strong> circuit that contains all points.




<em>Note: </em>as mentioned in class, ordinarily refactoring does <em>not</em> include bug-fixing, but since there’s a known bug here, you may as well fix it while you’re at it. =)




In your refactoring spreadsheet, update the row for Step 7 and indicate the line number in the Segments class where this method can be found. Then, indicate whether you were able to fix the bug (be honest!).







<h2>Step 8. Analyze the GameView class</h2>

Now that you’re done with the refactoring, the GameView class has changed quite a bit! Using the “internal quality” metrics discussed in class, describe in your refactoring spreadsheet one way in which the GameView class (or a method within it) has become <strong>better</strong>, and one way in which it has become <strong>worse</strong>.




For each (“better” and “worse”), specify the metric that you are using, the value of that metric in the original code that you downloaded, and the value of that metric after doing the refactoring.







<h1>Deliverables</h1>

You should submit a single .zip file containing the following.




<h2>1. Modified code</h2>

Submit the <em>entire</em> Android Studio project containing your refactored code, as well as all of the other subdirectories in the project (i.e., not just the .java files you refactored, but <em>everything</em> in the project). Please do not submit the original code.

<strong> </strong>

<h2>2. Refactoring spreadsheet</h2>

Also submit the completed spreadsheet (which was part of the Android Studio project that you downloaded) that answers each of the questions in Column B. Write all of your answers in Column C.








