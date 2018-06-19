---
title: Lib — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.Name
- VC.Project.VCLibrarianTool.TreatLibWarningsAsErrors
- VC.Project.VCLibrarianTool.Verbose
- vc.task.lib
- VC.Project.VCLibrarianTool.ErrorReporting
- VC.Project.VCLibrarianTool.LinkLibraryDependencies
- VC.Project.VCLibrarianTool.LinkTimeCodeGeneration
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), LIB task
- LIB task (MSBuild (Visual C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 69dec38691969eafa92a13dea0333fbc17060354
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31574223"
---
# <a name="lib-task"></a>LIB — Zadanie
Zawijania narzędzie Microsoft 32-bitowy Library Manager lib.exe. Library Manager tworzy i którymi zarządza biblioteki plików obiektów wspólnej obiektu pliku formatu (COFF). Library Manager może tworzyć pliki eksportu i Importuj biblioteki do definicji odwołania wyeksportowane. Aby uzyskać więcej informacji, zobacz [odwołanie do biblioteki LIB](/cpp/build/reference/lib-reference) i [systemem LIB](/cpp/build/reference/running-lib).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **LIB** zadań. Większość parametrów zadania odpowiada opcji wiersza polecenia.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalDependencies**|Opcjonalne **String []** parametru.<br /><br /> Określa dodatkowe elementy do dodania do wiersza polecenia.|  
|**AdditionalLibraryDirectories**|Opcjonalne **String []** parametru.<br /><br /> Powoduje zastąpienie środowiska ścieżki biblioteki. Określ nazwę katalogu.<br /><br /> Aby uzyskać więcej informacji, zobacz [/libpath (dodatkowa Libpath)](/cpp/build/reference/libpath-additional-libpath).|  
|**AdditionalOptions**|Opcjonalne **ciąg** parametru.<br /><br /> Lista opcji lib.exe określone w wierszu polecenia. Na przykład **"*** / opcja 1 /option2 /option#*". Ten parametr umożliwia określenie opcji lib.exe, które nie są reprezentowane przez inne **LIB** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz [systemem LIB](/cpp/build/reference/running-lib).|  
|**DisplayLibrary**|Opcjonalne **ciąg** parametru.<br /><br /> Wyświetla informacje o bibliotece wyjściowej. Określ nazwę pliku, aby przekierować informacje w pliku. Określ "CON" lub nic przekierowania informacje do konsoli.<br /><br /> Ten parametr odpowiada **/LIST** opcji lib.exe.|  
|**ErrorReporting**|Opcjonalne **ciąg** parametru.<br /><br /> Określa, jak wysyłać do firmy Microsoft informacji o błędach wewnętrznych, jeśli lib.exe zakończy się niepowodzeniem w czasie wykonywania.<br /><br /> Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.<br /><br /> -   **NoErrorReport** -   **/errorreport: Brak**<br />-   **PromptImmediately** - **/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport** -   **/errorreport: Send**<br /><br /> Aby uzyskać więcej informacji, zobacz **/errorreport** opcji wiersza polecenia w [systemem LIB](/cpp/build/reference/running-lib).|  
|**ExportNamedFunctions**|Opcjonalne **String []** parametru.<br /><br /> Określa co najmniej jedną funkcję do wyeksportowania.<br /><br /> Ten parametr odpowiada **/EXPORT:** opcji lib.exe.|  
|**ForceSymbolReferences**|Opcjonalne **ciąg** parametru.<br /><br /> Wymusza lib.exe załączanie odwołań do określonego symbolu.<br /><br /> Ten parametr odpowiada **/INCLUDE:** opcji lib.exe.|  
|**IgnoreAllDefaultLibraries**|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, usuwa wszystkie domyślne biblioteki z listy bibliotek tego lib.exe wyszukuje podczas rozpoznawania odwołań zewnętrznych.<br /><br /> Ten parametr odnosi się do postaci bez parametrów **/nodefaultlib** opcji lib.exe.|  
|**IgnoreSpecificDefaultLibraries**|Opcjonalne **String []** parametru.<br /><br /> Usuwa określony bibliotek z listy bibliotek tego lib.exe wyszukuje podczas rozpoznawania odwołań zewnętrznych.<br /><br /> Ten parametr odpowiada **/nodefaultlib** opcji lib.exe pobierającej `library` argumentu.|  
|**LinkLibraryDependencies**|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, określa, czy biblioteka wyników z odwoływanych projektów jest automatycznie konsolidowana.|  
|**LinkTimeCodeGeneration**|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, określa generowanie łączonych kodów czasowych.<br /><br /> Ten parametr odpowiada **/LCTG** opcji lib.exe.|  
|**Parametru MinimumRequiredVersion**|Opcjonalne **ciąg** parametru.<br /><br /> Określa minimalną wymaganą wersję podsystemu. Określ listę rozdzielanych przecinkami liczby dziesiętne w zakresie od 0 do 65 535.|  
|**ModuleDefinitionFile**|Opcjonalne **ciąg** parametru.<br /><br /> Określa nazwę pliku definicji modułu (.def).<br /><br /> Ten parametr odpowiada **/DEF** opcji lib.exe pobierającej `filename` argumentu.|  
|**Nazwa**|Opcjonalne **ciąg** parametru.<br /><br /> Podczas tworzenia biblioteki importowanej, określa nazwę biblioteki dll, dla której jest tworzona biblioteki importu.<br /><br /> Ten parametr odpowiada **/NAME** opcji lib.exe pobierającej `filename` argumentu.|  
|**OutputFile**|Opcjonalne **ciąg** parametru.<br /><br /> Zastępuje domyślną nazwę i lokalizację programu tego lib.exe tworzy.<br /><br /> Ten parametr odpowiada **/OUT** opcji lib.exe pobierającej `filename` argumentu.|  
|**RemoveObjects**|Opcjonalne **String []** parametru.<br /><br /> Pomija określony obiekt z biblioteki wyjściowej. Lib.exe tworzy bibliotekę wyjściową, łącząc wszystkie obiekty (zarówno w plikach obiektu lub biblioteki), a następnie usuwając wszystkie obiekty, które są określone przez tę opcję.<br /><br /> Ten parametr odpowiada **lub usuwanie** opcji lib.exe pobierającej `membername` argumentu.|  
|**Źródeł**|Wymagane `ITaskItem[]` parametru.<br /><br /> Określa listę plików źródłowych, rozdzielając je spacjami.|  
|**SubSystem**|Opcjonalne **ciąg** parametru.<br /><br /> Określa środowisko dla pliku wykonywalnego. Wybór podsystemu wpływa na symbol punktu wejścia lub funkcję punktu wejścia.<br /><br /> Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.<br /><br /> -   **Konsola** - **opcji**<br />-   **Windows** - **/SUBSYSTEM:WINDOWS**<br />-   **Native** - **/SUBSYSTEM:NATIVE**<br />-   **Aplikacja EFI** - **/SUBSYSTEM:EFI_APPLICATION**<br />-   **Sterownik usługi rozruchu interfejsu EFI** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** - **/SUBSYSTEM:EFI_ROM**<br />-   **EFI Runtime** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**ReplaceThisText<br />-   **POSIX** - **/SUBSYSTEM:POSIX**<br /><br /> Aby uzyskać więcej informacji, zobacz [/Subsystem (Określ podsystem)](/cpp/build/reference/subsystem-specify-subsystem).|  
|**SuppressStartupBanner**|Opcjonalne **logiczna** parametru.<br /><br /> Jeśli `true`, uniemożliwia wyświetlanie wiadomości copyright i wersji, podczas uruchamiania zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nologo** opcji na [systemem LIB](/cpp/build/reference/running-lib).|  
|**TargetMachine**|Opcjonalne **ciąg** parametru.<br /><br /> Określa platformę docelową dla tego programu lub DLL.<br /><br /> Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.<br /><br /> -   **MachineARM** - **/MACHINE:ARM**<br />-   **MachineEBC** - **/MACHINE:EBC**<br />-   **MachineIA64** - **/MACHINE:IA64**<br />-   **MachineMIPS** - **/MACHINE:MIPS**<br />-   **MachineMIPS16** - **/MACHINE:MIPS16**<br />-   **MachineMIPSFPU** -**/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**<br />-   **MachineSH4** - **/MACHINE:SH4**<br />-   **MachineTHUMB** - **/MACHINE:THUMB**<br />-   **MachineX64** - **/MACHINE:X64**<br />-   **MachineX86** - **/MACHINE:X86**<br /><br /> Aby uzyskać więcej informacji, zobacz [/Machine (Określ platformy docelowej)](/cpp/build/reference/machine-specify-target-platform).|  
|**Katalog TrackerLogDirectory**|Opcjonalne **ciąg** parametru.<br /><br /> Określa katalog dziennika śledzenia.|  
|**TreatLibWarningAsErrors**|Opcjonalne **logiczna** parametru.<br /><br /> Jeśli `true`, powoduje, że **LIB** zadanie, aby nie generować pliku wyjściowego, jeśli lib.exe generuje ostrzeżenie. Jeśli `false`, jest generowany plik wyjściowy.<br /><br /> Aby uzyskać więcej informacji, zobacz **wx** opcji na [systemem LIB](/cpp/build/reference/running-lib).|  
|**UseUnicodeResponseFiles**|Opcjonalne **logiczna** parametru.<br /><br /> Jeśli `true`, instruuje system projektu generuje pliki odpowiedzi w kodowaniu UNICODE, gdy jest zduplikowany bibliotekarza. Określ `true` gdy pliki w projekcie posiadają ścieżki UNICODE.|  
|**Pełne**|Opcjonalne **logiczna** parametru.<br /><br /> Jeśli `true`, są wyświetlane szczegółowe informacje o postępie sesji; dotyczy to również nazw plików .obj dodawany. Informacje są wysyłane na wyjście standardowe i mogą zostać przekierowane do pliku.<br /><br /> Aby uzyskać więcej informacji, zobacz **/VERBOSE** opcji [systemem LIB](/cpp/build/reference/running-lib).|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)