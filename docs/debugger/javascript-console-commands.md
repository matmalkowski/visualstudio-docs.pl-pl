---
title: Konsola JavaScript poleceń w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/17/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- JavaScript Console commands [UWP apps]
- JavaScript debugging, console [UWP apps]
- debugging JavaScript, console [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
- cordova
ms.openlocfilehash: 2c0151bb0810529f0dad36d72b80a13ae519e8b0
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31478723"
---
# <a name="javascript-console-commands-in-visual-studio"></a>Polecenia konsoli języka JavaScript w programie Visual Studio
  
 Polecenia służą do wysyłania wiadomości i wykonywać inne zadania w oknie konsoli JavaScript programu Visual Studio. Aby uzyskać przykłady pokazujące, które przedstawiają sposób korzystania z tego okna, zobacz [Szybki Start: debugowanie JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md). Informacje przedstawione w tym temacie dotyczą do aplikacji platformy uniwersalnej systemu Windows oraz aplikacji utworzone przy użyciu programu Visual Studio Tools for Apache Cordova. Aby uzyskać informacje na temat obsługiwanych konsoli poleceń w aplikacji oprogramowania Cordova, zobacz [Debug Your App](https://taco.visualstudio.com/en-us/docs/debug-using-visual-studio/). Aby uzyskać informacje na temat używania konsoli programu w menu Narzędzia programu Internet Explorer F12, zobacz [w tym temacie](http://msdn.microsoft.com/library/ie/dn255006.aspx).  
  
 Jeśli nastąpi zamknięcie okna konsoli języka JavaScript, możesz otworzyć go podczas debugowania kodu w programie Visual Studio, wybierając **debugowania** > **Windows** > **JavaScript Konsola**.  
  
> [!NOTE]
>  Jeśli okno nie jest dostępna podczas sesji debugowania, upewnij się, że typ debugera jest ustawiona na **skryptu** we właściwościach debugowania dla projektu.  
  
## <a name="console-object-commands"></a>polecenia obiektu konsoli  
 W tej tabeli przedstawiono składnię `console` obiekt polecenia, czy można użyć w oknie konsoli języka JavaScript, lub że służy do wysyłania komunikatów do konsoli w kodzie. Ten obiekt udostępnia wiele formularzy, dzięki czemu można rozróżnić komunikaty informacyjne i komunikaty o błędach, jeśli chcesz.  
  
 Możesz użyć dłużej formularza polecenia `window.console.[command]` Aby uniknąć potencjalne problemy z lokalnych obiektów o nazwie konsoli.  
  
> [!TIP]
>  Starsze wersje programu Visual Studio nie obsługują pełny zestaw poleceń. Użyj funkcji IntelliSense na obiekt konsoli, aby uzyskać szybki informacji na temat obsługiwanych poleceń.  
  
|Polecenie|Opis|Przykład|  
|-------------|-----------------|-------------|  
|`assert(expression, message)`|Wysyła komunikat, jeśli `expression` daje w wyniku **false**.|`console.assert((x == 1), "assert message: x != 1");`|  
|`clear()`|Usuwa wiadomości z okna konsoli, łącznie z komunikatami błąd skryptu, a także czyści skrypt, który jest wyświetlany w oknie konsoli. Czyści skrypt, który wprowadzono w wierszu danych wejściowych.|`console.clear();`|  
|`count(title)`|Wysyła liczbę polecenia Statystyka została wywołana w oknie konsoli. Każde wywołanie count jest unikatowo identyfikowana przez opcjonalny `title`.<br /><br /> Istniejący wpis w oknie konsoli jest identyfikowany przez `title` parametr (jeśli istnieje) i zaktualizować za pomocą polecenia count. Nie utworzono nowy wpis.|`console.count();`<br /><br /> `console.count("inner loop");`|  
|`debug(message)`|Wysyła `message` w oknie konsoli.<br /><br /> To polecenie jest taki sam jak console.log.<br /><br /> Obiekty, które są przekazywane za pomocą polecenia są konwertowane na wartość ciągu.|`console.debug("logging message");`|  
|`dir(object)`|Wysyła obiekt określony w oknie konsoli i wyświetla je w wizualizatora obiektu. Wizualizator służy do sprawdzenia właściwości w oknie konsoli.|`console.dir(obj);`|  
|`dirxml(object)`|Wysyła Podany węzeł XML `object` w oknie konsoli i wyświetla je jako XML węzła drzewa.|`console.dirxaml(xmlNode);`|  
|`error(message)`|Wysyła `message` w oknie konsoli. Tekst komunikatu jest czerwona i poprzedzone symbolem błędu.<br /><br /> Obiekty, które są przekazywane za pomocą polecenia są konwertowane na wartość ciągu.|`console.error("error message");`|  
|`group(title)`|Uruchamia grupowanie komunikatów, które są wysyłane do okna konsoli, a następnie wysyła opcjonalny `title` jako etykieta grupy. Grupy mogą być zagnieżdżane i są wyświetlane w widoku drzewa w oknie konsoli.<br /><br /> Polecenia grupy * może ułatwić wyświetlić dane wyjściowe z okna konsoli w niektórych scenariuszach, na przykład gdy jest używany model składników.|`console.group("Level 2 Header");` <br /> `console.log("Level 2");` <br /> `console.group();` <br /> `console.log("Level 3");` <br /> `console.warn("More of level 3");` <br /> `console.groupEnd();` <br /> `console.log("Back to level 2");` <br /> `console.groupEnd();` <br /> `console.debug("Back to the outer level");`|  
|`groupCollapsed(title)`|Uruchamia grupowanie komunikatów, które są wysyłane do okna konsoli, a następnie wysyła opcjonalny `title` jako etykieta grupy. Grupy, które są wysyłane przy użyciu `groupCollapsed` domyślnie wyświetlana w widoku zwiniętym. Grupy mogą być zagnieżdżane i są wyświetlane w widoku drzewa w oknie konsoli.|Użycie jest taka sama jak `group` polecenia.<br /><br /> Zobacz przykład `group` polecenia.|  
|`groupEnd()`|Kończy się bieżącą grupę.<br /><br /> Wymagania:<br /><br /> Visual Studio 2013|Zobacz przykład `group` polecenia.|  
|`info(message)`|Wysyła `message` w oknie konsoli. Komunikat jest poprzedzone symbolem informacji.|`console.info("info message");`<br /><br /> Aby uzyskać więcej przykładów, zobacz [formatowanie danych wyjściowych console.log](#ConsoleLog) dalszej części tego tematu.|  
|`log(message)`|Wysyła `message` w oknie konsoli.<br /><br /> W przypadku przekazania obiektu, to polecenie wysyła tego obiektu w oknie konsoli i wyświetla go w wizualizatora obiektu. Wizualizator służy do sprawdzenia właściwości w oknie konsoli.|`console.log("logging message");`|  
|`msIsIndependentlyComposed(element)`|Używane w aplikacji sieci web. Nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows przy użyciu języka JavaScript.|Nieobsługiwane.|  
|`profile(reportName)`|Używane w aplikacji sieci web. Nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows przy użyciu języka JavaScript.|Nieobsługiwane.|  
|`profileEnd()`|Używane w aplikacji sieci web. Nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows przy użyciu języka JavaScript.|Nieobsługiwane.|  
|`select(element)`|Wybiera określony kod HTML `element` w [Eksploratora modelu DOM](../debugger/quickstart-debug-html-and-css.md).|console.select(element);|  
|`time (name)`|Uruchamia czasomierz identyfikowany przez opcjonalny `name` parametru. W przypadku użycia z `console.timeEnd`, oblicza czas, jaki musi upłynąć między `time` i `timeEnd`i zwraca wynik (mierzony w ms) przy użyciu konsoli `name` ciągu jako prefiksu. Używana do umożliwienia Instrumentacja kodu aplikacji do pomiaru wydajności.|`console.time("app start");  app.start();  console.timeEnd("app start");`|  
|`timeEnd(name)`|Zatrzymuje czasomierz identyfikowany przez opcjonalny `name` parametru. Zobacz `time` konsoli poleceń.|`console.time("app start"); app.start(); console.timeEnd("app start");`|  
|`trace()`|Wysyła ślad stosu w oknie konsoli. Śledzenie stosu wywołań pełną i zawierają informacje, takie jak nazwa pliku, numeru wiersza i numer kolumny.|`console.trace();`|  
|`warn(message)`|Wysyła `message` w oknie konsoli poprzedzone symbolem ostrzeżenia.<br /><br /> Obiekty, które są przekazywane za pomocą polecenia są konwertowane na wartość ciągu.|`console.warn("warning message");`|  
  
## <a name="miscellaneous-commands"></a>Inne polecenia  
 Te polecenia są również dostępne w oknie konsoli języka JavaScript (nie są one dostępne z kodu).  
  
|Polecenie|Opis|Przykład|  
|-------------|-----------------|-------------|  
|`$0`, `$1`, `$2`, `$3`, `$4`|Zwraca określony element w oknie konsoli. `$0` Zwraca element aktualnie wybrane w programie DOM Explorer `$1` zwraca wybranego wcześniej w modelu DOM Explorer i tak dalej, aż czwartym elementem poprzednio wybranego elementu.|$3|  
|`$(id)`|Zwraca element według identyfikatora. To polecenie skrótów dla `document.getElementById(id)`, gdzie `id` jest ciągiem, który reprezentuje identyfikatorem elementu.|`$("contenthost")`|  
|`$$(selector)`|Zwraca tablicę elementów spełniających określony selektor przy użyciu składni selektora CSS. To polecenie skrótów dla `document.querySelectorAll()`.|`$$(".itemlist")`|  
|`cd()`<br /><br /> `cd(window)`|Umożliwia zmienianie kontekstu dla wyrażenia w oknie najwyższego poziomu domyślnej strony okna określonej ramce. Wywoływanie `cd()` bez parametrów zwraca kontekst do okna najwyższego poziomu.|`cd();`<br /><br /> `cd(myframe);`|  
|`select(element)`|Wybiera określony element w [Eksploratora modelu DOM](../debugger/quickstart-debug-html-and-css.md).|`select(document.getElementById("element"));`<br /><br /> `select($("element"));`<br /><br /> `select($1);`|  
|`dir(object)`|Zwraca wizualizatora dla określonego obiektu. Wizualizator służy do sprawdzenia właściwości w oknie konsoli.|`dir(obj);`|  
  
## <a name="checking-whether-a-console-command-exists"></a>Sprawdzanie, czy istnieje polecenia konsoli  
 Można sprawdzić, czy określone polecenie istnieje przed próbą użycia go. W tym przykładzie sprawdza istnienie `console.log` polecenia. Jeśli `console.log` istnieje, kod wywołuje go.  
  
```javascript  
if (console && console.log) {  
    console.log("msg");  
}  
  
```  
  
## <a name="examining-objects-in-the-javascript-console-window"></a>Badanie obiektów w oknie konsoli JavaScript  
 Możesz użyć dowolnego obiektu, który znajduje się w zakresie, korzystając z okna konsoli języka JavaScript. Aby sprawdzić obiekt poza zakresem w oknie konsoli, należy użyć `console.log` , `console.dir`, lub innych poleceń z poziomu kodu. Alternatywnie możesz użyć obiektu z okna konsoli, gdy znajduje się w zakresie ustawiając punkt przerwania w kodzie (**punktu przerwania** > **wstawić punktu przerwania**).  
  
##  <a name="ConsoleLog"></a> Formatowanie danych wyjściowych console.log  
 W przypadku przekazania wiele argumentów `console.log`, konsoli będzie traktować jako tablica argumentów i łączenie danych wyjściowych.  
  
```javascript  
var user = new Object();  
user.first = "Fred";  
user.last = "Smith";  
  
console.log(user.first, user.last);  
// Output:  
// Fred Smith  
  
```  
  
 `console.log` obsługuje również wzorce podstawienia "printf" do formatowania danych wyjściowych. Jeśli używasz wzorce podstawienia w pierwszym argumencie dodatkowe argumenty będzie używany do zastępowania określonego wzorce w kolejności, które są używane.  
  
 Obsługiwane są następujące wzorce podstawienia:  
  
-   %s - ciągu  
     %i — liczba całkowita  
     %d - Liczba całkowita  
     %f - liczb zmiennoprzecinkowych  
     %o — obiekt  
     %b - binarne  
     %x - szesnastkowe  
     %e - wykładnika  
  
 Oto kilka przykładów użycia wzorce podstawienia w `console.log`:  
  
```javascript  
var user = new Object();  
user.first = "Fred";  
user.last = "Smith";  
user.age = 10.01;  
console.log("Hi, %s %s!", user.first, user.last);  
console.log("%s is %i years old!", user.first, user.age);  
console.log("%s is %f years old!", user.first, user.age);  
  
// Output:  
// Hi, Fred Smith!  
// Fred is 10 years old!  
// Fred is 10.01 years old!  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Szybki Start: Debugowanie kodu JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)   
 [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)