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
ms.openlocfilehash: 7e911686d1f8bff191c439f4fc2b92c37d60a31f
ms.sourcegitcommit: 38097344f3ff74ba7b03bcfa45910015ca6bc2be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2017
---
1.  Na urządzeniu lub serwera komputera, na którym chcesz debugować (zamiast komputerze z programem Visual Studio) Pobierz poprawną wersję narzędzi remote Tools.

    |Wersja|Łącze|Uwagi|
    |-|-|-|
    |Visual Studio 2017 wersji 15,5 cala|[Zdalne narzędzia](https://www.visualstudio.com/downloads/#remote-tools-for-visual-studio-2017)|Zawsze pobierana wersja dopasowania system operacyjny urządzenia (x86 lub x64). Jeśli jest włączony tryb zwiększone zabezpieczenia (Windows Server), należy dodać nowy zaufanych witryn w przypadku wyświetlenia monitu.|
    |Visual Studio 2017 (starsze)|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Zdalne narzędzia dla wcześniejszych wersji programu Visual Studio 2017 r są dostępne z My.VisualStudio.com. Jeśli zostanie wyświetlony monit, sprzężenia wolnego grupy programu Visual Studio Dev Essentials lub zaloguj się przy użyciu subskrypcji programu Visual Studio identyfikator. Jeśli jest włączony tryb zwiększone zabezpieczenia (Windows Server), należy dodać nowy zaufanych witryn w przypadku wyświetlenia monitu.|
    |Visual Studio 2015 Update 3|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Jeśli zostanie wyświetlony monit, sprzężenia wolnego grupy programu Visual Studio Dev Essentials lub zaloguj się przy użyciu subskrypcji programu Visual Studio identyfikator. Jeśli jest włączony tryb zwiększone zabezpieczenia (Windows Server), należy dodać nowy zaufanych witryn w przypadku wyświetlenia monitu.|
    |Visual Studio 2015 (starsze)|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Jeśli zostanie wyświetlony monit, sprzężenia wolnego grupy programu Visual Studio Dev Essentials lub zaloguj się przy użyciu subskrypcji programu Visual Studio identyfikator. Jeśli jest włączony tryb zwiększone zabezpieczenia (Windows Server), należy dodać nowy zaufanych witryn w przypadku wyświetlenia monitu.|
    |Visual Studio 2013|[Zdalne narzędzia](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Pobierz strony w dokumentacji programu Visual Studio 2013|
    |Visual Studio 2012|[Zdalne narzędzia](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Pobierz strony w dokumentacji programu Visual Studio 2012|
  
2.  Na stronie pobierania wybierz wersję narzędzia zgodny system operacyjny (x 86, x64 lub ARM) i Pobierz narzędzia zdalnej.
  
    > [!IMPORTANT]
    >  Zaleca się zainstalować najnowszą wersję narzędzi remote tools odpowiadający posiadanej wersji programu Visual Studio. Niezgodne wersje nie są zalecane. Ponadto należy zainstalować narzędzia zdalnego, które mają taką samą architekturę co system operacyjny, na którym chcesz go zainstalować. Innymi słowy Jeśli chcesz debugować 32-bitowej aplikacji na komputerze zdalnym z systemem 64-bitowym systemie operacyjnym, należy zainstalować 64-bitowa wersja narzędzi remote Tools na komputerze zdalnym. 
    >   
    >  Powierzchnia 3 przełączony z ARM x64 architektury. ARM wersję narzędzi remote Tools nie jest dostępna dla programu Visual Studio 2017 r. Dla programu Visual Studio 2015 należy odnaleźć wersji ARM w Visual Studio 2015 RTW pobierania.
  
3.  Po zakończeniu pobierania pliku wykonywalnego, przejdź do następnej sekcji, a następnie postępuj zgodnie z instrukcjami instalacji.

Spróbuj skopiować zdalnego debugera (msvsmon.exe) z komputerem zdalnym i uruchom go, należy pamiętać, że **Kreatora konfiguracji zdalnego debugera** (**rdbgwiz.exe**) jest zainstalowany tylko wtedy, gdy można pobrać narzędzia. Konieczne może być Użyj kreatora do konfiguracji później, zwłaszcza, jeśli chcesz, aby zdalny debuger do uruchamiania jako usługa. Aby uzyskać więcej informacji, zobacz [(opcjonalnie) Konfigurowanie zdalnego debugera jako usługi](../../debugger/remote-debugging.md#bkmk_configureService).