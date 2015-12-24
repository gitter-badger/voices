# Core Features

* __general__
    * toggle listening
    * also allow other programs to communicate with it (for example setting global variables from another program)
    * auto start with operation system
    * about dialog

* __profiles__
    * general description (name, author, link to website, license)
    * each __profile__ consists of one or more __macros__
    * auto-activate them if the bound application is active
    * __IMPORTANT:__ Each profile needs an grammar file or a language model file!!!
    	* let the user either write his own grammar or let him enter sentences for the language model that will be created (first impl should only accept grammar files for easier usage and testing)
    	* --> we need to expand the dictionary for new words (like e.g. direshift in hearthstone)
    
* __macros__
    * general description (name, description)
    * each __macro__ consists of several __actions__
    * __macros__ can have multiple triggers (several voice commands)
        * example would be the usage of the hero power: 'use hero power', 'fireblast', 'armor up' etc
          the problem is that there is not an easy and clean way for doing this (well I didn't come up with one)
        * allow more natural way of using commands:
            * __'use card 1'__ is the same as __'card 1'__
            * __'and target enemy hero'__ is the same as __'on enemy hero'__
    * __macros__ can have varialbe triggers (I think this one is really really hard to do)
        * let users define a kind of template ('move my plants from %x to %y')
        * in hearthstone context this can be used to mulligan:
            * __'keep card 1, 2 and 4'__
            * __'reroll card 3'__
            * __'keep card 1'__
            * template would then be __'keep card (%pos | and %pos)+'__
                * I think that implementing this can be really difficult due to the immense combinations that are possible...
    * __macros__ can run __actions__ either in order as they are present or start background tasks (like services?) and then continue executing (don't really know if that is actually a good idea lol)
    * __macros__ can be triggered by using a shortcut that is assigned to them
    * __macros__ that can run as a background task (for example scanning the log file of hearthstone)
        * maybe use sort of a schedule system here
    
* __action__
    * defines __one__ procedure (like mouse movement and/or click, typing simulation, breaks etc...)

 ## Basic Action Ideas
  * mouse movement/clicks (direct movement by setting mouse location and smooth movement (emulating human movement), back to original position)
  * speech to text (for example messaging friends in hearthstone)
  * text to speech (can be used as responses)
  * dialogs (don't know if that is actually useful)
  * logical code execution (I think Javascript would be nice here...)
    * if else statements
    * loops
    * global variables (like screen width/height)
    * provide some basic functions (getpixelat, callmacro...)
    * make it user friendly too!
  * call other macros by name or unique id (increasing number: 'callmacro(12)')
  * play sound from file
  * execute other programs and wait for execution or continue while they execute (aka background task)
  * record mouse movement

---
# Expansions

* __update framework__
    * auto update application (maybe with json/xml file stored on github)
    * rather small framework, might aswell be extracted into own project