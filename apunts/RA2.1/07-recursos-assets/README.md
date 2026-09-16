# 7. Recursos i assets

Els apunts originals utilitzen la carpeta `/res` d'Android per organitzar recursos com `drawable`, `raw`, `values` i `menu`.

En Flutter, els fitxers que formen part de l'aplicació es poden declarar com a **assets**.

## Estructura

```text
assets/
├── images/
│   ├── logo.png
│   └── portada.jpg
└── data/
    └── dades.json
```

## pubspec.yaml

```yaml
flutter:
  assets:
    - assets/images/
    - assets/data/
```

## Utilitzar una imatge

```dart
Image.asset('assets/images/logo.png');
```

## Idea clau

A diferència d'Android, no existeix una còpia directa de l'estructura `/res`. Flutter organitza els recursos segons el sistema d'assets i les funcionalitats específiques que necessiti l'aplicació.
