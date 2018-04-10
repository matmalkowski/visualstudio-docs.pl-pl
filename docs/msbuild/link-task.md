---
title: Link Task | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.LinkStatus
- VC.Project.VCLinkerTool.CLRUnmanagedCodeCheck
- VC.Project.VCLinkerTool.SpecifySectionAttributes
- VC.Project.VCLinkerTool.SupportNobindOfDelayLoadedDLL
- VC.Project.VCLinkerTool.MinimumRequiredVersion
- VC.Project.VCLinkerTool.PerUserRedirection
- VC.Project.VCLinkerTool.CreateHotPatchableImage
- VC.Project.VCLinkerTool.DataExecutionPrevention
- VC.Project.VCLinkerTool.TreatLinkerWarningsAsErrors
- vc.task.link
- VC.Project.VCLinkerTool.ImageHasSafeExceptionHandlers
- VC.Project.VCLinkerTool.CLRSupportLastError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), Link task
- Link task (MSBuild (Visual C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
caps.latest.revision: 12
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a5c92a6faa558445bf85637f2e51ab7fb0e7a856
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="link-task"></a>Połącz — Zadanie
Opakowuje narzędzia konsolidatora Visual C++ link.exe. Narzędzia konsolidatora łączy pliki obiektów wspólnej obiektu pliku formatu (COFF) i biblioteki, aby utworzyć plik wykonywalny (.exe) lub biblioteki dołączanej (dynamicznie DLL). Aby uzyskać więcej informacji, zobacz [opcje konsolidatora](/cpp/build/reference/linker-options).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **łącze** zadań. Większość zadań parametrów i kilka zestawów parametrów, odpowiada opcji wiersza polecenia.  
  
-   **AdditionalDependencies**  
  
     Opcjonalne **String []** parametru.  
  
     Określa listę plików wejściowych, aby dodać do polecenia.  
  
     Aby uzyskać więcej informacji, zobacz [pliki danych wejściowych łączy](/cpp/build/reference/link-input-files).  
  
-   **AdditionalLibraryDirectories**  
  
     Opcjonalne **String []** parametru.  
  
     Powoduje zastąpienie środowiska ścieżki biblioteki. Określ nazwę katalogu.  
  
     Aby uzyskać więcej informacji, zobacz [/libpath (dodatkowa Libpath)](/cpp/build/reference/libpath-additional-libpath).  
  
-   **AdditionalManifestDependencies**  
  
     Opcjonalne **String []** parametru.  
  
     Określa atrybuty, które zostaną umieszczone w `dependency` sekcji pliku manifestu.  
  
     Aby uzyskać więcej informacji, zobacz [/MANIFESTDEPENDENCY (Określ zależności manifestu)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies). Zobacz też "Publisher konfiguracji pliki" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **AdditionalOptions**  
  
     Opcjonalne **ciąg** parametru.  
  
     Listy opcji konsolidatora określone w wierszu polecenia. Na przykład **"*** / opcja 1 /option2 /option#*". Ten parametr umożliwia określenie opcji konsolidatora, które nie są reprezentowane przez inne **łącze** parametru zadania.  
  
     Aby uzyskać więcej informacji, zobacz [opcje konsolidatora](/cpp/build/reference/linker-options).  
  
-   **AddModuleNamesToAssembly**  
  
     Opcjonalne **String []** parametru.  
  
     Dodaje odwołania modułu do zestawu.  
  
     Aby uzyskać więcej informacji, zobacz [/assemblymodule (Dodaj moduł MSIL do zestawu)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).  
  
-   **AllowIsolation**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, powoduje, że system operacyjny do manifestu wyszukiwań i ładuje. Jeśli `false`, wskazuje, że biblioteki DLL są ładowane tak, jakby nie było żadnych manifestu.  
  
     Aby uzyskać więcej informacji, zobacz [/ALLOWISOLATION (wyszukiwanie Manifest)](/cpp/build/reference/allowisolation-manifest-lookup).  
  
-   **AssemblyDebug**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, emituje **DebuggableAttribute** atrybutu wraz z debugowania informacji śledzenia i wyłącza optymalizacje JIT. Jeśli `false`, emituje **DebuggableAttribute** atrybut, ale wyłącza śledzenie informacji debugowania i włącza optymalizacje JIT.  
  
     Aby uzyskać więcej informacji, zobacz [/ASSEMBLYDEBUG (Dodaj DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).  
  
-   **AssemblyLinkResource**  
  
     Opcjonalne **String []** parametru.  
  
     Tworzy łącze do zasobu .NET Framework w pliku wyjściowym; plik zasobu nie jest umieszczony w pliku wyjściowym. Określ nazwę zasobu.  
  
     Aby uzyskać więcej informacji, zobacz [/assemblylinkresource (łącze do zasobów .NET Framework)](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).  
  
-   **AttributeFileTracking**  
  
     Niejawne **logiczna** parametru.  
  
     Umożliwia głębiej pliku śledzenia do przechwytywania zachowanie przyrostowe przez łącze. Zawsze zwraca `true`.  
  
-   **BaseAddress**  
  
     Opcjonalne **ciąg** parametru.  
  
     Ustawia adres podstawowy DLL konstruowany ani programów. Określ `{address[,size] | @filename,key}`.  
  
     Aby uzyskać więcej informacji, zobacz [/BASE (adres podstawowy)](/cpp/build/reference/base-base-address).  
  
-   **BuildingInIDE**  
  
     Opcjonalne **logiczna** parametru.  
  
     Wartość true wskazuje, że program MSBuild została wywołana z IDE. W przeciwnym razie wartość wskazuje, że program MSBuild została wywołana z wiersza polecenia.  
  
     Ten parametr nie oferuje konsolidatora odpowiednik opcji.  
  
-   **CLRImageType**  
  
     Opcjonalne **ciąg** parametru.  
  
     Ustawia typ wspólnej obrazu od języka wspólnego (CLR).  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.  
  
    -   **Domyślna** - *\<Brak >*  
  
    -   **ForceIJWImage** - **/CLRIMAGETYPE:IJW**  
  
    -   **ForcePureILImage** - **/CLRIMAGETYPE:PURE**  
  
    -   **ForceSafeILImage** - **/CLRIMAGETYPE:SAFE**  
  
     Aby uzyskać więcej informacji, zobacz [clrimagetype (określenie typu z obrazu CLR)](/cpp/build/reference/clrimagetype-specify-type-of-clr-image).  
  
-   **CLRSupportLastError**  
  
     Opcjonalne **ciąg** parametru.  
  
     Zachowuje ostatni kod błędu funkcji wywołanych za pomocą mechanizmu P/Invoke.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.  
  
    -   **Enabled** - **/CLRSupportLastError**  
  
    -   **Wyłączone** - **/CLRSupportLastError:NO**  
  
    -   **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**  
  
     Aby uzyskać więcej informacji, zobacz [/CLRSUPPORTLASTERROR (Zachowaj kod ostatniego błędu dla wywołań PInvoke)](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls).  
  
-   **CLRThreadAttribute**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa jawnie atrybut wątkowości dla punktu wejścia programu CLR.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.  
  
    -   **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE: Brak**  
  
    -   **MTAThreadingAttribute** - **: MTA**  
  
    -   **STAThreadingAttribute** - **/CLRTHREADATTRIBUTE:STA**  
  
     Aby uzyskać więcej informacji, zobacz [/CLRTHREADATTRIBUTE (Ustaw CLR wątku atrybut)](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).  
  
-   **CLRUnmanagedCodeCheck**  
  
     Opcjonalne **logiczna** parametru.  
  
     Określa, czy konsolidator użyje **SuppressUnmanagedCodeSecurityAttribute** do, generowanych przez konsolidator P/Invoke, wywołań z kodu zarządzanego do natywnych bibliotek DLL.  
  
     Aby uzyskać więcej informacji, zobacz [opcji/clrunmanagedcodecheck (Dodaj SupressUnmanagedCodeSecurityAttribute)](/cpp/build/reference/clrunmanagedcodecheck-add-supressunmanagedcodesecurityattribute).  
  
-   **CreateHotPatchableImage**  
  
     Opcjonalne **ciąg** parametru.  
  
     Przygotowuje obraz do poprawiania.  
  
     Określ jedną z następujących wartości, które odpowiada opcji konsolidatora.  
  
    -   **Włączone** - **/FUNCTIONPADMIN**  
  
    -   **X86Image** - **/FUNCTIONPADMIN:5**  
  
    -   **X64Image** - **/FUNCTIONPADMIN:6**  
  
    -   **ItaniumImage** - **/FUNCTIONPADMIN:16**  
  
     Aby uzyskać więcej informacji, zobacz [/FUNCTIONPADMIN (Utwórz obraz możliwych)](/cpp/build/reference/functionpadmin-create-hotpatchable-image).  
  
-   **DataExecutionPrevention**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, wskazuje, że plik wykonywalny w celu zachowania zgodności z funkcją zapobiegania wykonywaniu danych systemu Windows.  
  
     Aby uzyskać więcej informacji, zobacz [/NXCOMPAT (zgodny z zapobieganiem wykonywaniu danych)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).  
  
-   **DelayLoadDLLs**  
  
     Opcjonalne **String []** parametru.  
  
     Powoduje, że ten parametr *opóźnienie załadowanie* dll. Określ nazwę biblioteki DLL w celu opóźnienia ładowania.  
  
     Aby uzyskać więcej informacji, zobacz [/delayload (Opóźnij importowanie ładowania)](/cpp/build/reference/delayload-delay-load-import).  
  
-   **DelaySign**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, częściowo podpisuje zestawu. Domyślna wartość to `false`.  
  
     Aby uzyskać więcej informacji, zobacz [/DelaySign (częściowo podpisać zestaw)](/cpp/build/reference/delaysign-partially-sign-an-assembly).  
  
-   **Sterownik**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określ ten parametr, aby utworzyć sterownik trybu jądra systemu Windows NT.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.  
  
    -   **NotSet** - *\<none>*  
  
    -   **Driver** - **/Driver**  
  
    -   **UpOnly** - **/DRIVER:UPONLY**  
  
    -   **WDM** - **/DRIVER:WDM**  
  
     Aby uzyskać więcej informacji, zobacz [/Driver (sterownik trybu jądra systemu Windows NT)](/cpp/build/reference/driver-windows-nt-kernel-mode-driver).  
  
-   **EmbedManagedResourceFile**  
  
     Opcjonalne **String []** parametru.  
  
     Osadza plik zasobu w zestawie. Określ nazwę pliku wymaganego zasobu. Opcjonalnie określ nazwę logiczną jest używana do załadowania zasobu, i **PRYWATNEJ** opcja, która wskazuje w manifeście zestawu, że plik zasobu jest prywatny.  
  
     Aby uzyskać więcej informacji, zobacz [/assemblyresource (Osadź zarządzany zasób)](/cpp/build/reference/assemblyresource-embed-a-managed-resource).  
  
-   **EnableCOMDATFolding**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, umożliwia identycznych sekcji comdat.  
  
     Aby uzyskać więcej informacji, zobacz `ICF[= iterations]` argument [od (optymalizacje)](/cpp/build/reference/opt-optimizations).  
  
-   **EnableUAC**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, określa, że informacje kontroli konta użytkownika (UAC) jest osadzony w manifeście program.  
  
     Aby uzyskać więcej informacji, zobacz [/MANIFESTUAC (osadza informacje UAC w manifeście)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **EntryPointSymbol**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa funkcję punktu wejścia jako adres początkowy pliku typu .exe lub DLL. Określ nazwę funkcji jako wartość parametru.  
  
     Aby uzyskać więcej informacji, zobacz [/Entry (Symbol punktu wejścia)](/cpp/build/reference/entry-entry-point-symbol).  
  
-   **FixedBaseAddress**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, tworzy program lub DLL, który może zostać załadowany tylko pod jego preferowany adres podstawowy.  
  
     Aby uzyskać więcej informacji, zobacz [Fixed (stałe adresu podstawowego)](/cpp/build/reference/fixed-fixed-base-address).  
  
-   **ForceFileOutput**  
  
     Opcjonalne **ciąg** parametru.  
  
     Informuje konsolidator, aby utworzyć plik .exe prawidłowe lub biblioteki DLL nawet wtedy, gdy symbolu występują odwołania, ale nie zdefiniowany lub jest wielokrotnie zdefiniowane.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **Enabled** - **/FORCE**  
  
    -   **MultiplyDefinedSymbolOnly** - **/FORCE:MULTIPLE**  
  
    -   **UndefinedSymbolOnly** -   **/FORCE: NIEROZPOZNANY**  
  
     Aby uzyskać więcej informacji, zobacz [/Force (Wymuszaj produkt wyjściowy pliku)](/cpp/build/reference/force-force-file-output).  
  
-   **ForceSymbolReferences**  
  
     Opcjonalne **String []** parametru.  
  
     Ten parametr informuje konsolidator, aby dodał określony symbol do tabeli symboli.  
  
     Aby uzyskać więcej informacji, zobacz [/include (Wymuszaj odwołania do symboli)](/cpp/build/reference/include-force-symbol-references).  
  
-   **FunctionOrder**  
  
     Opcjonalne **ciąg** parametru.  
  
     Ten parametr optymalizuje program przez umieszczenie określonego spakowanych funkcji (Comdat) w obrazie w ustalonej kolejności.  
  
     Aby uzyskać więcej informacji, zobacz [/order (Put funkcje w kolejności)](/cpp/build/reference/order-put-functions-in-order).  
  
-   **GenerateDebugInformation**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, tworzy informacji debugowania dla pliku .exe lub DLL.  
  
     Aby uzyskać więcej informacji, zobacz [/Debug (generowanie informacji debugowania)](/cpp/build/reference/debug-generate-debug-info).  
  
-   **GenerateManifest**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, tworzy side-by-side pliku manifestu.  
  
     Aby uzyskać więcej informacji, zobacz [/MANIFEST (Manifest zestawu Utwórz Side-by-Side)](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest).  
  
-   **GenerateMapFile**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, tworzy *pliku mapy*. Rozszerzenie nazwy pliku mapy jest .map.  
  
     Aby uzyskać więcej informacji, zobacz [/map (Generowanie Mapfile)](/cpp/build/reference/map-generate-mapfile).  
  
-   **HeapCommitSize**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa ilość pamięci fizycznej na stercie przydzielić naraz.  
  
     Aby uzyskać więcej informacji, zobacz `commit` argument [/HEAP (Ustaw rozmiar stosu)](/cpp/build/reference/heap-set-heap-size). Zobacz też **HeapReserveSize** parametru.  
  
-   **HeapReserveSize**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa alokacji sterty całkowitej pamięci wirtualnej.  
  
     Aby uzyskać więcej informacji, zobacz `reserve` argument [/HEAP (Ustaw rozmiar stosu)](/cpp/build/reference/heap-set-heap-size). Zobacz też **HeapCommitSize** parametru w tej tabeli.  
  
-   **IgnoreAllDefaultLibraries**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, informuje konsolidator, aby usunąć jedną lub więcej bibliotek domyślnych z listy bibliotek wyszukiwania podczas rozpoznawania odwołań zewnętrznych.  
  
     Aby uzyskać więcej informacji, zobacz [/nodefaultlib (Ignoruj biblioteki)](/cpp/build/reference/nodefaultlib-ignore-libraries).  
  
-   **IgnoreEmbeddedIDL**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, określa, czy jakiekolwiek atrybuty IDL w kodzie źródłowym nie powinny być przetwarzane do pliku .idl.  
  
     Aby uzyskać więcej informacji, zobacz [/ignoreidl (nie atrybutów w MIDL)](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl).  
  
-   **IgnoreImportLibrary**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, określa, że biblioteka importowana, generowana przez tą konfigurację nie będzie importowana do projektów zależnych.  
  
     Ten parametr nie odpowiada opcji konsolidatora.  
  
-   **IgnoreSpecificDefaultLibraries**  
  
     Opcjonalne **String []** parametru.  
  
     Określa jedną lub więcej nazw bibliotek domyślnych do zignorowania. Rozdzielaj wielokrotne biblioteki przy użyciu średników.  
  
     Aby uzyskać więcej informacji, zobacz [/nodefaultlib (Ignoruj biblioteki)](/cpp/build/reference/nodefaultlib-ignore-libraries).  
  
-   **ImageHasSafeExceptionHandlers**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, konsolidator generuje obraz tylko wtedy, gdy można utworzyć również tabelę obrazu bezpieczną obsługę wyjątków.  
  
     Aby uzyskać więcej informacji, zobacz [opcja/SAFESEH (obraz ma bezpieczną obsługę wyjątków)](/cpp/build/reference/safeseh-image-has-safe-exception-handlers).  
  
-   **ImportLibrary**  
  
     Nazwa biblioteki importu określone przez użytkownika, który zastępuje domyślną nazwę biblioteki.  
  
     Aby uzyskać więcej informacji, zobacz [/IMPLIB (Nazwij bibliotekę importowaną)](/cpp/build/reference/implib-name-import-library).  
  
-   **KeyContainer**  
  
     Opcjonalne **ciąg** parametru.  
  
     Kontener, który zawiera klucz dla podpisanych zestawów.  
  
     Aby uzyskać więcej informacji, zobacz [/KeyContainer (Określanie kontenera klucza, aby podpisać zestaw)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly). Zobacz też **KeyFile** parametru w tej tabeli.  
  
-   **KeyFile**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa plik, który zawiera klucz dla podpisanych zestawów.  
  
     Aby uzyskać więcej informacji, zobacz [/KeyFile (Określ klucz lub parę klucz Aby podpisać zestaw)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly). Zobacz też **KeyContainer** parametru.  
  
-   **LargeAddressAware**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, aplikacja może obsługiwać adresy większe niż 2 gigabajty.  
  
     Aby uzyskać więcej informacji, zobacz [/largeaddressaware (Obsługa dużych adresów)](/cpp/build/reference/largeaddressaware-handle-large-addresses).  
  
-   **LinkDLL**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, kompilacje bibliotek DLL pliku wyjściowego głównego.  
  
     Aby uzyskać więcej informacji, zobacz [/dll (kompilowanie biblioteki DLL)](/cpp/build/reference/dll-build-a-dll).  
  
-   **LinkErrorReporting**  
  
     Opcjonalne **ciąg** parametru.  
  
     Pozwala zapewnić wewnętrznych kompilatora informacje o błędzie (ICE) bezpośrednio do firmy Microsoft.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **NoErrorReport** -   **/errorreport: Brak**  
  
    -   **PromptImmediately** - **/ERRORREPORT:PROMPT**  
  
    -   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**  
  
    -   **SendErrorReport** -   **/errorreport: Send**  
  
     Aby uzyskać więcej informacji, zobacz [/errorreport (zgłaszaj wewnętrzne błędy konsolidatora)](/cpp/build/reference/errorreport-report-internal-linker-errors).  
  
-   **LinkIncremental**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, włącza konsolidację przyrostową.  
  
     Aby uzyskać więcej informacji, zobacz [/incremental (łącze przyrostowo)](/cpp/build/reference/incremental-link-incrementally).  
  
-   **LinkLibraryDependencies**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, określa, czy biblioteka wyników z odwoływanych projektów jest automatycznie konsolidowana.  
  
     Ten parametr nie odpowiada opcji konsolidatora.  
  
-   **LinkStatus**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, że konsolidator ma wyświetlać wskaźnik postępu, który wskazuje, jaki procent konsolidacji jest pełny.  
  
     Aby uzyskać więcej informacji, zobacz `STATUS` argument [opcję/LTCG (Generowanie kodu w czasie Link)](/cpp/build/reference/ltcg-link-time-code-generation).  
  
-   **LinkTimeCodeGeneration**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa opcje dla optymalizacji sterowanych profilem.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **Domyślna** - *\<Brak >*  
  
    -   **UseLinkTimeCodeGeneration** - **/LTCG**  
  
    -   **PGInstrument** - **/LTCG:PGInstrument**  
  
    -   **PGOptimization** - **/LTCG:PGOptimize**  
  
    -   **PGUpdate**  
  
         \- **/LTCG:PGUpdate**  
  
     Aby uzyskać więcej informacji, zobacz [opcję/LTCG (Generowanie kodu w czasie Link)](/cpp/build/reference/ltcg-link-time-code-generation).  
  
-   **ManifestFile**  
  
     Opcjonalne **ciąg** parametru.  
  
     Zmiany domyślnej nazwy pliku manifestu z określoną nazwą pliku.  
  
     Aby uzyskać więcej informacji, zobacz [/MANIFESTFILE (nazwa pliku manifestu)](/cpp/build/reference/manifestfile-name-manifest-file).  
  
-   **MapExports**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, informuje konsolidator, aby dołączał eksportowane funkcje w pliku mapy.  
  
     Aby uzyskać więcej informacji, zobacz `EXPORTS` argument [/MapInfo (obejmują informacje do Mapfile)](/cpp/build/reference/mapinfo-include-information-in-mapfile).  
  
-   **MapFileName**  
  
     Opcjonalne **ciąg** parametru.  
  
     Zmiany domyślnej nazwy pliku mapy z określoną nazwą pliku.  
  
-   **MergedIDLBaseFileName**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa nazwę pliku i rozszerzenie nazwy pliku .idl.  
  
     Aby uzyskać więcej informacji, zobacz [/idlout (nazwy wyjściowe pliki MIDL)](/cpp/build/reference/idlout-name-midl-output-files).  
  
-   **MergeSections**  
  
     Opcjonalne **ciąg** parametru.  
  
     Scala sekcje w obrazie. Określ `from-section=to-section`.  
  
     Aby uzyskać więcej informacji, zobacz [/merge (Połącz sekcje)](/cpp/build/reference/merge-combine-sections).  
  
-   **MidlCommandFile**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określ nazwę pliku, który zawiera opcje wiersza polecenia MIDL.  
  
     Aby uzyskać więcej informacji, zobacz [/MIDL (Określanie MIDL wiersza polecenia opcji)](/cpp/build/reference/midl-specify-midl-command-line-options).  
  
-   **MinimumRequiredVersion**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa minimalną wymaganą wersję podsystemu. Argumenty są liczbami dziesiętnymi z zakresu od 0 do 65 535.  
  
-   **ModuleDefinitionFile**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa nazwę [plik definicji modułu](/cpp/build/reference/module-definition-dot-def-files).  
  
     Aby uzyskać więcej informacji, zobacz [/DEF (Określ plik definicji modułu)](/cpp/build/reference/def-specify-module-definition-file).  
  
-   **MSDOSStubFileName**  
  
     Opcjonalne **ciąg** parametru.  
  
     Dołącza określony programu procedury szczątkowej MS-DOS do programu systemu Win32.  
  
     Aby uzyskać więcej informacji, zobacz [/stub (nazwa pliku klasy zastępczej MS-DOS)](/cpp/build/reference/stub-ms-dos-stub-file-name).  
  
-   **NoEntryPoint**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, określa bibliotekę DLL tylko z zasobami.  
  
     Aby uzyskać więcej informacji, zobacz [/noentry (Brak punktu wejścia)](/cpp/build/reference/noentry-no-entry-point).  
  
-   **ObjectFiles**  
  
     Niejawne **String []** parametru.  
  
     Określa pliki obiektów, które są połączone.  
  
-   **OptimizeReferences**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, eliminuje funkcje i/lub dane, które nie istnieje odwołanie.  
  
     Aby uzyskać więcej informacji, zobacz `REF` argument [od (optymalizacje)](/cpp/build/reference/opt-optimizations).  
  
-   **OutputFile**  
  
     Opcjonalne **ciąg** parametru.  
  
     Przesłania domyślną nazwę i lokalizację programu tworzonego przez konsolidatora.  
  
     Aby uzyskać więcej informacji, zobacz [/OUT (nazwa pliku wyjściowego)](/cpp/build/reference/out-output-file-name).  
  
-   **PerUserRedirection**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true` i włączono rejestrowanie produktów wyjściowych rejestru wymusza zapisuje **wpisów z HKEY_CLASSES_ROOT** do **HKEY_CURRENT_USER**.  
  
-   **PreprocessOutput**  
  
     Opcjonalne `ITaskItem[]` parametru.  
  
     Określa tablicę elementów dane wyjściowe preprocesora, które mogą być używane i emitowane przez zadania.  
  
-   **PreventDllBinding**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, wskazuje plikowi Bind.exe połączonego obrazu nie powinny być powiązane.  
  
     Aby uzyskać więcej informacji, zobacz [/ALLOWBIND (zapobiec powiązanie biblioteki DLL)](/cpp/build/reference/allowbind-prevent-dll-binding).  
  
-   **Profile**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, tworzy plik wyjściowy, który może być używany z **narzędzi wydajności** profilera.  
  
     Aby uzyskać więcej informacji, zobacz [/profile (Profiler narzędzi wydajności)](/cpp/build/reference/profile-performance-tools-profiler).  
  
-   **ProfileGuidedDatabase**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa nazwę pliku .pgd, który będzie używany do przechowywania informacji o uruchomiony program  
  
     Aby uzyskać więcej informacji, zobacz [/PGD (Określ bazę danych dla optymalizacji Profile-Guided)](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations).  
  
-   **ProgramDatabaseFile**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa nazwę bazy danych programu (PDB) tworzonego przez konsolidatora.  
  
     Aby uzyskać więcej informacji, zobacz [/PDB (Użyj bazy danych programu)](/cpp/build/reference/pdb-use-program-database).  
  
-   **RandomizedBaseAddress**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, generuje obraz wykonywalny, który może być losowo przebazowanych w czasie obciążenia za pomocą *randomizacji układu przestrzeni adresów* funkcji (ASLR) systemu Windows.  
  
     Aby uzyskać więcej informacji, zobacz [/DYNAMICBASE (randomizacji układu przestrzeni adresowej Użyj)](/cpp/build/reference/dynamicbase-use-address-space-layout-randomization).  
  
-   **RegisterOutput**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, rejestruje główny wynik tej kompilacji.  
  
-   **SectionAlignment**  
  
     Opcjonalne **całkowitą** parametru.  
  
     Określa wyrównanie każdej z sekcji w liniowej przestrzeni adresowej programu. Wartość parametru jest jednostka liczba bajtów i potęgą liczby dwa.  
  
     Aby uzyskać więcej informacji, zobacz [/align (wyrównanie sekcji)](/cpp/build/reference/align-section-alignment).  
  
-   **SetChecksum**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, ustawia sumę kontrolną w nagłówku pliku .exe.  
  
     Aby uzyskać więcej informacji, zobacz [/Release (Ustaw sumę kontrolną)](/cpp/build/reference/release-set-the-checksum).  
  
-   **ShowProgress**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa poziom szczegółowości Raporty postępu dla operacji łączenia.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **NotSet** - *\<none>*  
  
    -   **LinkVerbose** - **/VERBOSE**  
  
    -   **LinkVerboseLib** - **/VERBOSE:Lib**  
  
    -   **LinkVerboseICF** - **/VERBOSE:ICF**  
  
    -   **LinkVerboseREF** - **/VERBOSE:REF**  
  
    -   **LinkVerboseSAFESEH** - **/VERBOSE:SAFESEH**  
  
    -   **LinkVerboseCLR** - **/VERBOSE:CLR**  
  
     Aby uzyskać więcej informacji, zobacz [/verbose (Drukuj komunikaty o postępie)](/cpp/build/reference/verbose-print-progress-messages).  
  
-   **Źródeł**  
  
     Wymagane `ITaskItem[]` parametru.  
  
     Określa tablicę elementów MSBuild pliku źródłowego, które mogą być używane i emitowane przez zadania.  
  
-   **SpecifySectionAttributes**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa atrybuty sekcji. Przesłania atrybuty, które zostały określone, gdy plik .obj sekcji został skompilowany.  
  
     Aby uzyskać więcej informacji, zobacz [/Section (Określ atrybuty sekcji)](/cpp/build/reference/section-specify-section-attributes).  
  
-   **StackCommitSize**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa ilość pamięci fizycznej w każdej alokacji, gdy jest przydzielana pamięć dodatkowe.  
  
     Aby uzyskać więcej informacji, zobacz `commit` argument [/STACK (twórz stos z alokacji)](/cpp/build/reference/stack-stack-allocations).  
  
-   **StackReserveSize**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa całkowity rozmiar alokacji stosu w pamięci wirtualnej.  
  
     Aby uzyskać więcej informacji, zobacz `reserve` argument [/STACK (twórz stos z alokacji)](/cpp/build/reference/stack-stack-allocations).  
  
-   **StripPrivateSymbols**  
  
     Opcjonalne **ciąg** parametru.  
  
     Tworzy drugi plik bazy danych (PDB) program, który pomija symbole, których nie chcesz dystrybuować do klientów. Określ nazwę drugiego pliku PDB.  
  
     Aby uzyskać więcej informacji, zobacz [/pdbstripped (Usuń symbole prywatne)](/cpp/build/reference/pdbstripped-strip-private-symbols).  
  
-   **SubSystem**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa środowisko dla pliku wykonywalnego.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **NotSet** - *\<none>*  
  
    -   **Konsola** - **opcji**  
  
    -   **Windows** - **/SUBSYSTEM:WINDOWS**  
  
    -   **Native** - **/SUBSYSTEM:NATIVE**  
  
    -   **Aplikacja EFI** - **/SUBSYSTEM:EFI_APPLICATION**  
  
    -   **Sterownik usługi rozruchu interfejsu EFI** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**  
  
    -   **EFI ROM** - **/SUBSYSTEM:EFI_ROM**  
  
    -   **EFI Runtime** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**  
  
    -   **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**  
  
    -   **POSIX** - **/SUBSYSTEM:POSIX**  
  
     Aby uzyskać więcej informacji, zobacz [/Subsystem (Określ podsystem)](/cpp/build/reference/subsystem-specify-subsystem).  
  
-   **SupportNobindOfDelayLoadedDLL**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, informuje konsolidator, aby nie dołączenia powiązania tabelę adresów importu (IAT) do obrazu końcowego.  
  
     Aby uzyskać więcej informacji, zobacz `NOBIND` argument [przełącznik/DELAY (ustawienia opóźnienia importowania ładowania)](/cpp/build/reference/delay-delay-load-import-settings).  
  
-   **SupportUnloadOfDelayLoadedDLL**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, informuje funkcję pomocnicza ładowaną opóźnienia, aby wspierała jawne zwalnianie biblioteki dll.  
  
     Aby uzyskać więcej informacji, zobacz `UNLOAD` argument [przełącznik/DELAY (ustawienia opóźnienia importowania ładowania)](/cpp/build/reference/delay-delay-load-import-settings).  
  
-   **SuppressStartupBanner**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, uniemożliwia wyświetlanie wiadomości copyright i wersji, podczas uruchamiania zadania.  
  
     Aby uzyskać więcej informacji, zobacz [/nologo (Pomiń transparent początkowy) (konsolidator)](/cpp/build/reference/nologo-suppress-startup-banner-linker).  
  
-   **SwapRunFromCD**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, informuje system operacyjny, najpierw skopiować konsolidator dane wyjściowe do pliku wymiany, a następnie uruchomił obraz stamtąd.  
  
     Aby uzyskać więcej informacji, zobacz `CD` argument [/swaprun (Załaduj dane wyjściowe konsolidatora do pliku Swap)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Zobacz też **SwapRunFromNET** parametru.  
  
-   **SwapRunFromNET**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, informuje system operacyjny, najpierw skopiować konsolidator dane wyjściowe do pliku wymiany, a następnie uruchomił obraz stamtąd.  
  
     Aby uzyskać więcej informacji, zobacz `NET` argument [/swaprun (Załaduj dane wyjściowe konsolidatora do pliku Swap)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Zobacz też **SwapRunFromCD** parametru w tej tabeli.  
  
-   **TargetMachine**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa platformę docelową dla tego programu lub DLL.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **NotSet** - *\<none>*  
  
    -   **MachineARM** - **/MACHINE:ARM**  
  
    -   **MachineEBC** - **/MACHINE:EBC**  
  
    -   **MachineIA64** - **/MACHINE:IA64**  
  
    -   **MachineMIPS** - **/MACHINE:MIPS**  
  
    -   **MachineMIPS16** - **/MACHINE:MIPS16**  
  
    -   **MachineMIPSFPU** - **/MACHINE:MIPSFPU**  
  
    -   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**  
  
    -   **MachineSH4** - **/MACHINE:SH4**  
  
    -   **MachineTHUMB** - **/MACHINE:THUMB**  
  
    -   **MachineX64** - **/MACHINE:X64**  
  
    -   **MachineX86** - **/MACHINE:X86**  
  
     Aby uzyskać więcej informacji, zobacz [/Machine (Określ platformy docelowej)](/cpp/build/reference/machine-specify-target-platform).  
  
-   **TerminalServerAware**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, ustawia flagę w polu IMAGE_OPTIONAL_HEADER DllCharacteristics w obrazie programu opcjonalne nagłówki. Gdy ta flaga jest ustawiona, serwer terminali nie wprowadzić pewne zmiany do aplikacji.  
  
     Aby uzyskać więcej informacji, zobacz [/tsaware (Utwórz Terminal aplikację świadomą serwera)](/cpp/build/reference/tsaware-create-terminal-server-aware-application).  
  
-   **TrackerLogDirectory**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa katalog dziennika śledzenia.  
  
-   **TreatLinkerWarningAsErrors**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, powoduje, że plik wyjściowy nie zostanie wygenerowany, jeśli konsolidator wygeneruje ostrzeżenie.  
  
     Aby uzyskać więcej informacji, zobacz [/WX (Traktuj ostrzeżenia konsolidatora jako błędy)](/cpp/build/reference/wx-treat-linker-warnings-as-errors).  
  
-   **TurnOffAssemblyGeneration**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, tworzy obraz dla bieżącego pliku wyjściowego bez zestawu .NET Framework.  
  
     Aby uzyskać więcej informacji, zobacz [/noassembly (Utwórz moduł MSIL)](/cpp/build/reference/noassembly-create-a-msil-module).  
  
-   **TypeLibraryFile**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa nazwę pliku i rozszerzenie nazwy pliku .tlb. Określ nazwę pliku lub ścieżkę i nazwę.  
  
     Aby uzyskać więcej informacji, zobacz  [ /tlbout (nazwa. Plik biblioteki TLB)](/cpp/build/reference/tlbout-name-dot-tlb-file).  
  
-   **TypeLibraryResourceID**  
  
     Opcjonalne **całkowitą** parametru.  
  
     Określa wartość określone przez użytkownika dla biblioteki typów utworzonych przez konsolidator. Określ wartość z zakresu od 1 do 65 535.  
  
     Aby uzyskać więcej informacji, zobacz [/TLBID (Określ identyfikator zasobu dla TypeLib)](/cpp/build/reference/tlbid-specify-resource-id-for-typelib).  
  
-   **UACExecutionLevel**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa wymagany poziom wykonywania dla aplikacji, gdy jest uruchamiana z Kontrola konta użytkownika.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **AsInvoker** - `level='asInvoker'`  
  
    -   **HighestAvailable** - `level='highestAvailable'`  
  
    -   **RequireAdministrator** - `level='requireAdministrator'`  
  
     Aby uzyskać więcej informacji, zobacz `level` argument [/MANIFESTUAC (osadza informacje UAC w manifeście)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **UACUIAccess**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, aplikacja pomija poziomów ochrony interfejsu użytkownika i dyski wejściowych do systemu windows nowszej uprawnień na pulpicie, a w przeciwnym razie `false`.  
  
     Aby uzyskać więcej informacji, zobacz `uiAccess` argument [/MANIFESTUAC (osadza informacje UAC w manifeście)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).  
  
-   **UseLibraryDependencyInputs**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, wejścia do narzędzia bibliotekarza są używane zamiast pliku biblioteki samego w sobie podczas produktów wyjściowych biblioteki zależności projektów są dołączane.  
  
-   **Wersja**  
  
     Opcjonalne **ciąg** parametru.  
  
     Umieszczenie numeru wersji w nagłówku pliku .exe lub .dll. Określ "`major[.minor]`". `major` i `minor` argumenty są liczbami dziesiętnymi z zakresu od 0 do 65 535.  
  
     Aby uzyskać więcej informacji, zobacz [/Version (informacje o wersji)](/cpp/build/reference/version-version-information).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)