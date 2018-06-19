---
title: Rozwiązywanie problemów w skryptach (JavaScript) | Dokumentacja firmy Microsoft
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
helpviewer_keywords:
- automative type conversion
- troubleshooting scripts
ms.assetid: 0e0545d9-44e5-4179-befc-99a882c5c672
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e0193e6dc0996d5e2d0d3df7103c7705d29477
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24789064"
---
# <a name="troubleshooting-your-scripts-javascript"></a>Rozwiązywanie problemów w skryptach (JavaScript)
Brak miejsca w dowolnym języku programowania, które mają niespodzianki. Na przykład `null` wartość w [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] nie działają tak samo, jak `Null` wartość w językach C lub C++.  
  
 Oto kilka obszarów problemów, które mogą napotkać podczas pisania [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skryptów.  
  
## <a name="syntax-errors"></a>Błędy składniowe  
 Należy zwrócić uwagę na szczegółów podczas pisania skryptów. Na przykład ciągi musi być ujęta w cudzysłów.  
  
## <a name="order-of-script-interpretation"></a>Kolejność interpretacji skryptu  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]interpretacja wchodzi w skład proces analizowania HTML przeglądarki sieci Web. Jeśli umieścisz skryptu wewnątrz \<HEAD > znacznik w dokumencie, jest interpretowany przed dowolną część \<treści > tag. Jeśli masz obiektów, które są tworzone w \<treści > tag, nie istnieją w czasie \<HEAD > są analizowane i nie może być modyfikowany w zakresie przez skrypt.  
  
> [!NOTE]
>  Ten problem dotyczy programu Internet Explorer. ASP i WSH ma wykonywania różnych modeli (tak jak innych hostów).  
  
## <a name="automatic-type-coercion"></a>Koercja typu automatyczne  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]to język typowaniem luźnym z automatycznego wymuszenia. Mimo że o różnych typów wartości nie są takie same, obliczać wyrażeń w poniższym przykładzie **true**.  
  
```JavaScript  
"100" == 100;  
false == 0;  
```  
  
 Aby sprawdzić, czy typu i wartości są takie same, użyj operatora strict równości (=). Następujące zarówno oceny false:  
  
```JavaScript  
"100" === 100;  
false === 0;  
```  
  
## <a name="operator-precedence"></a>Kolejność wykonywania działań  
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md) Określa, kiedy jest wykonywane podczas obliczania wyrażenia. W poniższym przykładzie jest wykonywane przed odejmowania, mnożenia, mimo że odejmowania występuje jako pierwszy w wyrażeniu.  
  
```JavaScript  
theRadius = aPerimeterPoint - theCenterpoint * theCorrectionFactor;  
```  
  
## <a name="using-forin-loops-with-objects"></a>Przy użyciu for... w pętli z obiektami  
 Gdy iterację właściwości obiektu z [for... w](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) pętli, nie można przewidzieć lub kontrolować kolejność, w którym pola obiektu są przypisywane do zmiennej licznika pętli. Ponadto kolejność mogą być różne w różnych implementacji języka.  
  
## <a name="with-keyword"></a>with — słowo kluczowe  
 [z](../../javascript/reference/with-statement-javascript.md) instrukcja jest wygodną metodą uzyskiwania dostępu do właściwości, które już istnieją w określonym obiekcie, ale nie można użyć w celu dodania właściwości do obiektu. Aby utworzyć nowe właściwości w obiekcie, użytkownik musi odwoływać się do obiektu w szczególności.  
  
## <a name="this-keyword"></a>to słowo kluczowe  
 Mimo że używasz `this` — słowo kluczowe w definicji obiektu do odwoływania się do samego obiektu, nie można użyć `this` lub podobne słowa kluczowe do odwoływania się do aktualnie wykonywanych działać, jeśli funkcja nie jest częścią definicji obiektu. Jeśli funkcja można przypisać do obiektu jako metody, można użyć `this` — słowo kluczowe w funkcji do odwoływania się do obiektu.  
  
## <a name="writing-a-script-that-writes-a-script-in-internet-explorer"></a>Napisanie skryptu, który zapisuje skrypt w programie Internet Explorer  
 \< /SCRIPT > tag kończy bieżący skrypt, jeśli interpretera napotkał go. Aby wyświetlić "\</SCRIPT >", przepisywania to jako co najmniej dwa ciągi, na przykład "\</SCR" i "IPT >", który można następnie połączyć ze sobą w instrukcji, który dokonuje zapisu.  
  
## <a name="implicit-window-references-in-internet-explorer"></a>Okno niejawne odwołania w programie Internet Explorer  
 Ponieważ więcej niż jedno okno może być otwarty naraz, każde odwołanie niejawne okna wskazuje bieżącego okna. Dla innych oknach należy użyć jawnego odwołania.