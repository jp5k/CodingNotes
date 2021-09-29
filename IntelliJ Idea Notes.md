# IntelliJ Idea Notes

## Main shortcuts
* Ctl + Alt + L  = format code
* Ctl + Alt + O  = remove unused imports
* Ctl + E  = extremely useful, recent files and also Terminal etc
* Alt + F7 find usages across project 
* Just use the Ctl key pressed, whilst pointing to a class/method/variable to see where it is defined.  
* Run application = Alt + Shift + F10
* Iter = template for iterating over a collection (NOTE, similar itXX templates exist)



## Core IDE tools
* Help gives all shortcuts
* Double shift to search all
* Save file as scratch file for notes etc.  Can then search for scratches and delete them later.
* Preferences, increase decrease font size can bind to mouse wheel.
* Search intellij plugins for markdown source, eg markdown navigator.
* Preferences - project structure to set up module dependencies i.e libs needed in project.
* Can set up an artifact so that the project builds a .jar file.  Can also set up run cofiguration to run from the .jar file. 
* Can analyse code from the menu.

## Code navigation and generation
* DOUBLE SHIFT to search everywhere. V.useful. Also for commands, eg open terminal.Build project.
* Ctl + N for going to class directly.
* Ctl + E for open recent files and windows.  V.useful.
* Ctl + B to find parent method etc... when clicking on method.
* Ctl + shift + l for peek definition of class.
* Ctl F12 shows members within measuring tape - very useful one.
• Alt + F1 to open a class within a particular project window.
* Ctl+H to see class hierarchy.
* There is a shortcut key for constructor generation,
* Ctl + alt + T  to get surround code, e.g for loop, do loop, try catch etc..

## Code Inspections and Intentions
* Code inspections are code analysis rules.
* Ctl + s for code inspection.
* Alt + enter to show all intention suggestions.
* Ctl + shift + a  to type in suggestions.  Can type in 'inspect code' to inspect all code.
* Alt + enter also for suggestions.
* Note suggestions and intentions very similar.

## Refactoring
* Ctl + shift + alt + t  for refactoring options.
* If method has 4 or more params, then sensible to extract as param list. Ide does this all for you.
* Can move methods to a different class.
* Can extract interfaces.
* Can replace constructor with a factory method, create measuring tape rather than measuringtape constructor.
* Can safely decouple using delegation rather than inheritance in refactoring methods.

## IntelliJ live templates
* Boiler plate code out of the box.
* They are contextually aware.
* Fori tab gives for loop.
* Ctl + J for list of live templates.
* Sout for println
* Psvm  for main method
* Psf for public static final method
* Highlight code , ctl + alt + t to give refactoring, surround with try catch for example.
* Can create your own live templates within the ide, eg public method with variables etc...

## Debugging
* Run to cursor icon will go to next breakpoint.
* Right click variable, add to watches to constantly display variable value. 
* Can evaluate expressions, there is a shortcut key on debug window for this.  Takes scope of variables into account.
* List of breakpoints will be available in 'favourites' window.

## Git
* VCS version control system menu
* Good plugin for intellij called .ignore, which provides .git ignore files.
* Version control log gives the git commands which are issued in the gui.
* Log in vcs window shows history etc.. of commits.
* Right click on file to get context menu, then do a add to git ignore option to auto add file to git ignore.
* Very good merge editor too by using the IDE.
* Github integration also catered for.

## Junit
* New 'test' directory.  Mark the test directory as test sources root.
* Can right click on a class name and generate test methods directly from the class.
* Can 'share' test config in menu properties so that tests from different modules can all be run at the same time.
* Can run code coverage when running tests, or even when calling main method. 

## Maven
* Create a simple architype, will create .pom file etc for you. Very useful for getting Spring projects set up correctly off the bat.
* Maven tool window gives you all the maven plug in goals. 


## Tips and Tricks
* Ctl + W to get an incrementally larger selection of code.
* Once selected, ctl + shif + down will move block of code up and down.
* Shift + ctl + a for colour picker for css.
* CTL + ALT + L   V.IMPORTANT for Formatting Code.
* Can chose the scope to carry out code analysis.
* Menu allows you to remove duplicates in your code.
* Ctl + P for parameter info into a method. 
* Productivity guide allows you to see which commands you are using the most.  

