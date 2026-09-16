# 3. Cicle de vida

Els apunts originals expliquen el cicle de vida d'una Activity amb callbacks com `onCreate`, `onStart`, `onResume`, `onPause`, `onStop` i `onDestroy`.

Flutter té un model diferent.

## Cicle de vida d'un StatefulWidget

Els mètodes principals són:

- `createState()`
- `initState()`
- `build()`
- `didChangeDependencies()`
- `didUpdateWidget()`
- `deactivate()`
- `dispose()`

Exemple:

```dart
class ExempleLifecycle extends StatefulWidget {
  const ExempleLifecycle({super.key});

  @override
  State<ExempleLifecycle> createState() => _ExempleLifecycleState();
}

class _ExempleLifecycleState extends State<ExempleLifecycle> {
  @override
  void initState() {
    super.initState();
    // Inicialització.
  }

  @override
  Widget build(BuildContext context) {
    return const Text('Pantalla');
  }

  @override
  void dispose() {
    // Alliberar controllers, listeners, etc.
    super.dispose();
  }
}
```

## Idea important

`dispose()` és el lloc habitual per alliberar recursos associats al widget, com controllers i listeners.

El cicle de vida d'un widget no s'ha de confondre amb el cicle de vida global de l'aplicació.
