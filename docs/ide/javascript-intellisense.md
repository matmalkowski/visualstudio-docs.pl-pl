---
title: IntelliSense dla JavaScript | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 06/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c958958ca3b0621a4e348ebcbc4cffaf35d3cce9
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2018
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense

[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]udostępnia zaawansowane JavaScript edytowania dodatkowych zabiegów. Obsługiwane przez usługi języka TypeScript, na podstawie, Visual Studio oferuje bardziej zaawansowane funkcje IntelliSense, obsługę nowoczesnych funkcji JavaScript, i poprawę wydajności funkcji, takich jak Przejdź do definicji refaktoryzacji itd.

> [!NOTE]
> Usługa języka JavaScript w [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] używa nowy aparat do usługi języka (o nazwie "Salsa"). Szczegółowe informacje znajdują się w tym temacie i możesz również przeczytać ten tekst [wpis w blogu](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/more-productive-javascript-in-visual-studio-2017-rc). Nowe środowisko edytowania dotyczy również przede wszystkim Visual Studio Code. Zobacz [docs kodzie VS](https://code.visualstudio.com/docs/languages/javascript) Aby uzyskać więcej informacji.

Aby uzyskać więcej informacji na temat ogólne funkcje IntelliSense programu Visual Studio, zobacz [za pomocą funkcji IntelliSense](../ide/using-intellisense.md).

## <a name="whats-new-in-the-javascript-language-service-in-includevsdev15miscincludesvsdev15mdmd"></a>Nowości w usługa języka JavaScript w[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Począwszy od [!include[vs_dev15](../misc/includes/vs_dev15_md.md)], JavaScript IntelliSense wyświetla znacznie więcej informacji na listach parametrem i element członkowski.
To nowe informacje są udostępniane przez usługi języka TypeScript, która używa analizy statycznej w tle, aby lepiej zrozumieć kodu.
TypeScript używa wielu źródeł do zbudowania te informacje:

- [IntelliSense oparte na wnioskowanie o typie](#TypeInference)
- [IntelliSense w oparciu o JSDoc](#JsDoc)
- [IntelliSense oparte na plikach deklaracji TypeScript](#TsDeclFiles)
- [Automatyczne nabycie definicji typu](#Auto)

### <a name="TypeInference"></a>IntelliSense oparte na wnioskowanie o typie

W języku JavaScript w większości przypadków nie ma żadnych jawnego typu informacji dostępne. Szczęście zwykle jest dość proste typu podany kontekst otaczającego kodu.
Ten proces jest nazywany wnioskowanie o typie.

Zmienna lub właściwości Typ jest zwykle typ wartości używaną do inicjalizacji lub najnowszych przypisanie wartości.

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Typ zwracany dla funkcji, można wywnioskować na podstawie instrukcjach return.

Dla parametrów funkcji nie jest obecnie nie wnioskowania, ale istnieją sposoby obejścia tego problemu za pomocą JSDoc lub TypeScript `.d.ts` plików (zobacz kolejnych sekcjach).

Ponadto ma specjalnych wnioskowania dla następujących elementów:

- Klasy "ES3-style", określić przy użyciu konstruktora funkcji i przypisania do właściwości prototypu.
- Wzorce modułu CommonJS stylu, określony jako właściwość przydziały na `exports` obiektu lub przypisania do `module.exports` właściwości.

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

### <a name="JsDoc"></a>IntelliSense w oparciu o JSDoc

Gdzie wnioskowanie o typie nie dostarcza informacji odpowiedniego typu (lub do obsługi dokumentacji), informacje o typie można podać jawnie za pomocą adnotacji JSDoc.  Na przykład aby dać częściowo zadeklarowane obiektu określonego typu, możesz użyć `@type` tagów, jak pokazano poniżej:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Jak wspomniano, nigdy nie są wywnioskować parametrów funkcji. Jednak przy użyciu JSDoc `@param` znaczników dodaniu typów, aby również parametrów funkcji.

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```

Zobacz [tego dokumentu](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) dla adnotacji JsDoc obecnie obsługiwane.

### <a name="TsDeclFiles"></a>IntelliSense oparte na plikach deklaracji TypeScript

Ponieważ JavaScript i TypeScript, teraz są oparte na tej samej usługi języka, są one możliwość interakcji w sposób bardziej zaawansowane funkcje. Na przykład można podać JavaScript IntelliSense dla wartości zadeklarowany w `.d.ts` pliku ([więcej informacji o](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)), i typach interfejsów i klasy zadeklarowany w maszynie są dostępne do użycia w komentarzy JsDoc jako typy. 

Poniżej zostanie przedstawiony prosty przykład pliku definicji TypeScript udostępnienie takich informacji o typie (za pośrednictwem interfejsu) do pliku JavaScript w tym samym projekcie (przy użyciu tagu JsDoc).

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640"/>

### <a name="Auto"></a>Automatyczne nabycie definicji typu

W świecie TypeScript najbardziej popularnych bibliotek JavaScript mają swoje interfejsy API opisanego przez `.d.ts` plików i najbardziej typowych repozytorium dla definicji takich znajduje się na [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

Domyślnie usługa języka Salsa podejmie próbę wykrywania, które biblioteki języka JavaScript są w użyciu i automatycznie pobierania i odwołanie do odpowiedniego `.d.ts` pliku, który opisuje biblioteki w celu zapewnienia bardziej zaawansowane funkcje IntelliSense. Pliki są pobierane do pamięci podręcznej znajduje się w folderze użytkownika w `%LOCALAPPDATA%\Microsoft\TypeScript`.

> [!NOTE]
> Ta funkcja jest **wyłączone** domyślnie, jeśli przy użyciu `tsconfig.json` konfiguracji pliku, ale może być do węzła enabled Ustaw jako obramowane dalsze poniżej.

Obecnie działa automatyczne wykrywanie zależności pobrany z pakietu npm (odczytując `package.json` pliku), Bower (odczytując `bower.json` pliku) i utracić plików w projekcie, które odpowiadają liście około top 400 najbardziej popularnych bibliotek JavaScript. Na przykład, jeśli masz `jquery-1.10.min.js` w projekcie, plik `jquery.d.ts` zostanie pobrane i ładowany w celu zapewnienia lepszej edytowania. To `.d.ts` pliku nie będzie miała wpływu na projekt.

Jeśli nie chcesz używać automatycznego przejęcia, należy ją wyłączyć za dodawanie pliku konfiguracji opisanych poniżej. Możesz nadal umieścić pliki definicji do użycia bezpośrednio w ramach projektu ręcznie.

## <a name="see-also"></a>Zobacz także

[Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)