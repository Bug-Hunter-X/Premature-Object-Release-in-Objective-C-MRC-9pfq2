# Premature Object Release in Objective-C Manual Reference Counting (MRC)

This repository demonstrates a common but subtle error in Objective-C's manual memory management (MRC): prematurely releasing an object before all references to it have been removed. This can lead to crashes or unpredictable behavior.

The `bug.m` file contains code exhibiting the problem.  The `bugSolution.m` file provides a corrected version.

## How to Reproduce

1. Clone this repository.
2. Open the project in Xcode (an older version supporting MRC may be needed).
3. Build and run. Observe the crash or unexpected behavior in the original code.
4. Examine the corrected code in `bugSolution.m` to see how the issue is resolved.

## Understanding the Issue

The core problem is failing to maintain a proper balance of `retain` and `release` calls.  An object's retain count must be zero before it's deallocated. If an object is released while still referenced, attempting to access it will likely result in a crash.