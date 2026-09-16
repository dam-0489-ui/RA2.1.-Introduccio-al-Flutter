# 8. Textos i internacionalització

Els apunts originals expliquen `strings.xml` i els directoris `values-xx` per donar suport a diversos idiomes.

En Flutter es pot utilitzar el sistema de **localizations**.

## Estructura habitual

```text
lib/
└── l10n/
    ├── app_ca.arb
    ├── app_es.arb
    └── app_en.arb
```

Exemple:

```json
{
  "hello": "Hola"
}
```

## Idiomes suportats

```dart
MaterialApp(
  supportedLocales: const [
    Locale('ca'),
    Locale('es'),
    Locale('en'),
  ],
);
```

La configuració completa de localització dependrà del sistema de generació i dels delegats utilitzats pel projecte.

## Comparació

| Android | Flutter |
|---|---|
| `strings.xml` | Fitxers de localització / ARB |
| `values-ca` | Locale `ca` |
| `getString(...)` | Text localitzat generat/obtingut pel sistema de localització |
