# Array

Module for functions to manipulate immutable arrays.

## `first(Array(a)) : Maybe(a)`
Returns the first element of the array as `Maybe.just(a)` or `Maybe.nothing()`.
```mint
Array.first([]) == Maybe.nothing()
Array.first(["a", "x"]) == Maybe.just("a")
```

## `firstWithDefault(a, Array(a)) : a`
Returns the first element of the array or the default value.
```mint
Array.firstWithDefault("a", []) == "a"
Array.firstWithDefault("a", ["b", "x"]) == "b"
```

## `last(Array(a)): Maybe(a)`
Returns the last element of the array as `Just(a)` or `Nothing`.
```mint
Array.last([]) == Maybe.nothing()
Array.last(["x", "a"]) == Maybe.just("a")
```

## `lastWithDefault(a, Array(a)) : a`
Returns the last element of the array or the default value.
```mint
Array.lastWithDefault("a", []) == "a"
Array.lastWithDefault("a", ["x", "b"]) == "b"
```

## `size(Array(a)) : Number`
Returns the size of the array.
```mint
Array.size([]) == 0
Array.size([1, 2, 3]) == 3
```

## `push(a, Array(a)) : Array(a)`
Push an element to the end of an array.
```mint
Array.push("a", []) == ["a"]
Array.push(4, [1, 2, 3]) == [1, 2, 3, 4]
```

## `reverse(Array(a)) : Array(a)`
Returns a new array where the elements are reversed. The first array element becomes the last, and the last array element becomes the first.
```mint
Array.reverse([1, 2, 3]) == [4, 3, 2, 1]
```

## `map(Function(a, b), Array(a)) : Array(b)`
Creates a new array with the results of calling a provided function on every element in the given array.
```mint
Array.map((number : Number) : Number => { number + 1 }, [1, 2, 3]) == [2, 3, 4]
```

## `mapWithIndex(Function(a, Number, b), Array(a)) : Array(b)`
Creates a new array with the results of calling a provided function on every element in the given array while providing the index of the element.
```mint
Array.mapWithIndex(
  (index : Number, number : Number) : Number => { number + index }, [1, 2, 3]) == [2, 4, 6]
```

## `select(Function(a, Bool), Array(a)) : Array(a)`
Returns all elements that matches the predicate function.
```mint
Array.select((number : Number) : Bool => { number % 2 == 0 }, [1, 2, 3, 4]) == [2, 4]
```

## `reject(Function(a, Bool), Array(a)) : Array(a)`
Returns all elements that does not matches the predicate function.
```mint
Array.reject((number : Number) : Bool => { number % 2 == 0 }, [1, 2, 3, 4]) == [1, 3]
```

## `find(Function(a, Bool), Array(a)) : Maybe(a)`
Finds the first element in the array that matches the predicate function.
```mint
Array.find((number : Number) : Bool => { number % 2 == 0 }, [1, 2, 3, 4]) == Maybe.just(2)
```

## `any(Function(a, Bool), Array(a)) : Bool`
Returns `true` if any item in the array matches the predicate function `false` otherwise.
```mint
Array.any((number : Number) : Bool => { number % 2 == 0 }, [1, 2, 3, 4]) == true
Array.any((number : Number) : Bool => { number % 2 == 0 }, [1, 3]) == false
```

## `sort(Function(a, a, Number), Array(a)) : Array(a)`
Returns a new sorted array using the given sorting function.
```mint
Array.sort((a : Number, b : Number) : Number => { a - b }, [4, 1, 3, 2]) == [1, 2, 3, 4]
```

## `sortBy(Function(a, b), Array(a)) : Array(a)`
Returns a new sorted array using the given functions return as the base of the sorting.
```mint
Array.sortBy((number : Number) : Number => { number }, [4, 1, 3, 2]) == [1, 2, 3, 4]
```

## `slice(Number, Number, Array(a)) : Array(a)`
Returns a copy of a portion of an array (end not included).
```mint
Array.slice(2, 4, ["ant", "bison", "camel", "duck", "elephant"]) == ["camel", "duck"]
```

## `isEmpty(Array(a)) : Bool`
Returns whether or not the array is empty.
```mint
Array.isEmpty([]) == true
Array.isEmpty(["a", "b"]) == false
```

## `intersperse(a, Array(a)) : Array(a)`
Inserts the given element between the elements of the given array.
```mint
Array.intersperse("a", ["x", "y", "z"]) == ["x", "a", "y", "a", "z"]
```

## `contains(a, Array(a)) : Bool`
Checks whether or not the given element exists in the array.
```mint
Array.contains("a", ["a", "b", "c"]) == true
Array.contains("a", ["x", "y", "z"]) == false
```

## `range(Number, Number) : Array(Number)`
Creates an array of numbers starting from the first argument and ending in the last.
```mint
Array.range(0, 5) == [0, 1, 2, 3, 4, 5]
```

## `delete(a, Array(a)) : Array(a)`
Deletes every occurrence of the given element from the array.
```mint
Array.delete("a", ["a", "b", "c"]) == ["b", "c"]
```

## `max(Array(Number)) : Number`
Returns the maximum value of an array of numbers.
```mint
Array.max([0, 1, 2, 3, 4]) == 4
Array.max([]) == 0
```

## `sample(Array(a)) : Maybe(a)`
Returns an random element from the array.
```mint
Array.sample(["a"]) == Maybe.just("a")
Array.sample() == Maybe.nothing()
```

## `at(Number, Array(a)) : Maybe(a)`
Returns the element at the given index.
```mint
Array.at(0, [0]) == Maybe.just(0)
Array.at(1, [0]) == Maybe.nothing()
```

## `do(Array(Void)) : Void`
Collapses an array of voids into a single void.
```mint
Array.do([
  do {
    Debug.log("a")
  },
  do {
    Debug.log("b")
  }
])
```

## `reduce(a, Function(b, a, b), Array(a)) : b`
Applies the given function against an accumulator and each element in the array (from left to right) to reduce it to a single value.
```mint
Array.reduce(
  0,
  (memo : Number, item : Number) : Number => { memo + item },
  [1, 2, 3]) == 6
```
