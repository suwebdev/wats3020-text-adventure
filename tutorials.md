# Tutorials for WATS 3020 Text Adventure
There are five basic requirements for this assignment that must be complete:
1. Add a function to get the current page.
2. Add a function that records the user's choice.
3. Add a function that will undo the last choice.
4. Add a function to update the text in the DOM.
5. Add a function that advances to the next page.

## Add a function to get the current page.
In this part of the assignment, we must create a function called `getCurrentPage()`. This function will accept a single parameter, a _slug_ that is a reference or key to another page in the story data. This function will fetch the page corresponding to that _slug_ and return that page.
1. Define the function and its parameters.
    ```JavaScript
    function getCurrentPage(pageSlug) {
        // function code goes here
    }
    ```
2. Get the page of the story corresponding to the _slug_.
    ```JavaScript
    let newPage = storyData[pageSlug];
    ```
3. Return the story page as the return value.
    ```JavaScript
    return newPage;
    ```
### Notes
1. Steps 2 + 3 could be combined, eliminating the need for declaring a new variable.
    ```JavaScript
    return storyData[pageSlug];
    ```
2. If the slug passed to the function is invalid, this function will not detect the error and will instead return _undefined_. As a STRETCH goal, consider adding code to check if there is valid _page_ data for the _slug_ provided.

## Add a function that records the user's choice.
In this part of the assignment, we must create a function called `recordChoice()` that will accept a single parameter, a _slug_, and add it to the `choiceList` array. The most straightforward method to do this would be to use the [array `push()` method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push).
1. Define the function and its parameters.
    ```JavaScript
    function recordChoice(pageSlug) {
        // function code goes here
    }
    ```
2. Add the new _slug_ data to the array using the [array `push()` method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push).
    ```JavaScript
    choiceList.push(pageSlug);
    ```
## Add a function that will undo the last choice.
In this part of the assignment, we must create a function called `undoChoice()` that will remove the last _slug_ in the `choiceList` array and return the new last _slug_ in the array. This function is called by the `click` event listener added to the "Undo last choice" text at the bottom of the page.
1. Define the function and its parameters.
    ```JavaScript
    function undoChoice() {
        // function code goes here
    }
2. Remove the last item in the `choiceList` array using the [array `pop()` method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop).
    ```JavaScript
    choiceList.pop();
    ```
3. Return the last element of the array.
    ```JavaScript
    return choiceList[choiceList.length-1];
    ```
### Notes
1. If the `choiceList` array has 1 or fewer elements, this function will not detect the error and will instead return _undefined_. As a STRETCH goal, consider adding code to prevent this case.

## Add a function to update the text in the DOM.
In this part of the assignment, we must accomplish two tasks. First, we must create two variables that we will use to reference the DOM elements that correspond to the page text and the list of choices, both of which will be updated every time the page changes. Second, we must create a function called `updatePage()` that accepts a _page_ as a parameter and updates the DOM to correspond to that page. Once that is done, it should run the function `addEventListeners()` to add `click` listeners to the choice buttons.
1. Create the variables `pageContent` and `choicesUL` and use DOM selectors to make them reference the elements with IDs `#story-text` and `choices`, respectively. This could be done with [`document.querySelector()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector) or [`document.getElementByID()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById).
    ```JavaScript
    let pageContent = document.getElementById('story-text');
    let choicesUL = document.getElementById('choices');
    ```
    **OR**
    ```JavaScript
    let pageContent = document.querySelector('#story-text');
    let choicesUL = document.querySelector('#choices');
    ```
2. Define the function and its parameters.
    ```JavaScript
    function updatePage(storyPage) {
        // function code goes here
    }
    ```
3. Set the text of `pageContent` equal to the story text.
    ```JavaScript
    pageContent.textContent = storyPage.text;
    ```
4. Clear the content of `choicesUL` and loop through the choices in the _page_ data.
    ```JavaScript
    choicesUL.innerHTML = '';
    for (choice of storyPage.choices){
        // code goes here
    }
    ```
5. In the loop, create a new `<li>` element with the choice text and the attribute `data-slug` equal to the link data.
    ```JavaScript
    let newLI = document.createElement('li');
    newLI.textContent = choice.text;
    newLI.setAttribute('data-slug', choice.link);
    choicesUL.appendChild(newLI);
    ```
6. After the loop is complete, run the `addEventListeners()` function.
    ```JavaScript
    addEventListeners();
    ```

## Add a function that advances to the next page.
In this part of the assignment, we must create a function called `changePage()`. This function will accept a single parameter, a _slug_, and uses it to "turn the page" of the story to this page. This involves three steps: (1) call the `recordChoice()` function, passing it the _slug_ as a parameter; (2) set the current page by calling the `getCurrentPage()` function, passing it the _slug_ as a parameter; and (3) call the `updatePage()` function, passing it the return value from `getCurrentPage()` as a parameter.
1. Define the function and its parameters.
    ```JavaScript
    function changePage(newSlug){
        // function code goes here
    }
2. Call the `recordChoice()` function, passing it the _slug_.
    ```JavaScript
    recordChoice(newSlug);
    ```
3. Set the current page by calling the `getCurrentPage()` function, passing it the _slug_ as a parameter.
    ```JavaScript
    let newPage = getCurrentPage(newSlug);
    ```
4. Update the page text by calling the `updatePage()` function, passing it the page data returned from the `getCurrentPage()` function.
    ```JavaScript
    updatePage(newPage);
    ```
### Notes
1. Steps 3 + 4 could be combined, eliminating the need for declaring a new variable.
    ```JavaScript
    updatePage(getCurrentPage(newSlug));
    ```

This completes all of the basic requirements for this assignment.