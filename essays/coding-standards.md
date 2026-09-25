---
layout: essay
type: essay
title: "Professionals Have Standards"
# All dates must be YYYY-MM-DD format!
date: 2026-09-23
published: true
labels:
  - Programming
  - Coding Standards
  - ESLint
  - VSCode
---

<img width="200px" class="rounded float-start pe-4" src="../img/Output Pictures/thinking-person.png">

Having standards just makes sense when we want to maintain a certain level of quality not just in our own lives but also in the way we write code with the concept of coding standards.

## What are coding standards?
Not to be confused with code writing conventions, coding standards are created by groups, organizations, or companies. These standards require that code be formatted or written according to how the creator of the standard prefers. 
For example, an additional new line at the end of the program normally doesn’t break any functionality in Javascript, but the Airbnb Javascript coding standards would flag this as an error and require it be fixed.


## Why should we have to follow coding standards?
If you’ve ever looked at someone else’s code and wondered what would possess them to write it in such a way, then you can already see some of the intention behind coding standards.

Coding standards are put into place because the groups that create them have a vested interest in ensuring that code that is written for their purposes follows a certain format and style. By keeping these rules consistent, maintaining, updating, and parsing code becomes much more streamlined and integrating it into existing codebases becomes much easier. These standards may or may not deal with the actual functionality of the code or syntax but rather are rules to enforce code style.

 ## My experience with coding standards
As part of my ICS 314: Software Engineering I class, we use our own set of coding standards through ESLint in VSCode. The process involves the following:
```
Install:
sample.eslintrc.js, rename it to .eslintrc.js.
sample.eslintignore, rename it to .eslintignore.
sample.gitignore, rename it to .gitignore.
sample.package.json, rename it to package.json.
sample.tsconfig.json, rename it to tsconfig.json.

In terminal:
Invoke npm install to install ESLint.
```

These files provide the settings and plugins that npm will install for ESLint to reflect our class coding standards. Some examples of the rules include strings needing to use single quotes instead of double quotes, no leading spaces, and there can only be one new line at the end of the file.

Here is what is inside package.json
```json
{
  "name": "eslint_sample",
  "version": "1.0.0",
  "description": "Sample package.json for eslint",
  "devDependencies": {
    "@typescript-eslint/eslint-plugin": "^7.18.0",
    "@typescript-eslint/parser": "^7.18.0",
    "eslint": "^8.57.1",
    "eslint-config-airbnb": "^19.0.4",
    "eslint-config-airbnb-typescript": "^18.0.0",
    "eslint-plugin-import": "^2.32.0",
    "prettier": "^3.9.9",
    "prettier-eslint": "^17.1.2",
    "typescript": "^5.8.3"
  },
  "dependencies": {},
  "scripts": {
    "lint": "eslint *.ts",
    "lint-fix": "eslint *.ts --fix"
  },
  "private": true
}

```
