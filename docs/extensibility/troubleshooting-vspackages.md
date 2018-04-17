---
title: Rozwiązywanie problemów z VSPackages | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73c754de72238671dd10235e792c43fb6d0a1b5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-vspackages"></a>Rozwiązywanie problemów z VSPackages
Poniżej przedstawiono typowe problemy, które mogą wiązać Ciebie z VSPackage i wskazówki dotyczące rozwiązywania problemów.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Aby rozwiązać pakiet VSPackage, który przechowuje uruchomienie programu Visual Studio  
  
-   Uruchom [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w trybie awaryjnym.  
  
     Aby uruchomić [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w trybie awaryjnym, w wierszu polecenia, wpisz **devenv.exe /safemode**.  
  
     W trakcie tego procesu nie VSPackages są ładowane z wyjątkiem VSPackages, które są dołączone do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Aby rozwiązać pakiet VSPackage, który nie zostanie załadowany  
  
1.  Upewnij się, czy korzystają z katalogu głównego rejestru, w którym pakiet VSPackage jest zarejestrowany do uruchomienia, zwykle katalog główny eksperymentalne rejestru.  
  
     Aby uzyskać więcej informacji, zobacz [eksperymentalne wystąpienie](../extensibility/the-experimental-instance.md).  
  
2.  Jeśli pakiet VSPackage jest przeznaczony do uruchamiania w folderze głównym rejestru eksperymentalne, upewnij się, czy korzystasz z wersji eksperymentalne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Aby uruchomić wersję eksperymentalne, wpisz następujące polecenie w oknie poleceń: **devenv/rootsuffix exp**.  
  
3.  Sprawdź wpisy rejestru pakiet VSPackage.  
  
     Aby uzyskać więcej informacji, zobacz [rejestrowanie VSPackages](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd) i [Zarządzanie VSPackages](../extensibility/managing-vspackages.md).  
  
4.  Otwórz **dane wyjściowe** okna wystąpienia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] który nie powiodło się załadowanie pakietu VSPackage. Informacje o Dlaczego pakiet VSPackage niepowodzenie ładowania mogą być wyświetlane w danym przedziale.  
  
    > [!NOTE]
    >  Jeśli uruchamiasz eksperymentalne wersja [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE), sprawdzić **dane wyjściowe** okna obie wersje.  
  
5.  Sprawdź dziennik aktywności.  
  
     Aby uzyskać więcej informacji, zobacz [porady: Korzystanie z dziennika aktywności](../extensibility/how-to-use-the-activity-log.md).  
  
6.  Aby uzyskać więcej informacji na temat wyjątków zgłaszanych przez IDE, kliknij przycisk **wyjątki** na **debugowania** menu włączenie wyjątków. W **wyjątki** okno dialogowe Wybieranie typów wyjątków, o których chcesz uzyskać więcej informacji.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Aby rozwiązać pakiet VSPackage, która nie jest zarejestrowana  
  
1.  Upewnij się, że zestaw pakiet VSPackage znajduje się w zaufanej lokalizacji. RegPkg nie można zarejestrować zestawów w niezaufanych lub częściowo zaufanej lokalizacji, takiej jak udziału sieciowego w domyślnej konfiguracji zabezpieczeń platformy .net. Mimo że zawsze, gdy użytkownik tworzy projekt w niezaufanej lokalizacji zostanie wyświetlone ostrzeżenie, pole wyboru "nie pokazuj tego komunikatu ponownie" uniemożliwia to ostrzeżenie występowaniu.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Aby rozwiązać polecenia, który nie jest widoczny lub generuje błąd, po kliknięciu polecenia  
  
1.  Scalanie nowych lub zmienionych polecenia i już w IDE, wpisując na następujących [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wiersza polecenia: **/rootsuffix devenv/Setup Exp**.  
  
2.  Upewnij się, że [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można znaleźć UI.dll VSPackage.  
  
    1.  Znajdź identyfikator CLSID pakiet VSPackage w sekcji pakiety rejestru:  
  
         HKLM\Software\Microsoft\Visual Studio\\*\<wersji >*\Packages  
  
    2.  Sprawdź poprawność przez podklucz SatelliteDll podanej ścieżce.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Aby rozwiązać pakiet VSPackage, który zachowuje się nieoczekiwanie  
  
1.  Ustaw punkty przerwania w kodzie.  
  
     Dobrym punktów początkowych do debugowania są konstruktora i metodę inicjowania. W obszarze, który ma zostać oceniona, takie jak polecenie menu można również ustawić punktów przerwania. Aby włączyć punkty przerwania, należy uruchomić w debugerze.  
  
    1.  Na **projektu** menu, kliknij przycisk **właściwości**.  
  
    2.  Na **strony właściwości** okno dialogowe, wybierz opcję **debugowania** kartę.  
  
    3.  W **argumenty wiersza polecenia** wpisz główny sufiks środowisko projektowe który celów pakiet VSPackage. Na przykład, aby wybrać eksperymentalne kompilacji, wpisz: **RootSuffix Exp**.  
  
    4.  Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie** lub naciśnij klawisz F5.  
  
        > [!NOTE]
        >  Jeśli debugowany projekt, należy utworzyć lub teraz załadować istniejącego wystąpienia projektu.  
  
2.  Użyj dziennika aktywności.  
  
     Śledzenie zachowania pakiet VSPackage przy zapisywania informacji dziennika aktywności w punktach klucza. Ta technika jest szczególnie przydatna podczas uruchamiania pakiet VSPackage w środowisku sprzedaży detalicznej. Aby uzyskać więcej informacji, zobacz [porady: Korzystanie z dziennika aktywności](../extensibility/how-to-use-the-activity-log.md).  
  
3.  Użyj symboli publicznych.  
  
     Aby poprawić czytelność podczas debugowania, możesz dołączyć symboli do debugera.  
  
    1.  Z **narzędzia/Opcje** menu, przejdź do **debugowanie/symbole** okno dialogowe.  
  
    2.  Dodaj tę **symboli (.pdb) lokalizacja_pliku**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  Aby zwiększyć wydajność, należy określić folder pamięci podręcznej symboli, na przykład:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Aby rozwiązać problemy, brak pakiet VSPackage lub jednej z jego zależności  
  
1.  Dla kodu zarządzanego upewnij się, że ścieżek odwołania są poprawne.  
  
    1.  Na **projektu** menu, kliknij przycisk **właściwości**.  
  
    2.  Wybierz **odwołania** karcie **strony właściwości** okno dialogowe i upewnij się, że wszystkie ścieżki są prawidłowe. Alternatywnie można użyć **przeglądarki obiektów** do przeglądania dla obiektów, do którego istnieje odwołanie.  
  
         Dla kodu zarządzanego, można użyć [Fuslogvw.exe (Podgląd dziennika powiązań zestawów)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) można wyświetlić szczegółów załadowań zestawów nie powiodło się.  
  
2.  Dla niezarządzanego kodu, Znajdź identyfikator CLSID pakiet VSPackage w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] węzła rejestru CLSID:  
  
     HKLM\Software\Microsoft\Visual Studio\\*\<wersji >*\CLSID  
  
 Upewnij się, że wpis InprocServer32 ma poprawną ścieżkę pliku dll pakiet VSPackage.  
  
## <a name="see-also"></a>Zobacz też  
 [Pakiety VSPackage](../extensibility/internals/vspackages.md)