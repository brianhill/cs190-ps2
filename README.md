# CS 190 Problem Set #2&mdash;Accepting Keyboard Input and Canonicalizing Registers

In this problem set, in Parts 1 and 2, you will complete the part of the keyboard that enters digits. This is done with Xcode's storyboard editor.

In Part 3, you will complete the code that canonicalizes register C from whatever is currently in register A and B. Together these things put us well on our way to taking keyboard input, which will be the subject of Problem Set #3.

Course Home Page: http://physics.stmarys-ca.edu/classes/CS190_S16/index.html.

My St. Mary's Home Page: http://physics.stmarys-ca.edu/lecturers/brianrhill/index.html.

New due date: Before the beginning of class, Thursday, February 25th, 2016.

## Reading that is Related to this Week's Lectures or this Problem Set

* iOS Technology (The View Heirarchy and View Controllers):
 * https://developer.apple.com/library/ios/documentation/WindowsViews/Conceptual/ViewPG_iPhoneOS/Introduction/Introduction.html
 * https://developer.apple.com/library/prerelease/ios/featuredarticles/ViewControllerPGforiPhoneOS/ (this document is pretty jargon-heavy&mdash;maybe just read the section titled "View Management")
* iOS Technology (Creating an Outlet Connection):
 * https://developer.apple.com/library/ios/recipes/xcode_help-IB_connections/chapters/CreatingOutlet.html (Unfortunately the code examples in this document are Objective-C)
* More Advanced iOS Technology (very specific technology I used to make the display flicker&mdash;only read if you have a particular interest in animations):
 * https://developer.apple.com/library/ios/documentation/QuartzCore/Reference/CADisplayLink_ClassRef/index.html.
* Good Software Engineering Practices:
 * See PS #1's version control references and learn about merges and rebasing.
 * Unit testing with XCTest: https://developer.apple.com/library/prerelease/ios/documentation/DeveloperTools/Conceptual/testing_with_xcode/chapters/04-writing_tests.html (yes, this is about a specific Apple technology, but analogous unit testing support found on every decent platform).
* Computer Science (Chapters on Functions, Structs and Enums in the Swift language):
 * https://itunes.apple.com/us/book/the-swift-programming-language/id881256329.

## Directions Specific to this Problem Set

1. (2 pts) The keyboard is incomplete. Add the nine missing buttons. Make sure they align nicely with the buttons that are already present and that the view constraints do not generate warnings, and work reasonably (in portrait mode only because there isn't nearly enough space in landscape mode for this layout).

2. (3 pts) Connect the new buttons up using the target-action method defined on the view controller. You can check your work by setting a breakpoint in the debugger and making sure that it is hit each time you press a button. Make sure that the action is sent on Touch Down rather than the default (Touch Up Inside). We're doing that so the calculator feels more authentic.

3. (5 pts) In this part, you will implement the function canonicalize() in the class CPUState. To do this part, you will have to read and understand the way the calculator holds data in Registers A, B and C. The relevant references for this are in the comments in the code. You can QA your work by running the unit tests in CPUStateTests.swift. Perhaps the very first thing to do before doing any coding is to run the unit tests and see what fails. When you are done all the tests should pass. If you are overwhelmed getting all the test cases to pass, a way to cut back would be to focus on getting the cases with positive exponentials to pass.

If you want to see someone else's sofware version of the HP-35, try the HP-35 emulation here:

http://home.citycable.ch/pierrefleur/HP-Classic/HP-Classic.html

That is an emulation, not a simulation. As a result, it is extremely faithful to an actual HP-35! In fact, the first HP-35's sold had some bugs that became famous and the above emulation even reproduces the bugs.

## Rebasing

In class we covered rebasing on Thursday. If you haven't really gotten the hang of it yet, below is a cookbook-y rebase session
that might work depending on what changes you have made.

The first part, you only need to do this once per repo, not once per rebase. The first part is just to add my repo as the upstream remote:

    $ cd ~/Classwork/cs190-ps2/
    $ git remote add upstream http://github.com/brianhill/cs190-ps2.git
    $ git fetch upstream 
    From ....
    * new branch      master     -> upstream/master

Before going further, make sure that all the changes you intend to keep are committed. Any other changes that you don't want should be discarded. A way of discarding changes is to use the git checkout command. Be careful it discards work without asking "are you sure."

Now you merge in upstream changes (note that this can get a load more complicated if there are merge conflicts between your changes and the upstream changes&mdash;I'm arranging for you _not_ to experience that complexity yet by having you only modify Main.storyboard whilst I have been taking special care in the last couple of days not to have modified Main.storyboard, but pretty soon, you'll run into and have to deal with merge conflicts):

    $ git rebase upstream/master
    HEAD is now at ....
    $ git push origin master

Assuming you successfully rebased your local repo, the last step pushes the rebased state to _your_ fork at GitHub.

Under some circumstances, because rebasing rewrites history, you might need to force the last step by doing:

    $ git push -f origin master

## General Directions for all Problem Sets

1. Fork this repository to create a repository in your own Github account. Then clone your fork to whatever machine you are working on. More detailed directions for this step were given in the README for Problem Set #1: https://github.com/brianhill/cs190-ps1.

2. These problem sets are created with the latest version of Xcode and Mac OS X: XCode 7.2.1 and OS X 10.11.3. Do not run beta versions of Apple's software. During the term, we might move to Xcode 7.3, depending on Apple's release schedule, the value we perceive in 7.3, and how much burden upgrading would put on IT. Currently Xcode 7.3 is in its third beta and the release notes issues list is pretty long.

3. Under no circumstances copy-and-paste any part of a solution from another student in the class. Also, under no circumstances ask outsiders on Stack Exchange or other programmers' forums to help you create your solution. It is however fine&mdash;especially when you are truly stuck&mdash;to ask others to help you with your solution, provided you do all of the typing. They should only be looking over your shoulder and commenting. It is of course also fine to peruse StackExchange and whatever other resources you find helfpul.

4. Your solution should be clean and exhibit good style. At minimum, Xcode should not flag warnings of any kind. Your style should match Apple's as shown by their examples and declarations. Use the same indentation and spacing around operators as Apple uses. Use their capitalization conventions. Use parts of speech and grammatical number the same way as Apple does.  Use descriptive names for variables. Avoid acronyms or abbreviations. In the Xcode preferences pane, set a page guide at Column 120 and don't exceed it. (I notice though that Apple is now exceeding 120 character. As an example, take a look at AppDelegate.swift which is created by Xcode from a template. Maybe it's time to scrap the 120 character limit and rely 100% on soft wrapping?!?) I am still coming up to speed on good Swift style. When there appears to be conflict, copy Apple's style, not mine.

5. When completed, before the class the problem set is due, commit your changes to your fork of the repository. More detailed directions for this step were also given in the README for Problem Set #1. I should be able to simply clone your fork, build it and execute it in my environment without encountering any warnings, adding any dependencies or making any modifications.

###### _The contents of this repository are licensed under the_ [Creative Commons Attribution-ShareAlike License](http://creativecommons.org/licenses/by-sa/3.0/)
