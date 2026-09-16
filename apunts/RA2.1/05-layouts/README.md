# 5. Layouts

En Android tradicional, els layouts es podien definir en XML. En Flutter la composició es fa amb widgets.

## Column

Distribució vertical:

```dart
Column(
  children: const [
    Text('Nom'),
    Text('Cognoms'),
    Text('Correu'),
  ],
)
```

## Row

Distribució horitzontal:

```dart
Row(
  children: const [
    Icon(Icons.home),
    SizedBox(width: 8),
    Text('Inici'),
  ],
)
```

## Expanded

Reparteix l'espai disponible:

```dart
Row(
  children: [
    Expanded(child: Container()),
    Expanded(child: Container()),
  ],
)
```

## Stack

Permet superposar widgets:

```dart
Stack(
  children: [
    Image.asset('assets/images/foto.png'),
    const Positioned(
      bottom: 16,
      left: 16,
      child: Text('Títol'),
    ),
  ],
)
```

## Responsive

Per adaptar la interfície a diferents mides es poden utilitzar `LayoutBuilder` i altres eines de Flutter.

```dart
LayoutBuilder(
  builder: (context, constraints) {
    if (constraints.maxWidth < 600) {
      return const Column(
        children: [Text('Pantalla estreta')],
      );
    }

    return const Row(
      children: [Text('Pantalla ampla')],
    );
  },
)
```

## Equivalències conceptuals

| Android | Flutter |
|---|---|
| LinearLayout vertical | Column |
| LinearLayout horitzontal | Row |
| RelativeLayout | Composició de widgets |
| Superposició de vistes | Stack |
| `layout_weight` | Expanded / Flexible |
