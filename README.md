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
3. Wykorzystaj komponent z zadania drugiego i utwórz dwa inputy, które będą przechowywały wartość w zmiennych. Utwórz metodę, która po kliknięciu utworzy dwie tablice z inputów, każda wartość znajdująca się np. po przecinku powinna być nową wartością w tablicy, następnie metoda powinna przypisać do zmiennej newArray, tablice z inputa 1  bez elementów znajdujących się w tablicy inputa 2.Wyświetl nową tablicę jako listę.

Przykład newArray - tablica a = [‘a’,’b’,’c’] tablica b= [‘b’], tablica newA

robert.hapka@machineportal.com