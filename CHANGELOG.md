# Changelog

## 0.2.0

- Rename package manifests, source files, imports, automation, and documentation from Mog to Kelvra; require Kelvra 0.2.0 or newer.

- Correct the minimum supported runtime to Kelvra 0.1.4, the first release that
  embeds its configured package-compatibility version correctly.
- Add pinned CI/release automation with tag checks, 0.1.4/current-runtime tests,
  checksummed archives, and automated action updates.
- Add the standard `adler32` checksum with fixed-width hexadecimal output.
- Add `legacyPolynomialChecksum` as an explicit name for the original
  non-standard algorithm; retain `checksum` as a compatibility alias.
- Document installation, imports, byte-level behavior, failure behavior, and
  runtime compatibility.
- Expand coverage for empty inputs, round trips, RFC unreserved characters,
  canonical Adler-32 vectors, legacy compatibility, and malformed inputs.
- Correct manifest license metadata to `GPL-3.0-only` to match `LICENSE`.

## 0.1.1

- Reject malformed Base64 padding instead of silently accepting invalid input.
- Require Kelvra runtime 0.1.1 or newer for the string primitive support used by this package.

## 0.1.0

- Initial foundation package contract.
