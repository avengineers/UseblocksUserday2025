
## What are our key challenges?

* Project diversity <div class="fragment" style="color:red">Software Product Lines</div>
* Documentation and verification of software quality <div class="fragment" style="color:red">A.SPICE</div>
* Continuous Integration <div class="fragment" style="color:red">Less is more</div>

Note:
In der Automobilwelt haben wir es mit einer unglaublichen Produktvielfalt zu tun. Zig verschiedene Hersteller, mit verschiedenen Modellen, Modellvarianten und dann noch angepasst an verschiedene Märkte und Regionen, je nach gesetzlichen Vorgaben.
Hier jedes Produkt als Einzelprojekt aufzusetzen und die Software immer wieder neu zu schreiben, wäre für jedes Unternehmen der Tod.
Man muss einen geeigneten Weg finden, diese Vielzahl von Produktvarianten über Konfigurationen abzubilden.
Wir lösen das über Software-Produktlinien und brechen damit die Komplexität unserer Produktpalette ein Stück weit auf.

(click)

Dazu müssen wir die Qualität unserer Produkte ständig überprüfen. Das gilt im Prinzip für jedes Softwareprodukt.
In der Automobilwelt geht es aber sehr häufig um sicherheitsrelevante Funktionen, bei denen also Menschenleben oder zumindest deren Unversehrtheit im Vordergrund stehen.
Dafür bekommt jeder Entwickler ein Prozessregelwerk an die Hand. Mit dessen Hilfe kann Software in solchen Umgebungen standardisiert entwickelt werden.
Auch wenn viele das als Hindernis sehen, ist es eher als Hilfe gedacht. 
Ich spreche hier von Automotive Spice, kurz A.SPICE.

(click)

Drittens wollen wir unsere Produkte natürlich schnell fertig stellen und ausliefern.
Time-to-Market ist vielleicht nicht alles, aber es ist eine gute Basis.
Wie unsere Lösung aussieht und warum man für ein gutes CI eigentlich gar nicht so viel braucht, werden wir nun Stück für Stück erklären.
