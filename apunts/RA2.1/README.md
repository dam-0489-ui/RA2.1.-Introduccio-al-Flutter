# RA2.1 — Pantalles, navegació, layouts, estils i recursos

## Introducció

En Android tradicional, una aplicació pot estar formada per diferents **Activities**, que permeten la interacció amb l'usuari.

En Flutter, la interfície es construeix mitjançant un **arbre de widgets** i cada pantalla es pot representar habitualment mitjançant un widget.

## Índex

1. [Introducció a Flutter](01-introduccio/README.md)
2. [Widgets i estructura](02-widgets-i-estructura/README.md)
3. [Cicle de vida](03-cicle-de-vida/README.md)
4. [Navegació i Intents](04-navegacio/README.md)
5. [Layouts](05-layouts/README.md)
6. [Elements d'interfície](06-elements-interficie/README.md)
7. [Recursos i assets](07-recursos-assets/README.md)
8. [Textos i internacionalització](08-textos-i-internacionalitzacio/README.md)
9. [Temes i estils](09-temes-i-estils/README.md)
10. [Estat](10-estat/README.md)
11. [Fragments i widgets reutilitzables](11-fragments-i-widgets-reutilitzables/README.md)
12. [Exemples pràctics](12-exemples/README.md)

## Mapa de conceptes

```text
Android + Java
      │
      ├── Activity ───────────────► Widget / Screen
      ├── XML Layout ─────────────► Widget tree
      ├── Intent ─────────────────► Navigator / routes
      ├── View ───────────────────► Widget
      ├── LinearLayout ───────────► Row / Column
      ├── resources ──────────────► assets / l10n / theme
      ├── styles.xml ─────────────► ThemeData / TextStyle
      └── Fragment ───────────────► Widget reutilitzable
```
