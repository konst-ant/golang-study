- Basic CLI commands
    - `go mod init <module_name>`
      convention for module name is like: github.com/path/../path/module
      if you want to publish module can use only path/../path/module
      as a result we get go.mod file in the project. note we can rename module directly in go.mod
    - `go build`
      builds project, with outcome build of executable
      resulting executable is native (for any OS platform), is self-contained and not requiring Go installed
      resulting executable will have name of the module, e.g. for module path/../path/module - named 'module'
    - `go run <file.go>`
      execute without building executable, will require Go installed
      NOTE: in more general case e.g. when package spans several files, we need to do `go run .` from project root rather than by file name
    - `go get github.com/fatih/color` - install Go package from github
      After installation package and it's deps (including transients) will appear in go.mod, and file go.sum will be changed

      NOTE: we should save into git go.mod, and then `go get` will restore all deps on new laptop
    - `go mod tidy` - cleans-up go.mod file to keep used deps, remove unused deps, and sort deps as direct / indirect (transient)
      NOTE: this is recommended to be run when you do any change of used deps in the project (and before committing changes)