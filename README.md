author: Maxime LUMEAU, Robin CAROFF and Pierre TIBULLE
summary: Kotlin Multiplatform Workshop
id: codelab-kotlin-Multiplatform
categories: codelab,kotlin
environments: Web
status: Published
feedback link: https://github.com/RobinCaroff/workshop-kmp
analytics account: ???

# Workshop Kotlin Multiplatform

## CodeLab Overview
Duration: 0:02:00

Sharing Kotlin code between iOS and Android 

In this codelab we will create an iOS and Android application, by making use of Kotlin's code sharing features. 
For Android we'll be using Kotlin/JVM, while for iOS it will be Kotlin/Native.

This codelab will show you the ability to share code within Kotlin and the benefits it provides. While what we'll be looking at is a simplified application, what is shown here can be applied to real world applications, independent of their size or complexity.

You will learn how to:

* Create an Android app with Android Studio
* Create a shared Kotlin library
  - Use it from Android app
  - Start the Android application
* Create an iOS app with Xcode
  - Use the shared Kotlin library from iOS app
  - Use Kotlin from Swift
  - Start the iOS application
* Improve the shared library
  - Use Coroutines to validate the asynchronous ability
  - Use the multiplatform Http client Ktor to call a Json Api 
  
The application we're going to create will <TODO>.

**Resources:** 
* This codelab is inspired by the Jetbrains tutorial : https://kotlinlang.org/docs/tutorials/native/mpp-ios-android.html

<TODO tout le reste !!!>

## Environment Setup
Duration: 0:04:00

In order to create a CodeLab you need *Go* and *claat* (the codelabs command line tool) installed.

The instructions below are what worked for me on Mac, but you can also find instructions [here](https://github.com/googlecodelabs/tools/tree/master/claat) 

#### Install Go & claat
``` bash
$ brew install go
$ go get -u -v -x github.com/googlecodelabs/tools/claat
```

#### Setup Environment Variables
``` bash
$ export GOPATH=$HOME/Go
$ export GOROOT=/usr/local/opt/go/libexec
$ export PATH=$PATH:$GOPATH/bin
$ export PATH=$PATH:$GOROOT/bin
```

You should now have the *claat* command available to you. 
``` bash
$ claat
```

## Create your initial CodeLab
Duration: 0:05:00

Now that we have the environment setup let's go ahead and create a markdown file where we'll create the actual codelab. 

``` bash
$ vim codelab.md
```


#### Fill-in the header metadata
Copy and paste the headers below into your markdown file and change the values appropriately. 
Guidelines are available below the sample headers. 

``` bash
author: Author Name
summary: Summary of your codelab that is human readable
id: unique-codelab-identifier
categories: codelab,markdown
environments: Web
status: Published
feedback link: A link where users can go to provide feedback (Maybe the git repo)
analytics account: Google Analytics ID
```

Metadata consists of key-value pairs of the form "key: value". Keys cannot
contain colons, and separate metadata fields must be separated by blank lines.
At present, values must all be on one line. All metadata must come before the
title. Any arbitrary keys and values may be used; however, only the following
will be understood by the renderer:

* Summary: A human-readable summary of the codelab. Defaults to blank.
* Id: An identifier composed of lowercase letters ideally describing the
  content of the codelab. This field should be unique among
  codelabs.
* Categories: A comma-separated list of the topics the codelab covers.
* Environments: A list of environments the codelab should be discoverable in.
  Codelabs marked "Web" will be visible at the codelabs index. Codelabs marked
  "Kiosk" will only be available at codelabs kiosks, which have special
  equipment attached.
* Status: The publication status of the codelab. Valid values are:
  - Draft: Codelab is not finished.
  - Published: Codelab is finished and visible.
  - Deprecated: Codelab is considered stale and should not be widely advertised.
  - Hidden: Codelab is not shown in index.
* Feedback Link: A link to send users to if they wish to leave feedback on the
  codelab.
* Analytics Account: A Google Analytics ID to include with all codelab pages.

#### Add the Title
Next add your title using a single '#' character
```
# Title of codelab
```

#### Add Sections & Durations
Then for each section use Header 2 or '##' & specify an optional duration beneath for time remaining calculations
Optional section times will be used to automatically total & remaining tutorial times
In markdown I've found that the time is formatted hh:mm:ss

Example
``` bash
## Section 1
Duration: 0:10:00

## Section 2
Duration: 0:05:00
```

#### Add Section Content
Now that we have 2 sections to our titled codelab let's go ahead and add some content to each section. 
Make up your own or copy & paste the example below: 

Copy into section 1 (Below Duration and above Section 2):
```
### Info Boxes
Plain Text followed by green & yellow info boxes 

Negative
: This will appear in a yellow info box.

Positive
: This will appear in a green info box.

You created info boxes!

### Bullets
Plain Text followed by bullets
* Hello
* CodeLab
* World

You created bullets!
```

Copy into section 2 (Below Duration): 
```
### Add a Link
Let's add a link!
[Example of a Link](https://www.google.com)

### Add an Image
Let's add an image!
![image_caption](https://googlecloud.tips/img/031/codelabs.png)
```

See the "Markdown Syntax Backup" section for more examples of what can be done. 
More Markdown Parser examples can be found [here](https://github.com/googlecodelabs/tools/tree/master/claat/parser/md).

## Export & Serve
Duration: 0:02:00

Now that you have an initial codelab defined in your markdown file let's go ahead and generate the static site content. 
We can export & serve the content locally using the `claat` command that we installed earlier. 

``` bash
$ claat export codelab.md
$ claat serve
```

* Your browser should have opened (if it doesn't then try going to localhost:9090 in your browser). 
* Choose the directory that matches your "id" that you put in the headers. 
* Viola! You should have your first codelab!

## Host Your CodeLab
Duration: 0:01:00

When you ran the `claat export` command you created the static web content needed to host your codelab. 
It placed static web content in a directory specified by your unique "id" and you can view it locally by opening the index.html page. 

Negative
: Note that when you view it locally by opening index.html some of the graphics may not show up (such as access_time, Next, Back), but they work once online. 


Now that you have the static content you can host it however you want.
One option is pushing it to github and serving it up from Netlify.  

If you'd like to create your own landing page for codelabs, [like this one](https://codelabs.developers.google.com), there is a tool to do that as well! 
Check it out here: [CodeLabs Site](https://github.com/googlecodelabs/tools/blob/master/site/README.md)


## Markdown Syntax Backup
Duration: 0:00:00

``` Java
public static void main(String args[]){
  System.out.println("Hello World!");
  }
```

Adding an `inline code` snippet

Positive
: This will appear in a green info box.

Negative
: This will appear in a yellow info box.

 [Example of a Link](https://www.google.com)

Adding an image
![image_caption](https://s3-eu-west-1.amazonaws.com/released-artifacts-3.x/assets/tutorial_images/creating-styles/step1.png)

* List
* using 
* bullets

###

1. List
1. Using
1. Numbers

###

#### Embed an iframe
Negative
: Note that the content you embed must be whitelisted in the "IframeWhitelist" var [here](https://github.com/googlecodelabs/tools/blob/master/claat/types/node.go)
Currently whitelisted include content starting with google.com, google.dev, dartlang.org, web.dev, observablehq.com, repl.it & codepen.io

###
![https://codepen.io/tzoght/embed/yRNZaP](https://en.wikipedia.org/wiki/File:Example.jpg "Try Me Publisher")
