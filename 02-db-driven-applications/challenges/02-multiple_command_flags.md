# Multiple Command Flags

## Introduction

The biggest advantage of [Command-line flags][flags] over command-line arguments
are adding context to the information passed to the program. In the last
exercise, it would have actually been easier to simply use command-line
arguments rather than a flag. The reason for this is there was only one type of
data passed to the program. However if multiple types or options are available,
this can be difficult to manage.

The pattern difference is similar to having many arguments to a JavaScript
function. If you just add a parameter for each item, it requires the user of the
function to know the order of the arguments.

Example:

```js
function Car (year, make, model, color, trim, mileage, vin, plate) {
    this.color = color
    this.make = make
    this.mileage = mileage
    this.model = model
    this.plate = plate
    this.trim = trim
    this.vin = vin
    this.year = year
}

const car = new Car(2017, 'Honda', 'Civic', 'Black', 'Hatchback', 100, '1FMDK01135GA37315', 'TN ABC 123')
```

If you get the order wrong, you can trigger an Error or worse, have a silent bug
in your app. However if you change the function to accept an object instead, it
makes the function much easier to use.

Example:

```js
function Car (obj) {
    this.color = obj.color
    this.make = obj.make
    this.mileage = obj.mileage
    this.model = obj.model
    this.plate = obj.plate
    this.trim = obj.trim
    this.vin = obj.vin
    this.year = obj.year
}

const car = new Car({
    color: 'Black',
    make: 'Honda',
    mileage: 100,
    model: 'Civic',
    plate: 'TN ABC 123'
    trim: 'Hatchback',
    vin: '1FMDK01135GA37315',
    year: 2017,
})
```

Similar to the pattern above, command-line flags map easily to JavaScript
objects. This gives your data context and the order doesn't matter.

## Requirements

For this exercise you will create a pizza ordering app for hackers. This
command-line app will accept multiple command-line flags to calculate the total
cost of the order.

Expected:

```
$ ./pizza.js --size large --pepperoni --sausage --thick-crust --drink coke --name Mario
Mario ordered a Large Thick-Crust pizza with pepperoni and sausage with a Coke to drink.
The total due is $12.97
```

Use [yargs][yargs] to parse the command-line flags. Any parser error, such as a
bad topping i.e. `./pizza.js --dogfood` should return the usage statement.

Expected:

```
$ ./pizza.js
Usage: blah blah blah
$ ./pizza.js --dogfood
Usage: blah blah blah
```

Make sure that the total returns a two decimal money format "$12.00" that does
not have a floating point error:

i.e.
Good: $1.23, $12.30, $123.00
Bad $12.30000000000000004

Allow for several pizza options. Below are the minimum, but you can add more.

-   Allow for 5 different pizza sizes and each with different prices
    *   Personal 8"
    *   Small 10"
    *   Medium 12"
    *   Large 14"
    *   Extra Large 16"
-   Allow for 4 different crusts and each with different prices, but include a
    default
    *   Thick
    *   Thin
    *   Traditional Hand Tossed
    *   Stuffed
-   Allow for at least 10 different toppings, with a per topping cost that
    depends on the pizza size: i.e. 49¢, 79¢, 99¢, $1.29, and $1.49 per topping
    *   Pepperoni
    *   Sausage
    *   Green Peppers
    *   Etc...
-   Allow for several drink options with potentially different prices
    *   Coca-Cola
    *   Miller Lite
    *   Coffee
    *   Water

## Bonus

-   Allow double, triple, etc... toppings
-   Allow for multiple drinks
-   Allow for half and half pizzas i.e. half pepperoni and half cheese
-   Add additional error handling (thick and thin crusts, selecting multiple
    sizes, etc...)

## Additional Reading

[Command-line flags][flags]

[flags]: https://en.wikipedia.org/wiki/Command-line_interface#Command-line_option
[yargs]: http://yargs.js.org/
