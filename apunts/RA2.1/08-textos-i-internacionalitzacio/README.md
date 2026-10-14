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

## 8.1. Implementació de la internacionalització en Flutter

En Flutter podem preparar una aplicació per treballar amb diversos idiomes utilitzant el sistema de **localizations** i fitxers de traducció en format **ARB** (*Application Resource Bundle*).

Per exemple, podem tenir una aplicació en català i anglès:

```text
Català 🇨🇦
English 🇬🇧
```

L'avantatge és que els textos de l'aplicació no queden escrits directament dins del codi, sinó que es separen en fitxers de traducció.

---

### 8.1.1. Afegir les dependències necessàries

El primer pas és modificar el fitxer:

```text
pubspec.yaml
```

A la secció `dependencies` afegim:

```yaml
dependencies:
  flutter:
    sdk: flutter

  flutter_localizations:
    sdk: flutter
```

A més, dins de la secció `flutter` activem la generació de localitzacions:

```yaml
flutter:
  uses-material-design: true
  generate: true
```

Si tenim recursos, com ara imatges, es mantenen també dins d'aquesta secció:

```yaml
flutter:
  uses-material-design: true
  generate: true

  assets:
    - assets/isard.png
```

> `generate: true` indica a Flutter que utilitzarem el sistema de generació de localitzacions.

---

### 8.1.2. Executar `flutter pub get`

Després de modificar `pubspec.yaml`, cal actualitzar les dependències del projecte.

Des de la terminal:

```bash
flutter pub get
```

Aquest comandament descarrega i prepara les dependències especificades al `pubspec.yaml`.

---

### 8.1.3. Crear la carpeta `l10n`

Dins de `lib/` creem una carpeta anomenada:

```text
l10n
```

Per exemple:

```text
lib/
├── l10n/
├── main.dart
├── pantalla1.dart
└── pantalla2.dart
```

La carpeta `l10n` és una convenció habitual per agrupar els recursos de **localització**.

---

### 8.1.4. Crear els fitxers ARB

Dins de `lib/l10n/` creem un fitxer per cada idioma.

Per exemple:

```text
lib/
└── l10n/
    ├── app_ca.arb
    └── app_en.arb
```

Els sufixos:

```text
ca
en
```

són codis d'idioma estandarditzats:

```text
ca → català
en → anglès
es → castellà
fr → francès
de → alemany
```

El format `.arb` és un format basat en JSON utilitzat per gestionar textos i altres recursos de localització.

---

### 8.1.5. Crear el fitxer de català

Per exemple, `app_ca.arb`:

```json
{
  "pantalla1": "Pantalla 1",
  "pantalla2": "Pantalla 2",
  "formulari": "Formulari",
  "nom": "Nom",
  "correu": "Correu electrònic",
  "acceptoCondicions": "Accepto les condicions",
  "seleccionaCurs": "Selecciona un curs",
  "flutter": "Flutter",
  "dart": "Dart",
  "firebase": "Firebase",
  "anarPantalla2": "Anar a la pantalla 2",
  "valorRetornat": "Valor retornat",
  "segonaPantalla": "Aquesta és la segona pantalla",
  "tornarAmbValor": "Tornar amb un valor",
  "holaPantalla2": "Hola des de la pantalla 2!"
}
```

La primera cadena és la **clau** i la segona és el text traduït.

Per exemple:

```json
"formulari": "Formulari"
```

On:

```text
formulari → clau
Formulari → traducció catalana
```

---

### 8.1.6. Crear el fitxer d'anglès

Creem `app_en.arb`:

```json
{
  "pantalla1": "Screen 1",
  "pantalla2": "Screen 2",
  "formulari": "Form",
  "nom": "Name",
  "correu": "Email",
  "acceptoCondicions": "I accept the terms and conditions",
  "seleccionaCurs": "Select a course",
  "flutter": "Flutter",
  "dart": "Dart",
  "firebase": "Firebase",
  "anarPantalla2": "Go to screen 2",
  "valorRetornat": "Returned value",
  "segonaPantalla": "This is the second screen",
  "tornarAmbValor": "Return with a value",
  "holaPantalla2": "Hello from screen 2!"
}
```

La clau és la mateixa que en català:

```json
"formulari"
```

però el text canvia:

```text
Català → Formulari
Anglès → Form
```

És important que les claus coincideixin entre els diferents fitxers.

---

