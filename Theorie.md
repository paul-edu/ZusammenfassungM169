# Theorie

## YAML

### Vorteile
* weniger sonderzeichen
* besser erweiterbar
* schlanker
* Kommentare
* Syntax verkürzbar

### Nachteile
* nur Leerzeichen keine Tabs (umgewöhnung)
* weniger verbreitet

### Aufbau

```txt
key: value
```
Die obige Struktur besteht aus einem Schlüssel (key) und einem Wert (value), die durch einen Doppelpunkt (:) getrennt sind. In YAML können Sie auch mehrere Schlüssel-Wert-Paare definieren, indem Sie sie untereinander aufzählen:
```txt
key1: value1
key2: value2
key3: value3
```
Um eine verschachtelte Struktur zu definieren, können Sie einen Einzug (Leerzeichen oder Tabulatoren) verwenden, um die untergeordneten Elemente von ihren Eltern zu unterscheiden:

```txt
parent:
  child1: value1
  child2: value2
  child3: value3
```
In YAML können auch Listen definiert werden, indem man sie unter Verwendung von Bindestrichen (`-`) hintereinander aufzählt:
```txt
liste:
  - eintrag1
  - eintrag2
  - eintrag3
```
## Key-Values auf gleicher linie definieren:

In Docker Compose, you can define key-value pairs on a single line by separating them with a space. For example, to define the environment variables for a service, you could write:
```txt
environment:
KEY1: value1, KEY2: value2
```


