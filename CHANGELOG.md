# Changelog

## 2.2.1

### Fixed

- **Redirect signature verification never validated a real redirect.** The
  verifier computed a pre-audit payload; it now matches the backend signer
  exactly — HMAC-SHA256 hex over
  `status|short_code|transaction_id|amount_paid|currency`, with the amount taken
  verbatim from the query parameter rather than reformatted. Comparison is
  constant-time.
- **`PATCH` and `DELETE` requests were silently sent as `GET`.** The request
  helper only handled `POST` and `GET`, so every other verb fell through and hit
  the wrong endpoint.
- Added the missing `package:crypto` import required by the signature helpers.
- Removed an unused `dart:typed_data` import.

### Changed

- Version and `User-Agent` aligned at 2.2.1.
- Added `pubspec.yaml` so the SDK can be consumed as a package at all.
