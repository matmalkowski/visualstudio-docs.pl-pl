---
title: "Przy użyciu środowiska uruchomieniowego systemu Windows w języku JavaScript | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c81f5d83056ceb87987e263f09c0d5e5017dbb6f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="using-the-windows-runtime-in-javascript"></a>W języku JavaScript za pomocą środowiska wykonawczego systemu Windows
Podczas pisania aplikacji systemu Windows platformy Uniwersalnej środowiska wykonawczego systemu Windows klas, metod i właściwości można użyć w podobnie jak że użyje natywny obiektów JavaScript, metod i właściwości. Ten temat zawiera informacje wprowadzające i linki do tematów dotyczących podstawowych koncepcji przy użyciu interfejsów API środowiska wykonawczego systemu Windows w języku JavaScript, w tym wyjaśnienie sposobu typów środowiska wykonawczego systemu Windows są reprezentowane, jak używać metod asynchronicznych środowiska wykonawczego systemu Windows, i jak do nasłuchiwania i obsługi zdarzeń środowiska wykonawczego systemu Windows.  
  
 Możesz znaleźć dokumentację referencyjną JavaScript w [dokumentację języka JavaScript](../javascript/javascript-language-reference.md).  
  
> [!IMPORTANT]
>  Funkcje środowiska wykonawczego systemu Windows nie są dostępne dla aplikacji, które są uruchamiane w programie Internet Explorer.  
  
## <a name="windows-runtime-reference-documentation"></a>Dokumentacja odwołania do środowiska wykonawczego systemu Windows  
 Dokumentację referencyjną dla [odwołania do środowiska wykonawczego systemu Windows](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx). Przykłady kodu są dostępne w języku JavaScript, a także w języku C++, C# i Visual Basic.  
  
## <a name="writing-windows-runtime-components-in-c-c-or-visual-basic"></a>Pisanie składników środowiska wykonawczego systemu Windows w języku C++, C# lub Visual Basic  
 Aby uzyskać instrukcje i wytyczne dotyczące pisania składników środowiska wykonawczego systemu Windows, które mogą być używane w języku JavaScript, zobacz [tworzenia składników środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp) i [tworzenia składników środowiska wykonawczego systemu Windows w języku C# i Visual Podstawowe](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
## <a name="casing-conventions-with-windows-runtime-features"></a>Konwencje wielkości liter z funkcji środowiska uruchomieniowego systemu Windows  
 Konwencje wielkości liter dla funkcji środowiska uruchomieniowego systemu Windows w języku JavaScript różnić się nieznacznie od tych dla innych języków:  
  
-   Obszary nazw i klasy znajdują się w przypadku Pascal:  
  
    ```JavaScript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   W camelcase są członkami klas, metod i właściwości oraz elementy członkowskie struktury i wyliczenia, w tym:  
  
    ```JavaScript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   Nazwy zdarzenia są liter:  
  
    ```JavaScript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi dotyczące korzystania z interfejsu API środowiska wykonawczego systemu Windows](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [Używanie metod asynchronicznych środowiska wykonawczego systemu Windows](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [Obsługa zdarzeń środowiska wykonawczego systemu Windows w języku JavaScript](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [Reprezentacja JavaScript typów środowiska wykonawczego systemu Windows](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [Rzutowanie JavaScript DateTime środowiska wykonawczego systemu Windows i przedziału czasu](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)