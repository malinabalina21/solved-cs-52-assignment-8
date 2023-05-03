Download Link: https://assignmentchef.com/product/solved-cs-52-assignment-8
<br>
<strong>Background:</strong>The purpose of this assignment is to practice dealing with exception handling.  Exception handling is a very important part of being an object-oriented programming.  Rather returning some kind of int return value every time you tickle an object, C++ programmers expect methods to focus on their task at hand.  If something bad happens, C++ programmers expect methods to throw exceptions.  When caught, exceptions can be processed.  When uncaught, they cause a program to terminate dead in its tracks.  The typical pattern in this course is to have class code throw exceptions and driver code catch them.  Because of exceptions, when writing client driver code, our try blocks will not be polluted with error processing statements.

<h3><strong>part_a: flashdrive 3.0 (exceptions)</strong></h3>

The purpose of this assignment is to work with exceptions.  As you may recall, I have provided you with a sample class named FlashDrive which has been diagrammed below.  You can acquire the source to the FlashDrive class by clicking <a href="http://www.smcclasses.net/courses/Spring08/CS52OnLine/units/FileManager/Demo_Source/FlashDriveDotNet.zip">here</a>.  I’d like you to enhance this class so that invoking its methods or operators potentially throw exceptions, rather than just printing error messages to cout.  Currently, our favorite exception class is std::logic_error.  You can create a logic_error by passing a string value to its constructor.  Officially, you should also say #include &lt;stdexcept&gt; to begin working with logic_error, but Visual Studio (being a badly behaved child…) let’s you get away without it.  Once you get it all working correctly, the driver code should run as described in class.

Although the sample driver code might not code for all these circumstances, I would like you to throw exceptions when:

<ul>

 <li>more stuff has been put onto the drive than it can safely hold (due to writeData)</li>

 <li>a negative number is potentially used as a my_StorageUsed value (due to operator – or bad values being sent to the constructor call)</li>

 <li>a negative number is potentially used as a my_StorageCapacity value (due to operator – or bad values being sent to the constructor call)</li>

</ul>

So carefully wind your way thru all the operators and methods of the class ensuring that logic_error gets thrown in each of these circumstances.

I’d also like you to get operator &lt;&lt; and operator &gt;&gt; working for the class FlashDrive.

<table border="1" width="98%" cellspacing="0" cellpadding="0">

 <tbody>

  <tr>

   <td width="38%">

    <table border="1" width="98%" cellspacing="0" cellpadding="0">

     <tbody>

      <tr>

       <td width="100%"><strong>FlashDrive</strong></td>

      </tr>

      <tr>

       <td width="100%">FlashDrive( );FlashDrive( int capacity, int used, bool pluggedIn );void plugIn( );void pullOut( );void writeData( int amount );void eraseData( int amount );void formatDrive( );int getCapacity( );void setCapacity( int amount );int getUsed( );void setUsed( int amount );bool isPluggedIn( );</td>

      </tr>

      <tr>

       <td width="100%">int my_StorageCapacity;int my_StorageUsed;bool my_IsPluggedIn;</td>

      </tr>

     </tbody>

    </table></td>

   <td width="100%">

    <table border="1" width="100%" cellspacing="0" cellpadding="0">

     <tbody>

      <tr>

       <td width="100%"><strong>Sample Driver Code</strong></td>

      </tr>

      <tr>

       <td width="100%">#include &lt;iostream&gt;#include “FlashDrive.h”void main( ){using namespace cs52;cs52::FlashDrive empty;cs52::FlashDrive drive1( 10, 0, false );cs52::FlashDrive drive2( 20, 0, false );drive1.plugIn( );drive1.formatDrive( );drive1.writeData( 5 );drive1.pullOut( );drive2.plugIn( );drive2.formatDrive( );drive2.writeData( 1 );drive2.pullOut( );// read in a FlashDrive…// the class designer for FlashDrive (that’s you!)// gets to decide which fields matter and should be read incs52::FlashDrive sample;cin &gt;&gt; sample;// print out a FlashDrive…// the class designer for FlashDrive (that’s you!)// gets to decide which fields matter and should be printedcout &lt;&lt; sample &lt;&lt; endl;cs52::FlashDrive combined = drive1 + drive2;cout &lt;&lt; “this drive’s filled to ” &lt;&lt; combined.getUsed( ) &lt;&lt; endl;cs52::FlashDrive other = combined – drive1;cout &lt;&lt; “the other cup’s filled to ” &lt;&lt; other.getUsed( ) &lt;&lt; endl;if (combined &gt; other) {cout &lt;&lt; “looks like combined is bigger…” &lt;&lt; endl;}else {cout &lt;&lt; “looks like other is bigger…” &lt;&lt; endl;}if (drive2 &gt; other) {cout &lt;&lt; “looks like drive2 is bigger…” &lt;&lt; endl;}else {cout &lt;&lt; “looks like other is bigger…” &lt;&lt; endl;}if (drive2 &lt; drive1) {cout &lt;&lt; “looks like drive2 is smaller…” &lt;&lt; endl;}else {cout &lt;&lt; “looks like drive1 is smaller…” &lt;&lt; endl;}// let’s throw some exceptions…try {empty = empty – combined;cout &lt;&lt; “something not right here…” &lt;&lt; endl;} catch( std::logic_error ) {// an exception should get thrown…// so the lines of code here should// be run, not the cout statement…}try {drive2.writeData( 10000 );cout &lt;&lt; “something not right here…” &lt;&lt; endl;} catch( std::logic_error ) {// an exception should get thrown…// so the lines of code here should// be run, not the cout statement…}try {cs52::FlashDrive f( -1, -1, false );cout &lt;&lt; “something not right here…” &lt;&lt; endl;} catch( std::logic_error ) {// an exception should get thrown…// so the lines of code here should// be run, not the cout statement…}}</td>

      </tr>

     </tbody>

    </table></td>

  </tr>

 </tbody>

</table>




<table border="1" width="29%" cellspacing="0" cellpadding="0">

 <tbody>

  <tr>

   <td width="15%"><img decoding="async" width="105" height="72" data-recalc-dims="1" data-src="https://i0.wp.com/www.howardstahl.com/cs52/flash1.jpg?resize=105%2C72" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

    <noscript>

     <img decoding="async" src="https://i0.wp.com/www.howardstahl.com/cs52/flash1.jpg?resize=105%2C72" width="105" height="72" data-recalc-dims="1">

    </noscript></td>

   <td width="11%"><img decoding="async" width="87" height="100" data-recalc-dims="1" data-src="https://i0.wp.com/www.howardstahl.com/cs52/flash2.jpg?resize=87%2C100" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

    <noscript>

     <img decoding="async" src="https://i0.wp.com/www.howardstahl.com/cs52/flash2.jpg?resize=87%2C100" width="87" height="100" data-recalc-dims="1">

    </noscript></td>

  </tr>

 </tbody>

</table>

<h3><strong>Overall</strong></h3>

<ul>

 <li>Your submission should follow this organization:

  <ul>

   <li>part_a

    <ul>

     <li>main.cpp</li>

     <li>flashdrive_3_0.h</li>

     <li>flashdrive_3_0.cpp</li>

    </ul></li>

  </ul></li>

</ul>