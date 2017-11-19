---
title: Konfigurowanie Zapory systemu Windows do zdalnego debugowania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9432c65ec6a481b23655fb2a92915a4a4365ed5e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>Konfigurowanie Zapory systemu Windows do zdalnego debugowania
W tym temacie opisano, jak skonfigurować zaporę tak, aby włączyć debugowanie zdalne na komputerach z następującymi systemami operacyjnymi:  
  
-   Windows 10  
  
-   Windows 8/8.1  
  
-   Windows 7   
  
-   Windows Server 2012 z dodatkiem R2  

-   Windows Server 2012
  
-   Windows Server 2008 z dodatkiem R2 
  
 Jeśli w sieci, na którym debugowania nie jest chroniony przez zaporę, ta konfiguracja jest konieczne. W przeciwnym razie zarówno komputera hostującego program Visual Studio i komputerem zdalnym, który ma być debugowana wymaga zmian w konfiguracji zapory.  
  
 **IPSec** Jeśli sieć wymaga tej komunikacji jest wykonywane przy użyciu protokołu IPSec, należy otworzyć porty dodatkowe na komputerze hosta programu Visual Studio i komputerem zdalnym.  
  
 **Serwer sieci Web** przypadku debugowania zdalnego serwera sieci Web, należy otworzyć port dodatkowy na komputerze zdalnym. (Dla usług IIS, port 80 musi być otwarty.)  
  
 Należy pamiętać, że oba komputery nie musi mieć ten sam system operacyjny. Na przykład na komputerze programu Visual Studio może działać systemu Windows 10 i komputer zdalny można uruchomić systemu Windows Server 2012 R2.      
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Porty na komputerze zdalnym, umożliwiających debugowanie zdalne  
  
|||||  
|-|-|-|-|  
|**Porty**|**Przychodzącego/wychodzącego**|**Protokół**|**Opis**|   
|4022|przychodzące|TCP|Dla wersji programu VS 2017 r. Numer portu jest zwiększany o 2 dla każdej wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Visual przypisania portów debugera zdalnego Studio](../debugger/remote-debugger-port-assignments.md).|  
|4023|przychodzące|TCP|Dla wersji programu VS 2017 r. Numer portu jest zwiększany o 2 dla każdej wersji programu Visual Studio. (Tylko używane do zdalnego debugowania procesu 32-bitowych z 64-bitowej wersji zdalnego debugera.) Aby uzyskać więcej informacji, zobacz [Visual przypisania portów debugera zdalnego Studio](../debugger/remote-debugger-port-assignments.md).| 
|3702|Wychodzące|UDP|(Opcjonalnie) Wymagany w przypadku odnajdywania zdalnego debugera.|    
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Jak skonfigurować porty w Zaporze systemu Windows  

