---
title: String — obiekt (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- String_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object
- String object, overview
ms.assetid: 8063ecd5-5778-4e87-b985-b21420171914
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d58f567bb301b29324fee8ed75fc95fd1a4791ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792193"
---
# <a name="string-object-javascript"></a>String — Obiekt (JavaScript)
Umożliwia formatowanie ciągów tekstowych i manipulowanie nimi oraz określanie lokalizacji podciągów wewnątrz ciągów.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
newString = new String(["stringLiteral"])  
```  
  
## <a name="parameters"></a>Parametry  
 `newString`  
 Wymagany. Nazwa zmiennej, do której `String` obiekt jest przypisany.  
  
 `stringLiteral`  
 Opcjonalny. Jakakolwiek grupa znaków Unicode.  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]udostępnia sekwencji unikowych, które można uwzględnić w ciągach znaków, których nie można wpisać bezpośrednio utworzyć. Na przykład `\t` określa znak tabulacji. Aby uzyskać więcej informacji, zobacz [znaki specjalne](../../javascript/advanced/special-characters-javascript.md).  
  
## <a name="string-literals"></a>Literały ciągu  
 A *literału ciągu* zero lub więcej znaków ujęty w pojedynczym lub podwójnym cudzysłowie. Literał ciągu ma typ danych (pierwotne) podstawowych `string`. A *obiekt String* jest tworzona przy użyciu [operatora new](../../javascript/reference/new-operator-decrementjavascript.md), i ma typ danych elementu `Object`.  
  
 W poniższym przykładzie pokazano, że typ danych literału ciągu znaków nie jest taka sama, jak te `String` obiektu.  
  
```JavaScript  
var strLit = "This is a string literal.";  
var strObj = new String("This is a string object.");  
  
document.write(typeof strLit);  
document.write("<br/>");  
document.write(typeof strObj);  
// Output:  
// string  
// object  
```  
  
## <a name="methods-for-string-literals"></a>Metody literałów ciągów  
 Jeżeli wywołujesz metodę na literale ciągu, ciąg ten jest tymczasowo konwertowany na obiekt opakowany typu string. Literał ciągu jest traktowany jako `new` operatora użyto do jego utworzenia.  
  
 Następujący przykład dotyczy `toUpperCase` metodę literału ciągu.  
  
```JavaScript  
var strLit = "This is a string literal.";  
  
var result1 = strLit.toUpperCase();  
  
var result2 = (new String(strLit)).toUpperCase();  
  
document.write(result1);  
document.write("<br/>");  
document.write(result2);  
// Output:   
// THIS IS A STRING LITERAL.  
// THIS IS A STRING LITERAL.  
```  
  
## <a name="accessing-an-individual-character"></a>Uzyskiwanie dostępu do pojedynczego znaku  
 Indywidualne znaki ciągu są dostępne jako właściwość tylko do odczytu indeksowana tablicowo. Ta funkcja została wprowadzona w [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)]. Poniższy przykład uzyskuje dostęp do poszczególnych znaków w ciągu.  
  
```JavaScript  
var str = "abcd";  
var result = str[2];  
document.write (result);  
// Output: c  
  
var result = "the"[0];  
document.write(result);  
// Output: t  
```  
  
## <a name="requirements"></a>Wymagania  
 `String Object` Została wprowadzona w systemie [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)]. Niektóre elementy członkowskie wymienione na poniższej liście zostały wprowadzone w nowszych wersjach.  
  
<a name="js56jsobjstringprop"></a>   
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono właściwości `String` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[constructor — właściwość](../../javascript/reference/constructor-property-string.md)|Określa funkcję, która tworzy obiekt.|  
|[length — właściwość (ciąg)](../../javascript/reference/length-property-string-javascript.md)|Zwraca długość `String` obiektu.|  
|[prototype — właściwość](../../javascript/reference/prototype-property-string.md)|Zwraca odwołanie do prototypu klasy obiektów.|  
  
## <a name="functions"></a>Funkcje  
 W poniższej tabeli wymieniono funkcje `String` obiektu.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[Funkcja String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)|Zwraca ciąg utworzony z wielu wartości znaków Unicode.|  
|[String.fromcodepoint — funkcja](../../javascript/reference/string-fromcodepoint-function-javascript.md)|Zwraca ciąg skojarzone z punkt kodu Unicode UTF-16.|  
|[String.RAW — funkcja](../../javascript/reference/string-raw-function-javascript.md)|Zwraca ciąg szablonu formę nieprzetworzony ciąg.|  
  
<a name="js56jsobjstringmeth"></a>   
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `String` obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[zakotwiczenia — metoda](../../javascript/reference/html-tag-methods-javascript.md)|Umieszcza wokół tekstu kotwicę HTML, która zawiera atrybut NAME.|  
|[big — metoda](../../javascript/reference/html-tag-methods-javascript.md)|Umieszcza HTML \<BIG > tagi wokół tekstu.|  
|[BLINK — metoda](../../javascript/reference/html-tag-methods-javascript.md)|Umieszcza HTML \<BLINK > tagi wokół tekstu.|  
|[Bold — metoda](../../javascript/reference/html-tag-methods-javascript.md)|Umieszcza HTML \<B > tagi wokół tekstu.|  
|[charAt — metoda](../../javascript/reference/charat-method-string-javascript.md)|Zwraca znak pod określonym indeksem.|  
|[charCodeAt — metoda](../../javascript/reference/charcodeat-method-string-javascript.md)|Zwraca kodowanie Unicode określonego znaku.|  
|[codepointat — metoda](../../javascript/reference/codepointat-method-string-javascript.md)|Zwraca punkt kodu znaku Unicode UTF-16.|  
|[Metoda concat (ciąg)](../../javascript/reference/concat-method-string-javascript.md)|Zwraca ciąg, który zawiera połączenie dwóch podanych ciągów.|  
|[endsWith — metoda](../../javascript/reference/endswith-method-string-javascript.md)|Zwraca wartość logiczną, wskazującą, czy ciąg lub podciąg kończy się ciągiem przekazana.|  
|[includes — metoda](../../javascript/reference/includes-method-string-javascript.md)|Zwraca wartość logiczną, wskazującą, czy przekazano ciągu znajduje się w obiekcie string.|  
|[Fixed — metoda](../../javascript/reference/html-tag-methods-javascript.md)|Umieszcza HTML \<TT > tagi wokół tekstu.|  
|[fontcolor — metoda](../../javascript/reference/html-tag-methods-javascript.md)|Umieszcza HTML \<czcionki > tag z atrybutem kolor wokół tekstu.|  
|[FontSize — metoda](../../javascript/reference/html-tag-methods-javascript.md)|Umieszcza HTML \<czcionki > tag z atrybutem rozmiar wokół tekstu.|  
|[hasOwnProperty — metoda](../../javascript/reference/hasownproperty-method-object-javascript.md)|Zwraca wartość logiczną, która wskazuje, czy obiekt ma właściwość o określonej nazwie.|  
|[indexOf — metoda (ciąg)](../../javascript/reference/indexof-method-string-javascript.md)|Zwraca pozycję znaku, w której podciąg po raz pierwszy występuje wewnątrz ciągu.|  
|[isPrototypeOf — metoda](../../javascript/reference/isprototypeof-method-object-javascript.md)|Zwraca wartość logiczną, która wskazuje, czy obiekt istnieje w łańcuchu prototypów innego obiektu.|  
|[italics — metoda](../../javascript/reference/html-tag-methods-javascript.md)|Umieszcza HTML \<I > tagi wokół tekstu.|  
|[lastIndexOf — metoda (ciąg)](../../javascript/reference/lastindexof-method-string-javascript.md)|Zwraca ostatnie wystąpienie podciągu wewnątrz ciągu.|  
|[Link — metoda](../../javascript/reference/html-tag-methods-javascript.md)|Umieszcza wokół tekstu kotwicę HTML, która zawiera atrybut HREF.|  
|[localeCompare — metoda](../../javascript/reference/localecompare-method-string-javascript.md)|Zwraca wartość, która wskazuje, czy dwa ciągi są równoważne przy bieżących ustawieniach regionalnych.|  
|[Match — metoda](../../javascript/reference/match-method-string-javascript.md)|Wyszukuje ciąg przy użyciu dostarczonego **wyrażenia regularnego** obiektu i zwraca wynik w postaci tablicy.|  
|[Normalizuj — metoda](../../javascript/reference/normalize-method-string-javascript.md)|Zwraca forma normalizacji Unicode określonego ciągu.|  
|[propertyIsEnumerable — metoda](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Zwraca wartość logiczną, która wskazuje, czy określona właściwość jest częścią obiektu i czy jest wyliczalna.|  
|[REPEAT — metoda](../../javascript/reference/repeat-method-string-javascript.md)|Zwraca obiekt ciągu o wartości równej oryginalnego ciągu powtórzone określoną liczbę razy.|  
|[replace — metoda](../../javascript/reference/replace-method-string-javascript.md)|Korzysta z wyrażenia regularnego, aby zamienić tekst w ciągu i zwraca wynik.|  
|[Search — metoda](../../javascript/reference/search-method-string-javascript.md)|Zwraca pozycję pierwszego dopasowania podciągu w przypadku wyszukiwania wyrażeń regularnych.|  
|[Metoda slice (ciąg)](../../javascript/reference/slice-method-string-javascript.md)|Zwraca część ciągu.|  
|[Small — metoda](../../javascript/reference/html-tag-methods-javascript.md)|Umieszcza HTML \<małych > tagi wokół tekstu.|  
|[split — metoda](../../javascript/reference/split-method-string-javascript.md)|Zwraca tablicę ciągów, która powstaje, gdy ciąg zostaje podzielony na podciągi.|  
|[startsWith — metoda](../../javascript/reference/startswith-method-string-javascript.md)|Zwraca wartość logiczną, wskazującą, czy ciąg lub podciąg rozpoczyna się od ciągu przekazana.|  
|[znalezienia — metoda](../../javascript/reference/html-tag-methods-javascript.md)|Umieszcza HTML \<ZNALEZIENIA > tagi wokół tekstu.|  
|[Sub — metoda](../../javascript/reference/html-tag-methods-javascript.md)|Umieszcza HTML \<SUB > tagi wokół tekstu.|  
|[substr — metoda](../../javascript/reference/substr-method-string-javascript.md)|Zwraca podciąg rozpoczynający się w podanym miejscu i o określonej długości.|  
|[substring — metoda](../../javascript/reference/substring-method-string-javascript.md)|Zwraca podciąg w określonej lokalizacji w ramach `String` obiektu.|  
|[sup — metoda](../../javascript/reference/html-tag-methods-javascript.md)|Umieszcza HTML \<SUP > tagi wokół tekstu.|  
|[toLocaleLowerCase — metoda](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|Zwraca ciąg, w którym wszystkie znaki alfabetyczne są konwertowane na małe litery z uwzględnieniem bieżących ustawień regionalnych środowiska hosta.|  
|[toLocaleString — metoda](../../javascript/reference/tolocalestring-method-object-javascript.md)|Zwraca obiekt przekonwertowany na ciąg przy użyciu bieżących ustawień regionalnych.|  
|[toLocaleUpperCase — metoda](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|Zwraca ciąg, w którym wszystkie znaki alfabetyczne są konwertowane na wielkie litery z uwzględnieniem bieżących ustawień regionalnych środowiska hosta.|  
|[toLowerCase — metoda](../../javascript/reference/tolowercase-method-javascript.md)|Zwraca ciąg, w którym wszystkie znaki alfabetyczne są konwertowane na małe litery.|  
|[toString — metoda](../../javascript/reference/tostring-method-string-1.md)|Zwraca ciąg.|  
|[toUpperCase — metoda](../../javascript/reference/touppercase-method-string-javascript.md)|Zwraca ciąg, w którym wszystkie znaki alfabetyczne są konwertowane na wielkie litery.|  
|[TRIM — metoda](../../javascript/reference/trim-method-string-javascript.md)|Zwraca ciąg z usuniętymi początkowymi i końcowymi białymi znakami oraz znakami zakończenia wiersza.|  
|[valueOf — metoda](../../javascript/reference/valueof-method-string.md)|Zwraca ciąg.|  
  
## <a name="see-also"></a>Zobacz też  
 [New — Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Przewijanie, przesuwać i powiększać przykładowej aplikacji](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)