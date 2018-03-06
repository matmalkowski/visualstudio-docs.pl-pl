---
title: JavaScript w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 04/10/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: 
author: bowdenk7
ms.author: wilkelly
manager: ghogen
ms.openlocfilehash: 5b13f01a1a5ba13503932c73aef3a4825115497e
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2018
---
# <a name="javascript-in-visual-studio-2017"></a>Język JavaScript w programie Visual Studio 2017 r.

JavaScript jest językiem pierwszą klasą w programie Visual Studio. Podczas pisania kodu w języku JavaScript w środowisku IDE programu Visual Studio można używać większości lub wszystkich standardowych ułatwień edycji (fragmenty kodu, technologia IntelliSense itd.). Można napisać kod JavaScript dla wielu typów aplikacji i usług.

## <a name="ES6"></a> Obsługa języka ECMAScript 2015 (ES6) i później

Program Visual Studio teraz obsługuje składni dla aktualizacji w języku ECMAScript takich jak ECMAScript 2015 2016.

### <a name="what-is-ecmascript-2015"></a>Co to jest używany język ECMAScript 2015?

JavaScript jest wciąż rozwijana jako język programowania i [TC39](http://www.ecma-international.org/memento/TC39.htm) jest odpowiedzialny za wprowadzanie aktualizacji Komitetu.
ECMAScript 2015 jest aktualizacją języka JavaScript, wprowadzający przydatne nowej składni i funkcje. Aby uzyskać szczegółowe informacje na temat funkcji ES6, zapoznaj się z [to](http://es6-features.org) lokacji odniesienia.

Oprócz obsługi języka ECMAScript 2015 Visual Studio obsługuje ECMAScript 2016 i trzeba będzie pomocy technicznej w przyszłych wersjach programu ECMAScript po ich wydaniu. Nadążyć TC39 i najnowsze zmiany w języku ECMAScript, należy wykonać pracę [github](https://github.com/tc39).

### <a name="transpile-javascript"></a>Transpile JavaScript

To powszechny problem ze skryptem JavaScript jest mają korzystać z najnowszych funkcji języka ES6 + ponieważ pomagają są bardziej wydajni, ale środowiska środowiska uruchomieniowego (często przeglądarki) nie obsługują te nowe funkcje. To oznacza, że należy posiadać do śledzenia przeglądarki obsługuje funkcje (które może być niewygodny), lub należy przekonwertować kodu ES6 + na wersję dokładnie, środowiska uruchomieniowe sieci docelowej (zazwyczaj ES5). Konwertowanie kodu na wersję obsługującą środowiska uruchomieniowego jest często określana jako "transpiling".

Jedną z kluczowych funkcji usługi maszynie jest transpile możliwości ES6 + kod ES5 lub ES3, tak aby napisać kod, który zwiększa najbardziej wydajni, ale nadal uruchamiać kod na dowolnej platformie. Ponieważ JavaScript w [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] używa tego samego języka usługi jako języka TypeScript, zbyt może korzystać z ES6 + do ES5 transpilation.

Przed transpilation można skonfigurować, niektóre wiedzę na temat opcji konfiguracji jest wymagana.
TypeScript jest skonfigurowana za pośrednictwem `tsconfig.json` pliku.
W przypadku braku takiego pliku niektóre wartości domyślne są używane.
Ze względu na zgodność, te ustawienia domyślne różnią się w kontekście, w przypadku, gdy tylko pliki JavaScript (i opcjonalnie `.d.ts` pliki) są obecne.
Aby skompilować pliki JavaScript `tsconfig.json` można dodać pliku, a niektóre z tych opcji musi być ustawiony w sposób jawny.

Wymagane ustawienia dla pliku tsconfig są następujące:

 - `allowJs`: Ta wartość musi być równa `true` plików JavaScript być rozpoznawane. Wartość domyślna to `false`, ponieważ TypeScript kompiluje się do języka JavaScript i kompilator nie może zawierać pliki go skompilować.
 - `outDir`: Ta wartość powinna być równa lokalizacji nie dołączony do projektu, aby emitowany pliki JavaScript nie są wykrywane i dołączony do projektu (zobacz `exclude`).
 - `module`: Jeśli przy użyciu modułów, to ustawienie informuje kompilator, który format modułu kodu emitowany należy używać (na przykład `commonjs` dla węzła lub narzędzia tworzące pakiety, takie jak Browserify).
 - `exclude`: To ustawienie stanów foldery, które nie, aby uwzględnić w projekcie.
 Lokalizacja danych wyjściowych, jak również folderów poza projektem, takich jak `node_modules` lub `temp`, powinny zostać dodane do tego ustawienia.
 - `enableAutoDiscovery`: To ustawienie umożliwia automatyczne wykrywanie i pobierania plików definicji w sposób opisany wcześniej.
 - `compileOnSave`: To ustawienie informuje kompilator, jeśli jego ponowne skompilowanie zawsze, gdy plik źródłowy jest zapisywany w programie Visual Studio.
 - `typeAcquisition`: Ten zestaw ustawień kontrolowania zachowania typu automatycznego przejęcia (dokładniejszego wyjaśnienia w [w tej sekcji](https://docs.microsoft.com/en-us/visualstudio/ide/javascript-intellisense#Auto))

Aby można było przekonwertować pliki JavaScript do modułów CommonJS i umieść je w `./out` folderu, można użyć następującego `tsconfig.json` pliku:

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typeAcquisition": {
    "enable": true
  }
}
```

Z ustawieniami w miejscu, jeśli plik źródłowy (`./app.js`) istnieje i zawiera kilka funkcji języka ECMAScript 2015 w następujący sposób:

```js
import {Subscription} from 'rxjs/Subscription';  // ES6 import

class Foo {  // ES6 Class
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;  // ES6 template string
    }
}

export let sqr = x => x * x;  //ES6 export, let, and arrow function
export default Subscription;  //ES6 default export
```

Wówczas plik będzie emitowany do `./out/app.js` używany język ECMAScript 5 (ustawienie domyślne), która wygląda podobnie do następującej:

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
```

## <a name="better-intellisense"></a>Lepsza technologia IntelliSense

IntelliSense dla JavaScript w [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] będą teraz wyświetlane znacznie więcej informacji na temat parametrów i listach elementów członkowskich. To nowe informacje są udostępniane przez usługi języka TypeScript, która używa analizy statycznej w tle, aby lepiej zrozumieć kodu. Możesz przeczytać więcej na temat nowego środowiska IntelliSense i jak działa [tutaj](/visualstudio/ide/javascript-intellisense/).

## <a name="JSX"></a> Obsługa składnia JSX

Język JavaScript w [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] ma szeroką obsługę składnia JSX. JSX to zestaw składni, które pozwalają tagów HTML w plikach języka JavaScript.

Na poniższej ilustracji przedstawiono składnik platformy React zdefiniowane w `comps.tsx` plików TypeScript, a następnie tego składnika używany z `app.jsx` pliku ukończone z IntelliSense dla zakończeń i dokumentacji w wyrażeniach JSX.
Nie ma potrzeby TypeScript w tym miejscu, w tym przykładzie określonych tylko stanie się zawierają części kodu TypeScript.

<img src="./media/react.png" height="500" width="640"/>

> [!NOTE]
> Aby przekonwertować składnia JSX platformy React wywołuje, ustawienie `"jsx": "react"` musi zostać dodany do `compilerOptions` w `tsconfig.json` pliku.

Plik JavaScript utworzonego w dniu ". / out/app.js podczas kompilacji zawierałoby kod:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>Konfigurowanie projektu w języku JavaScript

Usługa języka jest obsługiwany przez analizę statyczną, co oznacza, że analizę kodu źródłowego bez rzeczywistego wykonania go w celu zwracania wyników IntelliSense i udostępnia inne funkcje edycji.
W związku z tym im jest większa od liczby i rozmiaru plików, które są uwzględniane kontekst projektu, więcej pamięci i procesora CPU, które będą używane podczas analizy.
W związku z tym istnieje kilka założenia domyślne wprowadzone o kształt projektu:

- `package.json` i `bower.json` listy zależności używany w projekcie i domyślnie znajdują się w nabycia typu automatyczne (ATA)
- Najwyższego poziomu `node_modules` folder zawiera kod źródłowy biblioteki oraz jego zawartość, są wykluczane w kontekście projektu domyślnie
- Co drugi `.js`, `.jsx`, `.ts`, i `.tsx` plik jest prawdopodobnie jednym z *własne* pliki źródłowe i muszą być zawarte w kontekście projektu

W większości przypadków można po prostu otwórz projekt i mieć wspaniały użycie domyślnej konfiguracji projektu. Jednak w projektach, które są duże lub mieć inny folder struktury, może być pożądane, aby kontynuować konfigurowanie usługi języka aby lepiej fokus tylko dla plików źródłowych.

### <a name="override-defaults"></a>Zastąp domyślne wartości

Można zastąpić domyślną konfigurację, dodając `tsconfig.json` plik do katalogu głównym projektu.
A `tsconfig.json` ma kilka różne opcje, których można manipulować kontekst projektu.
Niektóre z nich są wymienione poniżej, ale do pełnego zestawu wszystkie opcje dostępne, [Zobacz Schemat magazynu](http://json.schemastore.org/tsconfig).

## <a name="important-tsconfigjson-options"></a>Ważne `tsconfig.json` opcje

```json
{
  "compilerOptions": {
    "allowJs": true,          // include .js and .jsx in project context (defaults to only .ts and .tsx)
    "noEmit": true            // turns off downlevel compiler
  },
  "files": [],                // list of explicit files to include in the project context. Highest priority.
  "include": [],              // list of folders or glob patterns to include in the project context.
  "exclude": [],              // list of folders or glob patterns to exclude. Overridden by files array.
  "typeAcquisition": {
    "enable": true,           // Defaulted to "false" with a tsconfig. Enables better IntelliSense in JS.
    "include": [ "jquery" ],  // Specific libs to fetch .d.ts files that weren't picked up by ATA
    "exclude": [ "node" ]     // Specific libs to not fetch .d.ts files for
  }
}
```

### <a name="example-project-configuration"></a>Przykładowa konfiguracja projektu

Podane projekt o następujące ustawienia:

- pliki źródłowe projektu są w `wwwroot/js`
- pliki projektu lib znajdują się w `wwwrrot/lib`
- `bootstrap`, `jquery`, `jquery-validation`, i `jquery-validation-unobtrusive` są wyświetlane w `bower.json`
- `kendo-ui` został dodany ręcznie do folderu lib

![Struktura folderów](./media/folderStructure.png)

Można użyć następującego `tsconfig.json` się upewnić się, że język usługi analizuje tylko plików źródłowych w `js` folderu, ale nadal pobiera i używa `.d.ts` pliki bibliotek w Twojej `lib` folderu.

```json
{
  "compilerOptions": {
    "allowJs": true,
    "noEmit": true
  },
  "exclude": ["wwwroot/lib"],  //ignore lib folders, we will get IntelliSense via ATA
  "typeAcquisition": {
    "enable": true,
    "include": [ "kendo-ui" ]  //kendo-ui wasn't added via bower, so we need to list it here
  }
}
```
# <a name="troubleshooting-the-javascript-language-service-has-been-disabled-for-the-following-projects"></a>Rozwiązywanie problemów z usługi języka JavaScript zostało wyłączone dla następujących projektach
Po otwarciu projektu w języku JavaScript, który ma bardzo dużą ilość zawartości, może otrzymać komunikat o treści "Usługa języka JavaScript zostało wyłączone dla następujących projektach". Najczęstszą przyczyną występowania bardzo dużą ilość źródłowego JavaScript wynika z tym bibliotek z kodem źródłowym, która przekracza limit projektu 20 MB.

Prosty sposób, aby zoptymalizować projektu jest dodanie `tsconfig.json` pliku w katalogu głównym projektu, aby umożliwić usługi języka wiadomo, które pliki są bezpiecznie zignorować. Użyć poniższy przykład wykluczyć najczęściej katalogów, w którym będą przechowywane biblioteki:

```json
{
  "compilerOptions": {
    "allowJs": true,
    "allowSyntheticDefaultImports": true,
    "maxNodeModuleJsDepth": 2,
    "noEmit": true,
    "skipLibCheck": true
  },
  "exclude": [
    "**/bin",
    "**/bower_components",
    "**/jspm_packages",
    "**/node_modules",
    "**/obj",
    "**/platforms"
  ]
}
```

Dodaj więcej katalogów zgodnie z własnymi potrzebami. Oto inne przykłady "dostawca" lub "wwwroot/lib" katalogów. 

> [!NOTE]
> Właściwość kompilatora `disableSizeLimit` można również wyłączyć limit wyboru 20 MB. Mają specjalne środki ostrożności w przypadku za pomocą tej właściwości, ponieważ wyłączenie limitu mogą ulec awarii usługi języka.

## <a name="notable-changes-from-visual-studio-2015"></a>Ważne zmiany z programu Visual Studio 2015

Jako [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] funkcji całkowicie nowej usługi języka, istnieje kilka zachowania, które będą się różnić lub brak możliwości poprzedniej.
Najbardziej znaczące zmiany są zastąpienia VSDoc z JSDoc, usunięcie niestandardowe `.intellisense.js` rozszerzenia i ograniczona IntelliSense dla określonego kodu wzorców.

### <a name="no-more-references-or-referencesjs"></a>Brak `///<references/>` lub `_references.js`

Wcześniej były dość skomplikowane, aby zrozumieć, w danym momencie pliki będące w zakresie Twoich obowiązków IntelliSense. Czasami jest pożądane, aby wszystkie pliki w zakresie oraz innym razem, który nie był i to doprowadziło do złożonych konfiguracji, obejmujących zarządzania ręczne odwołanie. Idąc dalej, nie trzeba myśleć o zarządzania odwołania, a więc nie trzeba potrójnym ukośnikiem odwołuje się komentarze lub `_references.js` plików.

Zobacz [IntelliSense dla JavaScript](/visualstudio/ide/javascript-intellisense/) strony, aby uzyskać więcej informacji na działanie funkcji IntelliSense.

### <a name="vsdoc"></a>VSDoc

Komentarze dokumentacji XML, czasami określane jako VSDocs, wcześniej mogą służyć do dekoracji kodu źródłowego za pomocą dodatkowych danych, które będzie służyć do pasjonatem się wyniki IntelliSense.
VSDoc nie jest już obsługiwana uzyskać [JSDoc](http://usejsdoc.org/about-getting-started.html) który jest łatwiejsze do zapisu i zaakceptowane standard obsługi języka JavaScript.

### <a name="intellisensejs-extensions"></a>`.intellisense.js` Rozszerzenia

Wcześniej, można utworzyć [rozszerzenia IntelliSense](https://msdn.microsoft.com/en-us/library/hh874692.aspx) pozwoliłoby na dodawanie wyników zakończenia niestandardowych bibliotek innych firm.
Te rozszerzenia były dość trudne do zapisu i instalowanie i odwołanie się do nich został obciążeniem, więc przyszłości nowej usługi języka nie obsługuje tych plików.
Jako alternatywę łatwiejsze może zapisać pliku definicji TypeScript zapewnienie tego samego korzyści IntelliSense jako stary `.intellisense.js` rozszerzenia.
Dowiedz się więcej o deklaracji (`.d.ts`) tworzenia pliku [tutaj](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html).

### <a name="unsupported-patterns"></a>Wzorce nieobsługiwane

Ponieważ nowej usługi języka jest obsługiwany przez analizę statyczną zamiast aparat wykonywania (odczytu [ten problem](https://github.com/Microsoft/TypeScript/issues/4789) informacji o różnicach), istnieje kilka wzorców JavaScript, które nie mogą być wykrywane.
Najbardziej typowe wzorzec jest wzorzec "expando".
Obecnie usługa języka nie może dostarczyć IntelliSense dla obiektów, których przyczepiana po deklaracji właściwości.
Na przykład:

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

Aby uzyskać obejścia tego problemu, należy deklarowanie właściwości podczas tworzenia obiektu:

```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

Można również dodać komentarzy JSDoc w następujący sposób:

```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```
