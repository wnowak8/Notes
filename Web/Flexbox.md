<h1>FlexBox</h1>
<b>justify-content</b> pozwala na pozycjonowanie w osi głównej (poziomej)
- flex-start: Elementy wyrównują się do lewej strony kontenera.
- flex-end: Elementy wyrównują się do prawej strony kontenera.
- center: Elementy wyrównują się do środka kontenera.
- space-between: Elementy wyświetlają się na całej szerokości kontenera z równymi odstępami.
- space-around: Każdy z elementów wyświetla się z taką samą ilością przestrzeni wokół.


<b>align-items</b> wyrównuje elementy w pionie i przyjmuje wartości:
- flex-start: Elementy wyrównują się do górnej krawędzi kontenera.
- flex-end: Elementy wyrównują się do dolnej krawędzi kontenera.
- center: Elementy zostaną wyśrodkowane w pionie.
- baseline: Elementy zostaną wyświetlone na linii odniesienia kontenera.
- stretch: Elementy zostaną powiększone tak, aby wypełnić kontener.

<b>flex-direction </b> określa kierunek w jakim elementy są rozmieszczone w kontenerze i przyjmuje wartości:
- row: Elementy zostaną rozmieszczone tak jak tekst.
- row-reverse: Elementy zostaną rozmieszczone odwrotnie do kierunku tekstu.
- column: Elementy zostaną rozmieszczone od góry do dołu.
- column-reverse: Elementy zostaną rozmieszczone od dołu do góry.

Czasami odwracanie wierszy i kolumn kontenera nie wystarcza. W takich przypadkach, możemy zastosować własność <b>order</b> do pojedynczego elementu. Domyślnie elementy mają wartość 0, ale przy pomocy tej własności możemy ustalić kolejność na dowolną dodatnią lub ujemną wartość.

Następną własnością stosowaną wobec każdego elementu z osobna jest <b>align-self</b>. Przyjmuje ona wartości takie same jak align-items, ale ma zastosowanie tylko wobec konkretnego elementu.

Przy pomocy własności <b>flex-wrap</b> można rozpraszać elementy, jej wartości to:
- nowrap: Każdy element dopasowuje się do pojedynczego wiersza.
- wrap: Elementy wystające przechodzą do kolejnych linii.
- wrap-reverse: Elementy wystające do kolejnych linii w odwrotnej kolejności.

Jednoczesne zastosowanie własności flex-direction i flex-wrap występuje bardzo często, dlatego też utworzono własność skrótową <b>flex-flow</b>. Przyjmuje ona dwie wartości rozdzielone spacją.

Na przykład: wpisując flex-flow: row wrap uzyskamy efekt ułożenia elementów w wierszu i zawijanie ich do kolejnych linii w przypadku gdy któryś wystawałby poza kontener.

Własność align-content pomaga ustalić odległość wierszy kontenera od siebie. Własność ta przyjmuje takie wartości:
- flex-start: Wiersze upychają u góry kontenera.
- flex-end: Wiersze upychają się w dolnej części kontenera.
- center: Wiersze upychane są pośrodku kontenera.
- space-between: Wiersze wyświetlane są z równymi odstępami.
- space-around: Wiersze wyświetlane są z równymi odstępami dookoła.
- stretch: Wiersze rozszerzają się tak, aby dopasować się do kontenera.

Source:
- [flexboxfroggy](https://flexboxfroggy.com/#pl)
- [tutorial - yt](https://www.youtube.com/watch?v=o_GnXwio5Hs&ab_channel=Jakzacz%C4%85%C4%87programowa%C4%87%3F)