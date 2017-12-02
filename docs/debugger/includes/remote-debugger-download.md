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
ms.openlocfilehash: 109d9d8718a2c46dbd982e58b22dcf43e55b2205
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2017
---
1.  Na urządzeniu lub serwera komputera, na którym chcesz debugować (zamiast komputerze z programem Visual Studio) Pobierz poprawną wersję narzędzi remote Tools.

    |Wersja|Łącze|Uwagi|
    |-|-|-|
    |Visual Studio 2017 Update 4|[Zdalne narzędzia](https://www.visualstudio.com/downloads/#remote-tools-for-visual-studio-2017)|Zawsze pobierana wersja dopasowania system operacyjny urządzenia (x86 lub x64). Dla starszych przeglądarek, użyj następujących linków bezpośrednich: [narzędzia zdalnej (x64)](https://go.microsoft.com/fwlink/?LinkId=746570&clcid=0x409) i [narzędzia zdalnej (x86)](https://go.microsoft.com/fwlink/?LinkId=746569&clcid=0x409).|
    |Visual Studio 2017 (starsze)|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Jeśli zostanie wyświetlony monit, dołączenie do wolnego grupy programu Visual Studio Dev Essentials lub można zalogować się przy użyciu prawidłowej subskrypcji programu Visual Studio. Dla starszych przeglądarek należy dodać nowy zaufanych witryn, jeśli zostanie wyświetlony monit.|
    |Visual Studio 2015 Update 3|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Jeśli zostanie wyświetlony monit, dołączenie do wolnego grupy programu Visual Studio Dev Essentials lub można zalogować się przy użyciu prawidłowej subskrypcji programu Visual Studio. Dla starszych przeglądarek należy dodać nowy zaufanych witryn, jeśli zostanie wyświetlony monit.|
    |Visual Studio 2015 (starsze)|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Jeśli zostanie wyświetlony monit, dołączenie do wolnego grupy programu Visual Studio Dev Essentials lub można zalogować się przy użyciu prawidłowej subskrypcji programu Visual Studio. Dla starszych przeglądarek należy dodać nowy zaufanych witryn, jeśli zostanie wyświetlony monit.|
    |Visual Studio 2013|[Zdalne narzędzia](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Pobierz strony w dokumentacji programu Visual Studio 2013|
    |Visual Studio 2012|[Zdalne narzędzia](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Pobierz strony w dokumentacji programu Visual Studio 2012|
  
2.  Na stronie pobierania wybierz wersję narzędzia zgodny system operacyjny (x 86, x64 lub ARM) i Pobierz narzędzia zdalnej.
  
    > [!IMPORTANT]
    >  Zaleca się zainstalować najnowszą wersję narzędzi remote tools odpowiadający posiadanej wersji programu Visual Studio. Niezgodne wersje nie są zalecane. Ponadto należy zainstalować narzędzia zdalnego, które mają taką samą architekturę co system operacyjny, na którym chcesz go zainstalować. Innymi słowy Jeśli chcesz debugować 32-bitowej aplikacji na komputerze zdalnym z systemem 64-bitowym systemie operacyjnym, należy zainstalować 64-bitowa wersja narzędzi remote Tools na komputerze zdalnym. 
    >   
    >  Powierzchnia 3 przełączony z ARM x64 architektury. ARM wersję narzędzi remote Tools nie jest dostępna dla programu Visual Studio 2017 r. Dla programu Visual Studio 2015 należy odnaleźć wersji ARM w Visual Studio 2015 RTW pobierania.
  
3.  Po zakończeniu pobierania pliku wykonywalnego, przejdź do następnej sekcji, a następnie postępuj zgodnie z instrukcjami instalacji.

Spróbuj skopiować zdalnego debugera (msvsmon.exe) z komputerem zdalnym i uruchom go, należy pamiętać, że **Kreatora konfiguracji zdalnego debugera** (**rdbgwiz.exe**) jest zainstalowany tylko wtedy, gdy można pobrać narzędzia. Konieczne może być Użyj kreatora do konfiguracji później, zwłaszcza, jeśli chcesz, aby zdalny debuger do uruchamiania jako usługa. Aby uzyskać więcej informacji, zobacz [(opcjonalnie) Konfigurowanie zdalnego debugera jako usługi](../../debugger/remote-debugging.md#bkmk_configureService).