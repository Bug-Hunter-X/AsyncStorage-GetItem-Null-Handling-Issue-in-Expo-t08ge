# AsyncStorage GetItem Null Handling Issue in Expo

This repository demonstrates a common, yet subtle, error when working with AsyncStorage in Expo applications.  The problem occurs when attempting to access a key that doesn't exist in AsyncStorage.  The asynchronous nature of `AsyncStorage.getItem` can lead to unexpected behavior if you don't properly handle the `null` value that's returned when the key is missing.

This is not a typical `TypeError: null is not an object` as the null value is not explicitly checked in a naive approach.

The `bug.js` file shows the problematic code.  The `bugSolution.js` file presents a corrected version that uses `async/await` and proper error handling to address the issue.

## Problem and Solution

The core problem is that the asynchronous operation of `AsyncStorage.getItem` isn't waited for properly. The code tries to use the result before it's even available, causing an error. The solution is to use `async/await` to ensure the value is retrieved before any operations are performed on it.  Additionally, explicitly checking for `null` prevents errors when a key does not exist.