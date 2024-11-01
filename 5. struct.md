- Struct

    - `type account struct {
      login string
      password string
      url string
      }` -  declare the struct type
      Note: also see -OOP "Composition" below showing how to declare struct with embedded field

    - `account1 := account{
      "login",
      "password",
      "url",
      }` - create account variable (comma inside field declaration is everywhere mandatory)
      NOTE: order of field declaration here is important
      NOTE: we can use variables in place of literals here

    - `account2 := account{
      login: "login",
      password: "password",
      url: "url",
      }` - create account variable with explicit binding
      NOTE: with this notation we can partially initialize struct variable, the omitted fields getting default values. We can have uninitialized (empty) struct variable as well
      NOTE: we can print structures with `fmt.Print(account2)`

- Struct methods

    - `func (account) outputPassword(acc *account) {}` - declare method upon account structure
      NOTE: methods are declared outside of structs (this gives some flexibility? Huh?)
      NOTE: declare methods in same package and near with struct declaration

    - `func (acc account) outputPassword() {}` - alternatively we can declare method binding with "instance declaration", acc variable is now the bound account instance
      NOTE: for methods that need mutate object, we would need to do pointer declaration
      `func (acc *account) generationPassword() {}`
      NOTE: constructor method (function) is just a function, in which you create strict instance and return typically pointer (to avoid object copying)