Section: [[Systems Programming (Root)]]

Recall that the compiling process for C files using gcc can get quite complicated. The make command provides a ruleset to compile files together. This requires a document called a "Makefile"

The format of each rule is as follows:

```
target [target...]: [component...]
	[command 1]
	...
	[command n]
```

The target is what you want to make and the component is something which needs to exist
# Pattern Rules

We can specify a pattern rule to match multiple files, like compiling C files into object files