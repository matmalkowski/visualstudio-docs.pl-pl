---
title: Activexobject — obiekt (JavaScript) | Dokumentacja firmy Microsoft
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
- ActiveXObject
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ActiveXObject object
- Automation objects, ActiveXObject objects
ms.assetid: 9c7bed07-853f-48aa-92db-3131324746ec
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77bb743aeab563f7d7711e4caa9a0fcf0b45ff58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24789256"
---
# <a name="activexobject-object-javascript"></a>ActiveXObject — Obiekt (JavaScript)
Włącza i zwraca odwołanie do obiektu automatyzacji.  
  
 Ten obiekt jest używany tylko do tworzenia obiektów automatyzacji i nie ma elementów członkowskich.  
  
> [!WARNING]
>  Ten obiekt jest rozszerzeniem firmy Microsoft i jest obsługiwana w programie Internet Explorer, nie [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
newObj = new ActiveXObject(servername.typename[, location])  
```  
  
## <a name="parameters"></a>Parametry  
 `newObj`  
 Wymagany. Nazwa zmiennej, do którego `ActiveXObject` jest przypisany.  
  
 `servername`  
 Wymagany. Nazwa aplikacji dostarczającej obiekt.  
  
 `typename`  
 Wymagany. Typ lub klasa obiektu, który należy utworzyć.  
  
 `location`  
 Opcjonalny. Nazwa serwera sieciowego, na którym ma zostać utworzony obiekt.  
  
## <a name="remarks"></a>Uwagi  
 Serwery automatyzacji zapewniają co najmniej jeden typ obiektu. Na przykład aplikacja edytora tekstów może dostarczyć obiekt aplikacji, obiekt dokumentu i obiekt paska narzędzi.  
  
 Można zidentyfikować `servername.typename` wartości na komputerze hosta w `HKEY_CLASSES_ROOT` klucza rejestru. Poniżej przedstawiono kilka przykładów wartości, które można tam znaleźć, w zależności od tego, jakie programy są zainstalowane:  
  
-   Excel.Application  
  
-   Excel.Chart  
  
-   Scripting.FileSystemObject  
  
-   WScript.Shell  
  
-   Word.Document  
  
> [!IMPORTANT]
>  Obiekty ActiveX mogą spowodować problemy z zabezpieczeniami. Aby użyć `ActiveXObject`, może być konieczne dostosowanie ustawień zabezpieczeń strefy zabezpieczeń w programie Internet Explorer. Na przykład dla strefy Lokalny intranet zazwyczaj trzeba zmienić niestandardowe ustawienie na „Inicjowanie i wykonywanie skryptów formantów ActiveX niezaznaczonych jako bezpieczne do wykonywania”.  
  
 Aby zidentyfikować elementów członkowskich obiektu automatyzacji używanej w kodzie, może być konieczne korzystanie z przeglądarki obiektów COM, takie jak [przeglądarka obiektów OLE/COM](http://msdn.microsoft.com/library/d0kh9f4c.aspx), jeśli dokumentacji nie jest dostępna dla obiekt automatyzacji.  
  
 Aby utworzyć obiekt automatyzacji, przypisz nowe `ActiveXObject` zmiennej obiektu:  
  
```JavaScript  
var ExcelApp = new ActiveXObject("Excel.Application");  
var ExcelSheet = new ActiveXObject("Excel.Sheet");  
```  
  
 Ten kod uruchamia aplikację tworzącą obiekt (w tym przypadku arkusz programu Microsoft Excel). Gdy obiekt zostanie utworzony, można się do niego odwoływać w kodzie przy użyciu zdefiniowanej zmiennej obiektu. W poniższym przykładzie dostęp właściwości i metody dla nowego obiektu przy użyciu zmiennej obiektu `ExcelSheet` i innych obiektów programu Excel, w tym obiekcie aplikacji i kolekcji ActiveSheet.Cells.  
  
```JavaScript  
// Make Excel visible through the Application object.  
ExcelSheet.Application.Visible = true;  
// Place some text in the first cell of the sheet.  
ExcelSheet.ActiveSheet.Cells(1,1).Value = "This is column A, row 1";  
// Save the sheet.  
ExcelSheet.SaveAs("C:\\TEST.XLS");  
// Close Excel with the Quit method on the Application object.  
ExcelSheet.Application.Quit();  
```  
  
## <a name="requirements"></a>Wymagania  
 Obsługiwane w następujących trybach dokumentu: Osobliwości (Quirks), standardy programu Internet Explorer 6, standardy programu Internet Explorer 7, standardy programu Internet Explorer 8, standardy programu Internet Explorer 9, standardy programu Internet Explorer 10 i standardy programu Internet Explorer 11. Nieobsługiwane w [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji. Zobacz [Informacje o wersji](../../javascript/reference/javascript-version-information.md).  
  
> [!NOTE]
>  Tworzenie `ActiveXObject` na serwerze zdalnym nie jest obsługiwany w [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] lub nowszej.  
  
## <a name="see-also"></a>Zobacz też  
 [GetObject — funkcja](../../javascript/reference/getobject-function-javascript.md)   
 [Unikatowy uwierzytelnianie przy użyciu Magic HTML5/WCF przykładowej aplikacji](http://code.msdn.microsoft.com/Unique-Authentication-f32d2da0)