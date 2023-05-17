# Machineportal.com recruitment task

## Task 1
The goal of the task was to create a button component that will show a blue square and on further click it will hide said square.
The task was modified in the following ways:
1. The blue qquare was also defined in a seperate component `CustomSquare`. 
2. Linear gradient was applied to the square instead of a plain blue color.
3. In order to retain the space on the page when the square is hidden, class with `display: hidden` is applied based on the value of `showSquare` component prop. The other solution would be to tinker around with css instead so that the divs storing components have fixed height, this way we would be able to use `v:show` or `v:if` directives - see comments in `/src/components/CustomSquare.vue`for more information in that regard.

## Task 2
The goal of this task was to create an input component that will handle two-way data binding with the variable being passed using v-model to the parent component.
The task was done with the following approach:
1. The input was declared in the `CustomInput` component.
2. The value from the input is a string containing a definition for the color gradient -> value of the css `background` property.
3. The value instead of simply being displayed is now passed to the parent component and then to the `CustomSquare` component in order to change the `background` property of the square.

## Task 3
The goal of the task was to use two inputs components defined in the previous task. The following assumptions and/or improvements were made:
1. Input component was overhauled, its purpose is to accept a 3 numbers from an inclusive range 0 through 255, seperated by a comma. A method was added to validate its current value - if user types in a value that doesn't meet the above requirements the color of the text changes to red.
2. To make changing color of the square easier, gradient is now computed based on the values from the two input components - first one sets the starting color, the second one controlls the ending color. This way, the user is required to only input RGB values, i.e `30, 50, 90` instead of the whole `linear-gradient(...)` string.
3. To meet the other requirements of the task - manipulating the arrays - two arrays were created based on the string values from the inputs and the difference of those two sets (arrays) is displayed below the input compontents as a list. If the resulting array is empty, `[]` is displayed indicating that the array exists, though it doesn't contain any elements whatsoever.
4. The default `B` for the `RGB` in both inputs was set to the same value to speed up the testing process.

## End notes
To sum up, the 3 main tasks were compiled into one view / application and each following task improved the solution from the previous version of the app. Though I've tried inspecting css of machineportal.com (https://machineportal.com/css/app.164ffaaf.css), I wasn't exactly sure of the guidelines and it is most likely a subject to change. A similar logic applies to *.vue files code formatting - personally I was using VSC extension prettier to take care of it and adjusting the style should the need for it arise will not be a problem.