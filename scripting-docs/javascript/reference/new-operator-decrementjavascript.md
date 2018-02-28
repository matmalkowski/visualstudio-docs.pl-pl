---
title: "New — Operator (JavaScript) | Dokumentacja firmy Microsoft"
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
- new_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- new operator in JavaScript
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ad004abb534d69bed1a1bd9bbd2ae96755544b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="new-operator-javascript"></a>new — Operator (JavaScript)
Tworzy nowy obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```  
new constructor ([arguments])   
```  
  
## <a name="parameters"></a>Parametry  
 `constructor`  
 Wymagany. Konstruktor obiektu. Nawiasy można pominąć, jeśli nie przyjmuje żadnych argumentów konstruktora.  
  
 `arguments`  
 Opcjonalny. Argumenty do przekazania do konstruktora nowego obiektu.  
  
## <a name="remarks"></a>Uwagi  
 `new` Operator wykonuje następujące zadania:  
  
-   Tworzy obiekt bez członków.  
  
-   Wywołuje konstruktor dla tego obiektu, przekazywanie wskaźnik do nowo utworzony obiekt jako `this` wskaźnika.  
  
-   Konstruktor następnie inicjuje obiekt zgodnie z argumentami przekazany do konstruktora.  
  
 Przykłady prawidłowego użycia **nowe** operatora.  
  
```JavaScript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Function — instrukcja](../../javascript/reference/function-statement-javascript.md)