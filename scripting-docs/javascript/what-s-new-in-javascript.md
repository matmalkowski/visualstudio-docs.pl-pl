---
title: Jaki &#39; s nowego w języku JavaScript | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 342b68ef-df93-48c4-81de-bdf6b6ce58d9
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 540d10958a7f2d406a6d70a633fc09a2cada8f41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792151"
---
# <a name="what39s-new-in-javascript"></a>Jaki &#39; s nowego w języku JavaScript
Ten dokument zawiera listę nowych funkcji w języku JavaScript, które są obsługiwane zarówno w [tryb Edge](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx), [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)]i aplikacji ze Sklepu Windows Phone.  
  
 Aby dowiedzieć się, które elementy języka JavaScript są obsługiwane w trybie krawędzi, lecz uznane za przestarzałe w [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] aplikacji, zobacz [informacje o wersji](../javascript/reference/javascript-version-information.md).  
  
> [!IMPORTANT]
>  Aby uzyskać informacje o sposobie tworzenia [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] i aplikacji ze Sklepu Windows Phone przy użyciu języka JavaScript, w tym informacje o Edytorze JavaScript programu Visual Studio i innych funkcji, zobacz [deweloperów Sklepu Windows przy użyciu programu Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkID=238263).  
  
## <a name="new-features-in-javascript"></a>Nowe funkcje w języku JavaScript  
  
|Funkcja|Opis|  
|-------------|-----------------|  
|Klasy|Deklaracji obsługuje nowej składni [klasy](../javascript/reference/class-statement-javascript.md).|  
|Ze zobowiązania|[Ze zobowiązania](../javascript/reference/promise-object-javascript.md) umożliwia łatwiejsze i czyszcząca asynchroniczne kodowania. Konstruktory Promise są obsługiwane, wraz z `all` i `race` metody narzędziowe.|  
|Iteratory|Teraz można iteracja iterable obiekty (w tym tablic, tablicy obiektów i Iteratory), wywoływania haku niestandardowych iteracji, instrukcji do wykonania dla wartości każdej różne właściwości. Aby uzyskać więcej informacji, zobacz [Iteratory i generatory](../javascript/advanced/iterators-and-generators-javascript.md). **Uwaga:** generatory nie są jeszcze obsługiwane.|  
|Funkcje Strzałka|Funkcji strzałkowej (= >) zapewnia składni skrótu dla `function` — słowo kluczowe, które funkcje leksykalne `this` powiązania.|  
|Nowych metod wbudowanych obiektów|[Obiekt Array](../javascript/reference/array-object-javascript.md), [Math — obiekt](../javascript/reference/math-object-javascript.md), [Number obiektu](../javascript/reference/number-object-javascript.md), [obiekt obiektu](../javascript/reference/object-object-javascript.md), i [ciągu obiektu](../javascript/reference/string-object-javascript.md) obiekty wbudowane obejmują wiele nowych funkcji narzędzia i właściwości dla manipulowanie i zapoznanie się dane.|  
|Ulepszenia literału obiektu|Obiekty obsługują teraz właściwości obliczanej, definicje zwięzły — metoda i składni skrótu dla właściwości, której wartość jest ustawiana na zmiennej o tej samej nazwie. Aby uzyskać więcej informacji, zobacz [Tworzenie obiektów](../javascript/creating-objects-javascript.md).|  
|Serwery proxy|[Serwery proxy](../javascript/reference/proxy-object-javascript.md) włączyć niestandardowe zachowanie dla obiektów.|  
|Parametrów REST|Parametry REST umożliwiają włączenie kolejnych argumentów w wywołaniu funkcji do tablicy. Aby uzyskać więcej informacji, zobacz [funkcji](../javascript/functions-javascript.md).|  
|Operator rozwijania|[Operator rozpiętości](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md) (`...`) rozszerza iterable wyrażeń oddzielne argumenty. Na przykład `a.b(...array)` około jest taka sama jak `a.b.apply(a, array)`.|  
|Symbole|[Symbol](../javascript/reference/symbol-object-javascript.md) obiektów Zezwalaj na właściwości mają zostać dodane do istniejących obiektów z możliwości ingerencji z istniejącej właściwości obiektów, nie niezamierzone widoczność i innych dodatków nieskoordynowane przez inny kod.|  
|Ciągi szablonu|[Ciągi szablonu](../javascript/advanced/template-strings-javascript.md) są literałów ciągów, umożliwiające wyrażeń, które ma zostać obliczone i połączony z literału ciągu.|  
|Ulepszenia Unicode|Wprowadzono ulepszenia Obsługa standardu Unicode. Na przykład nowy format sekwencji ucieczki obsługuje punktów kodowych błyszczące (punktów kodu z więcej niż czterech cyfr szesnastkowych). Aby uzyskać więcej informacji, zobacz [znaki specjalne](../javascript/advanced/special-characters-javascript.md).|  
|WeakSet|A [WeakSet](../javascript/reference/weakset-object-javascript.md) jest kolekcją obiektów, które będą bezużytecznych, jeśli nie są one odwołuje się do dowolnego miejsca.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka JavaScript](../javascript/javascript-language-reference.md)