### 8.1.7. Crear `l10n.yaml`

A l'arrel del projecte, al mateix nivell que `pubspec.yaml`, creem:

```text
l10n.yaml
```

Per tant:

```text
projecte/
├── l10n.yaml
├── pubspec.yaml
├── assets/
└── lib/
    └── l10n/
        ├── app_ca.arb
        └── app_en.arb
```

El contingut de `l10n.yaml` serà:

```yaml
arb-dir: lib/l10n
template-arb-file: app_ca.arb
output-localization-file: app_localizations.dart
```

#### Significat de cada propietat

```yaml
arb-dir: lib/l10n
```

Indica on es troben els fitxers `.arb`.

```yaml
template-arb-file: app_ca.arb
```

Indica quin és el fitxer de referència o plantilla.

En aquest cas utilitzem el català.

```yaml
output-localization-file: app_localizations.dart
```

Indica el nom de la classe de localització que Flutter generarà.

---

### 8.1.8. Generar les classes de localització

Una vegada creats els fitxers `.arb` i `l10n.yaml`, executem:

```bash
flutter gen-l10n
```

Flutter generarà automàticament les classes necessàries per accedir a les traduccions.

Entre altres elements, disposarem de:

```dart
AppLocalizations
```

Aquesta classe permetrà accedir als textos traduïts des del codi Dart.

Important: cal executar la generació automàtica de classes cada vegada que afegim nous idiomes.

---

### 8.1.9. Configurar `main.dart`

Cal importar les localitzacions de Flutter:

```dart
import 'package:flutter_localizations/flutter_localizations.dart';
```

I també la classe generada:

```dart
import 'l10n/app_localizations.dart';
```

Dins de `MaterialApp` indiquem els idiomes disponibles:

```dart
supportedLocales: const [
  Locale('ca'),
  Locale('en'),
],
```

I els delegats de localització:

```dart
localizationsDelegates: const [
  AppLocalizations.delegate,
  GlobalMaterialLocalizations.delegate,
  GlobalWidgetsLocalizations.delegate,
  GlobalCupertinoLocalizations.delegate,
],
```

Per exemple:

```dart
MaterialApp(
  supportedLocales: const [
    Locale('ca'),
    Locale('en'),
  ],

  localizationsDelegates: const [
    AppLocalizations.delegate,
    GlobalMaterialLocalizations.delegate,
    GlobalWidgetsLocalizations.delegate,
    GlobalCupertinoLocalizations.delegate,
  ],

  home: const Pantalla1(),
);
```

---

### 8.1.10. Utilitzar les traduccions en una pantalla

A la pantalla on volem utilitzar les traduccions importem:

```dart
import 'l10n/app_localizations.dart';
```

Dins de `build()` obtenim les localitzacions:

```dart
final textos = AppLocalizations.of(context)!;
```

A partir d'aquest moment podem utilitzar les claus definides als `.arb`.

Per exemple:

```dart
Text(textos.formulari)
```

En lloc de:

```dart
Text('Formulari')
```

Si l'idioma és català:

```text
Formulari
```

Si l'idioma és anglès:

```text
Form
```

---

### 8.1.11. Aplicar les traduccions als widgets

Les traduccions també es poden utilitzar en widgets reutilitzables.

Per exemple, el nostre widget:

```dart
CampText(
  controller: nomController,
  label: textos.nom,
)
```

En català mostrarà:

```text
Nom
```

En anglès:

```text
Name
```

També podem utilitzar-les en:

```dart
CheckboxListTile(
  title: Text(textos.acceptoCondicions),
)
```

o:

```dart
DropdownButtonFormField<String>(
  decoration: InputDecoration(
    labelText: textos.seleccionaCurs,
  ),
)
```

---

### 8.1.12. Traduir els textos de `Pantalla2`

El mateix procediment s'aplica a la segona pantalla.

Per exemple:

```dart
final textos = AppLocalizations.of(context)!;
```

I:

```dart
AppBar(
  title: Text(textos.pantalla2),
)
```

El botó:

```dart
ElevatedButton(
  onPressed: () {
    Navigator.pop(
      context,
      textos.holaPantalla2,
    );
  },
  child: Text(textos.tornarAmbValor),
)
```

D'aquesta manera, fins i tot el valor que retorna `Pantalla2` queda traduït.

---

### 8.1.13. Canvi manual d'idioma

Per defecte, Flutter pot utilitzar l'idioma del sistema o del dispositiu.

