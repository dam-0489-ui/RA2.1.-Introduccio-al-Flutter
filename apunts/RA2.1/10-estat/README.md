# 10. Estat

La gestió de l'estat és una diferència important respecte del model tradicional d'Android.

## Estat local

```dart
class Comptador extends StatefulWidget {
  const Comptador({super.key});

  @override
  State<Comptador> createState() => _ComptadorState();
}

class _ComptadorState extends State<Comptador> {
  int comptador = 0;

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Text('$comptador'),
        ElevatedButton(
          onPressed: () {
            setState(() {
              comptador++;
            });
          },
          child: const Text('Incrementar'),
        ),
      ],
    );
  }
}
```

## `setState()`

Quan es modifica l'estat local d'un `StatefulWidget`, `setState()` indica a Flutter que la interfície s'ha de reconstruir.

## Estat compartit

Quan l'estat s'ha de compartir entre diferents parts de l'aplicació es poden utilitzar diferents patrons i paquets de gestió d'estat.

En aquest RA2.1 ens centrem en l'estat local bàsic.
