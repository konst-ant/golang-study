- OOP & Generic
    - Go has no inheritance concept
    - Composition
        - `accountWithTimestamp {
          createdAt time,
          updatedAt time,
          account // embedded field
          }` - declare extended structure base on existing "account"

        - `extendedAcc := &accountWithTimestamp {
          createdAt: time.Now(),
          updatedAt: time.Now(),
          account: {
          url: "url",
          login: "login",
          password: "password",
          }
          }` - create variable of composition structure
          NOTE: we can access embedded field by `extendedAcc.account.url` or equivalently by `extendedAcc.url`

    - Dependency injection
      To do DI basically we can use composition struct, that will include our target struct and dependencies, that it needs in the form of interfaces

        - `type VaultWithDb struct {
          Vault
          db files.JsonDb
          }` - struct including target struct and it's dependency

    - Interface
        - `type Db interface {
          Read() ([]byte, error)
          Write([]byte)
          }` - declaration of interface
          NOTE: we don't need to "implement" the interface, because any struct having the methods of interface automatically are "implementing" this interface. So meaning interface defines the contract.

        - `type Reader interface {
          Read() ([]byte, error)
          }

          type Writer interface {
          Write([]byte)
          }

          type Db {
          Reader
          Writer
          }
          ` - declaration of embedded interface

        - `func PrintError(value any) {
          fmt.Println(value)
          }` - this function can accept int, string, etc.
          NOTE: any is equivalent to `interface{}` - also known as empty interface

        - `func PrintError(value any) {
          switch t:= value.(type) {
          case string:
          fmt.Println(t)
          case int:
          fmt.Println("Error code %d", t)
          default:
          fmt.Println("Unknown type")
          }
          }` - getting the type of `any` variable
          NOTE: to extract specific type for `any` variable use expression e.g. `intValue, okFlag = value.(int)`. okFlag will denote successful or not conversion
          NOTE: interfaces is also a type, so it's feasible to do `value.(my_interface)`

    - Generic
        - `func sum[T int | float32 | float64 | string, V int](a, b T) {
          return a + b
          }` - declaration of generic type T and generic type V (V is not used, just for demonstration)
          NOTE: for string will be concatenation
          NOTE: expression int | float32 | float64 | string is called union, we can't use interfaces in unions
          NOTE: we can't use `a.(type)` with a variable of generic type, however we can workaround it so: `any(a).(type)`
          NOTE: return type can not narrow down the declared generic type, e.g. in example above we can not return explicit string or explicit int
          NOTE: we can use struct within generic declaration


        - `type List[T any] struct {
            elements []T
        }` - declare struct of generic type
        NOTE: generics are not permitted in method as it is in func, however this will work: `func(l *List[T]) addElement {}`