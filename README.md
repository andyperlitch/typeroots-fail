# Getting `typeRoots` to work for custom declaration files

This project is intended to show how to actually use the `typeRoots` option of tsconfig. It is woefully underdocumented and difficult to remember how to do right.

## The Problem: You have to add `paths`

The main issue is that setting `typeRoots` alone is not enough. You ALSO have to add/update the `paths` option of your tsconfig so that the file is actually found:

```json
{
  "baseUrl": ".",
  "typeRoots": ["./node_modules/@types", "./custom-types"],
  "paths": {
    "*": ["*", "./custom-types/*"]
  }
}
```

The frustrating part is that you don't have to explicitly add `./node_modules/@types/*` to the `paths` config.
