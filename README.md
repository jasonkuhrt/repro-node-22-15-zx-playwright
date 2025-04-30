# Repro For Node@22.15.0 + Playwright@1.52.0 + ZX@8.4.1

## TL;DR

```sh
pnpm start
```

## Details

1. You need to be using Node@22.15.0.

1. Run:

    ```sh
    pnpm install
    pnpm playwright test
    ```

1. Then observe an unexpected failure:

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

## Links

- https://github.com/microsoft/playwright/issues/35812
- https://github.com/google/zx/issues/1205
