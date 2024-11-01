- Misc
    - `label1:` - declare label, which can be used as reference, e.g. break label1
    - `import math.rand.v2` - for random generator
    - `time` - package to use time
    - `os` - package for work with OS (create files, etc.)
    - `json` - package for marshall/unmmarshall JSON

    - Meta-Tags
      ```type Account struct {login string `json:"login" xml:"test"`} ```  - this is meta-teg, kind of annotation which can be used e.g. for
      serialization/des of objects from JSON etc. Standard package reflect
      uses meta-tags.
      
      NOTE: to be able marshall/unmarshall fields of the struct need being public that is "Login" instead of "login"

- Questions
    - Will `append(myDynamicSlice, 100)` allocate new memory and copy array to new memory? If yes, isn't is suboptimal?
    - How can I do join / subtract / ... of arrays / slices in Go?
    - Assume we have a dynamic slice `myDynamicSlice := []int{1, 2, 3}`, how can we remove the 0-th element from it? And would the address of the slide be changed (requiring change of variables)?
