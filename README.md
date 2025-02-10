# Express.js Route Handler Missing Error Handling for Invalid User ID

This repository demonstrates a common error in Express.js route handlers: the lack of proper error handling for invalid input.  Specifically, the `/users/:id` route attempts to parse the `id` parameter as an integer but doesn't handle cases where the ID is not a valid integer, resulting in potential crashes or unexpected behavior.

## Bug Description

The `bug.js` file contains the erroneous code. The route handler doesn't check if `req.params.id` is a valid number before parsing it with `parseInt()`. If a non-numeric value is provided, `parseInt()` will return `NaN`, leading to the `users.find()` method failing silently or throwing an error (depending on how the `users` array is structured).

## Solution

The `bugSolution.js` file shows a corrected version of the code.  The solution includes error handling to check if `parseInt(userId)` is a valid number (not `NaN`) before proceeding with finding the user.  If the ID is invalid, it returns a proper 400 Bad Request response.