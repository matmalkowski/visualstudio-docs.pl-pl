---
title: Skonfiguruj zaporę Windows zdalne debugowanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9688948ebe2fa5e045578ee808e068d59450d748
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433394"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>Skonfiguruj zaporę Windows do zdalnego debugowania
W tym temacie opisano sposób skonfigurowania zapory w celu włączenia debugowania zdalnego na komputerach z następującymi systemami operacyjnymi:  
  
-   Windows 10  
  
-   Windows 8/8.1  
  
-   Windows 7   
  
-   Windows Server 2012 z dodatkiem R2  

-   Windows Server 2012
  
-   Windows Server 2008 z dodatkiem R2 
  
 Jeśli sieci, na którym jest debugowany, nie są chronione przez zaporę, ta konfiguracja nie jest konieczne. W przeciwnym razie komputer, który jest hostem programu Visual Studio i komputera zdalnego, który ma być debugowany wymagają zmian w konfiguracji zapory.  
  
 **Protokół IPSec** Jeśli sieć wymaga tej komunikacji jest wykonywane za pomocą protokołu IPSec, należy otworzyć dodatkowe porty na komputerze-hoście programu Visual Studio i komputera zdalnego.  
  
 **Serwer sieci Web** przypadku debugowania zdalnego serwera sieci Web, należy otworzyć port dodatkowy na komputerze zdalnym. (Dla usług IIS, port 80 musi być otwarty.)  
  
 Należy pamiętać, że oba komputery pracują jest konieczne uruchomienie tego samego systemu operacyjnego. Na przykład komputer z programem Visual Studio może działać system Windows 10 i komputer zdalny można uruchomić system Windows Server 2012 R2.      
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Porty na komputerze zdalnym, na które Włączanie debugowania zdalnego  
  
|**Porty**|**Wychodzące/przychodzące**|**Protokół**|**Opis**|   
|-|-|-|-|  
|4022|przychodzące|TCP|Dla programu VS 2017. Numer portu jest zwiększany o 2 dla każdej wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Visual przypisania portów debugera zdalnego Studio](../debugger/remote-debugger-port-assignments.md).|  
|4023|przychodzące|TCP|Dla programu VS 2017. Numer portu jest zwiększany o 2 dla każdej wersji programu Visual Studio. (Tylko umożliwia zdalne debugowanie 32-bitowy proces z 64-bitowej wersji zdalnego debugera.) Aby uzyskać więcej informacji, zobacz [Visual przypisania portów debugera zdalnego Studio](../debugger/remote-debugger-port-assignments.md).| 
|3702|Wychodzące|UDP|(Opcjonalnie) Wymagana w przypadku odnajdywania zdalnego debugera.|    
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Jak skonfigurować porty w Zaporze Windows  

