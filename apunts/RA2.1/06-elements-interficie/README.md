# 6. Elements d'interfície

## Equivalències

| Android | Flutter |
|---|---|
| TextView | Text |
| EditText | TextField / TextFormField |
| Button | ElevatedButton / TextButton / FilledButton |
| CheckBox | Checkbox |
| RadioButton | Radio |
| ImageView | Image |
| Spinner | DropdownButton |

## Text

```dart
const Text('Hola món');
```

## TextField

```dart
final controller = TextEditingController();

TextField(
  controller: controller,
  decoration: const InputDecoration(
    labelText: 'Nom',
  ),
);
```

## Botó

```dart
ElevatedButton(
  onPressed: () {
    print('Premut');
  },
  child: const Text('Acceptar'),
);
```

## Checkbox

```dart
Checkbox(
  value: seleccionat,
  onChanged: (valor) {
    setState(() {
      seleccionat = valor ?? false;
    });
  },
);
```

## Radio

```dart
Radio<String>(
  value: 'A',
  groupValue: resposta,
  onChanged: (valor) {
    setState(() {
      resposta = valor;
    });
  },
);
```

## Imatge

```dart
Image.asset('assets/images/logo.png');
```

## Dropdown

```dart
DropdownButton<String>(
  value: opcio,
  items: const [
    DropdownMenuItem(
      value: 'A',
      child: Text('Opció A'),
    ),
    DropdownMenuItem(
      value: 'B',
      child: Text('Opció B'),
    ),
  ],
  onChanged: (value) {
    setState(() {
      opcio = value!;
    });
  },
);
```
