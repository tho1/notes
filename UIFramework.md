Looking at User interfaces via the rear view mirror.

## Ancestor of UI framework
What about other UI frameworks that had been in use for a long time?

Many would consider the UI came from the Xerox. That is where the idea of graphical user interface is being born.  One would perform actions like click a button, open another window for the application to work. 

[X windows] (https://en.wikipedia.org/wiki/X_Window_System)  is one of the precursor of the graphics system, and it set the standard for most applications.  Widgets, button, drop down boxes, slider and many more.  

There had been multiple widget [frameworks] (https://en.wikipedia.org/wiki/List_of_widget_toolkits), built on top of this idea. They are all based on the ideas of a windows system. 

## The other approach

One would consider the game libraries would be another approach to present user interface.  They are built catered to the particular use case scearnio games.  They had a different set of requirement, as they don't follow the windows system.
End user of games expected fast graphics updates, and different control to interact with the environment. E.g. keyboard and mouse vs Joystick.

Therefore,  the game developer usually need to build the rendering engine from scratch to cater to the user requirement.

Games build in lates 1980 would not use a game engine, as the hardware could not handle the game engine requirement.  Game developers would resort to writing games in assembly language code, and use many graphics technique to make the raster graphics look fast.  An example would be compiled bitmap.

The rise of graphics card had given the freedom to create video games with realistic graphics with shader technology and many others. This also give rise to new graphics framework like DirectX, Apple Metal, and many others. 

Nowadays the course of building a video games had become a costly endeavour, game developer would use existing game engines to build their games on top of frameworks.  Primary examples would be [Unity] (https://en.wikipedia.org/wiki/Unity_%28game_engine%29) , [Unreal Game Engines] (https://en.wikipedia.org/wiki/Unreal_Engine) ,and many others.

The graphics card itself has its root as a math coprocessor where the system needs a way to draw a lot of rectangles, and it gives rise to new set of video games with outstanding graphics reality.  And it also come full circle as graphics card also provide the ability to do computation intensive tasks.  Concept like [SIMD Single instructions mutiple data] (https://en.wikipedia.org/wiki/SIMD) comes to mind.  And a primary example is the [CUDA] ( https://en.wikipedia.org/wiki/CUDA) framework. 

## The third approach

The other approach is the text based interfaces.  Before the rise of GUI environment, end users interacted with the computer by typing command lines with option to execute functions.

Some prefer the text based environment because of the following advantage.

1. Greater control and customization of the application
2. The application usually run faster as there is no overhead with graphics environment
3. The ability to automate the sequence of commands via shell scripts and many other tools.

However, text based environment had disadvantages too.

1. End user had to remember arcane set of commands to perform a function. e.g. Text editor VI had different keystrokes to perform task.
2. They usually had a high learning curve, as the commands are derived from the end user's memory, instead presenting to a user as a set of dialog boxes or other helper system.

There had been many attempt to merge both systems together.



## The web approach
UI framework had been fascinating. Due to the proliferation of the web, lots of desktop applications had been migrated to the using HTML technology plus CSS, SASS, Javascript and many technologies.  

Some of us who had been around for awhile remember the HTML pages build had the flashing text and falling snow in the background.  This reminds of <blink> html tag that had been made obsolete.  With the rise of html5 and the use of canvas tag, more interesting applications had been doable in HTML5.  

## Transition of Desktop application to Web based application
A fine example is the Winamp desktop audio player that is first release in 1997.  Doing this in a webpage back in late 1990 is not possible.  Then we have the <audio> tag that becomes available to play audio file within a browser.  And lately the github user Jordan Eldredge reimplmented the winamp look and feels using HTML5 and javascript.  See [webamp] (https://github.com/captbaritone/webamp). 


[Frontend Developments in 2020] ( https://medium.com/dailyjs/a-realworld-comparison-of-front-end-frameworks-2020-4e50655fe4c1)


Understanding the basics of UI framework. 
[GET or POST? 11 interview questions that most devs get wrong.] (https://medium.com/javascript-in-plain-english/get-vs-post-are-you-confident-about-the-differences-189562fac0a7)