Po zainstalowaniu programu Visual Studio lub zdalnego debugera oprogramowania spróbuje otworzyć porty. Jednak w niektórych scenariuszach (na przykład za pomocą zapory innej firmy), może być konieczne otwarcie portu ręcznie. Jeśli musisz potwierdzić, że porty są otwarte, zobacz [Rozwiązywanie problemów](#troubleshooting). Instrukcje dotyczące otwierania portu mogą się różnić w starszych wersjach systemu Windows.

Aby otworzyć port:
  
1. Otwórz **Start** menu, wyszukaj **Zapora systemu Windows z zabezpieczeniami zaawansowanymi**.

2. Następnie wybierz pozycję **reguły ruchu przychodzącego > Nowa reguła > portu**, a następnie kliknij przycisk **dalej**. (W przypadku reguł wychodzących, wybierz **reguły wychodzące** zamiast.)

3. Wybierz **TCP** lub **UDP**w oparciu o numer portu.

4. W obszarze **określone porty lokalne**, wprowadź numer portu, kliknij przycisk **dalej**.

5. Kliknij przycisk **zezwalały na połączenie** , a następnie kliknij przycisk **dalej**.

6. Wybierz co najmniej jeden typ sieci można włączyć dla portu, a następnie kliknij przycisk **dalej**.

    Wybrany typ musi zawierać sieci, do którego jest podłączony komputera zdalnego.
7. Dodaj nazwę (na przykład **polecenia msvsmon**, **IIS**, lub **narzędzia Web Deploy**) dla regułę i kliknij przycisk **Zakończ**.

    Powinna zostać wyświetlona nowej reguły na liście reguły ruchu przychodzącego lub wychodzącego reguły.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli problemy z podłączania do aplikacji z zdalny debuger może być konieczne Sprawdź, czy porty są otwarte.

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-visual-studio-computer"></a>Sprawdź, czy porty są otwarte w Zaporze systemu Windows na komputerze programu Visual Studio  
 Instrukcje dotyczące konfigurowania Zapory systemu Windows się nieco różnić w różnych systemach operacyjnych. Systemu Windows 8/8.1, Windows 10 i Windows Server 2012, słowo **aplikacji** jest używany; w systemie Windows 7 lub Windows Server 2008, słowo **program** jest używany;  W poniższych krokach używamy słowa **aplikacji**.  
  
1.  Otwórz stronę zapory systemu Windows. (W **Start** menu pole wyszukiwania, wpisz **zapory systemu Windows**).  
  
2.  Kliknij przycisk **Zezwalaj aplikacji lub funkcji przez zaporę systemu Windows**.  
  
3.  W **dozwolone aplikacje i funkcje** listy, wyszukiwanie **programu Visual Studio zdalnego debugera odnajdywania**. Jeśli ta opcja jest wyświetlana, upewnij się, że jest zaznaczona, a także wybrano jeden lub więcej typów sieci.  
  
4.  Jeśli **programu Visual Studio zdalnego debugera odnajdywania** jest nie na liście, kliknij przycisk **Zezwalaj na inną aplikację**. Jeśli nadal nie jest widoczny w **Dodaj aplikację** okna, kliknij przycisk **Przeglądaj** i przejdź do  **\<katalogu instalacyjnego programu Visual Studio > \Common7\IDE\Remote debugera**. Znajdź odpowiedni folder dla aplikacji (x86, x64, Appx), a następnie wybierz **msvsmon.exe**. Następnie kliknij przycisk **Dodaj**.  
  
5.  W **dozwolone aplikacje i funkcje** listy, wybierz **zdalny debuger programu Visual Studio**. Sprawdź, co najmniej jeden typ sieci (**domeny głównej/pracy (prywatny), publicznego**), które mają monitor debugera zdalnego do komunikowania się z. Typy musi zawierać sieci, do którego jest podłączony komputer programu Visual Studio. 

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-remote-computer"></a>Sprawdź, czy porty są otwarte w Zaporze systemu Windows na komputerze zdalnym  
 Składniki zdalnego debugowania można zainstalowany na komputerze zdalnym lub uruchom z udostępnionego katalogu. W obu przypadkach musi być skonfigurowany zapory komputera zdalnego. Składniki zdalnego debugowania znajdują się w:  
  
 **\<Katalog instalacyjny usługi Visual Studio > \Common7\IDE\Remote debugera**  
  
 Instrukcje dotyczące konfigurowania Zapory systemu Windows się nieco różnić w różnych systemach operacyjnych. Systemu Windows 8/8.1, Windows 10 i Windows Server 2012, słowo **aplikacji** jest używany; w systemie Windows 7 lub Windows Server 2008, słowo **program** jest używany;  W poniższych krokach używamy słowa **aplikacji**.  
  
1.  Otwórz stronę zapory systemu Windows. (Na **Start** menu pole wyszukiwania, wpisz **zapory systemu Windows**.)  
  
2.  Kliknij przycisk **Zezwalaj aplikacji lub funkcji przez zaporę systemu Windows**.  
  
3.  W **dozwolone aplikacje i funkcje** listy, wyszukiwanie **zdalny debuger programu Visual Studio**. Jeśli ta opcja jest wyświetlana, upewnij się, że jest zaznaczona, a także wybrano jeden lub więcej typów sieci.  
  
4.  Jeśli **zdalny debuger programu Visual Studio** jest nie na liście, kliknij przycisk **Zezwalaj na inną aplikację**. Jeśli nadal nie jest widoczny w **dodać okna aplikacji**, kliknij przycisk **Przeglądaj** i przejdź do  **\<katalogu instalacyjnego programu Visual Studio > \Common7\IDE\Remote debugera**. Znajdź odpowiedni folder dla aplikacji (x86, x64, Appx), a następnie wybierz **msvsmon.exe**. Następnie kliknij przycisk **Dodaj**.  
  
5.  W **dozwolone aplikacje** listy, wybierz **zdalny debuger programu Visual Studio**. Sprawdź, co najmniej jeden typ sieci (**domeny głównej/pracy (prywatny), publicznego**), które mają monitor debugera zdalnego do komunikowania się z. Typy musi zawierać sieci, do którego jest podłączony komputer programu Visual Studio. 

### <a name="managed-or-native-compatibility-mode-open-additional-ports-on-the-remote-computer"></a>(Tryb zgodności zarządzanego i natywnego) Otwórz dodatkowych portów na komputerze zdalnym

Jeśli używasz trybu zgodności dla debugera (**Narzędzia > Opcje > debugowanie**), dodatkowych portów będzie musiał zostać otwarty. Tryb zgodności umożliwia starszych wersji debugera i inne porty są wymagane.

> [!NOTE]
> Starszych wersji debugera jest debuger programu Visual Studio 2010.
  
|||||  
|-|-|-|-|  
|**Porty**|**Przychodzącego/wychodzącego**|**Protokół**|**Opis**|  
|135, 139, 445|Wychodzące|TCP|Wymagany.|  
|137, 138|Wychodzące|UDP|Wymagany.|  
|500, 4500|Wychodzące|UDP|Wymagane, jeśli zasad domeny wymaga komunikacji w sieci, można wykonać za pomocą protokołu IPSec.|  
|80|Wychodzące|TCP|Wymagany w przypadku debugowania na serwerze sieci Web.|
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)