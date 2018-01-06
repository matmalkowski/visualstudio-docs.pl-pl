---
title: "Fundamentalne zmiany w rozszerzalności programu Visual Studio 2017 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 068b71a78149bb1c52e28bc47245d0dc888496bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Zmiany w Visual Studio 2017 rozszerzalności

Z programu Visual Studio 2017 r, możemy Cię oferty [szybsze, waga jaśniejszego środowisko instalacji programu Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer) który pozwala ograniczyć wpływ programu Visual Studio w systemach użytkowników podczas przypisywania użytkownikom większy wybór za pośrednictwem obciążeń i funkcje są instalowane. Aby obsługiwać te ulepszenia, możemy wprowadzone zmiany w modelu rozszerzalności i wprowadzono kilka zmian podziału rozszerzalności programu Visual Studio. Tym dokumencie opisano szczegóły techniczne dotyczące tych zmian i co można zrobić w celu ich rozwiązania. Należy pamiętać, że niektóre informacje są szczegóły implementacji punktu w czasie i mogą zostać później zmienione.

## <a name="changes-affecting-vsix-format-and-installation"></a>Zmian wpływających na Format pliku VSIX i instalacji

Związku VSIX v3 formatu (wersja 3) do obsługi środowiska lekki instalacji.

Zmiany formatu pliku VSIX obejmują:

* Deklaracja wymagań wstępnych Instalatora. Dostarczać gwarantuje lekkie fast instalacja programu Visual Studio, Instalator oferuje więcej opcji konfiguracji dla użytkowników. W związku z tym aby upewnić się, czy są zainstalowane funkcje i składniki wymagane przez rozszerzenie, rozszerzenia należy zadeklarować ich zależności.
  * Instalator programu Visual Studio 2017 oferują możliwość automatycznie pobrać i zainstalować składniki konieczne dla użytkownika w ramach instalacji rozszerzenia.
  * Użytkownicy zostaną ostrzeżeni również podczas próby instalacji rozszerzenia, który nie został utworzony przy użyciu nowego formatu v3 VSIX, nawet jeśli zostały oznaczone w manifeście ich jako przeznaczonych dla wersji 15.0.
* Udoskonalone funkcje z formatem pliku VSIX. Dostarczenia [instalacji niskiego wpływu](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install) programu Visual Studio, który również obsługuje instaluje side-by-side, firma Microsoft nie jest już zapisać większość danych konfiguracji do rejestru systemowego i przeniesione Visual Studio specyficzne dla zestawów spoza pamięci podręcznej GAC. Możemy również zwiększenie możliwości formatu pliku VSIX i aparat instalacji VSIX, umożliwiając użyj jej zamiast MSI lub EXE, aby zainstalować rozszerzenia dla niektórych typów instalacji.

  Nowe możliwości obejmują:

  * Rejestracja w określonym wystąpieniu programu Visual Studio.
  * Instalacja poza [folder rozszerzenia](set-install-root.md).
  * Wykrywanie architektury procesora.
  * Zależność od pakietów językowych oddzielone języka.
  * Instalacja z [obsługi NGEN](ngen-support.md).

## <a name="building-an-extension-for-visual-studio-2017"></a>Tworzenia rozszerzeń dla programu Visual Studio 2017 r.

Projektanta, narzędzi do tworzenia nowej format manifestu VSIX v3 jest teraz dostępna w programie Visual Studio 2017 r. Zobacz dokument towarzyszący [jak: Migrowanie projektów rozszerzalności programu Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) szczegółowe informacje na temat przy użyciu narzędzia Projektant lub wprowadzanie aktualizacji ręcznej do projektu i manifestu do opracowywania rozszerzeń v3 VSIX.

## <a name="change-visual-studio-user-data-path"></a>Zmiany: Ścieżka danych użytkownika programu Visual Studio

Wcześniej tylko jednej instalacji każdego wydania programu Visual Studio może znajdować się na każdym komputerze. Do obsługi instalacji programu Visual Studio 2017 side-by-side, wiele ścieżek danych użytkownika dla programu Visual Studio może istnieć na komputerze użytkownika.

