# SFMLTips
## Small Little Game Tips For SFML Game Dev
SFML brings many things onto the table, and it is very important to be able to organize your projects for readability and usage

### 1. Assets
Assets are basically a bunch of external data, images, fonts, music or any other files needed to be loaded in from non-internal or static sources. They're basically resources you use in your project to make it look pretty or have specific functionality. These assets can get tricky and unreadable very fast especially when using only SFML built-in functionality. These types of resources usually should only be loaded in once as they serve as pixel or sound templates that can be cast on existing objects via pointers. Creating for example an sf::Font for every single sf::Text object is a crime. It's best to deal with Asset types or external resources like this by just loading them in, in for example a seperate namespace which can hold all the single use objects. This also enables the usage of multiple layered namespace names for further need of grouping up the resources.

//code

We come to a problem though. Creating SFML objects of for example sf::Font isnt enough. We need to load these fonts or textures in from specific file names. We can do this by using the build in loadFromFile() SFML function, but unfortunately it's usage isn't included in the class's constructor. Creating our own little class for this specific usage fixes this problem.

//>> code

With the above code we can now create texturex, fonts and all sorts of different resources and create them in one line in one fell swoop.

>> code

### 3. Texts
Some SFML classes require many starting value properties to be set before they can fully be functional in the program. One of such examples is the sf::Text class. It in inself requires a font to be loaded, character size to be set as well as a string for the actual text to be visible. Every other option is a non-necessity (color, position, outlines etc.). These multiple starting values usually create blocks of code for single object parameter setting which isn't ideal nor readable. We can create our own class to fight this, and make it inherit all its aspects from sf::Text class for the same functionality. The only difference here would be that we will add specific constructors that will benefit us. One constructor for example that would require all the parameters we would want the object to have, enabling the creation of such objects be done in a single line. This form of program making will be benefitial for custom SFML programs as it creates the change of higher control over the code you're making. One can also use the aformentioned Assets to quickly and smoothly set text fonts without much hassle.

//code


### 4. Buttons
Buttons are in their base form a shape which can be pressed with either an image or text slapped on top of it. Creating a class that would engulf this idea is a must in any GUI or graphical application.

### 5. Input Fields


### 2. Screens
SFML introdus a nice way of creating and drawing graphical applications. It accomplishes this with a window class/object as well as a specific main function:
//Code

The above main function provides all the necessary information needed to draw a window.
The main function can be divided into four main parts:
1. Creation of needed objects used in the project (before while loop)
2. Event loop for single triggers
3. Loop code which should be done in every while loop iteration
4. drawing of objects onto window
With projects of any type, quickly ammasing many internal variables, structures, classes and functions, maintaining such a huge main function would be disastrous. Thats why dividing and organising the code up into pieces is the right call to make. The way to this is simple with the following trick. Let's assume a project will have three main parts of the application. A form of starting point, middle point with the main purpose of the function, and an ending point which will leave the application in some way or form. We can call these points "screens" from now on. Let's create a class for each of these screens and in those classes implement an empty constructor, events, loop and draw functions that are needed for each of the main functions core parts. Let's also add a variable that will define if the screen is active or not to be able to somehow maintain sanity in the multiple possible screen classes. Active value will be true when the screen should be active, drawn, and all events and loop code used, whereas the constructor will define starting parameters for each of the objects defined in the class. Any and all objects defined in these classes are objects that should be related to the screen it's on. We wouldn't want to add the title of the program onto the ending screen nor would we want a game to be played when on starting screen.


