# 1. Introducció a Flutter

## Què és Flutter?

Flutter és un framework per crear interfícies d'aplicacions amb **Dart**.

La interfície es construeix mitjançant widgets.

## Primera aplicació

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'RA2.1',
      home: Scaffold(
        appBar: AppBar(
          title: const Text('Primera aplicació'),
        ),
        body: const Center(
          child: Text('Hola Flutter!'),
        ),
      ),
    );
  }
}
```

## Idees clau

- `main()` és el punt d'entrada de l'aplicació.
- `runApp()` inicia la interfície Flutter.
- `MaterialApp` configura l'aplicació.
- `Scaffold` proporciona una estructura de pantalla.
- `Text` mostra text.
- `Center` centra el seu fill.

### Android → Flutter

```text
Activity + XML
      ↓
Widget / Screen + build()
```

No és una equivalència 1:1: Flutter utilitza un model basat en composició de widgets.
