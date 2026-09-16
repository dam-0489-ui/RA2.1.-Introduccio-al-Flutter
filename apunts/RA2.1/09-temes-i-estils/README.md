# 9. Temes i estils

Els apunts originals diferencien entre **temes**, aplicats a l'aplicació, i **estils**, aplicats a elements concrets.

En Flutter el principal mecanisme és `ThemeData`.

## Tema global

```dart
MaterialApp(
  theme: ThemeData(
    useMaterial3: true,
    colorScheme: ColorScheme.fromSeed(
      seedColor: Colors.blue,
    ),
  ),
  home: const HomePage(),
);
```

## TextTheme

```dart
Text(
  'Títol',
  style: Theme.of(context).textTheme.headlineSmall,
);
```

## Estil local

```dart
Text(
  'Important',
  style: const TextStyle(
    fontSize: 20,
    fontWeight: FontWeight.bold,
  ),
);
```

## Tema clar i fosc

```dart
MaterialApp(
  theme: ThemeData.light(),
  darkTheme: ThemeData.dark(),
  themeMode: ThemeMode.system,
  home: const HomePage(),
);
```

## Comparació

| Android | Flutter |
|---|---|
| Tema | `ThemeData` |
| `styles.xml` | Tema i configuració de widgets |
| Estil de text | `TextStyle` / `TextTheme` |
| Tema clar/fosc | `theme`, `darkTheme`, `themeMode` |
