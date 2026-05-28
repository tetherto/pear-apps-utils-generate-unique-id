# pear-apps-utils-generate-unique-id

Generate unique IDs for Pear Apps

## Features

- Generates a cryptographically secure random identifier using `crypto.randomUUID()` when available, falling back to a 32-character hex string.
- Accepts an optional `skipUUID` flag to always produce the hex-string format.
- Works in browser, Node.js, and Pear runtimes — any environment that exposes `globalThis.crypto`.

## Security Notice

1. To ensure the security and integrity of your projects, please note that official PearPass packages are distributed exclusively through our GitHub organization.
2. Any packages with similar names found on the npm registry or other third-party package managers are not affiliated with PearPass and should be strictly avoided. We recommend installing directly from this repository to ensure you are using the verified, open-source version.

## Installation

Install the package using npm:

```bash
npm install git+https://github.com/tetherto/pear-apps-utils-generate-unique-id.git
```

## Testing

To run the tests, use the following command:

```bash
npm test
```

## Usage Examples

### Default (UUID v4 when available)

```javascript
import { generateUniqueId } from '@tetherto/pear-apps-utils-generate-unique-id';

const id = generateUniqueId();
// => "f47ac10b-58cc-4372-a567-0e02b2c3d479"  (UUID v4)
```

### Force hex-string format

Pass `{ skipUUID: true }` to always get a 32-character hex string, even on runtimes that support `crypto.randomUUID()`.

```javascript
const hexId = generateUniqueId({ skipUUID: true });
// => "a3f1c2d4e5b6a7f8c9d0e1f2a3b4c5d6"  (32-char hex)
```

### API

```
generateUniqueId(options?)
```

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `options.skipUUID` | `boolean` | `false` | When `true`, skips `crypto.randomUUID()` and returns a 32-char hex string instead |

**Returns** `string` — UUID v4 or 32-character hex string.

**Throws** `Error` if `globalThis.crypto` is unavailable (no secure random source).

> **Note:** This function is intended for generating record/session identifiers. It is **NOT** suitable for secrets, authentication tokens, or authorization keys.

## Related Projects

- [@tetherto/pearpass-app-mobile](https://github.com/tetherto/pearpass-app-mobile) - A mobile app for PearPass, a password manager
- [@tetherto/pearpass-app-browser-extension](https://github.com/tetherto/pearpass-app-browser-extension) - A browser extension for PearPass, a password manager
- [@tetherto/pearpass-app-desktop](https://github.com/tetherto/pearpass-app-desktop) - A desktop app for PearPass, a password manager

## License

This project is licensed under the Apache License, Version 2.0. See the [LICENSE](./LICENSE) file for details.
