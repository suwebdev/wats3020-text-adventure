# WATS 3020 Text Adventure

In this project, you will be asked to create a simple text adventure game that
allows a user to make choices that influence the outcome. To accomplish this
goal, you will use functions that can execute whenever an Event is triggered.
(Note: You will not be required to create the Events.)

Here is the interaction that we're going for:

1. User arrives on page, sees first page of story.
2. User selects a choice.
3. User sees the next page based on their choice.
4. User continues to make choices on each page until they reach an ending to the story.

This fits the typical "choose-your-own-adventure" template, so if you're
familiar with those kinds of stories, then you should be able to imagine what
this will look like.

## Basic Requirements
In order to complete this project successfully, you will need to fulfill these
requirements:

* Add a function to prompt the user for a character name.
* Add a function to retreive the next chunk of text.
* Add a function to "undo" choices the player has made.
* Add a function to restart the game.


## Stretch Goals
If this project is too easy, attempt these stretch goals to make it more
challenging.


* Enhance the project with an original story, or a more ambitious story, or one that explores allowing for more than two choices. (You might consult some resources like ["How to Write Your Own Choose Your Own Adventure Story"](http://blog.karenwoodward.org/2014/06/how-to-write-choose-your-own-adventure.html) by Karen Woodward, or ["Designing Branching Narratives"](https://thestoryelement.wordpress.com/2015/02/11/designing-branching-narrative/) by Paul Nelson.)
* In your new story you could add additional characters that the User could name. Write functions to prompt the user for those names and then manage their insertion into the text in appropriate places.
* **ADVANCED:** Log the time started so that you can provide a "total time played" update on each page (you will need to edit the `updatePage()` function to add this output). (Look into the JS [`Date` object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) to make that happen.)
* **ADVANCED:** Enhance the `storyData` object to use a property called `timeLimit` on pages: If there is a `timeLimit` for a page, then edit the `updatePage()` function to use a `setTimeout` command that will send the user to a failure page if they don't make a choice within the allotted time.