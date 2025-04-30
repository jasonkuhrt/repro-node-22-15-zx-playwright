# Repro For Node@22.15.0 + Playwright@1.52.0 + ZX@8.4.1

Run:

```
pnpm start
```

## Details

You need to be running Node v22.15.0.

<details>
<summary>Example enforcement (for repro script)</summary>

```js
const expectedNodeVersion = 'v22.15.0'
const isRightNodeVersion = process.version === expectedNodeVersion

if (!isRightNodeVersion) {
  console.log(`Your Node version must be ${expectedNodeVersion}. Got: ${process.version}`)
  process.exit(1)
}
```
</details>

Then run tests and see failure:

```js
import { $ } from 'zx'

await $`pnpm playwright test`.nothrow().pipe(process.stdout)
```

```txt
Running 1 test using 1 worker

  ✘  1 repro.test.ts:8:1 › is there (5ms)


  1) repro.test.ts:8:1 › is there ──────────────────────────────────────────────────────────────────

    Error: expect(received).toBeDefined()

    Received: undefined

       7 |
       8 | test(`is there`, () => {
    >  9 |   expect($).toBeDefined()
         |             ^
      10 | })
      11 |
        at /Users/jasonkuhrt/projects/jasonkuhrt/repro-node-22-15-zx-playwright/repro.test.ts:9:13

    Error Context: test-results/repro-is-there/error-context.md

  1 failed
    repro.test.ts:8:1 › is there ───────────────────────────────────────────────────────────────────
```
