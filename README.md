<!-- A. //WORKING ON THE LIKE BUTTON/ICON -->

1. var likeIcons = document.querySelectorAll(".fa-heart");
   // - Selects all HTML elements with the class fa-heart (heart icons) and stores them in the likeIcons variable.

2. likeIcons.forEach(function (icon) { ... });
   // - Iterates over each heart icon using a forEach loop.

3. let isliked = false;
   // - Initializes a variable isliked to false, indicating that the heart icon is not liked initially.

4. icon.addEventListener("click", function () { ... });
   // - Attaches a click event listener to each heart icon.

5. isliked = !isliked;
   // - Toggles the isliked variable between true and false on each click.

6. if (isliked === true) { icon.style.color = "red"; } else { icon.style.color = "black"; }
   // - Changes the icon's color to red when liked (true) and black when not liked (false).

<!-- How the like Button work: -->

> > > User clicks an increment button.
> > > The event listener triggers.
> > > Increments the quantity display.
> > > Updates the total cost by adding the item's price.

<!-- B.//WORKING ON THE INCREMENT/PLUS BUTTON & UPDATING THE TOTAL WHENEVER THE BUTTON IS CLICKED -->

<!-- //Initialization -->

1. var plusButtons = document.querySelectorAll(".fa-plus-circle");
   //Selects all elements with the class fa-plus-circle (increment buttons).

2. let total = 0;
   //Initializes a variable total to keep track of the overall total cost.

3. var totalElement = document.querySelector(".total");
   //Selects the element displaying the total cost.

<!-- //Event Listener (we are still in the increment button function) -->

4. plusButtons.forEach(function (plusClick) { ... });
   //Iterates over each increment button.

5. plusClick.addEventListener("click", function () { ... });
   //Attaches a click event listener to each increment button.

//Increment Quantity

6. var quantityClass = plusClick.nextElementSibling;
   //Gets the sibling element containing the quantity.

7. let quantity = parseInt(quantityClass.textContent);
   //Parses the quantity text into an integer.

8. quantity = quantity + 1;
   //Increments the quantity.

9. quantityClass.textContent = quantity;
   //Updates the quantity display.

<!-- //Updating the  Total (we are still in the increment button function)-->

10. var priceValue = plusClick.closest(".card-body").querySelector(".unit-price");
    //Finds the price element within the same card.

11. var itemAmount = parseInt(priceValue.textContent.slice(0, -1));
    //Extracts the price value (excluding the dollar sign).
    <!-- //parseInt() is a JavaScript function that converts a string into an integer.For example parseInt("123"); // returns 123. It was used so that what ever numeric value it holds will be treated as a number and not as an array.-->

<!-- .textContent returns the text content, without any HTML tags. For example if you have a paragraph tag with a class name as myName, and the text as Ema. See illustration -- <p class="myName">Ema</p> in this case myName.textcontent, will return the text content as Ema -->

<!-- .slice() is a JavaScript method that extracts a subset of characters from a string:
        .slice(startIndex, endIndex) returns a new string containing the characters from startIndex to endIndex. For example if Original String: "HelloEma$"

    Index (from start): 0 1 2 3 4 5
    Index (from end): -6 -5 -4 -3 -2 -1
    Character: H e l l o E m a $

.slice(0, -1) means:

Start at index 0 (from start)
End at index -1 (last character, from end)

Result: "HelloEma" (last character "$" removed) -->

12. total = total + itemAmount;
    //Adds the item's price to the total.

13. totalElement.textContent = total + " $ ";
    //Updates the total display.

<!-- How the increment button works: -->

> > > User clicks an increment button.
> > > The event listener triggers.
> > > Increments the quantity display.
> > > Updates the total cost by adding the item's price.

<!-- C. //WORKING ON THE DECREMENT/MINUS BUTTON &  UPDATING THE TOTAL WHENEVER THE BUTTON IS CLICKED-->

<!-- Initialization -->

1. var minusButtons = document.querySelectorAll(".fa-minus-circle");
   //Selects all elements with the class fa-minus-circle (decrement buttons).

<!-- Event Listener function -->

2. minusButtons.forEach(function (minusClick) { ... });
   //Iterates over each decrement button using a for loop method (forEach).
3. minusClick.addEventListener("click", function () { ... });
   //Attaches a click event listener to each decrement button.

<!-- Decrement Quantity -->

4. var quantityClass = minusClick.previousElementSibling;
   //Gets the sibling element containing the quantity.
      <!-- For Example
   <!-- <div>
     <p id="p1">My</p>
     <p id="p2">Name is</p>
     <p id="p3">Ema</p>
   </div> -->
   <!-- const p2 = document.getElementById('p2');
   const previousSibling = p2.previousElementSibling;
   console.log(previousSibling.textContent); // Outputs: "Name is" -->
5. let quantity = parseInt(quantityClass.textContent);
   //Parses the quantity text into an integer.
6. if (quantity <= 0) { return; }
   //Prevents decrementing below 0.
7. quantity = quantity - 1;
   //Decrements the quantity by minus one each time the minus icon is cliked.
8. quantityClass.textContent = quantity;
   //Updates the quantity display, which is test content.

<!-- Update Total -->

9. var priceValue = minusClick.closest(".card-body").querySelector(".unit-price");
   //Finds the price element within the same card.
10. var itemAmount = parseInt(priceValue.textContent.slice(0, -1));
    //Extracts the price value (excluding the dollar sign).
11. total = total - itemAmount;
    //Decrements the total by the item amount.
12. totalElement.textContent = total + " $ ";
    //Updates the total display.

<!-- How it works: -->

> > > User clicks a decrement button.
> > > The event listener triggers.
> > > Decrements the quantity display (if above 0).
> > > Updates the total cost by subtracting the item's price

<!--C //WORKING ON THE DELETE ICON -->
<!-- 1: Selecting Delete Icons --> -->

var deleteIcons = document.querySelectorAll(".fa-trash-alt");
//Selects all HTML elements with the class fa-trash-alt (delete icons) using document.querySelectorAll()

<!-- 2: Attaching Event Listeners -->

deleteIcons.forEach(function (delIcon) { ... });
//Iterates over each delete icon using forEach().
//Attaches a click event listener to each delete icon using addEventListener("click", function () { ... });.

<!-- 3: Delete Icon Click Handler -->

delIcon.addEventListener("click", function () { ... });
//Handles the click event on each delete icon.

<!-- 4: Finding Related Elements -->

var itemsContainer = delIcon.closest(".card");
//Finds the closest parent element with the class card using .closest().

var QuantityElement = itemsContainer.querySelector(".quantity");
var PriceElement = itemsContainer.querySelector(".unit-price");
//Finds the quantity and price elements within the itemsContainer using querySelector().

<!-- 5: Calculating Total -->

var itemQuantity = parseInt(QuantityElement.textContent);
var itemPrice = parseInt(PriceElement.textContent.slice(0, -1));
//Parses the quantity and price text into integers using parseInt().
//Removes the dollar sign from the price using slice(0, -1).

total = total - itemQuantity \* itemPrice;
//Subtracts the item's total price from the overall total.

<!-- 6: Updating Total Display -->

totalElement.textContent = total.toString() + " $ ";
//Updates the total display element with the new total.

<!-- 7: Removing Item -->

itemsContainer.remove();
//Removes the item's container element from the DOM.

<!-- How It Works -->

> > > User clicks delete icon (.fa-trash-alt)
> > > Event listener triggers
> > > Find item's container (.card), quantity (.quantity), and price (.unit-price)
> > > Calculate item's total price
> > > Subtract item's total from overall total
> > > Update total display
> > > Remove item's container from DOM
