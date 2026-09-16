# 4. Navegació i Intents

## Android

Els `Intent` permeten llançar Activities i comunicar informació entre components.

## Flutter

Per navegar entre pantalles s'utilitza habitualment `Navigator`.

### Obrir una pantalla

```dart
Navigator.push(
  context,
  MaterialPageRoute(
    builder: (context) => const SegonaPantalla(),
  ),
);
```

### Tornar

```dart
Navigator.pop(context);
```

### Retornar un resultat

```dart
final resultat = await Navigator.push<String>(
  context,
  MaterialPageRoute(
    builder: (context) => const SeleccioPage(),
  ),
);
```

I des de la segona pantalla:

```dart
Navigator.pop(context, 'Opció A');
```

## Rutes amb nom

```dart
MaterialApp(
  routes: {
    '/': (context) => const HomePage(),
    '/detall': (context) => const DetallPage(),
  },
);
```

```dart
Navigator.pushNamed(context, '/detall');
```

## Comparació

| Android | Flutter |
|---|---|
| `startActivity()` | `Navigator.push()` |
| `finish()` | `Navigator.pop()` |
| Resultat d'una Activity | Valor retornat per `Navigator.pop()` |
| Intent explícit | Navegació cap a una pantalla concreta |

Els Intents implícits que obren aplicacions externes no tenen una equivalència directa amb `Navigator`; depenent de l'acció es poden necessitar APIs de plataforma o paquets Flutter.
