- Variable & Constant & Types
    - `var myVar = 5.2`
      declare and initialize `myVar` variable
      NOTE: with this declaration myVar type is inferred => float64

    - `var myVar float64 = 5.2`
        explicitly define variable type
            NOTE: we can declare variable without initialization only this way, e.g. `var myVar float64`

    - `myVar := 5.2`
        type is always inferred with this way, we can not use explicit type declaration

    - `const myConst = 2`
        use 'const' similarly with 'var' to declare and init constants
        NOTE: if type not declared, `myConst` gets type `untyped` and flexible to auto convert to compatible types (like in Java)

    - NOTE: all variables/constants must be used, otherwise code will not run. Same apply for functions, and more.

    - NOTE: Golang is strictly typed language - it can not automatically transfer between compatible types as in Java
        we need to explicitly cast type using standard functions e.g. `float(myVarInt)` casts int to float64

    - Golang types:
        - Basic types
            - int, int8, int16, int32, int64
            - float32, float64
            - uint, uint8, uint16, uint32, uint64, uintptr (keep pointer)
                NOTE: byte - syntactic alias to uint8
            - string
        - Aggregate types
            - array
            - struct
        - Reference types
            - slice
            - map
            - function
            - channel
            NOTE: reference type variables are passed by pointer (reference), hence can be changed directly in receiving function
        - Interface type
            
        - Pointer
            `num := 10
             numPointer := &num` - declaring pointer, which will be pointing to a variable num and thus be reference type
             NOTE: use pointer to avoid copying if required, or if you want to mutate the variable

             `var p &int` - declaring pointer variable

             `func(num *int)` -declaring function, which receives a pointer
             NOTE: for pointer variables you will see them like this *int (as in C), basically keeping the memory address. And we dereference pointer with (*numPointer) as well

             `*num = *num * 2` - if num is a pointer, this is how we can set new value to the variable (say, inside function receiving a pointer)
             NOTE: for array pointer operating with dereferenced pointer would look like this `(*arr)[index]`, however it's exempted to use just arr[index]
             NOTE: dereferencing pointer to nil will make runtime error

        - Rune
            - Rune is not an independent data type, but syntactic sugar (equivalent int32) for reading out string Unicode symbols into letters (runes)

            - `for _, ch := range str {
                        fmt.Print(ch, string(ch))
               }` - will split str into Runes, and print out Unicode code and representation of each symbol in string

            - alternatively declare `[]rune(str)` - same build slice of runes from string, but with syntactic sugar

            - To convert back slice of runes into string do `string(rune)`

    - Type alias:
        `type stringMap = map[string]string` - declares 'stringMap' type that is an alias of map[string]string
        bookmarks stringMap - declare variable using type alias, type alias can be used in all places where type can be used