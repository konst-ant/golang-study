- Array & Slice
    - `var myArr = [5]int`
      declare array of int, size 5 (will be initialized with default int value 0)

    - `myArr := [5]int{1, 2, 3}`
      declare and initialize array of int size 5
      NOTE: we could initialize array partially, the rest elements will get default values as above

    - `myArr := [5]int{}`
      create empty array of int size 5
      `myArr := []int{}`
      create just an empty array

    - `var myInt = myArr[1]`
    - `myArr[1] = 8`
      get/set element of an array

    - `mySlice := myArr[1:3]`
      create slice of myArr from index 1 (inclusive) to index 3 (excluded)
      NOTE: left / right boundary of slice expression can be omitted

    - `myDynamicSlice := []int{1, 2, 3}`
      create a slice of size 3 and capacity 3

    - We can create slice over slice, with any nesting, and they all have same behaviour

    - `len(mySlice)`
    - `cap(mySlice)`
      get length and capacity of mySlice
      NOTE:
      len() will return length of the "window" the slice represents
      cap() will return size of available slots (up to the end of array) upon which the slice is standing. So a slice is extendable beyond it's right boundary up to the end of array

    - `extendedSlice := append(myDynamicSlice, 100)``
      add 100 to the tail of slice (extending it)
      NOTE: be careful when using append() on slices, old slice variables will remain unchanged. Reassign old slice variables if you want them to get updated, e.g. `myDynamicSlice = append(myDynamicSlice, 100)`

    - Slice is not using new memory -n not copying from original array, but it is a "window" in original array. Changing slice will change the array
        - smth similar to Java:
          `Integer[] arr = new Integer[] {1, 2, 3};
          List list = Arrays.asList(arr);`

    - extendedSlice[1:] - will remove the 0-th element of the slice

    - `mergedSlices := append(myDynamicSlice1, myDynamicSlice2...)` - unpack elements of myDynamicSlice2 to return a sequence of elements

    - `for index, value := range mySlice {}` - iterate through the slice

    - `slice = append(slice[:i], slice[i+1:]...)` - delete i-th element from slice (or array).
      Note: like Java, deleting element in array will cause copying of memory for the tail length of array

- Map
    - `m := map[string]string {"one" : "apple", "two": "windows"}` -
      declare and initialize map string -> string
    - `m["one"]` - 
      get value from map by key
    - `m["one"] = "pineapple"` -
      change map value by key, or add value if the key is not in the map
    - `delete(m, "one")` - 
      delete element from map by key. if key doesn't exist there will be no error
    - `for key, value := range m {
      }` - 
      iterate through map
    - `len(m)` - 
      return length of the map.
      NOTE: map has no capacity
    - `make(map[string]string, 3)` - create map and allocate memory for 3 elements
      If we wouldn't use make, adding new elements to the map will allocate memory during adding
    - `make([]int, 10)` - create and allocate memory for slice (array underneath of ints)
    - NOTE: getting non-existent key from the map will return default value of the map's value type