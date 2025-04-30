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
```
