# Objective-C KVO and Weak References: A Subtle Crash Bug

This repository demonstrates a common yet easily missed bug in Objective-C related to Key-Value Observing (KVO) and weak references.  When using weak references with KVO, it's crucial to remove the observer before the observed object is deallocated to prevent crashes.

## The Bug
The `weakKVOBug.m` file contains code that adds a weak observer to an object.  If the observed object is deallocated before the observer is removed, accessing the object after deallocation leads to an EXC_BAD_ACCESS crash.

## The Solution
The `weakKVOFix.m` file shows the corrected code.  The solution involves ensuring the observer is removed in the appropriate dealloc method or using techniques to handle the case where the observed object might be deallocated prematurely. 

This issue is often difficult to debug because the crash doesn't always occur consistently, depending on the timing of object deallocation and garbage collection.