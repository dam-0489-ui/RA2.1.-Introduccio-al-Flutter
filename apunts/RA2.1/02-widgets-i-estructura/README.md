# 2. Widgets i estructura

## StatelessWidget

S'utilitza quan el widget no necessita mantenir un estat mutable propi.

```dart
class Salutacio extends StatelessWidget {
  const Salutacio({super.key});

  @override
  Widget build(BuildContext context) {
    return const Text('Hola!');
  }
}
```

## StatefulWidget

S'utilitza quan la interfície depèn d'un estat que pot canviar.

```dart
class Comptador extends StatefulWidget {
  const Comptador({super.key});

  @override
  State<Comptador> createState() => _ComptadorState();
}

class _ComptadorState extends State<Comptador> {
  int valor = 0;

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Text('Valor: $valor'),
        ElevatedButton(
          onPressed: () {
            setState(() {
              valor++;
            });
          },
          child: const Text('Incrementa'),
        ),
      ],
    );
  }
}
```

## Comparació

| Android | Flutter |
|---|---|
| XML | Codi Dart amb widgets |
| `setContentView()` | `build()` |
| `View` | `Widget` |
| `ViewGroup` | Widgets contenidors/compositors |
| `android:id` | Controllers, callbacks, claus i estat segons la necessitat |
