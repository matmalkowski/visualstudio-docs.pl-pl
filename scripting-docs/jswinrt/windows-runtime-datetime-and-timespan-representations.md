---
title: "DateTime środowiska wykonawczego systemu Windows i reprezentacje TimeSpan | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime dates and times
- TimeSpan [JavaScript]
- DateTime [JavaScript]
ms.assetid: 9743e9ac-9054-463e-8264-427183e4905f
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d7c394b57eb0215e3dff857d935b367e602c2b0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="windows-runtime-datetime-and-timespan-representations"></a>Data i godzina środowiska wykonawczego systemu Windows i reprezentacje TimeSpan
Reprezentacja JavaScript daty i godziny jest inna niż wersja środowiska wykonawczego systemu Windows. Środowiska uruchomieniowego systemu Windows [DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx) struktura jest reprezentowana w języku JavaScript jako [data](../javascript/reference/date-object-javascript.md) mający magazynu zapasowego, który odpowiada `DateTime` danych (i ma inny zakres i dokładność z poziomu języka JavaScript `Date`). Zmodyfikowanie ten niestandardowy `Date` obiektu, staje się standardowego języka JavaScript `Date` i powoduje utratę precyzji. JavaScript `Date` wartości mogą zostać przekazane do środowiska wykonawczego systemu Windows `DateTime` i będzie zakresu po zaznaczeniu tej opcji, co może spowodować organizowanie wyjątków.  
  
 Środowisko wykonawcze systemu Windows [TimeSpan](http://msdn.microsoft.com/en-us/c5defb66-819c-4796-85b5-07ed249a5d86) struktury jest konwertowana milisekund i zwracane jako numer JavaScript.  
  
## <a name="see-also"></a>Zobacz też  
 [W języku JavaScript za pomocą środowiska wykonawczego systemu Windows](../jswinrt/using-the-windows-runtime-in-javascript.md)