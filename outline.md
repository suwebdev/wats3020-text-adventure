# The Text Adventure Program

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

In order to understand how this program works, it helps to consider both a functional outline of the program and the structure of the `storyData` variable, which contains all of the actual story information.

## Functional Outline of the Text Adventure

This program relies on a series of functions to make it work. The program starts by running the `updatePage()` function. The `updatePage()` function changes the text of elements in the DOM to reflect the content of the starting page of the story. In addition, it runs the `addEventListeners()` function, which adds `click` event listeners to each choice item on the page. When clicked, the link will run the `changePage()` function to move the story forward.

In addition to running the `updatePage()` function, the program also adds a `click` event listener to the "Undo last choice" `<p>` element at the bottom of the page. When clicked, this runs the `undoChoice()` function.

Every time the user selects one of the choices presented, the program runs the `changePage()` function. This function does multiple things. It records the user's choice using the `recordChoice()` function and then runs the `updatePage()` function to reset the content of the DOM.

## The structure of the `storyData` variable
The `storyData` variable featured in this assignment has a structure that is helpful to understand before you set to work on this assignment. It is a JavaScript Object that contains a number of JS Objects corresponding to different "pages" in an adventure story. Each page has a unique key, or _slug_, that is used to reference it.

Each page in the story follows the following format:
```JavaScript
    {
        // text is what is displayed to the user when they go to this page in the story.
        text: `Story text.`,
        // choices is an array of options that the user may select.
        choices: [
            {
                // each individual choice has two properties:
                // the text that is shown to the user
                text: `Choice #1.`,
                // and the KEY for the page that this choice leads to.
                link: 'page74'
            }, {
                text: `Choice #2.`,
                link: 'page17'
            }
        ]
    }
```

The `storyData` object also contains one additional property: `title`, the story's title which is displayed on the page.

