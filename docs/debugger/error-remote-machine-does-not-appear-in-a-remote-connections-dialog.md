---
title: "Błąd: Maszyna zdalna nie są wyświetlane w oknie dialogowym zdalne połączenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 72a891219b24f1cb80ec9e65988f57ebfb04fcd6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Błąd: Maszyna zdalna nie są wyświetlane w oknie dialogowym połączenia zdalne
Jeśli komputer zdalny nie ma w oknie dialogowym zdalne połączenia, sprawdź następujące typowe przyczyny.  
  
 Jeśli korzystasz z zarządzanego trybu zgodności, sprawdź w dokumentacji programu Visual Studio 2010: [Rozwiązywanie problemów z zdalnego debugowania — Visual Studio 2010](https://msdn.microsoft.com/en-us/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Typowe przyczyny tego błędu  
  
-   Komputer zdalny jest uruchomiona na komputerze, na którym znajduje się w innej podsieci. Aby rozwiązać ten problem, ręcznie wpisać nazwę lub adres IP w oknie dialogowym kwalifikatora  
  
-   Debuger zdalny nie jest uruchomiona na komputerze zdalnym. Aby rozwiązać ten problem, uruchom zdalny debuger.  
  
-   Zapora blokuje komunikację między Visual Studio i komputer zdalny. Aby rozwiązać ten problem, Skonfiguruj zaporę, aby umożliwić Visual Studio i zdalnego debugera (polecenie msvsmon) do komunikacji.  
  
-   Oprogramowanie antywirusowe blokuje komunikację między Visual Studio i komputer zdalny. Aby rozwiązać ten problem, należy skonfigurować oprogramowanie antywirusowe, aby umożliwić Visual Studio i zdalnego debugera (polecenie msvsmon) do komunikowania się.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)