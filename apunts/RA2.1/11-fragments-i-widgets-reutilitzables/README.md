# 11. Fragments i widgets reutilitzables

Els apunts originals expliquen els `Fragment` com una manera de mostrar parts d'una interfície dins d'una Activity.

Flutter no utilitza `Fragment` com a component equivalent.

La reutilització es fa creant **widgets**.

## Exemple

```dart
class TargetaUsuari extends StatelessWidget {
  final String nom;

  const TargetaUsuari({
    super.key,
    required this.nom,
  });

  @override
  Widget build(BuildContext context) {
    return Card(
      child: Padding(
        padding: const EdgeInsets.all(16),
        child: Text(nom),
      ),
    );
  }
}
```

Ús:

```dart
Column(
  children: const [
    TargetaUsuari(nom: 'Anna'),
    TargetaUsuari(nom: 'Joan'),
  ],
)
```

## Comparació conceptual

```text
Android

Activity
├── Fragment
└── Fragment


Flutter

Screen
├── Widget
└── Widget
```

No és una equivalència de cicle de vida: el model de Flutter és diferent.
