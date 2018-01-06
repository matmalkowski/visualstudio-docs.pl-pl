---
title: "Przewodnik administratora programu Podgląd pomocy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-help-viewer
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5f509b0ace14c4e0becd714e25ee9ec26770c6e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="help-viewer-administrator-guide"></a>Przewodnik administratora podglądu pomocy
Podgląd Pomocy umożliwia zarządzanie lokalnym instalacje pomocy dla środowisk sieci lub bez dostępu do Internetu. Lokalnej zawartości pomocy jest skonfigurowany na podstawie na komputerze. Domyślnie użytkownicy muszą mieć uprawnienia administratora do ich lokalnej pomocy instalacji aktualizacji.  
  
Jeśli środowisko sieciowe umożliwia klientom dostęp do Internetu, można użyć pliku wykonywalnego menedżera zawartości pomocy do wdrożenia zawartość lokalnej pomocy z Internetu. Aby uzyskać więcej informacji na temat składni wiersza polecenia HlpCtntMgr.exe, zobacz [argumenty wiersza polecenia do menedżera zawartości Pomocy](../ide/command-line-arguments-for-the-help-content-manager.md).

Tworzenie punktu końcowego usługi w sieci intranet i podobne typy działań, zobacz informacji o tworzeniu zawartości, [SDK podglądu pomocy](../extensibility/internals/microsoft-help-viewer-sdk.md).  
  
Jeśli nie masz dostępu do Internetu w danym środowisku sieciowym, podglądu pomocy można wdrożyć zawartość lokalnej pomocy w intranecie lub w udziale sieciowym. Można również wyłączyć za pomocą opcji Pomoc programu Visual Studio IDE [przesłania klucza rejestru](../ide/help-content-manager-overrides.md) funkcji, takich jak:

- online i pomoc w trybie offline

- do instalacji zawartości podczas pierwszego uruchomienia IDE

- Określanie intranetową usługę zawartości

- Zarządzanie zawartością 
  
## <a name="deploying-local-help-content-from-the-internet"></a>Wdrażanie lokalnej zawartości pomocy z Internetu  
Mananger zawartości pomocy (HlpCtntMgr.exe) służy do wdrażania zawartości pomocy z Internetu na komputerach klienckich. Należy użyć następującej składni:  
  
```
\\%ProgramFiles(x86)%\Microsoft Help Viewer\v2.3\HlpCtntmgr.exe /operation \<*name*> /catalogname \<*catalog name*> /locale \<*locale*>
```
  