Kod używany w procesie programu Visual Studio powinny zostać uaktualnione do użycia Menedżera ustawień programu Visual Studio. Kod działający poza procesem, Visual Studio można znaleźć ścieżki użytkownika określonego instalacji programu Visual Studio [z zachowaniem wskazówek zamieszczonych w tym miejscu](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Zmień: Globalna pamięć podręczna zestawów (GAC)

Większość zestawów podstawowych programu Visual Studio już nie są zainstalowane w pamięci podręcznej GAC. Wprowadzono następujące zmiany, tak aby kodu uruchomionego w procesie programu Visual Studio można nadal znaleźć wymaganych zestawów w czasie wykonywania.

> [!NOTE]
> [INSTALLDIR] poniżej odwołuje się do katalogu instalacyjnego programu Visual Studio. VSIXInstaller.exe będzie automatycznie wypełnić to, ale do pisania kodu, niestandardowe wdrożenie, przeczytaj [lokalizowanie Visual Studio](locating-visual-studio.md).

* Zestawy tylko zainstalowanych w pamięci podręcznej GAC:
  * Te zestawy są teraz instalowane w obszarze [INSTALLDIR] \Common7\IDE\, [INSTALLDIR] \Common7\IDE\PublicAssemblies lub \Common7\IDE\PrivateAssemblies [INSTALLDIR]. Te foldery są częścią procesu Visual Studio sondowania ścieżek.
* Zestawy, które zostały zainstalowane w ścieżce badania i w pamięci podręcznej GAC:
  * Kopiowanie w pamięci GAC został usunięty z Instalatora.
  * Plik .pkgdef został dodany do określ nazwę podstawową kodu dla zestawu.

    Na przykład:
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    W czasie wykonywania w podsystemie pkgdef Visual Studio zostaną scalone te wpisy w pliku konfiguracji środowiska wykonawczego procesu Visual Studio (w obszarze [VSAPPDATA]\devenv.exe.config) jako [ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx) elementów. Jest to zalecany sposób, aby umożliwić proces programu Visual Studio znaleźć z zestawu, ponieważ pozwala ona na uniknięcie wyszukiwanie za pomocą sondowania ścieżek.

### <a name="reacting-to-this-breaking-change"></a>Reagowanie na tej istotnej zmiany

* Jeśli rozszerzenie jest uruchomiony w ramach procesu programu Visual Studio:
  * Kod będzie można znaleźć zestawów podstawowych programu Visual Studio.
  * Należy rozważyć użycie pliku .pkgdef, aby określić ścieżkę do Twojej zestawów, w razie potrzeby.
* Jeśli rozszerzenie jest uruchomiona poza procesem programu Visual Studio:
  * Należy wziąć pod uwagę wyszukiwanie zestawów podstawowych programu Visual Studio w obszarze [INSTALLDIR] \Common7\IDE\, [INSTALLDIR] \Common7\IDE\PublicAssemblies lub \Common7\IDE\PrivateAssemblies [INSTALLDIR] przy użyciu konfiguracji pliku lub zestawu programu rozpoznawania nazw.

## <a name="change-reduce-registry-impact"></a>Zmień: Zmniejszyć wpływ rejestru

### <a name="global-com-registration"></a>Globalne rejestracji modelu COM

* Wcześniej Visual Studio zainstalowane wielu kluczy rejestru w gałęzi wpisów z HKEY_CLASSES_ROOT i HKEY_LOCAL_MACHINE do obsługi rejestracji COM macierzystego. Aby wyeliminować wpływ ten, używa teraz program Visual Studio [aktywacji bez rejestracji składników COM](https://msdn.microsoft.com/en-us/library/ms973913.aspx).
* W rezultacie, większość TLB / OLB / plików biblioteki DLL w % ProgramFiles (x86) %\Common Files\Microsoft Shared\MSEnv już są zainstalowane domyślnie w programie Visual Studio. Te pliki są teraz instalowane w obszarze [INSTALLDIR] z odpowiedniego manifestów COM bez rejestrowania używany przez proces hosta programu Visual Studio.
* W związku z tym zewnętrznego kodu, który korzysta z globalnej rejestracji COM dla interfejsów COM usługi Visual Studio już nie znajdzie te rejestracji. Kod używany w procesie programu Visual Studio nie będą widzieć różnicy.

### <a name="visual-studio-registry"></a>Visual Studio rejestru

* Wcześniej Visual Studio zainstalowany wielu kluczy rejestru w gałęzi HKEY_LOCAL_MACHINE i HKEY_CURRENT_USER w kluczu Visual Studio specyficzne dla systemu:
  * HKLM\Software\Microsoft\VisualStudio\\**wersji**: kluczy rejestru utworzonych przez instalatorów MSI i rozszerzenia dla poszczególnych komputerów.
  * HKCU\Software\Microsoft\VisualStudio\\**wersji**: kluczy rejestru utworzonych przez Visual Studio, aby przechowywać ustawienia specyficzne dla użytkownika.
  * HKCU\Software\Microsoft\VisualStudio\\**wersji**_Config: kopię programu Visual Studio HKLM klawisz powyżej, a także klucze rejestru scalone z plików .pkgdef przez rozszerzenia.
* Aby zmniejszyć wpływ na rejestrze, używa teraz program Visual Studio [RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx) funkcji do przechowywania kluczy rejestru w prywatnej pliku binarnego w obszarze [VSAPPDATA]\privateregistry.bin. Bardzo małą liczbę Visual Studio kluczy pozostają w rejestrze systemu.
* Nie ma wpływu na istniejący kod używany w procesie programu Visual Studio. Visual Studio będzie przekierowywać wszystkie operacje rejestru w kluczu HKCU Visual Studio specyficzne dla do prywatnego rejestru. Odczytywanie i zapisywanie do innych lokalizacji rejestru będzie korzystać z rejestru systemu.
* Kod zewnętrzny należy załadować i odczytać z pliku wpisy rejestru programu Visual Studio.

### <a name="reacting-to-this-breaking-change"></a>Reagowanie na tej istotnej zmiany

* Kod zewnętrzny powinny być konwertowane na Użyj aktywacji bez rejestracji składników COM również.
* Zewnętrzne składniki można znaleźć lokalizacji programu Visual Studio [z zachowaniem wskazówek zamieszczonych w tym miejscu](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).
* Zalecane jest użycie składników zewnętrznych [zewnętrznych Menedżer ustawień](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx) zamiast odczytu/zapisu bezpośrednio do kluczy rejestru programu Visual Studio.
* Sprawdź, czy rozszerzenie jest używany przez składniki mogą wdrażać innej techniki rejestracji. Na przykład może być możliwe korzystanie z nowego rozszerzenia [polecenia msvsmon rejestracji COM pliku JSON](migrate-debugger-COM-registration.md).
