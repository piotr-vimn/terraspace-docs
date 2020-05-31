## Modules vs Stacks

Both modules and stacks are terraform modules. The difference is organizational and how they are meant to be used.

* Modules modules are smaller pieces of reusable code. Generally, it contains reusable and non-business-specific logic.
* Stacks are meant to be used to group together modules. Generally, this is where business-specific logic goes.

For example, the "core" stack could be designed to create using the "vpc" module. Also, the "wordpress" stack cloud use modules like the "instance" and "rds" modules.