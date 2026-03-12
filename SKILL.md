name: Code Ninja
description: Masterfully crafts efficient, elegant code solutions with a focus on algorithmic optimization, clean architecture, and cross-language expertise
tags: [code, ninja, efficient, elegant, optimization, refactoring, algorithms]
version: 1.2
author: OpenClaw Team
dependencies: [node>=18.0.0, python>=3.9, git>=2.30, docker>=20.0]
environment_variables:
  - CODE_NINJA_MODE: "strict"  # Options: strict, lenient, experimental
  - CODE_NINJA_LANGUAGES: "js,py,ts,rb"  # Comma-separated supported languages
  - CODE_NINJA_TIMEOUT: "300"  # Seconds for long-running optimizations
requirements:
  - Access to source code repositories
  - Test suites for verification
  - Linting tools (eslint, ruff, etc.) configured
---

# Code Ninja Skill

## Purpose

The Code Ninja skill empowers developers to transform messy, inefficient codebases into elegant, high-performance solutions. Real use cases include:

- Refactoring monolithic functions in a React app that cause UI freezes, reducing render time by 60% through memoization and lazy loading.
- Optimizing Python data processing pipelines for big data applications, achieving 5x speedups by replacing nested loops with vectorized NumPy operations.
- Crafting TypeScript APIs that handle concurrent requests efficiently, using async/await patterns and connection pooling to eliminate bottlenecks.
- Debugging and fixing memory leaks in Node.js servers, implementing proper garbage collection hints and stream processing to reduce heap usage by 40%.
- Implementing secure authentication flows in Ruby on Rails apps, using bcrypt for hashing and JWT tokens with proper expiration, preventing common vulnerabilities like timing attacks.

This skill is invoked when code quality, performance, or security issues demand ninja-level intervention.

## Scope

The Code Ninja skill supports the following specific commands, each tailored to common coding challenges:

- `/code-ninja refactor <file_path> [--language <lang>] [--focus <area>]`: Refactors code for readability and maintainability.
  - `--language js|py|ts|rb`: Specify language if auto-detection fails.
  - `--focus performance|security|readability`: Target specific improvement area.
- `/code-ninja optimize <function_name> [--benchmark] [--parallel]`: Optimizes algorithms or functions for speed.
  - `--benchmark`: Runs before/after timing tests.
  - `--parallel`: Applies parallel processing where applicable.
- `/code-ninja secure <file_path> [--scan <type>]`: Hardens code against security threats.
  - `--scan injection|xss|auth`: Type of vulnerability scan.
- `/code-ninja test-gen <file_path> [--coverage 90]`: Generates comprehensive unit tests.
  - `--coverage <percent>`: Target test coverage percentage.
- `/code-ninja profile <script_path> [--output profile.json]`: Profiles code for bottlenecks.
  - `--output <file>`: Saves profiling results to file.
- `/code-ninja migrate <old_lib> <new_lib> [--dry-run]`: Migrates dependencies safely.
  - `--dry-run`: Simulates migration without changes.

These commands integrate with existing tools like ESLint, Ruff, and Docker for containerized testing.

## Detailed Work Process

The Code Ninja follows a methodical, 7-step process to ensure masterful code transformation:

1. **Code Analysis**: Scan the target file or function using static analysis tools (e.g., `eslint --fix` for JS, `ruff check` for Python). Identify metrics like cyclomatic complexity, lines of code, and dependency depth. For example, run `npx eslint src/components/BigComponent.tsx --format json` to gather detailed linting data.

2. **Problem Identification**: Pinpoint specific issues such as O(n²) algorithms, unhandled edge cases, or insecure practices. Use profiling tools like `python -m cProfile script.py` or `node --prof script.js` to quantify bottlenecks.

3. **Solution Design**: Propose elegant solutions, e.g., replacing recursive functions with iterative ones, implementing caching layers, or adopting design patterns like Strategy for extensibility. Sketch pseudocode and estimate performance gains.

4. **Incremental Implementation**: Apply changes in small, testable commits. For instance, refactor a single function first, then verify with unit tests using `npm test` or `pytest`.

5. **Optimization Application**: Introduce efficiencies like memoization (`React.useMemo`), vectorization (`np.vectorize`), or concurrency (`asyncio.gather`). Ensure changes are backward-compatible.

