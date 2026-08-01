# moglang/encoding

Portable hexadecimal, Base64, percent-encoding, and checksum helpers for Mog.

## Install and import

From a Mog project directory:

```sh
mog add github.com/moglang/encoding@v0.2.0
```

```mog
const encoding = @import("github.com/moglang/encoding")

var wire str = encoding.base64Encode("Mog")
print(wire)                         // TW9n
print(encoding.base64Decode(wire)) // Mog
print(encoding.urlEncode("a b"))  // a%20b
print(encoding.adler32("Mog"))    // 022f0124
```

The canonical import is `github.com/moglang/encoding`. The complete public
contract is in `package.api.mog`.

## API behavior

- `hexEncode`/`hexDecode` convert string bytes to and from hexadecimal.
- `base64Encode`/`base64Decode` use canonical padded RFC 4648 Base64. The
  decoder rejects malformed characters, padding placement, and padding bits.
- `urlEncode`/`urlDecode` implement RFC 3986 percent encoding. A plus sign is
  treated literally; this is not HTML form encoding.
- `adler32` returns the standard Adler-32 value as eight lowercase hexadecimal
  digits. It is useful for accidental-corruption checks, not security.
- `legacyPolynomialChecksum` names the package's original non-standard
  polynomial checksum explicitly. `checksum` remains an alias for it so
  existing programs do not change behavior. New code should use `adler32`.

All helpers operate on Mog string bytes. They do not normalize Unicode text.
Decode failures raise a runtime error.

`tests/main.mog` contains successful vectors and round trips. Programs under
`tests/errors/` are negative fixtures and pass when the interpreter rejects
them.

## Compatibility

Version 0.2.0 requires Mog runtime `^0.1.4`. It is a source package and has no
native build or operating-system dependency. It is licensed under
GPL-3.0-only; see `LICENSE`.
