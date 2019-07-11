# Sets lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.


## Question 1

Ms. Gabriel Williams is a botany professor at District College. One day, she asked her student Mickey to compute the average of all the plants with distinct heights in her greenhouse.

Input: heights of trees below:
`161 182 161 154 176 170 167 171 170 174`

Output:
`169.375`

Answer: (Where does the .375 in the output come from when the heights are all Ints (or have .0 if double)?)
```swift
var plantHeights: [Int] = [161, 182, 161, 154, 176, 170, 167, 171, 170, 174]
var uniquePlantHeights: Set<Int> = Set(plantHeights)
var sumHeights = 0

for height in uniquePlantHeights {
sumHeights += height
}

var averageHeight = sumHeights/(uniquePlantHeights.count)
print(averageHeight)
```

## Question 2

Determine if a String is a pangram. A pangram is a string that contains every letter of the alphabet at least once.

 e.g `"The quick brown fox jumps over the lazy dog"` is a pangram
 e.g `"The quick brown fox jumped over the lazy dog"` is NOT a pangram

Answer:
```swift
let alphabet: Set<String> = ["a","b","c","d","e","f","g","h","i","j","k","l","m","n","o","p","q","r","s","t","u","v","w","x","y","z"," "]
var someString: String = "The quick brown fox jumps over the lazy dog"
var stringArray = [String]()

for character in someString.lowercased() {
stringArray.append(String(character))
}

var stringSet = Set(stringArray)
print(stringSet)

if stringSet == alphabet {
print("It is a pangram")
} else {
print("It is NOT a pangram")
}
```

## Question 3

The set S originally contains numbers from 1 to n in ascending order. Unfortunately, due to the data error, one of the numbers in the set was duplicated to another number in the set. This results in the repetition of one number and loss of another number in the set.

You are given an array `nums` representing the data status of the set S after the error occurred. Your task is to first find the number occurs twice and then find the number that is missing from the sequence. Return these two values in the form of an array.

 Example 1:
 Input: `nums = [1,2,2,4]`
 Output: `[2,3]`

 Example 2:
 Input: `nums = [1,1]`
 Output: `[1,2]`

 Example 3:
 Input: `nums = [2,2]`
 Output: `[2,1]`

Answer (using dictionary):
```swift
var nums = [1,2,2,4]
var dict = [Int:Int]()
var outputArray = [Int]()
let range = nums.count
var missingNumber:Int = 0

for num in 1...range {
if nums[num-1] != num {
missingNumber = num
}
}

for number in nums {
if dict.keys.contains(number) {
dict.updateValue(dict[number]!+1, forKey: number)
} else {
dict[number] = 1
}
}

for (key, value) in dict {
if value == 2 {
outputArray.append(key)
}
}
outputArray.append(missingNumber)
print(outputArray)
```
Answer (without using dictionary):
```swift
var nums = [1,2,2,4]

let range = nums.count
var missingNumber:Int = 0
var numHolder = 0


for num in 1...range {
if nums[num-1] != num {
missingNumber = num
}
}

var numsSet = Set(nums)

for num in nums {
if num != numHolder {
numHolder = num
} else {
print("[\(num),\(missingNumber)]")
}
}
```

## Question 4

Given the 4 arrays of Ints below, create a new array, sorted in ascending order, that contains all the values without duplicates.

```swift
let arr1 = [2, 4, 5, 6, 8, 10, 12]
let arr2 = [1, 2, 3, 4, 5, 6]
let arr3 = [5, 6, 7, 8, 9, 10, 11, 12]
let arr4 = [1, 3, 4, 5, 6, 7, 9]
```

Answer:
```swift
let arr1 = [2, 4, 5, 6, 8, 10, 12]
let arr2 = [1, 2, 3, 4, 5, 6]
let arr3 = [5, 6, 7, 8, 9, 10, 11, 12]
let arr4 = [1, 3, 4, 5, 6, 7, 9]
let arr1Set = Set(arr1)
let arr2Set = Set(arr2)
let arr3Set = Set(arr3)
let arr4Set = Set(arr4)


let arrUnion: Set<Int> = arr1Set.union(arr2Set.union(arr3Set.union(arr4Set)))
let arrUnionArray = Set(arrUnion)

print(arrUnionArray.sorted())
```

## Question 5

Perform the following set operations on the lists below:

1. Find the intersection and print the result
2. Find the symmetric difference and print the result
3. Find the union and print the result
4. What is the outcome of subtracting `list2` from `list1`? Print the result

```swift
let list1: Set = [1, 3, 4, 6, 2, 7, 9]
let list2: Set = [3, 7, 13, 10, 4]
```
Answer:
```swift
let list1: Set = [1, 3, 4, 6, 2, 7, 9]
let list2: Set = [3, 7, 13, 10, 4]

//1. Find the intersection and print the result
let intersectingNumbers = list1.intersection(list2)
print(intersectingNumbers)

//2. Find the symmetric difference and print the result
let symmetricDifference = list1.symmetricDifference(list2)
print(symmetricDifference)

//3. Find the union and print the result
let union = list1.union(list2)
print(union)

//4. What is the outcome of subtracting `list2` from `list1`? Print the result
let list1SubList2 = list1.subtracting(list2)
print(list1SubList2)
```

## Question 6

What output will be produced by the code below? Select one answer.

```swift
var spaceships = Set()

spaceships.insert("Serenity")
spaceships.insert("Enterprise")
spaceships.insert("TARDIS")
spaceships.insert("Serenity")

print(spaceships.count)
```

- 3
- 4
- Nothing will be output
- 0
- This code will not compile
- 1
- This code will compile but crash

Answer: This code will not compile (There would be an error because the set was not defined properly.). If the set was declared properly, the answer would be 3.

## Question 7

What output will be produced by the code below?

```swift
var spaceships1 = Set()

spaceships1.insert("Serenity")
spaceships1.insert("Enterprise")
spaceships1.insert("TARDIS")

let spaceships2 = spaceships1

if spaceships1.isSubset(of: spaceships2) {
  print("This is a subset")
} else {
  print("This is not a subset")
}
```

- This code will compile but crash
- "This is not a subset"
- This code will not compile
- "This is a subset"
- Nothing will be output

Answer:  This code will not compile (There would be an error because the set was not defined properly.). If the set was declared properly, the answer would be: "This is a subset".
