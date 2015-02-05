# fe-coding-conventions
Coding Convention Frontend

*   1[Generell](#CodeConventions-Generell)

    *   1.1[.editorconfig](#CodeConventions-.editorconfig)
    *   1.2[Bezeichnungen](#CodeConventions-BezeichnungenBezeichnungen)
    *   1.3[Kommentare](#CodeConventions-KommentareKommentare)

*   2[Git](#CodeConventions-Git)
*   3[Frontend](#CodeConventions-Frontend)

    *   3.1[HTML](#CodeConventions-HTML)
    *   3.2[CSS / SASS](#CodeConventions-CSS/SASS)

            *   3.2.1[Dokumentation](#CodeConventions-Dokumentation)
        *   3.2.2[Naming](#CodeConventions-Naming)

        *   3.3[Javascript](#CodeConventions-Javascript)
    *   3.4[Assets Allgemein](#CodeConventions-AssetsAllgemein)

            *   3.4.1[Naming](#CodeConventions-Naming.1)

* * *

## <a name="Generell"></a>Generell

**!HINWEIS: **Dieser Bereich ist ein Living-Standard. Sollte es jedoch Änderungen am Codestyle geben, müssen diese unverzüglich dem Team kommuniziert werden.

### <a name="Generell"></a>.editorconfig

Es wird prinzipiell eine '.editorconfig' angelegt, die den Grundlegenden Codestyle wiedergibt. (Beispiel [.editorconfig](.editorconfig)) Alle Sprachspezifischen Abweichungen werden hier zusätzlich notiert. [Weiterführende Informationen zum thema .editorconfig unter: editorconfig.org](http://editorconfig.org)

Sollte die IDE die Datei nicht interpretieren können sollte ein entsprechendes Plugin installiert werden. Sollte es irgendeine IDE oder einen Editor geben, welcher weder von sich aus, noch durch ein Plugin die Codestyles berücksichtigt, muss Commit-Aktuell der Codestyle entsprechend manuell in die lokal verwendeten Programme hinzugefügt werden.

**Wichtig ist das der Codestyle auf dem wir uns commiten einheitlich ins Git eingecheckt wird.**

**Vorschlag (Anhand: [.editorconfig](.editorconfig)):**

```sh
    indent_style=space
    indent_size = 4
    end_of_line = lf
    charset = utf-8
    trim_trailing_whitespace = true
    insert_final_newline = true
```

Also Spaces statt Tabs, Einrückungsgröße 4 Leerzeichen, Unix-style newlines, utf-8, Entferung von unbenutzten Leerzeichen, Zuletzt immer ein Zeilenumbruch.

### <a name="Bezeichnungen"></a>Bezeichnungen

Klassennamen, Funktionsnamen und Variablen müssen erkennen lassen was oder wofür sie etwas machen -> in Englisch.

### <a name="Kommentare"></a>Kommentare

Nicht selbsterklärender Code sollte kommentiert werden. Warum macht der Code etwas, nicht was macht der Code -> in Englisch.

## <a name="Git"></a>Git

Commitmessages werden sofern mit Ticketsystem gearbeitet wird, mit der Ticket ID geprefixt. Zum Beispiel: 

```sh
    git commit -m"[BDT-21] add Imprint Styles"
```

oder

```sh
    git commit -m"[BDT-18] config the User Agent Sniffing for Android devices"
```

## <a name="Frontend"></a>Frontend

Für den Frontendpart gilt: Es wird sich an die Global definierten Codestyles gehalten. Ausnahmen: '.json' und '.js' Dateien. Hier bietet es sich an mit 2 Spaces Einrückung zu arbeiten.

Für den gesamten Frontendbereich gilt: Wir arbeiten mobile first und vermeiden Redundanz. Bevor eine Zeile Code in das Projekt kommt, wird erst einmal analysiert ob eine Zeile Code entfernt werden kann.

### <a name="HTML"></a>HTML

*   Semantische Auszeichnung aller Module nach den HTML5 Standards.
*   Grundlagen der Zugänglichkeit und Benutzererfahrung wahren und im Zweifel Feedbackrunden mit Grafik oder Projektmanagement
     z.B.: kein Inputmarkup ohne Labels, Headlines die gegen sinnvolle SEO oder Semantik sprechen etc.
*   Kleinschreibung für HTML-Elemente und Attribute
*   Für den IE8 gibt es ein Fallback html5shiv oder html5shim, auch wenn dem Browser keine Projektunterstützung widerfährt.
*   Nicht selbsterklärender Code sollte kommentiert werden. Warum macht der Code etwas, nicht was macht der Code. Siehe: [Allgemein -> Kommentare](#CodeConventions-Kommentare)
*   HTML-Kommentare werden wie folgt verfasst:
    ```html
        <!-- + Beschreibung/Modulname -->
    ```
    Bei längeren Modulen oder Bereichen wird dieser auch wieder geschlossen.
    ```html
        <!-- = Beschreibung/Modulname -->
    ```


### <a name="CSS / SASS"></a>CSS / SASS

*   Alle Klassennamen werden per Separator (-) getrennt. Kein CamelCase, keine Großbuchstaben. Gleiches gilt für Placeholder und Mixins. Ausnahme hier sind Funktionen, welche in CamelCase geschrieben werden.
*   Es werden Klassen bevorzugt und keine ID´s gestyled.
*   Im Zweifel für das styling eine extra Klasse anlegen, statt HTML-Elemente oder Attribute zu stylen
*   So oft wie möglich auf globale Klassen zurückgreifen.
*   auf gestylte Klassen sollte im Normalfall keine Javascript-Funktionalität gelegt werden. (JavaScript Hooks: Hier sollten wir uns auf ein prefix wie "js-" einigen)
*   Maximale Selektorendichte sollte 3 Selektoren nicht überschreiten.
*   @extend nur per %placeholder, kein direktes extenden von Selektoren


#### <a name="Dokumentation"></a>Dokumentation

*   Dependencies müssen im Code dokumentiert werden.
*   Funktionen und Mixins müssen dokumentiert werden.
*   Ansonsten gilt, Module sollten Beschrieben werden, muss aber nicht. Im Zweifel lieber ein Kommentar zuviel als zuwenig.
*   Initial werden wir für die Dokumentation von css/scss/sass Dateien auf eine PHPDoc-nahe Adaption für SASS zurückgreifen ([SassDoc ](http://sassdoc.com/)[http://sassdoc.com/](http://sassdoc.com/)[).](http://sassdoc.com/)

```scss
    /**
     * + Modulname
     * Beschreibung
     *
     * @type {partial} (#)
     *
     * @link http://www.link-to-example/description/source.com (#)
     *
     * @requires {type} name (#)
     *
     * @example (#)
     * <div class="content-box">
     * <h2 class="content-box__headline">This is a headline</h2>
     * </div>
     */
```

CSS-Kommentare werden wie folgt verfasst:

```css
    // + Modulname
```

Bei längeren Modulen oder Bereichen wird dieser auch wieder geschlossen.

```css
    // = Modulname
```

Bei längeren Kommentaren:

```css
    /**
     * + Modulname
     *
     * Beschreibung Lorem Ipsum
     * Dolore
     * Blubb ...
     */
```

Beispiele:

```scss
    /**
     * Function to calculate Fontsize in 'rem'
     *
     * @group Fonts
     *
     * @param {int} $size - Fontsize as integer
     *
     * @author mg, fh
     *
     * @returns {int} returns calculated rem
     *
     */
     @function calculateRem($size) {
     $remSize: $size / 16px;
     @return $remSize * 1rem;
     }
```

```scss
    /**
     * Mixin to calculate Fontsize in 'rem'
     *
     * @group Fonts
     *
     * @param {int} $size - Fontsize as integer
     *
     * @author mg, fh
     *
     * @example
     * @include font-size(14px)
     *
     * @requires {variable} $size - With px value
     * @requires {function} calculateRem - Funktion to calculate $size
     *
     *
     * @todo change function syntax soon
     *
     */
     @mixin font-size($size) {
     font-size: $size;
     font-size: calculateRem($size);
     }
```

#### <a name="Naming"></a>Naming

*   siehe [Generell -> Bezeichnungen](#CodeConventions-Bezeichnungen)
*   Klassennamen und Id´s sollten Modular aufgebaut werden.
*   zB.: .news-list, .page-header
     hier auf Lesbarkeit achten:
     .collapse-header, .notification-footer statt: .clp-hd, .nf-ft
*   Als Pseudostandard wird für CSS eine Modifikation von BEM (**B**lock **E**lement **M**odifier) genutzt. (Mehr zum Thema BEM: [https://bem.info/](https://bem.info/), [http://www.smashingmagazine.com/2012/04/16/a-new-front-end-methodology-bem/](http://www.smashingmagazine.com/2012/04/16/a-new-front-end-methodology-bem/) )
     
Module werden also nach folgendem Schema aufgebaut:

| Block | Element    | Modifier | Output          |
|-------|------------|----------|-----------------|
| news  |            |          | .news           |
| news  | __headline |          | .news__headline |
| news  |            | --latest |                 |

Alternative Darstellung zum Anzeigen eines Element-Modifiers:

| Block      | Element | Modifier | Output                    |
|------------|---------|----------|---------------------------|
| navigation |         |          | .news                     |
| navigation | __link  |          | .navigation__link         |
| navigation | __link  | --active | .navigation__link--active |

Das folgt dem objektorientierten Ansatz, spart aber Selektoren und ist gut lesbar und einfach zu warten.

CSS kompilierung durch SASS. Dateien in Module aufsplitten und Modulbasiert benennen. Als Dateiendung wird SCSS genutzt.

Selektoren mit nur einer Eigenschaft werden auf einer Zeile geschrieben.

**Beispiel einzeiliger Code**

```scss
.button--large { font-size: $font-size-large; }
```

Bei Selektoren mit mehreren Eigenschaften und Werten werden diese entsprechend den globalen Code-Styles eingerückt.

**Beispiel mehrzeiliger Code**

```scss
    /**
     * + Clearfix
     * Clear Floats
     * @link http://nicolasgallagher.com/micro-clearfix-hack/ source we use
     * =====================================================================
     */
     @mixin clearfix() {
     &:before,
     &:after {
     content: " ";
     display: table;
     }
     &:after {
     clear: both;
     }
     }
     /* = Clearfix */
```

Partials werden mit Underscore geprefixt. Bsp.: _buttons.scss, _clearfix.scss und sollten gruppiert nach nutzen in sepperaten Ordnern angelegt werden. Bsp.:

*   **styles**
    *   main.scss
    *   _variables.scss
    *   **mixins**
        *   _clearfix.scss
        *   _font-size.scss

    *   **modules**
    *   _reset.scss
        *   _navigation.scss


### <a name="Javascript"></a>Javascript

*   Naming siehe [Generell -&gt; Bezeichnungen](#CodeConventions-Bezeichnungen)
*   Module sollten einzeln angelegt werden und je nach Größe und globalen Umfang des Projektes entweder minifiziert und gemerged ausgegeben werden, oder per Dependencie-Loader nachgeladen werden.
*   Scripte sollten je nach Projektverlauf weitestgehend gemerged und minifiziert ausgeliefert werden.
*   Scripte sollten on the fly, spätestens beim build gelinted werden. (mit [jshint](http://jshint.com/docs/), [indent 2 Spaces](#CodeConventions-Ausnahme-gitignore-js_json), quotemarks Single Quote ['])
*   Dependencies müssen im Code dokumentiert werden.

Bereich Javascript kann gerne noch erweitert werden,

### <a name="Assets Allgemein"></a>Assets Allgemein

*   User generierter Content hat nichts im GIT zu suchen

#### <a name="Naming"></a>Naming

*   Sinnvolle Benennung in der entsprechenden Landessprache. Ausnahme Design-Assets -&gt; Benennung Global, bzw. Modulbasiert, einheitlich in Englischer Sprache.
*   Dateibenennung der Assets kein CamelCase, keine Gro&szlig;buchstaben, Trennung der Wörter durch Seperator (-) statt Underscore (_).

Das grundsätzliche Schema für Dateibenennungen von Grafiken ist folgenderma&szlig;en: [parent|module*]-[type]-[position*]-[name*].[filetype]
Parameter mit einem * sind optional. Der Parameter &ldquo;typ&rdquo; ist immer zu nutzen. Der Parameter &ldquo;parent|module&rdquo; ist immer dann sinnvoll, wenn man ähnliche Grafiken hat, diese aber je nach Modul etwas anders aussehen, Bsp. icon-arrow. Ein derartiges Image könnte in einem Slider, für eine Navigation und einen Newslink verwendet werden. Hier würde sich anbieten vor dem Typ das übergeordnete Modul im Namen mit anzugeben um eine Art &ldquo;Scope&rdquo; zu erzeugen, also: slider-icon-arrow, newsbox-icon-arrow, nav-icon-arrow.

**Beispiele:**

*   sprite.png =&gt; [type].[filetype]
*   sprite-icons.png =&gt; [type]-[name].[filetype]
*   icon-arrow-left.png =&gt; [type]-[name]-[position].[filetype]
*   news-gradient-header.gif =&gt; [parent|module]-[type]-[name].[filetype]


<!--
Copyright (c) 2015 Michael Gerstmann
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
-->
