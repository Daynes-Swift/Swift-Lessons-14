# Lesson 14 - Arrays and Loops

# Exercise: Count

If you try to use an index that’s outside of the array, your program will crash with a “fatal error.” How can you make sure this doesn't happen?

You can find out the number of items in an array using the count property:

```swift
let devices = ["iPhone", "iPad", "iPod", "iMac"]
devices.count
```

The only safe indices to use for an array are those less than the count.

## Exercise
Using what you’ve learned about making decisions, write an if statement that will only access the array if the value of index is less than the array's count. Uncomment and update the code below, then update the index constant to different numbers and see the results.

```swift
let index = 5
if index < devices.count {
    devices[index]
}
```

# Exercise: Karaoke Host

You have a friend who loves singing karaoke with a big group of people. The karaoke singers add songs they’d like to sing to a list and the karaoke host calls out the songs one by one.

Your friend and has asked you to write software to help manage the song list.

## Exercise
Create an empty array to hold song titles as strings, and use the append method to add three or four songs one at a time.

```swift
var songs = [String]()
songs.append("Easy Lover")
songs.append("Walk of Life")
songs.append("Home Again")
```

## Exercise
One enthusiastic singer wants to add three songs at once. Create an array holding this one singer's song list and use the += operator to append their whole list to the end of the group's song list.

```swift
let rockSong = ["Killing in the name of!", "Chop Suey", "Free Bird"]
songs += rockSong
```

## Exercise
Write a for…in loop and, for every song title in the array, print an encouraging announcement to let the next singer know that it's their turn.

```swift
for song in songs {
    print("Lets go Rocker! Sing this one: \(song)")
}

// Output: 
// Lets go Rocker! Sing this one: Easy Lover
// Lets go Rocker! Sing this one: Walk of Life
// Lets go Rocker! Sing this one: Home Again
// Lets go Rocker! Sing this one: Killing in the name of
// Lets go Rocker! Sing this one: Chop Suey
// Lets go Rocker! Sing this one: Free Bird
```

## Exercise
After the loop has called everyone up to sing, use the removeAll method on the song list to clear out all the past songs.

```swift
songs.removeAll()
```

# Exercise: Counting Votes

You're implementing a poll app for your class. You start with a basic yes-no question counter and now you have your first batch of answers back, parsed into arrays below.

This is a lot of data! But don't worry too much about the long arrays. Whether you're planning to loop over two items or two thousand, you’ll write the loop in exactly the same way.

```swift
let shouldMascotChangeVotes: [Bool] = [false, false, false, true, false, true, true, true, false, true, true, true, true, false, true, true, false, true, true, true, false, true, true, true, true, true, true, true, false, true, false, true, false, true, true, false, false, true, true, false, false, true, true, true, false, true, false, true, true, false, true, true, false, true, false, false, true, false, true, true, false, false, true, false, true, true, true, false, true, true, false, false, true, false, true, true, false, false, false, true, false, true, true, false, true, true, true, true, true, true, true, false, true, false, true, false, true, true, true, true, true, true, true, false, true, true, false, true, true, true, true, true, true, true, false, true, true, false, true, true, false, true, true, true, true, true, false, false, false, false, true, true, true, false, true, true, false, false, true, false, false, true, true, true, true, false, true, true, true, true, false, true, true, false, true, false, false, true, true, false, true, false, false, false, true, false, false, false, true, false, true, true, false, true, true, false, true, true, true, false, false, false, true, false, true, false, true, true, true, true, false, true, false, false, true, true, true, true, true, false]

let shouldInstallCoffeeVendingMachineVotes: [Bool] = [true, true, false, false, false, true, true, false, true, true, true, true, false, true, false, false, true, false, true, false, true, true, false, false, false, false, false, true, true, true, false, false, true, true, false, true, true, true, true, false, true, false, true, true, false, false, false, false, false, false, true, false, true, true, false, true, true, true, true, false, false, true, true, false, false, false, false, true, true, false, false, true, true, true, true, false, false, true, true, false, true, false, true, false, true, true, true, false, true, true, true, false, false, false, false, false, false, false, false, false, false, false, true, false, true, false, false, true, true, false, true, false, true, true, true, false, false, false, false, false, false, true, true, false, false, true, true, true, true, true, true, false, false, false, true, true, true, true, false, false, false, true, true, false, true, true, true, false, false, true, false, true, false, true, false, false, true, false, true, true, true, true, true, true, true, false, true, false, true, true, false, false, true, false, false, true, false, false, false, true, false, true, true, true, false, false, false, false, false, false, true, false, true, false, true, true, false, false, false, true]

let shouldHaveMorePollOptionsVotes: [Bool] = [false, false, true, true, false, true, false, false, false, false, false, false, true, false, true, true, false, true, true, false, false, true, true, false, false, false, false, false, false, false, true, false, false, false, false, true, false, false, false, false, false, false, true, true, false, true, true, false, true, false, true, true, false, false, false, false, true, false, true, true, false, false, false, false, true, true, true, true, false, true, false, false, true, true, false, false, false, false, false, false, true, true, false, false, false, false, false, true, true, false, false, false, false, false, false, false, false, false, false, false, false, true, true, true, true, true, false, false, true, false, true, false, false, false, true, false, true, true, true, true, true, true, true, false, false, false, false, true, false, false, false, false, false, true, false, false, true, false, false, true, false, false, true, false, false, true, false, false, true, false, false, false, false, false, true, false, false, false, false, false, false, true, true, true, false, true, false, false, false, false, false, false, false, false, true, true, true, true, false, true, true, false, false, true, false, true, true, false, false, true, true, false, true, false, false, false, true, true, false, false]
```

