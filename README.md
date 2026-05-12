<p align="center"><img src="logo.png" alt="ShegerPay" width="200" /></p>

# ShegerPay Dart/Flutter SDK

Official Dart/Flutter SDK for ShegerPay — Ethiopian payment verification.

## Install

```yaml
# pubspec.yaml
dependencies:
  shegerpay: ^2.2.0
```

Or via CLI:

```bash
dart pub add shegerpay
# or
flutter pub add shegerpay
```

## Quick Start (Flutter)

```dart
import 'package:shegerpay/shegerpay.dart';

final client = ShegerPay(apiKey: 'sk_live_...');

final result = await client.verify(
  transactionId: 'FT26062K7WMY',
  amount: 1000,
  provider: 'cbe',
);

if (result.verified) {
  print('Payment confirmed: ${result.transactionId}');
}
```

## Requirements

- Dart SDK 2.17+
- Flutter 3.0+ (if using with Flutter)

## License

MIT