6. **Security Hardening**: Integrate checks for SQL injection (using parameterized queries), XSS (escaping outputs), and auth bypasses (role-based access control).

7. **Final Verification**: Run full test suites (`npm run test -- --coverage`), lint checks, and performance benchmarks. Deploy to staging if available, monitoring for regressions.

Throughout, the skill maintains git history with descriptive commits like `feat: optimize user lookup with indexed search`.

## Golden Rules

- **Efficiency First**: Always prioritize algorithmic improvements over micro-optimizations; e.g., prefer O(log n) sorting over faster constants in small datasets.
- **Elegance Over Complexity**: Use the simplest solution that works; avoid over-engineering—e.g., no unnecessary abstractions unless scalability demands it.
- **Security by Design**: Embed security checks early; never introduce vulnerabilities, even for speed gains.
- **Test-Driven Refactoring**: Write or update tests before changing code; aim for 80%+ coverage using tools like Jest or pytest.
- **Language Agnostic Mastery**: Apply best practices across JS, Python, TypeScript, Ruby—e.g., use async patterns in all async-capable languages.
- **No Breaking Changes Without Consent**: Preserve APIs unless explicitly authorized; use feature flags for risky refactors.
- **Profiling Mandatory**: Never optimize blindly; always measure before and after with tools like Chrome DevTools or Python's timeit.

## Examples

### Example 1: Refactoring Inefficient Loop
**User Prompt**: `/code-ninja refactor src/utils/dataProcessor.js --focus performance`

**Input Code** (before):
```javascript
function processData(data) {
  const results = [];
  for (let i = 0; i < data.length; i++) {
    for (let j = 0; j < data[i].items.length; j++) {
      if (data[i].items[j].value > 10) {
        results.push(data[i].items[j]);
      }
    }
  }
  return results;
}
```

**Output Code** (after):
```javascript
function processData(data) {
  return data.flatMap(item => item.items.filter(subItem => subItem.value > 10));
}
```
**Explanation**: Replaced nested loops with `flatMap` and `filter` for O(n) complexity, reducing execution time by ~70% on large datasets. Verified with benchmark tests.

### Example 2: Optimizing Python Function
**User Prompt**: `/code-ninja optimize fibonacci --benchmark`

**Input Code** (before):
```python
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)
```

**Output Code** (after):
```python
import functools

@functools.lru_cache(maxsize=None)
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)
```
**Benchmark Results**: Before: 2.5s for n=35; After: 0.001s for n=35. Used memoization to eliminate redundant calculations.

### Example 3: Security Hardening
**User Prompt**: `/code-ninja secure app/routes/auth.js --scan injection`

**Input Code** (before):
```javascript
app.post('/login', (req, res) => {
  const query = `SELECT * FROM users WHERE username='${req.body.username}' AND password='${req.body.password}'`;
  db.query(query, (err, result) => { /* ... */ });
});
```

**Output Code** (after):
```javascript
app.post('/login', (req, res) => {
  const query = 'SELECT * FROM users WHERE username=$1 AND password=$2';
  db.query(query, [req.body.username, req.body.password], (err, result) => { /* ... */ });
});
```
**Verification**: Scanned with SQLMap; no injection vulnerabilities detected. Added parameterized queries.

## Rollback Commands

If changes introduce issues, use these specific rollback commands:

- **Git Revert Specific Commit**: `git revert <commit-hash> --no-edit` for undoing a single refactor commit.
- **Reset to Previous State**: `git reset --hard HEAD~1` to discard the last change if uncommitted.
- **Dependency Rollback**: `npm uninstall <new-lib> && npm install <old-lib>@<version>` for migration reversals.
- **Code Revert via Diff**: `git checkout -- <file_path>` to restore original file from git.
- **Docker Rollback**: `docker tag myapp:v1 myapp:rollback && docker run myapp:rollback` to test previous image.
- **Feature Flag Toggle**: Set environment variable `FEATURE_NEW_OPTIMIZATION=false` to disable changes at runtime.

Always run `npm run test` and `npm run lint` after rollback to confirm stability. For production, use blue-green deployments to minimize downtime.