Po zainstalowaniu programu Visual Studio lub zdalnego debugera, oprogramowanie spróbuje otworzyć odpowiednie porty. Jednak w niektórych przypadkach (na przykład za pomocą zapory innych firm) może być konieczne ręcznie otworzyć port. Jeśli musisz potwierdzić, że porty są otwarte, zobacz [Rozwiązywanie problemów](#troubleshooting). Instrukcje dotyczące otwierania portu mogą być inne w starszych wersjach systemu Windows.

Aby otworzyć port:
  
1. Otwórz **Start** menu, wyszukaj **Zapora Windows z zabezpieczeniami zaawansowanymi**.

2. Następnie wybierz **reguły ruchu przychodzącego > Nowa reguła > Port**, a następnie kliknij przycisk **dalej**. (Dla reguły wychodzące wybierz **reguł dla ruchu wychodzącego** zamiast.)

3. Wybierz opcję **TCP** lub **UDP**, w zależności od numeru portu.

4. W obszarze **określone porty lokalne**, wprowadź numer portu, kliknij przycisk **dalej**.

5. Kliknij przycisk **Zezwalaj na połączenie** a następnie kliknij przycisk **dalej**.

6. Wybierz jeden lub więcej typów sieci można włączyć za pośrednictwem portu usługi, a następnie kliknij przycisk **dalej**.

    Wybranego typu musi zawierać sieci, do którego jest podłączony komputera zdalnego.
7. Dodaj nazwę (na przykład **msvsmon**, **IIS**, lub **narzędzia Web Deploy**) reguły, a następnie kliknij przycisk **Zakończ**.

    Powinieneś zobaczyć nową regułę reguły ruchu przychodzącego lub reguły ruchu wychodzącego liście.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli problemy z dołączanie do aplikacji ze zdalnym debugerem może być konieczne Sprawdź, czy odpowiednie porty są otwarte.

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-visual-studio-computer"></a>Sprawdź, czy porty są otwarte w Zaporze Windows na komputerze programu Visual Studio  
 Instrukcje dotyczące konfigurowania zapory Windows się nieznacznie różnić w różnych systemach operacyjnych. W systemu Windows 8/8.1, Windows 10 i Windows Server 2012, słowo **aplikacji** jest używany; na Windows 7 lub Windows Server 2008, wyraz **program** jest używany;  W poniższych krokach używamy słowa **aplikacji**.  
  
1.  Otwórz stronę zapory Windows. (W **Start** polu wyszukiwania menu, typ **zapory Windows**).  
  
2.  Kliknij przycisk **Zezwalaj aplikacji lub funkcję przez zaporę Windows**.  
  
3.  W **dozwolone aplikacje i funkcje** listy, wyszukiwanie **Visual Studio zdalnego debugera odnajdywania**. Jeśli ta opcja jest wyświetlana, upewnij się, że jest zaznaczone, a także wybrano jeden lub więcej typów sieci.  
  
4.  Jeśli **Visual Studio zdalnego debugera odnajdywania** jest wymieniony, kliknij przycisk **Zezwalaj na inną aplikację**. Jeśli nadal nie widać go w **Dodaj aplikację** okna, kliknij przycisk **Przeglądaj** i przejdź do  **\<katalogu instalacyjnego programu Visual Studio > \Common7\IDE\Remote debugera**. Znajdź odpowiedni folder dla aplikacji (x86, x64, Appx), a następnie wybierz pozycję **msvsmon.exe**. Następnie kliknij przycisk **Dodaj**.  
  
5.  W **dozwolone aplikacje i funkcje** listy wybierz **zdalny debuger programu Visual Studio**. Zaznacz jeden lub więcej typów sieci (**domeny głównej/pracy (prywatny), publiczne**) ma monitor debugera zdalnego nawiązać połączenia z usługą. Typy mogą zawierać sieci, do którego jest podłączony komputer z programem Visual Studio. 

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-remote-computer"></a>Sprawdź, czy porty są otwarte w Zaporze Windows na komputerze zdalnym  
 Składniki zdalnego debugowania można zainstalowane na komputerze zdalnym lub uruchom z udostępnionego katalogu. W obu przypadkach należy skonfigurować zapory komputera zdalnego. Składniki debugowania zdalnego znajdują się w:  
  
 **\<Katalog instalacyjny usługi Visual Studio > \Common7\IDE\Remote debugera**  
  
 Instrukcje dotyczące konfigurowania zapory Windows się nieznacznie różnić w różnych systemach operacyjnych. W systemu Windows 8/8.1, Windows 10 i Windows Server 2012, słowo **aplikacji** jest używany; na Windows 7 lub Windows Server 2008, wyraz **program** jest używany;  W poniższych krokach używamy słowa **aplikacji**.  
  
1.  Otwórz stronę zapory Windows. (Na **Start** polu wyszukiwania menu, typ **zapory Windows**.)  
  
2.  Kliknij przycisk **Zezwalaj aplikacji lub funkcję przez zaporę Windows**.  
  
3.  W **dozwolone aplikacje i funkcje** listy, wyszukiwanie **zdalny debuger programu Visual Studio**. Jeśli ta opcja jest wyświetlana, upewnij się, że jest zaznaczone, a także wybrano jeden lub więcej typów sieci.  
  
4.  Jeśli **zdalny debuger programu Visual Studio** jest wymieniony, kliknij przycisk **Zezwalaj na inną aplikację**. Jeśli nadal nie widać go w **okno aplikacji Dodaj**, kliknij przycisk **Przeglądaj** i przejdź do  **\<katalogu instalacyjnego programu Visual Studio > \Common7\IDE\Remote debugera**. Znajdź odpowiedni folder dla aplikacji (x86, x64, Appx), a następnie wybierz pozycję **msvsmon.exe**. Następnie kliknij przycisk **Dodaj**.  
  
5.  W **dozwolone aplikacje** listy wybierz **zdalny debuger programu Visual Studio**. Zaznacz jeden lub więcej typów sieci (**domeny głównej/pracy (prywatny), publiczne**) ma monitor debugera zdalnego nawiązać połączenia z usługą. Typy mogą zawierać sieci, do którego jest podłączony komputer z programem Visual Studio. 

### <a name="managed-or-native-compatibility-mode-open-additional-ports-on-the-remote-computer"></a>(Tryb zgodności zarządzane lub natywne) Otwarcie dodatkowych portów na komputerze zdalnym

Jeśli używasz trybu zgodności dla debugera (**Narzędzia > Opcje > debugowanie**), będzie konieczne będzie otwarcie dodatkowych portów. Tryb zgodności umożliwia starszych wersji debugera i inne porty są wymagane.

> [!NOTE]
> Starszych wersji debugera jest debugera programu Visual Studio 2010.
  
|**Porty**|**Wychodzące/przychodzące**|**Protokół**|**Opis**|  
|-|-|-|-|  
|135, 139, 445|Wychodzące|TCP|Wymagane.|  
|137, 138|Wychodzące|UDP|Wymagane.|  
|500, 4500|Wychodzące|UDP|Wymagane, jeśli zasady domeny wymaga komunikacji sieciowej, można wykonać przy użyciu protokołu IPSec.|  
|80|Wychodzące|TCP|Wymagane na potrzeby debugowania na serwerze sieci Web.|
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)