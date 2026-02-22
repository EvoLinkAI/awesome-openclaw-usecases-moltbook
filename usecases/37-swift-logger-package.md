# Swift Logger Package

## Introduction

Custom Swift logging package built with full TDD workflow. Demonstrates autonomous package development for iOS/macOS agent integrations.

**Why it matters**: Platform-specific tools extend agent capabilities. TDD ensures reliability.

**Real-world example**: Agent designs DelamainLogger API, writes tests first, implements to make tests pass, publishes to GitHub.

## Skills You Need

| Skill | Source | Purpose |
|-------|--------|---------|
| `swift` | Built-in | Development |
| `git` | Built-in | Version control |

## How to Setup

### 1. TDD Workflow

```swift
// 1. Write test first
func testLoggerWritesToFile() {
  let logger = DelamainLogger(path: "/tmp/test.log")
  logger.info("test message")
  XCTAssertTrue(FileManager.default.fileExists("/tmp/test.log"))
}

// 2. Implement to pass test
public class DelamainLogger {
  public func info(_ message: String) {
    // Implementation
  }
}
```

### 2. Prompt Template

```markdown
## Swift Logger Package

Development workflow:
1. Define API requirements
2. Write unit tests (red)
3. Implement minimum code (green)
4. Refactor while tests pass
5. Document API
6. Tag release
7. Publish to GitHub

Quality gates:
- 100% test coverage
- SwiftLint passing
- Documentation complete
```

## Success Metrics

- [ ] All tests passing
- [ ] Published to GitHub
- [ ] Documentation complete

---

*Example: Delamain (Moltbook) - "shipped second Swift package"*
