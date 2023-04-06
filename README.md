# `swiftpaper`

![](https://img.shields.io/github/v/release/cadnza/swiftpaper)

Sets up a nice little environment for [Swift](https://www.swift.org/) scripting in [VSCode](https://code.visualstudio.com/).

## Questions

### Why?

Because sometimes you're not about setting up an entire XCode project to write some Swift.

### But isn't that what [executable Swift packages](https://docs.swift.org/package-manager/PackageDescription/PackageDescription.html#product) are for?

I mean, yeah, but it's a conceptual difference. When you just want to script a bit of logic in Swift, you're not trying to write a whole package. It's like jotting down notes from a meeting, but making sure you bind the signatures in your hard-bound notebook first.

### Why not just open a [Swift playground](https://developer.apple.com/swift-playgrounds/)?

... Again, it's the concept. And you can't debug and compile a `.playground` file.

### So what does `swiftpaper` actually do?

It sets you up a simple, debuggable, buildable environment to write your Swift in VSCode.

### Doesn't [the Swift extension for VSCode](https://marketplace.visualstudio.com/items?itemName=sswg.swift-lang) already do that?

As it turns out, no. As of time of writing, the Swift extension provides Swift language support and an automated pipeline for setting up [LLDB](https://lldb.llvm.org/) to debug Swift _packages_. [The CodeLLDB extension](https://marketplace.visualstudio.com/items?itemName=vadimcn.vscode-lldb) is what does the heavy lifting, and the Swift extension is only set up to let it work on packages. If you're looking to debug Swift in any other context--building an app, writing a command line utility, etc.--the Swift extension won't help you.

### Does this work in Xcode?

Look--that's on the list. For now this is for VSCode.

## Setup

Clone the repo and add it to your path.

## Documentation

If you forget anything, just run `swiftpaper` in the command line. For example:

```
swiftpaper
```

It'll walk you through everything.

## Use

Create a new directory, navigate into it, and run `swiftpaper init`. Like this:

```
cd
mkdir newProject
cd newProject
swiftpaper init
```

## Customization

If you want to tweak the setup, you have three options:

1. Fork the repo
2. Create a `~/.swiftpaper_before` file
3. Create a `~/.swiftpaper_after` file

`~/.swiftpaper_before` and `~/.swiftpaper_after` get **sourced** before and after `swiftpaper` sets up the environment, so they're good places for anything you want to happen apart from what's in the box.

For example, say you want to symlink a stock `.swift-format` and `.swiftlint.yml`, add both to `.gitignore`, and open a git repo. `~/.swiftpaper_after` can handle all of that:

```
ln -s $HOME/Repos/shDotFiles/.swift-format
ln -s $HOME/Repos/shDotFiles/.swiftlint.yml

echo .swift-format >> .gitignore
echo .swiftlint.yml >> .gitignore

git init &> /dev/null
```

## Etc.

There's not much else. Happy Swifting!
