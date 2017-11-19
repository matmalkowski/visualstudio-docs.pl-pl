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
ms.openlocfilehash: 05a288a2d8dff776d8a5d3faea47b06d101f2ea3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
Musi mieć uprawnienia administracyjne na komputerze zdalnym.  
  
1.  Znajdź aplikację zdalny debuger. (Znajdź msvsmon.exe w lokalizacji, w którym został zainstalowany lub Otwórz Start menu i wyszukaj **zdalnego debugera**.)
  
     Jeśli używasz zdalnego debugera na serwerze zdalnym, można kliknąć prawym przyciskiem myszy aplikację zdalny debuger i wybrać **Uruchom jako administrator**. Jeśli nie używasz go na serwerze zdalnym, wystarczy ją uruchomić normalnie.
  
3.  Po uruchomieniu narzędzia zdalnej po raz pierwszy (lub przed został skonfigurowany), **konfiguracji zdalnego debugowania** zostanie wyświetlone okno dialogowe.  
  
     ![RemoteDebuggerConfWizardPage](../media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
4.  Jeśli interfejs API usługi systemu Windows nie jest zainstalowany (co się stanie, tylko w systemie Windows Server 2008 R2), wybierz **zainstalować** przycisku.  
  
5.  Wybierz typy sieci chcesz użyć narzędzia zdalnej na. Należy wybrać co najmniej jeden typ sieci. Jeśli komputery są połączone za pośrednictwem domeny, musisz wybrać pierwszego elementu. Jeśli komputery są połączone za pośrednictwem grupy domowej i grupy roboczej, należy wybrać element drugiego i trzeciego zależnie od potrzeb.  
  
6.  Wybierz **skonfigurować debugowania zdalnego** skonfigurować zapory i uruchomić narzędzie.  
  
7.  Po zakończeniu konfiguracji, zostanie wyświetlone okno zdalnego debugera.
  
     ![RemoteDebuggerWindow](../media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
     Zdalny debuger jest teraz oczekiwania na połączenie. Zanotuj nazwę serwera i portu numer, który jest wyświetlany, ponieważ musi on być zgodny konfiguracji, które później użyć programu Visual Studio.  
  
 Po zakończeniu debugowania i należy zatrzymać debuger zdalny kliknij **Plik > Zakończ** okna. Możesz uruchomić go ponownie z **Start** menu lub z wiersza polecenia:  
  
 **\<Katalog instalacyjny usługi Visual Studio > \Common7\IDE\Remote debugera\\< x86, x64 lub Appx\msvsmon.exe**.  