This is too many votes to tally quickly by hand, so you’ll write some code to tally it for you.

Note
This is also a lot of votes for Swift to use type inference to determine what kind of array it has. The type annotation is written in the array literals above to tell Swift the type of array. This prevents the playground from running slowly.

## Exercise

Create two variables, one to count yes votes and one to count no votes. Each should start off with a value of zero.

``swift
var noVotes = 0
var yesVotes = 0

````

## Exercise
Create a for…in loop that loops over one of the vote collections and checks the value of each vote. If the vote is true, the loop should add one vote to the yes variable. If it's false, it should add one vote to the no variable.

```swift
for vote in shouldAndroidBeBanned {
    if vote == true {
        yesVotes += 1
    } else {
        noVotes += 1
    }
}
````

## Exercise

After the loop has finished, write an if statement that compares the two values and prints a different message based on whether the vote passed or failed.

```swift
if yesVotes > noVotes {
    print("The vote to ban Android passed!")
} else {
    print("Sorry, Android isn't banned this year")
}
```

## Exercise

Test your code by calling the for…in loop on each of the vote collections.
Which measures won by popular vote?

```swift
yesVotes = 0
noVotes = 0

for vote in havingAFridge {
    if vote == true {
        yesVotes += 1
    } else {
        noVotes += 1
    }
}

if yesVotes > noVotes {
    print("The vote for having a fridge passed!")
} else {
    print("Sorry, no fridge this year")
}

yesVotes = 0
noVotes = 0

for vote in havingCoffee {
    if vote == true {
        yesVotes += 1
    } else {
        noVotes += 1
    }
}

if yesVotes > noVotes {
    print("The vote to have coffee passed!")
} else {
    print("Sorry, no coffee this year 😞")
}
```

# Extension

Your for…in loop would be even more powerful if you could easily reuse it. The easiest way to reuse code is to put it in a function.

## Exercise

Write a function that takes two arguments: a string describing the issue being voted on and an array with the issue's Bool votes. Move the for…in loop and the if statement inside the function, so it prints the results when you call the function with a particular issue's arguments. You should be able to call the function like this:

## Example

`printResults(forIssue: "Should we change the mascot?", withVotes:shouldMascotChangeVotes)`

A message like this should be printed to the console:
`Should we change the mascot? 54 yes, 23 no`

```swift
// Add your vote-processing function here:
func printResults(forIssue issue: String, withVotes votes: [Bool]) {
    print(issue)

    var yesVotes = 0
    var noVotes = 0

    for vote in votes {
        if vote == true {
            yesVotes += 1
        } else {
            noVotes += 1
        }
    }

    print("\(yesVotes) yes, \(noVotes) no")
}

printResults(forIssue: "Should we change the mascot?", withVotes: shouldMascotChangeVotes)
// Output: Should we change the mascot? 125 yes, 75 no
```

# Exercise: Goals

Think of a goal of yours that can be measured in progress every day, whether it’s minutes spent exercising, number of photos sent to friends, hours spent sleeping, or number words written for your novel.

## Exercise

Create an array literal with 20 to 25 items of sample data for your daily activity. It may be something like let milesBiked = [3, 7.5, 0, 0, 17 ... ] Feel free to make up or embellish the numbers, but make sure you have entries that are above, below and exactly at the goal you've thought of. Hint: Make sure to choose the right kind of array for your data, whether [Double] or [Int].

```swift
let milesBiked = [3, 7.5, 0, 0, 17, 2, 2.5, 3, 3.5, 4, 1.5, 1, 5, 3.5, 3, 2, 2.5, 21, 10, 9]
```

## Exercise

Write a function that takes the daily number as an argument and returns a message as a string. It should return a different message based on how close the number comes to your goal. You can be as ambitious and creative as you'd like with your responses, but make sure to return at least two different messages depending on your daily progress!

```swift
func goalAchieved(dailyNumber: Double) -> String {
    let goal = 5.0
    if dailyNumber >= goal {
        return "You've reached your goal! You went over your goal by \(dailyNumber - goal) miles!"
    } else {
        return "Unfortuantely, you did not reach the daily goal of \(goal) miles."
    }
}
```

## Exercise

Write a for…in loop that loops over your sample data, calls your function to get an appropriate message for each item, and prints the message to the console.

```swift
for dailyMiles in milesBiked {
    print(goalAchieved(dailyNumber: dailyMiles))
}
```

# Exercise: Screening Messages

You've somehow come to possess a huge list of messages about a series of characters: Caterpillar, Dormouse, Cheshire Cat, and others. The list is contained in the aliceMessages constant below.

Try to print out the aliceMessages array to see the whole list, but beware: It's large enough that it may cause your playground to run slowly.

```swift
import Foundation

aliceMessages
```

The Caterpillar has asked you to go through the messages and to relay any that contain the Caterpillar's name. Instead of reading all the text yourself, you decide to write more code to help.

## Exercise

Create a for…in loop to process the aliceMessages collection.
In the body of the loop, check whether each message contains the string "Caterpillar".
If the message refers to the Caterpillar, print it to the console.

* note:
 The contains method is part of the Foundation framework that you read about in the “Types” playground. If you try using it and get an error saying “Value of type 'String' has no member 'contains',” follow the instructions from that playground to import the framework into your project.

 ```swift
 // Write the `for…in` loop here:
for message in aliceMessages {
    if message.contains("Caterpillar") {
        print(message)
    }
}
```
