Section: [[Cyber Security (Root)]]
# Traces

Systems provide **atomic actions** like opening files and basic arithmetic. Combining them forms a **trace**, like a file management system. **Security policies** define which traces are secure.

**Malicious code execution** is the execution of a trace which is possible, but not secure.
## Closed System

These have a predetermined set of possible traces
## Open System

All actions are enabled by default, but non-secure traces are detected and avoided
# Reference Monitors

These are in charge of [[#Open System|open systems]] to check traces, they should be NEAT:

- Non-bypassable
- Evaluable
- Always-invoked
- Tamperproof
# Execution

Malicious code execution is the execution of a non-secure trace. Therefore it is only possible in [[#Open System|open systems]] where the [[#Reference Monitors|reference monitor]] is not **NEAT** in any given way
## Reverse Engineering

- Understanding how a product works based on the final product
- This allows us to bypass security checks
# Code Injection
## XSS

- Modifying a webpage on client-side by injecting content within that given by the server
## SQL Injection

- Often SQL queries take input data and return data. If we modify our input to restructure the query through symbols and syntax, we can create unexpected outputs like so:

` SELECT COUNT(*) FROM "users" WHERE user = "$u" and password = "$p" `

If user = `" or "1" = "1" --` and password = `""` then we get:

` SELECT COUNT(*) FROM "users" WHERE user = "" or "1" = "1" --" and password = "" `

This returns data for all users, since `"1" = "1"` is true and anything after a `--` is ignored
# Prevention

- Input sanitisation ensures that input content doesn't escape its scope
	- Like removing certain strings from variables
	- Detecting SQL or JS in web forms
	- Looking for python script in web forms
- Close the system by removing features that can be misused
	- Like preventing installation of new programs
- Analyse the input to allow only those that lead to secure behaviour
	- Signature matching checks for known patterns of bad code in inputs
	- Anomaly detection detects deviation from normal behaviour
- Confining code execution to only execute code at the privilege of the executing agent
	- Running queries on read-only permissions