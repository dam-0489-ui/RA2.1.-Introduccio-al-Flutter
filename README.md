# RA2 — Desenvolupament d'interfícies amb Flutter

Apunts i material introductori del RA2 per al desenvolupament d'aplicacions amb **Dart i Flutter**.

> 📚 Aquest repositori comença amb el **RA2.1 — Pantalles, navegació, layouts, estils i recursos**.

## Continguts

### RA2.1 — Pantalles, navegació, layouts, estils i recursos

- [01 · Introducció a Flutter](apunts/RA2.1/01-introduccio/README.md)
- [02 · Widgets i estructura](apunts/RA2.1/02-widgets-i-estructura/README.md)
- [03 · Cicle de vida](apunts/RA2.1/03-cicle-de-vida/README.md)
- [04 · Navegació i Intents](apunts/RA2.1/04-navegacio/README.md)
- [05 · Layouts](apunts/RA2.1/05-layouts/README.md)
- [06 · Elements d'interfície](apunts/RA2.1/06-elements-interficie/README.md)
- [07 · Recursos i assets](apunts/RA2.1/07-recursos-assets/README.md)
- [08 · Textos i internacionalització](apunts/RA2.1/08-textos-i-internacionalitzacio/README.md)
- [09 · Temes i estils](apunts/RA2.1/09-temes-i-estils/README.md)
- [10 · Estat](apunts/RA2.1/10-estat/README.md)
- [11 · Fragments i widgets reutilitzables](apunts/RA2.1/11-fragments-i-widgets-reutilitzables/README.md)
- [12 · Exemples pràctics](apunts/RA2.1/12-exemples/README.md)

## Organització

```text
RA2-Flutter/
├── README.md
├── .gitignore
├── apunts/
│   └── RA2.1/
│       ├── 01-introduccio/
│       ├── 02-widgets-i-estructura/
│       ├── 03-cicle-de-vida/
│       ├── 04-navegacio/
│       ├── 05-layouts/
│       ├── 06-elements-interficie/
│       ├── 07-recursos-assets/
│       ├── 08-textos-i-internacionalitzacio/
│       ├── 09-temes-i-estils/
│       ├── 10-estat/
│       ├── 11-fragments-i-widgets-reutilitzables/
│       └── 12-exemples/
│
├── exercicis/
└── projectes/
```

## Objectiu

Relacionar els conceptes del desenvolupament Android tradicional amb el model de desenvolupament de Flutter, entenent especialment:

- pantalles i widgets
- cicle de vida
- navegació
- composició de layouts
- elements d'interfície
- recursos
- internacionalització
- temes i estils
- estat
- components reutilitzables

## Android → Flutter

| Android / Java | Flutter / Dart |
|---|---|
| Activity | Widget / pantalla |
| XML layout | Arbre de widgets |
| `setContentView()` | `build()` |
| Intent / `startActivity()` | `Navigator.push()` |
| `finish()` | `Navigator.pop()` |
| TextView | Text |
| EditText | TextField |
| Button | ElevatedButton / TextButton |
| CheckBox | Checkbox |
| RadioButton | Radio |
| ImageView | Image |
| Spinner | DropdownButton |
| LinearLayout vertical | Column |
| LinearLayout horitzontal | Row |
| RelativeLayout | Composició de widgets |
| Recursos `res/` | Assets / localitzacions / configuració Flutter |
| styles.xml | ThemeData / TextStyle |
| Fragment | Widget reutilitzable |

## Nota

Les equivalències són **conceptuals**. Flutter té un model d'interfície i un cicle de vida diferents d'Android natiu.

---

📌 **Estat del repositori:** RA2.1 introductori preparat.
