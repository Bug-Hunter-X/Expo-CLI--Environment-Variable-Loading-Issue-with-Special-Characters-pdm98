# Expo CLI Environment Variable Issue

This repository demonstrates a bug in the Expo CLI where environment variables containing special characters (underscores, hyphens) are not properly loaded during development builds.  Standard environment variables without special characters work correctly.

## Bug Description

When using a .env file with environment variables that include underscores or hyphens, these variables are either ignored or cause unexpected behavior in the Expo application. This issue only occurs during the development build process; the build process itself seems to work but the environment variables are not properly applied.

## Reproduction Steps

1. Clone this repository.
2. Run `npm install` or `yarn install`.
3. Start the development server using `expo start`.
4. Observe the console output and the app's behavior.  The variables without special characters will display, while those with special characters will either not display or display an unexpected value.

## Solution

The bug was addressed by adding a mechanism in my project to specifically handle the loading and parsing of environment variables, particularly those with special characters. This involved handling the process of reading the .env file and directly inserting those variables into my javascript environment variables.  See bugSolution.js for more details.

## Note

This issue may be related to how Expo CLI internally parses and handles the .env files. This may be caused by incompatibilities between different versions of libraries and Expo. Future versions of Expo might address this issue.