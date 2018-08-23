---
title: Okno dialogowe rozstrzyganie niejednoznaczności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.Disambig
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 899531ab2345982d57143647710ef83435465589
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682261"
---
# <a name="resolve-ambiguity-dialog-box"></a>Rozwiązywania niejednoznaczności — Okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [rozwiązywania niejednoznaczności okno dialogowe](https://docs.microsoft.com/visualstudio/debugger/resolve-ambiguity-dialog-box).  
  
`Resolve Ambiguity` Pojawi się okno dialogowe, gdy debuger nie można wybrać lokalizację, aby wyświetlić. Na przykład jeśli używasz szablonów języka C++, można utworzyć wiele funkcji z pojedynczego szablonu funkcji. Jeśli debuger zatrzymuje się w lokalizacji źródłowej, w szablonie, a Ty podejmiesz `Go To Disassembly`, debuger ma wiele opcji. Każda funkcja tworzone na podstawie szablonu ma swój własny kod dezasemblacji i debuger nie wie, kod, który chcesz wyświetlić. `Resolve Ambiguity` Okno dialogowe pozwala wybrać lokalizację z listy wszystkich odpowiedniej lokalizacji.  
  
 `Choose the specific location`  
 Wyświetla listę wszystkich lokalizacji odpowiadającego do swojej dyspozycji.  
  
 `Address`  
 Pokazuje adresów pamięci dla każdej funkcji.  
  
 `Function`  
 Zawiera nazwę każdej funkcji.  
  
 `Module`  
 Zawiera moduł (plik EXE lub DLL) zawierająca kod obiektowy dla tej funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md)