Aby uzyskać więcej informacji na temat składni wiersza polecenia HlpCtntMgr.exe, zobacz [argumenty wiersza polecenia do menedżera zawartości Pomocy](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
Wymagania:  
  
-   Komputery klienckie muszą mieć dostęp do Internetu.  
  
-   Użytkownicy muszą mieć uprawnienia administratora do aktualizacji, Dodaj lub usuń zawartość lokalnej pomocy, po zakończeniu instalacji.  
  
 Ostrzeżenia:  
  
-   Domyślne źródło pomocy nadal być w trybie online.
  
### <a name="example"></a>Przykład  
W poniższym przykładzie instalowana zawartości w języku angielskim dla programu Visual Studio na komputerze klienckim.  
  
##### <a name="to-install-english-content-from-the-internet"></a>Aby zainstalować zawartość w języku angielskim z Internetu  
  
1.  Wybierz **Start** , a następnie wybierz **Uruchom**.  
  
2.  Wpisz następujące polecenie:  
  
     C:\Program pliki (x86) \Microsoft Help Viewer\v2.3\hlpctntmgr.exe /operation zainstalować/catalogname VisualStudio15/Locale en-us  
  
3.  Naciśnij klawisz **wprowadź**.  
  
## <a name="deploying-pre-installed-local-help-content-on-client-computers"></a>Wdrażanie wstępnie zainstalować zawartość lokalnej pomocy na komputerach klienckich
Można zainstalować zestaw zawartości online do jednego komputera, a następnie skopiuj zainstalowanego zestawu zawartości do innych komputerów.  
  
Wymagania:  
  
-   Komputer, na którym należy zainstalować zestaw zawartości do musi mieć dostęp do Internetu.  
  
-   Użytkownicy muszą mieć uprawnienia administratora do aktualizacji, Dodaj lub usuń zawartość lokalnej pomocy, po zakończeniu instalacji.  
  
    > [!TIP]
    >  Jeśli użytkownicy nie mają uprawnień administratora, zaleca się wyłączenie karcie Zarządzanie zawartością w Podglądzie pomocy. Aby uzyskać więcej informacji, zobacz [zastąpienia menedżera zawartości Pomocy](../ide/help-content-manager-overrides.md).  
  
Ostrzeżenia:
  
-   Domyślne źródło pomocy nadal być w trybie online.
  
### <a name="create-the-content-set"></a>Tworzenie zestawu zawartości.  
Przed utworzeniem podstawowego zestawu zawartości, należy najpierw odinstalować wszystkie lokalne zawartości programu Visual Studio na komputerze docelowym.  
  
#### <a name="to-uninstall-local-help"></a>Aby odinstalować pomocy lokalnej  
  
1.  W Podglądzie pomocy, wybierz opcję **zarządzania zawartością** kartę.  
  
2.  Przejdź do zestawu dokumentów programu Visual Studio.  
  
3.  Wybierz **Usuń** obok każdego elementu podrzędnego.  
  
4.  Wybierz **aktualizacji** do odinstalowania.
  
5.  Przejdź do %ProgramData%\Microsoft\HelpLibrary2\Catalogs\VisualStudio15 i sprawdź, czy folder zawiera tylko catalogType.xml pliku.  
  
 Po usunięciu wszystkich zainstalowanych wcześniej lokalnej pomocy programu Visual Studio zawartości, można przystąpić do pobierania podstawowego zestawu zawartości.  
  
#### <a name="to-download-the-content"></a>Aby pobrać zawartość  
  
1.  W Podglądzie pomocy, wybierz opcję **zarządzania zawartością** kartę.  
  
2.  W obszarze **zalecane dokumentacji** lub **dostępnej dokumentacji**, przejdź do zestawów dokumentacji, aby pobrać, a następnie wybierz pozycję **Dodaj**.  
  
3.  Wybierz **aktualizacji**.  
  
 Następnie należy do pakietu zawartości, dlatego może być wdrożony na komputerach klienckich.  
  
#### <a name="to-package-the-content"></a>Do pakietu zawartości  
  
1.  Utwórz folder do skopiowania zawartości do późniejszego wdrożenia. Na przykład: C:\VSHelp.  
  
2.  Otwórz cmd.exe z uprawnieniami administratora.  
  
3.  Przejdź do folderu, który został utworzony w kroku 1.  
  
4.  Wpisz następujące polecenie:  
  
     Xcopy %ProgramData%\Microsoft\HelpLibrary2 \< *nazwa_folderu*> \ /y /e /k /o  
  
     Na przykład:`Xcopy %ProgramData%\Microsoft\HelpLibrary2 c:\VSHelp\ /y /e /k /o`  
  
### <a name="deploying-the-content"></a>Wdrażanie zawartości  
  
#### <a name="to-deploy-the-content"></a>Aby wdrożyć zawartość  
  
1.  Utwórz udział sieciowy i skopiuj zawartość pomocy do tej lokalizacji.  
  
     Na przykład skopiuj zawartość C:\VSHelp do \\\myserver\VSHelp.  
  
2.  Utwórz plik .bat zawiera skrypt wdrażania zawartości pomocy. Ponieważ klient może prawdopodobnie mają blokady odczytu na dowolny plik usuwane w ramach powiadomienia wypychanego, powinny być zamknięty przed wypychania aktualizacji klienta. Na przykład:  
  
    ```  
    REM - copy pre-ripped content to ProgramData  
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o  
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to ProgramData (%ERRORLEVEL%)
    ```  
  
3.  Uruchom plik bat przeznaczone do zainstalowania zawartości pomocy na maszynach lokalnych.  
  
## <a name="see-also"></a>Zobacz także
[Argumenty wiersza poleceń Menedżera zawartości pomocy](../ide/command-line-arguments-for-the-help-content-manager.md)  
[Przesłonięcia Menedżera zawartości Pomocy](../ide/help-content-manager-overrides.md)  
[Podgląd Pomocy firmy Microsoft](../ide/microsoft-help-viewer.md)  
[Podgląd Pomocy zestawu SDK](../extensibility/internals/microsoft-help-viewer-sdk.md)