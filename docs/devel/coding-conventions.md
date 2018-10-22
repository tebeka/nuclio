# Code Conventions

  - Baseline
    - Follow the latest kubernetes coding conventions: https://github.com/kubernetes/kubernetes/blob/release-1.1/docs/devel/coding-conventions.md
  - Go
    - Functions should be short and call out to other short functions
    - Choose verbose, descriptive, human readable names (`handler` not `hdlr`, `handleFunctioncrAdd` not `add`). The only exception is with receivers (`func (c *Client) foo()`)
    - Insert newlines before comments and after blocks of code (e.g., a non-nested `}` within a function)
    - Functionality and state must be contained within instantiatable objects. Package level state variables are discouraged
    - Within a struct, exported methods go first, followed by non-exported methods. This holds true to methods conceptually belonging to a struct (e.g., "static" methods without receivers)
    - Follow the below convention for file-related variables (this has been known to save lives):
      - `somethingFileName`: The name of a file, without its location. e.g., `example.go`
      - `somethingDir`: The location of a directory. e.g., `/a/b/c`
      - `somethingPath`: The full location of a resource, which can be _either_ a file or directory (e.g., `/a/b/c` or `/a/b/c/example.go`). If the resource can _only_ be a dir, use `somethingDir`
      - `somethingFile`: The file object of something
      - `somethingFileContents`: The result of reading the file, i.e., with ReadAll
  - Testing
    - Use testify and testify suites (see existing examples)
    - Assert with `suite.Require().<assertion>`
    - Function order within a test suite should be:
      - Suite struct declaration
      - SetupSuite (if applicable)
      - SetupTest (if applicable)
      - TearDownTest (if applicable)
      - TearDownSuite (if applicable)
      - Tests
      - Unexported helpers