---
title: "Debuger — instrukcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- debugger_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- debugger statement
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e64e860cebd065f357857484e932b4aea3f05ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="debugger-statement-javascript"></a>debugger — Instrukcja (JavaScript)
Wstrzymuje wykonywanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
debugger  
```  
  
## <a name="remarks"></a>Uwagi  
 Możesz umieścić `debugger` instrukcje w dowolnym miejscu procedury, aby wstrzymać wykonywania. Przy użyciu `debugger` instrukcji jest podobne do punktu przerwania w kodzie.  
  
 `debugger` Instrukcji wstrzymuje wykonywanie, ale nie Zamknij wszystkie pliki lub wyczyść żadnych zmiennych.  
  
> [!NOTE]
>  `debugger` Instrukcji nie obowiązuje, chyba że skrypt jest debugowany.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `debugger` instrukcji, aby wstrzymać wykonywania dla każdej iteracji za pośrednictwem `for` pętli.  
  
> [!NOTE]
>  Do uruchomienia tego przykładu, muszą mieć zainstalowany debugera skryptów i skrypt musi działać w trybie debugowania.  
>   
>  Program Internet Explorer 8 zawiera [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] debugera. Jeśli używasz starszej wersji programu Internet Explorer, zobacz [porady: Włączanie i Rozpocznij debugowanie skryptu z programu Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```JavaScript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje JavaScript](../../javascript/reference/javascript-statements.md)   
 [Kompilacja warunkowa](../../javascript/advanced/conditional-compilation-javascript.md)