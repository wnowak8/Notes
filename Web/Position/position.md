<h1>Pozycjonowanie w CSS</h1>
Domyślnie każdy element ma pozycje statyczną:

```
position: static;
```

<b>Relatywne</b> - element zostaje ustawiony względem pierwotnej pozycji, czyli przesuwa się go w prawo, lewo, dół lub
w górę.

```
position: relative;
top/bottom/left/right: 5px;
```

<b>Absolutne</b> - element zostaje domyślnie ustawiony względem okna lub jeśli w nadrzędnym elemencie jest ustawiona pozycja relatywna to element ustawia się względem niego w miejscu określonym przez parametry.

```
position: absolute;
top/bottom/left/right: 5px;
```

<b>Fixed</b> - element zostaje ustawiony względem okna, nie zmienia pozycji w trakcie scrollowania strony


```
position: fixed;
top/bottom/left/right: 5px;
```

<b>Sticky</b> - (nie obsługiwane przez wczesne wersje przeglądarki MS Edge) na początku renderuje element jak static, ale po scrollowaniu strony element ustawi się, jak element stały w określonym przez parametry miejscu. (przydatne przy menu, które jest cały czas obecne w oknie)

```
position: fixed;
top/bottom/left/right: 5px;
```

<b>Inherit</b> - element przejmuje pozycje ustawioną w elemencie nadrzędnym.
```
position: inherit;
```

[Source](https://www.youtube.com/watch?v=RBnm8BaUo14&ab_channel=MikuCode)
