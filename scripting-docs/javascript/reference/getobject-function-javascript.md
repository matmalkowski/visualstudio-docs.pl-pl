---
title: GetObject — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- GetObject
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetObject function
ms.assetid: 62efcdbc-8b86-491d-9000-ef38aa9942a9
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d8bad127a0f260395a1ec19f44ff2d495006024
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790747"
---
# <a name="getobject-function-javascript"></a>GetObject — Funkcja (JavaScript)
Zwraca odwołanie do obiektu automatyzacji z pliku.  
  
> [!NOTE]
>  Ta funkcja nie jest obsługiwana w programie Internet Explorer 9 (tryb standardów) lub nowszym.  
  
## <a name="syntax"></a>Składnia  
  
```  
GetObject([pathname] [, class])  
```  
  
## <a name="parameters"></a>Parametry  
 `pathname`  
 Opcjonalny. Pełna ścieżka i nazwa pliku zawierającego obiekt do pobrania. Jeśli `pathname` zostanie pominięty, `class` jest wymagana.  
  
 `class`  
 Opcjonalny. Klasa obiektu.  
  
 `class` Argument używa składni `appname.objectype` i zawiera następujące części:  
  
 `appname`  
 Wymagany. Nazwa aplikacji, zapewniając obiektu.  
  
 `objectype`  
 Wymagany. Typ lub klasa obiektu do utworzenia.  
  
## <a name="remarks"></a>Uwagi  
 `GetObject` Funkcja nie jest obsługiwana w [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] lub nowszej.  
  
 Użyj `GetObject` funkcji dostępu do obiektu automatyzacji z pliku. Przypisz obiekt zwrócony przez `GetObject` zmiennej obiektu. Na przykład:  
  
```JavaScript  
var CADObject;  
CADObject = GetObject("C:\\CAD\\SCHEMA.CAD");  
```  
  
 Po wykonaniu tego kodu, aplikację skojarzoną z określonym `pathname` została uruchomiona, i jest aktywny obiekt w określonym pliku. Jeśli `pathname` jest ciągiem o zerowej długości (""), `GetObject` zwraca nowe wystąpienie obiektu określonego typu. Jeśli `pathname` pominięcia argumentu `GetObject` zwraca aktualnie aktywny obiekt określonego typu. Jeśli nie istnieje żaden obiekt określonego typu, wystąpi błąd.  
  
 Niektóre aplikacje umożliwiają uaktywnienie części pliku. Aby to zrobić, Dodaj wykrzyknika (!) na końcu nazwy pliku i wykonaj go ciągiem, który identyfikuje części pliku, który chcesz aktywować. Aby uzyskać informacje dotyczące sposobu tworzenia tych parametrów zobacz dokumentację dla aplikacji, który utworzył obiekt.  
  
 Na przykład w aplikacji do rysowania może mieć wiele warstw do rysunku przechowywane w pliku. Można użyć poniższego kodu, aby aktywować warstwy w rysunku o nazwie `SCHEMA.CAD`:  
  
```JavaScript  
var LayerObject = GetObject("C:\\CAD\\SCHEMA.CAD!Layer3");  
```  
  
 Jeśli nie określisz klasy obiektu, automatyzacji określa aplikację można uruchomić i który obiekt, aby aktywować, na podstawie nazwy pliku, podane przez użytkownika. Niektóre pliki, jednak może obsługiwać więcej niż jedną klasę obiektu. Przykładowo, rysunek może obsługiwać trzy różne typy obiektów: obiekt aplikacji, obiekt rysowania i obiekt paska narzędzi, które są częścią tego samego pliku. Aby określić, w pliku obiektu, który chcesz aktywować, Użyj opcjonalnego `class` argumentu. Na przykład:  
  
```JavaScript  
var MyObject;  
MyObject = GetObject("C:\\DRAWINGS\\SAMPLE.DRW", "FIGMENT.DRAWING");  
```  
  
 W powyższym przykładzie `FIGMENT` jest nazwą aplikacji do rysowania i `DRAWING` jest jednym z obsługiwanych typów obiektów. Po uaktywnieniu obiektu odwołania w kodzie za pomocą zmienna obiektu, który został zdefiniowany. W powyższym przykładzie uzyskujesz dostęp właściwości i metody dla nowego obiektu przy użyciu zmiennej obiektu `MyObject`. Na przykład:  
  
```JavaScript  
MyObject.Line(9, 90);  
MyObject.InsertText(9, 100, "Hello, world.");  
MyObject.SaveAs("C:\\DRAWINGS\\SAMPLE.DRW");  
```  
  
> [!NOTE]
>  Użyj `GetObject` działać, jeśli istnieje bieżącego wystąpienia obiektu lub jeśli chcesz utworzyć obiekt z plikiem już załadowany. Jeśli istnieje nie bieżącego wystąpienia, a nie chcesz, aby uruchomić obiektu załadowany plik, użyj `ActiveXObject` obiektu.  
  
 Jeśli obiekt zarejestrował się jako obiekt jednego wystąpienia, tylko jedno wystąpienie obiektu jest tworzony, niezależnie od tego, jak często `ActiveXObject` jest wykonywana. W przypadku obiektu jednego wystąpienia `GetObject` zawsze zwraca to samo wystąpienie wywołanego z ciągiem o zerowej długości ("") składni i powoduje błąd, jeśli `pathname` zostanie pominięty argument.  
  
## <a name="requirements"></a>Wymagania  
 Obsługiwane w następujących trybach dokumentu: Osobliwości, Standardy programu Internet Explorer 6, Standardy programu Internet Explorer 7 i standardy programu Internet Explorer 8. Zobacz [Informacje o wersji](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Activexobject — obiekt](../../javascript/reference/activexobject-object-javascript.md)