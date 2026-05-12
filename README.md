<p align="center"><img src="logo.png" alt="ShegerPay" width="200" /></p>

# ShegerPay Dart / Flutter SDK

[![Version](https://img.shields.io/badge/version-2.2.0-blue)](https://pub.dev/packages/shegerpay)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

Official Dart/Flutter SDK for ShegerPay — verify Ethiopian bank payments (CBE, Telebirr, BOA, Awash).

## Install

```bash
flutter pub add shegerpay
# or
dart pub add shegerpay
```

Or add to `pubspec.yaml`:
```yaml
dependencies:
  shegerpay: ^2.2.0
```

## Quick Start

```dart
import 'package:shegerpay/shegerpay.dart';
import 'dart:io';
import 'dart:convert';

final client = ShegerPay(apiKey: 'sk_live_YOUR_API_KEY');

// Verify a payment
final result = await client.verify(
  transactionId: 'FT26062K7WMY',
  amount: 1000,
  provider: 'cbe',
);
print(result.verified); // true/false

// Verify without amount (lookup only)
final result2 = await client.verify(
  transactionId: 'FT26062K7WMY',
  provider: 'telebirr',
);
print(result2.status);

// Verify from receipt screenshot
final imageBytes = await File('receipt.png').readAsBytes();
final imageBase64 = base64Encode(imageBytes);
final imgResult = await client.verifyImage(
  screenshot: imageBase64,
  provider: 'cbe',
);
print(imgResult.verified);

// Create payment link
final link = await client.createPaymentLink(
  title: 'Order #1234',
  amount: 1500,
  currency: 'ETB',
);
print(link['url']);

// Get supported providers
final providers = await client.getProviders();
```

## Supported Providers
`cbe` · `telebirr` · `boa` · `awash` · `ebirr_kaafi` · `ebirr_coop`

## Requirements
- Dart 2.17+
- Flutter 3.0+ (if using with Flutter)


## Support
- 📚 Docs: https://shegerpay.com/docs
- 💬 Telegram: [@shegerpay_0](https://t.me/shegerpay_0)
- 📧 Email: support@shegerpay.com
