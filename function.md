- Function
    - Function is a 1-st class passenger, can be used the same way as other types are used, e.g. `var strToFunc = map[string]func(string, int)int{
      "1": createAccount,
      "2": findAccount,
      "3": deleteAccount,
      }`
      NOTE: function can be used as an argument in other function, e.g. `func (vault *VaultWithDb) FindAccounts(url string, checker func(Account, string)boolean)` - universal function which searches accounts applying given checker function

    - `FindAccounts("search string", func(account Account, str String) boolean {
      return strings.Contains(acc.Url, str)
      })' - usage of anonymous function, e.g. passed into FindAccounts() function declare above
      NOTE: `func() {
      fmt.Println("Hi")
      }()` - declare and call anonymous function

    - `func promptData(prompt ...any) string {}` - declaration of function with argument of variable number
      NOTE: parameter of variable number of arguments can be used as slice, all operations like `for` are applicable
      NOTE: argument of variable number must be the last in function signature

    - `promptData(menu...)` - how to use slice variable `var menu = []string{"one", "two", "three",}` in the place of argument of variable size
      NOTE: same ... operator we can use to spread slice across function arguments

    - Closure
      NOTE: function may return the other function, e.g. as a pattern we could have a factory function: `func factory(a string) func(*account.VaultWithDb) {return findAccountByUrl}`

        - Closure is a function with it's additional context independent for each function instance (in other words function that captures arguments from external visibility context)
          `func menuCounter() func()  {
          i :-= 0 // context that will remain within the closure
          return func() {
          i++
          fmt.Println(i)
          }
          }` - declare the closure

          `counter := menuCounter()
          for  {
          ...
          counter() // will get incrementing counters 1,2,3,..
          }` - use closure