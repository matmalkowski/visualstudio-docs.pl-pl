---
title: 'Błąd: Maszyna zdalna nie są wyświetlane w oknie dialogowym zdalne połączenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c52a2ebd99b052171220fd8a06f1ae7ff5dc258e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471336"
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