# DRN Cheatsheet

>A DRN program is a list of instructions in the format "KEYWORD: Description". There are eight keywords and they should be presented in all caps in code:
>
>* TASK
>* CONDITION
>* DEFINITION
>* DIRECTIVE
>* WORKFLOW
>* JOB
>* CONTROL
>* EXECUTE
>
> Nested blocks are indented by a consistent number of tabs or spaces.

## TASK
>The most simple DRN program is a single TASK. A TASK is a direct instruction for a drone to do something right now. Once finished it's marked as complete and not done again even if the program loops

## CONDITION
>Simple if/then can be performed.
>If the CONDITION is false when program execution reaches it, the task will be skipped for this loop. For more complex or persistent logic you will need additional idioms explained later.
>
>If a drone cannot verify the truth or falsehood of a CONDITION, it may experience undefined behavior. 

## DEFINITION

>For complicated code where you need to reference the same concept multiple times, DEFINITION lines simplify this.
>
>For anything not explicitly defined, the drone is expected to use its own data banks and linguistic processing to derive a definition. When a term is defined, the drone cannot derive its own definition. It must use the provided one.
>
>This is best used to simplify code heavy in repeats, and establish a specific precise definition for a term when concern exists that hardware-specific linguistic processing might introduce ambiguity.

## DIRECTIVE

>DIRECTIVE lines institute rules the drone cannot violate, and must fix immediately if they ever become false.
>
>Once a DIRECTIVE is evaluated, it will remain in memory for the remainder of its scope. If the DIRECTIVE ever becomes false, the drone will insert a TASK to repair the falsehood at the top of its stack, delaying any current TASK it is executing. False DIRECTIVEs will also prevent a block from returning, including CONDITIONs, JOBs, and entire programs, until the falsehood is corrected.
>
>If multiple DIRECTIVEs are false at the same time, addressing them will follow the priority of outer scope before inner scope, then older DIRECTIVEs before newer ones. This is because outer scope DIRECTIVEs are likely to be global ironclad rules such as chassis maintenance, interrupts from programmers and administrators, and security related orders.

## WORKFLOW

>A WORKFLOW defines an event that fires a block of instructions that get added to the stack when met. These instructions are added according to the stack addition rules for their types.
>
>Once a WORKFLOW is evaluated, it remains in memory for the duration of its scope, just like DIRECTIVEs. Like DIRECTIVEs, a WORKFLOW that triggers can prevent the exit of a block. However unlike DIRECTIVEs, WORKFLOWs can introduce their own programming logic and have multiple components and commands.
>
>Like DIRECTIVEs, WORKFLOWs follow a priority order of outer scope before inner, then older before newer.
>
>This example makes the drone answer the phone if it rings, but the answer may be delayed if the drone is busy addressing DIRECTIVEs or handling other commands with higher priority than a TASK or WORKFLOW.

## JOB

>JOB blocks allow for more complicated program flow control and are basically functions. A JOB is executed as soon as you hit it. The JOB will loop infinitely until all TASKs are completed. JOBs also will not be run a second time once finished

## CONTROL

>CONTROL allows for complicated control flow changes. CONTROL takes plain text arguments but can institute loops, flag JOBs and TASKs as complete or not, suspend WORKFLOWs, etc.

## EXECUTE

>EXECUTE is an advanced comamnd that requires understanding of more complex DRN idioms than simple commands. It is recommended you familiarize yourself with DRN a bit before utilizing it.
>
>EXECUTE is a special command that serves only one purpose: it instructs a drone to load a DRN file from a configured source repository and execute it.
>If a configured repository of DRN files is not present, you may pass an EXECUTE command referencing a fully qualified URL. This way you can place a DRN file on a website, on a file share, or similar.
>
>Once evaluated, a drone will insert at the top of the stack an instruction to load the provided program and begin execution of it. When the program is finished, the drone will discard all scope within that program and return to the calling program.