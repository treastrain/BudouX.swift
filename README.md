# BudouX.swift

[BudouX](https://github.com/google/budoux) Swift implementation.

BudouX is the machine learning powered line break organizer tool.

## How it works

![](Docs/assets/sample.png)

The original [BudouX](https://github.com/google/budoux) uses HTML markup to ensure that clauses are broken properly. BudouX.swift inserts a `U+2060`(word joiner) and a `U+200B`(zero width space) between each character and clause to ensure that Cocoa's UI component to do the line breaking properly.

Here is a sample project in this repository "Example.swiftpm".

CLI tool `budoux-swift` contains in this repository as well.

## Usage

You can get a list of phrases by feeding a sentence to the parser.

```swift
import BudouX
// Load Default Japanese Parser
let parser = Parser()
// Parse
print(parser.parse("あなたに寄り添う最先端のテクノロジー。"))
// ["あなたに", "寄り添う", "最先端の", "テクノロジー。"]
```

You can also translate an Swift's `String` with word joiners and zero width spaces for semantic line breaks.

```swift
import BudouX
// Load Default Japanese Parser
let parser = Parser()
let sample = "あなたに寄り添う最先端のテクノロジー。"
print(parser.translate(sentence: sample))
// あ⁠な⁠た⁠に​寄⁠り⁠添⁠う​最⁠先⁠端⁠の​テ⁠ク⁠ノ⁠ロ⁠ジ⁠ー⁠。
```

Here's a convinience String extension method as well.

```swift
import BudouX

let sample = "あなたに寄り添う最先端のテクノロジー。"
print(sample.budouxed())
// あ⁠な⁠た⁠に​寄⁠り⁠添⁠う​最⁠先⁠端⁠の​テ⁠ク⁠ノ⁠ロ⁠ジ⁠ー⁠。
```

## Install

Support Swift Package Manager only. There are no plans to support other package management tools at this time.

```swift
package.append(
    .package(url: "https://github.com/griffin-stewie/BudouX.swift", from: "0.1.0")
)

package.targets.append(
    .target(name: "Foo", dependencies: [
        .productItem(name: "BudouX", package: "BudouX.swift")
    ])
)
```
