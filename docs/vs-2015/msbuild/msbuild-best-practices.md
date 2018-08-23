---
title: MSBuild — najlepsze praktyki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df388b4b5aeac30e5ee83e24dc08905507318f18
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42693977"
---
# <a name="msbuild-best-practices"></a>Najlepsze praktyki w programie MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [najlepszych rozwiązań MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-best-practices).  
  
  
Zalecamy następujące najlepsze rozwiązania dotyczące pisania skryptów programu MSBuild:  
  
-   Domyślne wartości właściwości najlepiej są obsługiwane przy użyciu `Condition` atrybutu, a nie przez zadeklarowanie właściwość, której domyślna wartość może zostać przesłonięta w wierszu polecenia. Na przykład użyć  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   Po zaznaczeniu elementów, należy unikać symboli wieloznacznych. Zamiast tego należy jawnie określić pliki. Ta funkcja ułatwia śledzenie błędów, które mogą wystąpić podczas dodawania i usuwania plików.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)