També podem permetre que l'usuari seleccioni manualment l'idioma.

Per fer-ho, `MyApp` ha de ser un `StatefulWidget`:

```dart
class MyApp extends StatefulWidget {
  const MyApp({super.key});

  @override
  State<MyApp> createState() => _MyAppState();
}
```

Guardem l'idioma seleccionat:

```dart
Locale _idioma = const Locale('ca');
```

I el passem a `MaterialApp`:

```dart
locale: _idioma,
```

Per canviar-lo podem crear una funció:

```dart
void canviarIdioma(Locale idioma) {
  setState(() {
    _idioma = idioma;
  });
}
```

Aquesta funció es pot passar a una pantalla:

```dart
home: Pantalla1(
  canviarIdioma: canviarIdioma,
),
```

I des de `Pantalla1` podem crear un desplegable:

```dart
DropdownButton<Locale>(
  value: Localizations.localeOf(context),

  items: const [
    DropdownMenuItem(
      value: Locale('ca'),
      child: Text('CA'),
    ),
    DropdownMenuItem(
      value: Locale('en'),
      child: Text('EN'),
    ),
  ],

  onChanged: (idioma) {
    if (idioma != null) {
      widget.canviarIdioma(idioma);
    }
  },
)
```

Quan l'usuari selecciona un idioma, es modifica el `Locale` de `MaterialApp` i Flutter actualitza les traduccions de l'aplicació.

---

### 8.1.14. Flux complet de la internacionalització

El procés complet és:

```text
1. pubspec.yaml
       ↓
2. flutter pub get
       ↓
3. Crear lib/l10n/
       ↓
4. Crear app_ca.arb
   Crear app_en.arb
       ↓
5. Crear l10n.yaml
       ↓
6. flutter gen-l10n
       ↓
7. Configurar MaterialApp
       ↓
8. supportedLocales
       ↓
9. localizationsDelegates
       ↓
10. Importar AppLocalizations
       ↓
11. Obtenir textos amb
    AppLocalizations.of(context)!
       ↓
12. Utilitzar les claus
    textos.nom
    textos.formulari
    textos.correu
    ...
       ↓
13. Opcionalment:
    selector manual d'idioma
```

---

### 8.1.15. Estructura final del projecte

Un projecte amb aquesta configuració pot tenir:

```text
projecte/
│
├── l10n.yaml
├── pubspec.yaml
│
├── assets/
│   └── isard.png
│
└── lib/
    │
    ├── main.dart
    ├── pantalla1.dart
    ├── pantalla2.dart
    │
    ├── l10n/
    │   ├── app_ca.arb
    │   └── app_en.arb
    │
    └── widgets/
        └── camp_text.dart
```

Les classes de localització generades per Flutter **no s'han de modificar manualment**. Es regeneren a partir dels fitxers `.arb`.

---

### 8.1.16. Afegir un nou idioma

Si posteriorment volem afegir castellà, per exemple, podem crear:

```text
app_es.arb
```

Amb:

```json
{
  "formulari": "Formulario",
  "nom": "Nombre",
  "correu": "Correo electrónico"
}
```

I afegir el nou idioma a `MaterialApp`:

```dart
supportedLocales: const [
  Locale('ca'),
  Locale('es'),
  Locale('en'),
],
```

Després tornem a generar les localitzacions:

```bash
flutter gen-l10n
```

---

### 8.1.17. Comparació amb Android

| Android                  | Flutter                         |
| ------------------------ | ------------------------------- |
| `strings.xml`            | Fitxers `.arb`                  |
| `values/`                | `lib/l10n/`                     |
| `values-ca/`             | `app_ca.arb`                    |
| `values-en/`             | `app_en.arb`                    |
| `getString(...)`         | `AppLocalizations.of(context)!` |
| String traduït           | Clau de localització            |
| Configuració de locale   | `Locale('ca')`, `Locale('en')`  |
| Recursos de localització | `localizationsDelegates`        |

### Resum

La internacionalització separa els **textos del programa** del **codi de la interfície**.

En lloc de:

```dart
Text('Nom')
```

utilitzem:

```dart
Text(textos.nom)
```

i els textos es defineixen als fitxers:

```text
app_ca.arb
app_en.arb
```

D'aquesta manera, la mateixa aplicació pot mostrar diferents idiomes sense haver de duplicar les pantalles ni modificar manualment tots els textos.
