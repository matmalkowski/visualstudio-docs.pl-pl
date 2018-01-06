---
title: Instalowanie aplikacji Isolated Shell | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: "40"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6672ed634ad8c8056ae372c9d1d9a3fa44b56243
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="installing-an-isolated-shell-application"></a>Instalowanie aplikacji Isolated Shell
Aby zainstalować aplikację powłoki, należy wykonać następujące kroki.  
  
-   Przygotuj rozwiązania.  
  
-   Utwórz pakiet Instalatora Windows (MSI) dla aplikacji.  
  
-   Tworzenie programu inicjującego Instalatora.  
  
 Cały kod przykładowy w tym dokumencie pochodzą z [Przykładowe wdrożenie powłoki](http://go.microsoft.com/fwlink/?LinkId=262245), który można pobrać z galerii kodu w witrynie MSDN. Przykład obejmuje wyników wykonania każdy z tych kroków.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby wykonać procedury opisane w tym temacie, następujących narzędzi musi można zainstalować na komputerze.  
  
-   Visual Studio SDK  
  
-   [Zestaw narzędzi XML Instalatora Windows](http://go.microsoft.com/fwlink/?LinkId=82720) wersji 3,6  
  
 Przykład wymaga również Microsoft Visualization and Modeling SDK, która wymaga powłoki nie wszystkie.  
  
## <a name="preparing-your-solution"></a>Przygotowywanie rozwiązania  
 Domyślnie powłoki szablony kompilacji do pakietów VSIX, ale to zachowanie jest przeznaczony przede wszystkim na potrzeby debugowania. Podczas wdrażania aplikacji powłoki, należy użyć pakiety MSI zezwolić na dostęp do rejestru i ponownego uruchomienia podczas instalacji. W celu przygotowania aplikacji do wdrożenia MSI, wykonaj następujące czynności.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Aby przygotować aplikację powłoki wdrożenia MSI  
  
1.  Edytuj każdego pliku .vsixmanifest w rozwiązaniu.  
  
     W `Identifier` elementu, Dodaj `InstalledByMSI` elementu i `SystemComponent` elementu, a następnie ustaw wartości `true`.  
  
     Te elementy uniemożliwić spróbujesz zainstalować składniki i użytkownika z je odinstalować przy użyciu Instalatora VSIX **rozszerzenia i aktualizacje** okno dialogowe.  
  
2.  Dla każdego projektu, który zawiera VSIX manifest edytować zadania kompilacji do wyjściowego zawartość do lokalizacji, w którym zostanie zainstalowany z pliku MSI. W danych wyjściowych kompilacji uwzględnić manifestu VSIX, ale nie tworzy plik .vsix.  
  
## <a name="creating-an-msi-for-your-shell"></a>Tworzenie pliku MSI dla powłoki  
 Aby utworzyć pakiet MSI, firma Microsoft zaleca się używanie [zestaw narzędzi XML Instalatora Windows](http://go.microsoft.com/fwlink/?LinkId=82720) ponieważ daje większą elastyczność niż standardowe projektu Instalatora.  
  
 W pliku Product.wxs Ustaw bloki wykrywania i układ składników powłoki.  
  
 Następnie należy utworzyć wpisy rejestru, zarówno w pliku reg dla rozwiązania i ApplicationRegistry.wxs.  
  
### <a name="detection-blocks"></a>Bloki wykrywania  
 Blok wykrywania składa się z `Property` element, który określa warunek wstępny, aby wykryć i `Condition` element, który określa komunikat, aby zwrócić, jeśli wymagań wstępnych nie jest zainstalowana na komputerze. Na przykład aplikacji powłoki wymaga programu Microsoft Visual Studio Shell pakietu redystrybucyjnego i blok wykrywanie będzie przypominać następujący kod znaczników.  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>Układ składników powłoki  
 Należy dodać elementy do identyfikowania strukturę katalogu docelowego i składniki do zainstalowania.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Aby ustawić układ składników powłoki  
  
1.  Utwórz hierarchię `Directory` elementy do reprezentowania wszystkich katalogów można utworzyć w systemie plików na komputerze docelowym, jak przedstawiono na poniższym przykładzie.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     Te katalogi są określane przez `Id` gdy są określone pliki, które muszą zostać zainstalowane.  
  
2.  Identyfikacja składników wymagających powłoka i aplikacji powłoki, jak przedstawiono na poniższym przykładzie.  
  
    > [!NOTE]
    >  Niektóre elementy mogą odwoływać się do definicji w innych plikach .wxs.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1.  `ComponentRef` Element odwołuje się do innego pliku .wxs identyfikujący pliki, które wymaga bieżącego składnika. Na przykład GeneralProfile ma następującą definicję w HelpAbout.wxs.  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         `DirectoryRef` Element określa, gdzie te pliki na komputerze użytkownika. `Directory` Element określa, czy ma być zainstalowany w podkatalogu, a każdy `File` — element reprezentuje plik wbudowane lub istnieje jako część rozwiązania i określa, gdzie ten plik znajduje się podczas tworzenia pliku MSI.  
  
    2.  `ComponentGroupRef` Element odwołuje się do grupy innych składników (lub składników i grup składników). Na przykład `ComponentGroupRef` w obszarze ApplicationGroup jest zdefiniowany w następujący sposób w Application.wxs.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  Wymagane są zależności dla aplikacji Shell (izolowany): DebuggerProxy, MasterPkgDef, zasobów (szczególnie plik .winprf), aplikacji i PkgDefs.  
  
### <a name="registry-entries"></a>Wpisy rejestru  
 Szablon projektu Shell (izolowany) zawiera *ProjectName*pliku reg dla kluczy rejestru do scalenia w instalacji. Te wpisy rejestru musi być częścią MSI dla instalacji i celów oczyszczania. Pasujące bloki rejestru należy utworzyć również w ApplicationRegistry.wxs.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Aby zintegrować wpisy rejestru do MSI  
  
1.  W **dostosowywania powłoki** folder, otwórz *ProjectName*. reg.  
  
2.  Zastąp wszystkie wystąpienia tokenu $ $RootFolder ze ścieżką katalogu docelowego instalacji.  
  
3.  Dodawanie innych wpisów rejestru wymagane przez aplikację.  
  
4.  Otwórz ApplicationRegistry.wxs.  
  
5.  Dla każdego wpisu rejestru w *ProjectName*reg, Dodaj blok rejestru odpowiednich jako poniższych przykładach.  
  
    |*ProjectName*reg.|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= "Obiekt PhotoStudio DTE"|\<Identyfikator klucza rejestru = głównego "DteClsidRegKey" = "HKCR" klucz = "$(var.) DteClsidRegKey) "Akcja ="createAndRemoveOnUninstall"><br /><br /> \<Typ RegistryValue = 'string' Name = "@" wartość = "$(var.) Obiekt ShortProductName) DTE "/ ><br /><br /> \</ RegistryKey >|  
    |[HKEY_CLASSES_ROOT\CLSID\\\LocalServer32 {bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= "$RootFolder$\PhotoStudio.exe"|\<Identyfikator klucza rejestru = głównego "DteLocSrv32RegKey" = "HKCR" klucz = "$(var.) \LocalServer32 DteClsidRegKey) "Akcja ="createAndRemoveOnUninstall"><br /><br /> \<Typ RegistryValue = 'string' Name = "@" wartość = "[INSTALLDIR] $(var.) ShortProductName) .exe "/ ><br /><br /> \</ RegistryKey >|  
  
     W tym przykładzie Var.DteClsidRegKey rozpoznaje do klucza rejestru w górnym wierszu. Var.ShortProductName jest rozpoznawana jako `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Tworzenie programu inicjującego Instalatora  
 Twoje ukończone MSI zainstaluje tylko wtedy, gdy wszystkie wstępnie wymagane składniki są najpierw zainstalowany. Aby ułatwić środowisko użytkownika końcowego, należy utworzyć program instalacyjny, który zbiera i instaluje wszystkie wymagania wstępne, przed instalacją aplikacji. W celu zapewnienia pomyślnej instalacji, należy wykonać następujące operacje:  
  
-   Wymuś instalacji przez administratora.  
  
-   Wykryj, czy jest zainstalowany program Visual Studio Shell (izolowany).  
  
-   Jeden lub oba instalatorów powłoki są uruchamiane w kolejności.  
  
-   Obsługuje żądania ponownego uruchomienia.  
  
-   Uruchom z pliku MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>Wymuszanie instalacji przez administratora  
 Ta procedura wymaganego do włączenia usługi Instalatora, aby uzyskać dostępu do katalogów wymaganych, takich jak pliki \Program\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Aby wymusić instalację przez administratora  
  
1.  Otwórz menu skrótów projektu Instalatora, a następnie wybierz pozycję **właściwości**.  
  
2.  W obszarze **pliku konfiguracji właściwości/konsolidatora/Manifest**ustaw **poziom wykonywania UAC** do **requireAdministrator**.  
  
     Ta właściwość umieszcza atrybut, który wymaga program można uruchomić jako Administrator do osadzonego pliku manifestu.  
  
### <a name="detecting-shell-installations"></a>Wykrywania instalacji powłoki  
 Aby ustalić, czy należy zainstalować program Visual Studio Shell (izolowany), należy najpierw określić, czy jest ona już zainstalowana, sprawdzając wartość rejestru HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
>  Te wartości są również odczytywane przez blok wykrywania powłoki w Product.wxs.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder Określa lokalizację, w którym został zainstalowany program Visual Studio Shell i plików można sprawdzić.  
  
 Na przykład sposobu wykrywania instalacji powłoki zobacz `GetProductDirFromReg` funkcja Utilities.cpp próby wdrożenia powłoki.  
  
 Jeśli jeden lub oba programu Visual Studio powłoki, który wymaga pakietu nie jest zainstalowany na komputerze, należy dodać je do listy Składniki do zainstalowania. Na przykład zobacz `ComponentsPage::OnInitDialog` funkcja ComponentsPage.cpp próby wdrożenia powłoki.  
  
### <a name="running-the-shell-installers"></a>Uruchomiona instalatorów powłoki  
 Aby uruchomić instalatorów powłoki, należy wywołać pakiety redystrybucyjne programu Visual Studio Shell przy użyciu poprawne argumenty wiersza polecenia. Co najmniej, należy użyć argumenty wiersza polecenia **/norestart/q** i obserwować kodu powrotnego w celu ustalenia, co należy zrobić dalej. W poniższym przykładzie uruchamiane Shell (izolowany) do dystrybucji.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Uruchomiona instalatorów pakiet języka powłoki  
 Jeśli okaże się zamiast tego, czy powłoki lub powłoki zostały zainstalowane i po prostu muszą pakiet językowy, można instalować pakiety językowe, jak w poniższym przykładzie pokazano.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Odszyfrowanie wartości zwracane  
 W niektórych systemach operacyjnych instalacja programu Visual Studio Shell (izolowany) będzie wymagać ponownego uruchomienia komputera. Ten warunek może będzie określany przez kod powrotny wywołania `ExecCmd`.  
  
|Wartość zwracana|Opis|  
|------------------|-----------------|  
|ERROR_SUCCESS|Instalacja została ukończona. Teraz można zainstalować aplikacji.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Instalacja została ukończona. Aplikację można zainstalować po ponownym uruchomieniu komputera.|  
|3015|Instalacja jest w toku. W celu kontynuowania instalacji jest wymagane ponowne uruchomienie komputera.|  
  
### <a name="handling-restarts"></a>Obsługa ponownego uruchomienia  
 Po uruchomieniu Instalatora powłoki przy użyciu **/norestart** , zostanie określony argument nie jego ponownego uruchomienia komputera lub poproś o ponownego uruchomienia komputera. Jednak może być wymagane ponowne uruchomienie i należy upewnić się, że Instalator programu będzie kontynuowane po ponownym uruchomieniu komputera.  
  
 Aby poprawnie obsłużyć zostanie ponownie uruchomiony, upewnij się, że tylko jeden program instalacyjny jest zestaw wznowić i poprawnie obsługiwane wznowienie procesu.  
  
 Zwracany jest ERROR_SUCCESS_REBOOT_REQUIRED lub 3015 kodu należy ponownie uruchomić komputer, przed kontynuowaniem instalacji.  
  
 Do obsługi ponownego uruchomienia, wykonaj następujące akcje:  
  
-   Wartość rejestru, aby wznowić instalację podczas uruchamiania systemu Windows.  
  
-   Podwójne uruchomić program inicjujący.  
  
-   Usuń klucz ResumeData Instalatora powłoki.  
  
-   Ponowne uruchomienie systemu Windows.  
  
-   Resetowanie ścieżki start MSI.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Ustawienie rejestru, aby wznowić instalację podczas uruchamiania systemu Windows  
 Klucz rejestru HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ wykonuje podczas uruchamiania systemu z uprawnieniami administracyjnymi i następnie usuwane. HKEY_CURRENT_USER zawiera podobne klucza, ale działa jako zwykłego użytkownika i nie jest odpowiednie dla instalacji. Można wznowić instalację, ustawiając wartość ciągu w kluczu RunOnce, która wywołuje Instalatorem. Firma Microsoft zaleca jednak wywołać Instalatora przy użyciu **i ponownym** lub podobny parametr, aby powiadomić aplikację, że trwa wznawianie zamiast uruchamiania. Możesz również uwzględnić parametry, aby wskazać, gdzie są w procesie instalacji, co jest szczególnie przydatne w przypadku instalacji, które mogą wymagać wielokrotne ponowne uruchomienie.  
  
 W poniższym przykładzie przedstawiono wartości klucza rejestru RunOnce wznawiania instalacji.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Instalowanie podwójne ponownego uruchomienia programu inicjującego  
 Jeśli Instalator jest używana bezpośrednio z RunOnce, nie będzie można całkowicie załadować pulpitu. Aby udostępnić pełny interfejs użytkownika, należy utworzyć inne uruchomienie Instalatora i kończyć wystąpienie RunOnce.  
  
 Instalator musi być wykonywany ponownie uzyska odpowiednie uprawnienia, a musi nadać wystarczających informacji, aby wiedzieć, gdzie został zatrzymany przed ponownym uruchomieniem, jak przedstawiono na poniższym przykładzie.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Usuwanie klucza ResumeData Instalatora powłoki  
 Instalator powłoki Ustawia klucz rejestru HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData z danymi, aby wznowić instalację po ponownym uruchomieniu. Ponieważ wznawia aplikacji, nie Instalatora powłoki usunąć tego klucza rejestru, jak przedstawiono na poniższym przykładzie.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Ponowne uruchomienie systemu Windows  
 Po ustawieniu wymagane klucze rejestru, można ponownie uruchomić system Windows. Poniższy przykład przedstawia wywoływanie polecenia ponownego uruchomienia dla różnych systemów operacyjnych Windows.  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>Resetowanie Start ścieżka pliku msi  
 Przed ponownym uruchomieniem bieżący katalog jest lokalizacji programu Instalatora, ale po ponownym uruchomieniu, lokalizacja staje się folderze System32. Program Instalator powinni resetować bieżącego katalogu przed każdym wywołaniu MSI, jak przedstawiono na poniższym przykładzie.  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>Uruchomienie aplikacji MSI  
 Po powrocie ERROR_SUCCESS Instalator programu Visual Studio Shell MSI można uruchomić aplikacji. Ponieważ program Instalator udostępnia interfejs użytkownika, należy uruchomić z pliku MSI w trybie cichym (**/q**) i z rejestrowaniem (**/L**), jak pokazano na poniższym przykładzie.  
  
```cpp  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Tworzenie podstawowej aplikacji Isolated Shell](walkthrough-creating-a-basic-isolated-shell-application.md)