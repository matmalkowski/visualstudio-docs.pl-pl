---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 95d76781f651b681b81e4dd18848b404d8a85664
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
 Można debugować kodu za pomocą symboli, które można wygenerować na komputerze programu Visual Studio. Wydajność zdalnego debugera jest znacznie lepiej, jeśli używasz symbole lokalne.  Należy użyć zdalnego symbole, należy najpierw sprawdzić monitor debugera zdalnego do wyszukiwania symboli na komputerze zdalnym.  
  
 Począwszy od programu Visual Studio 2013 Update 2, umożliwia przełącznik wiersza polecenia następujące polecenie msvsmon za pomocą zdalnego symboli dla kodu zarządzanego:`Msvsmon /FallbackLoadRemoteManagedPdbs`  
  
 Aby uzyskać więcej informacji, zobacz Pomoc zdalnego debugowania (naciśnij klawisz **F1** w oknie zdalnego debugera, lub kliknij przycisk **Pomoc > użycia**). Więcej informacji można znaleźć [.NET zdalnego Symbol ładowania zmiany w programie Visual Studio 2012 i 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)