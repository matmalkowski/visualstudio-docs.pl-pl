---
title: "CL — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), CL task
- CL task (MSBuild (Visual C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
caps.latest.revision: "18"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ffd317643b7ea1bfbf97bce6d533a76fd7bf1509
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cl-task"></a>CL — Zadanie
Zawijania narzędzie kompilatora Visual C++ cl.exe. Kompilator generuje pliki wykonywalne (.exe), pliki biblioteki dołączanej (dynamicznie dll) lub plików kodu modułu (modułu .netmodule). Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](/cpp/build/reference/compiler-options).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **CL** zadań. Większość zadań parametrów i kilka zestawów parametrów, odpowiada opcji wiersza polecenia.  
  
-   **AdditionalIncludeDirectories**  
  
     Opcjonalny parametr typu String [].  
  
     Dodaje katalog do listy katalogów, które są wyszukiwane pliki nagłówkowe.  
  
     Aby uzyskać więcej informacji, zobacz [/I (dodatkowe katalogi dołączenia)](/cpp/build/reference/i-additional-include-directories).  
  
-   **AdditionalOptions**  
  
     Opcjonalny parametr typu String.  
  
     Listę opcji wiersza polecenia. Na przykład "/*opcja 1* /*option2* /*opcji #*". Ten parametr umożliwia określenie opcji wiersza polecenia, które nie są reprezentowane przez innych parametrów zadania.  
  
     Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](/cpp/build/reference/compiler-options).  
  
-   **AdditionalUsingDirectories**opcjonalny ciąg [] parametru.  
  
     Określa, że kompilator będzie wyszukiwania można rozpoznać odwołania do pliku przekazany do katalogu **#using** dyrektywy.  
  
     Aby uzyskać więcej informacji, zobacz [/AI (Określ katalogi metadanych)](/cpp/build/reference/ai-specify-metadata-directories).  
  
-   **AlwaysAppend**  
  
     Opcjonalny parametr typu String.  
  
     Ciąg która zawsze pobiera emitowane w wierszu polecenia. Jego wartość domyślna to "**/c**".  
  
-   **AssemblerListingLocation**  
  
     Tworzy plik listy kodu zestawu.  
  
     Aby uzyskać więcej informacji, zobacz **/Fa** opcji [/FA, /Fa (wyświetlanie listy plików)](/cpp/build/reference/fa-fa-listing-file).  
  
-   **AssemblerOutput**  
  
     Opcjonalny parametr typu String.  
  
     Tworzy plik listy kodu zestawu.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **NoListing** - *\<Brak >*  
  
    -   **AssemblyCode** - **/FA**  
  
    -   **AssemblyAndMachineCode** -   **/FAC**  
  
    -   **AssemblyAndSourceCode** -   **/FAS**  
  
    -   **Wszystkie** -   **/facs**  
  
     Aby uzyskać więcej informacji, zobacz **/FA**, **/FAC**, **/FAS**, i **/facs** opcje w [/FA, /Fa (wyświetlanie listy plików)](/cpp/build/reference/fa-fa-listing-file).  
  
-   **BasicRuntimeChecks**  
  
     Opcjonalny parametr typu String.  
  
     Włącza i wyłącza funkcję Sprawdzanie błędów czasu wykonywania w połączeniu z [runtime_checks](/cpp/preprocessor/runtime-checks) pragma.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **Domyślna** -                          *\<Brak >*  
  
    -   **StackFrameRuntimeCheck** - **rtcs**  
  
    -   **UninitializedLocalUsageCheck** - **rtcu**  
  
    -   **EnableFastChecks** -                          **rtc1**  
  
     Aby uzyskać więcej informacji, zobacz [/RTC (błąd czasu wykonywania sprawdza)](/cpp/build/reference/rtc-run-time-error-checks).  
  
-   **BrowseInformation**  
  
     Opcjonalny parametr Boolean.  
  
     Jeśli `true`, tworzy plik informacji o przeglądaniu.  
  
     Aby uzyskać więcej informacji, zobacz **/FR** opcji [/FR, /Fr (Utwórz. Plik SBR)](/cpp/build/reference/fr-fr-create-dot-sbr-file).  
  
-   **BrowseInformationFile**  
  
     Opcjonalny parametr typu String.  
  
     Określa nazwę pliku dla pliku informacyjnego przeglądarki.  
  
     Aby uzyskać więcej informacji, zobacz **BrowseInformation** parametru w tej tabeli, a także zobacz [/FR, /Fr (Utwórz. Plik SBR)](/cpp/build/reference/fr-fr-create-dot-sbr-file).  
  
-   **BufferSecurityCheck**  
  
     Opcjonalny parametr Boolean.  
  
     Jeśli `true`, wykrywa niektóre przepełnienia buforu, które zastąpić adres zwrotny wspólnej technika wykorzystania kodu, który nie obsługuje wymuszania ograniczenia rozmiaru buforu.  
  
     Aby uzyskać więcej informacji, zobacz [/GS (Sprawdzanie zabezpieczeń bufora)](/cpp/build/reference/gs-buffer-security-check).  
  
-   **BuildingInIDE**  
  
     Opcjonalny parametr Boolean.  
  
     Jeśli `true`, oznacza to, że **MSBuild** jest wywoływany przez IDE. W przeciwnym razie **MSBuild** jest wywoływana w wierszu polecenia.  
  
-   **CallingConvention**  
  
     Opcjonalny parametr typu String.  
  
     Określa konwencję wywołania, określa kolejność, w którym funkcja argumenty są przenoszone na stosie, czy funkcja wywołujący lub wywołana funkcja usuwa argumenty ze stosu na końcu wywołanie, i Konwencji dekoracji nazwa który Kompilator używa do identyfikowania poszczególnych funkcji.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **Cdecl** - **/Gd**  
  
    -   **FastCall** -                          **gr**  
  
    -   **StdCall** -                          **GZ**  
  
     Aby uzyskać więcej informacji, zobacz [/Gd, / GR, GV, /Gz (Konwencja wywoływania)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).  
  
-   **CompileAs**  
  
     Opcjonalny parametr typu String.  
  
     Określa, czy należy skompilować plik wejściowy jako plik źródłowy języka C lub C++.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **Domyślna** - *\<Brak >*  
  
    -   **CompileAsC** -   **/TC**  
  
    -   **CompileAsCpp** - **/TP**  
  
     Aby uzyskać więcej informacji, zobacz [/TC, / TP, / TC, /TP (Określ źródłowy plik typ)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).  
  
-   **CompileAsManaged**  
  
     Opcjonalny parametr typu String.  
  
     Umożliwia aplikacji i składników można używać funkcji z środowisko uruchomieniowe języka wspólnego (CLR).  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **FALSE** - *\<Brak >*  
  
    -   **wartość true,** -   **/CLR**  
  
    -   **Czysty** -   **/CLR: pure**  
  
    -   **Bezpieczne** -   **/CLR: Safe**  
  
    -   **OldSyntax** - **: oldsyntax**  
  
     Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](/cpp/build/reference/clr-common-language-runtime-compilation).  
  
-   **CreateHotpatchableImage**  
  
     Opcjonalny parametr Boolean.  
  
     Jeśli `true`, informuje kompilator, aby przygotować obraz dla *poprawiania*. Tego parametru zapewnia, że pierwsza instrukcja każdej funkcji jest dwubajtowa, co jest wymagane do poprawiania.  
  
     Aby uzyskać więcej informacji, zobacz [/hotpatch (Utwórz obraz możliwych)](/cpp/build/reference/hotpatch-create-hotpatchable-image).  
  
-   **DebugInformationFormat**  
  
     Opcjonalny parametr typu String.  
  
     Wybiera typ informacji o debugowaniu stworzonej dla Twojego programu oraz czy te informacje są przechowywane w plikach obiektu (.obj) lub w bazie danych programu (PDB).  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **OldStyle** -   **/z7**  
  
    -   **ProgramDatabase** -   **/zi**  
  
    -   **EditAndContinue** -   **/zi**  
  
     Aby uzyskać więcej informacji, zobacz [/z7, / zi, /ZI (Format informacji debugowania)](/cpp/build/reference/z7-zi-zi-debug-information-format).  
  
-   **DisableLanguageExtensions**  
  
     Opcjonalny parametr Boolean.  
  
     Jeśli **true**, informuje kompilator, aby emitować błąd dotyczące konstrukcji języka, które nie są zgodne z ANSI C lub ANSI C++.  
  
     Aby uzyskać więcej informacji, zobacz **/Za** opcji [/Za, /Ze (Wyłącz rozszerzenia językowe)](/cpp/build/reference/za-ze-disable-language-extensions).  
  
-   **DisableSpecificWarnings**  
  
     Opcjonalny parametr typu String [].  
  
     Wyłącza numerów ostrzeżeń, które są określone w postaci listy rozdzielanej średnikami.  
  
     Aby uzyskać więcej informacji, zobacz `/wd` opcji [/w, /W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, / Wall, /wd, / możemy /wo, /Wv, wx (poziom ostrzegawczy)](/cpp/build/reference/compiler-option-warning-level).  
  
-   **EnableEnhancedInstructionSet**  
  
     Opcjonalny parametr typu String.  
  
     Określa architektury dla generowania kodu, który używa Streaming SIMD Extensions (SSE) i instrukcje Streaming SIMD Extensions 2 (SSE2).  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **StreamingSIMDExtensions** - **/arch:SSE**  
  
    -   **StreamingSIMDExtensions2** - **SSE2**  
  
     Aby uzyskać więcej informacji, zobacz [/arch (x86)](/cpp/build/reference/arch-x86).  
  
-   **EnableFiberSafeOptimizations**  
  
     Opcjonalny parametr Boolean.  
  
     Jeśli `true`, obsługa bezpieczeństwa włókien danych przydzielone za pomocą statycznego magazynu wątków lokalnych, czyli danych przydzielone za pomocą `__declspec(thread)`.  
  
     Aby uzyskać więcej informacji, zobacz [/GT (Obsługa włókien magazynu wątków lokalnych)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).  
  
-   **EnablePREfast**  
  
     Opcjonalny parametr Boolean.  
  
     Jeśli `true`, Włącz analizę kodu.  
  
     Aby uzyskać więcej informacji, zobacz [/ analyze (analiza kodu)](/cpp/build/reference/analyze-code-analysis).  
  
-   **ErrorReporting**  
  
     Opcjonalny parametr typu String.  
  
     Pozwala zapewnić wewnętrznych kompilatora informacje o błędzie (ICE) bezpośrednio do firmy Microsoft. Domyślnie to ustawienie w kompilacjach IDE **monitu** i ustawienie w kompilacji z wiersza polecenia jest **kolejki**.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **Brak** -   **/errorreport: Brak**  
  
    -   **Wiersz** - **/errorReport:prompt**  
  
    -   **Kolejka** - **/errorReport:queue**  
  
    -   **Wyślij** -   **/errorreport: Send**  
  
     Aby uzyskać więcej informacji, zobacz [/errorreport (zgłaszaj wewnętrzne błędy kompilatora)](/cpp/build/reference/errorreport-report-internal-compiler-errors).  
  
-   **ExceptionHandling**  
  
     Opcjonalny parametr typu String.  
  
     Określa model obsługi wyjątków, aby używane przez kompilator.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **FALSE** - *\<Brak >*  
  
    -   **Asynchroniczne** -   **/eha**  
  
    -   **Synchronizacja** -   **/ehsc**  
  
    -   **SyncCThrow** -   **/EHS**  
  
     Aby uzyskać więcej informacji, zobacz [/EH (Model obsługi wyjątku)](/cpp/build/reference/eh-exception-handling-model).  
  
-   **ExpandAttributedSource**  
  
     Opcjonalny parametr Boolean.  
  
     Jeśli `true`, tworzy pliku listy, która została rozszerzona atrybuty wstrzykiwane do pliku źródłowego.  
  
     Aby uzyskać więcej informacji, zobacz [/Fx (scalania wstrzyknięcie kodu)](/cpp/build/reference/fx-merge-injected-code).  
  
-   **FavorSizeOrSpeed**  
  
     Opcjonalny parametr typu String.  
  
     Określa, czy preferować rozmiar czy prędkość kodu.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **Ani** - *\<Brak >*  
  
    -   **Rozmiar** -   **/OS**  
  
    -   **Szybkość** - **/Ot**  
  
     Aby uzyskać więcej informacji, zobacz [/OS, /Ot (Preferuj mały kod, Preferuj szybki kod)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).  
  
-   **FloatingPointExceptions**  
  
     Opcjonalny parametr Boolean.  
  
     Jeśli `true`, umożliwia modelu niezawodnej zmiennoprzecinkowych wyjątków. Wyjątki będą zgłaszane natychmiast po ich wygenerowaniu.  
  
     Aby uzyskać więcej informacji, zobacz /**fp: except** opcji [/FP (Określ zachowanie Floating-Point)](/cpp/build/reference/fp-specify-floating-point-behavior).  
  
-   **FloatingPointModel**  
  
     Opcjonalny parametr typu String.  
  
     Ustawia wartość zmiennoprzecinkowa punktu modelu.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **Dokładne** -   **/FP: precise**  
  
    -   **Ściśle** -   **/FP: strict**  
  
    -   **Szybkie** - **Fast**  
  
     Aby uzyskać więcej informacji, zobacz [/fp (określenie zachowania Floating-Point)](/cpp/build/reference/fp-specify-floating-point-behavior).  
  
-   **ForceConformanceInForLoopScope**  
  
     Opcjonalny parametr Boolean.  
  
     Jeśli `true`, implementuje standardowego zachowania C++ w [dla](/cpp/cpp/for-statement-cpp) pętli, które używają rozszerzenia Microsoft ([/Ze](/cpp/build/reference/za-ze-disable-language-extensions)).  
  
     Aby uzyskać więcej informacji, zobacz [/Zc: forscope (Wymuszaj zgodność w zakresie pętli for)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).  
  
-   **ForcedIncludeFiles**  
  
     Opcjonalne `String[]` parametru.  
  
     Powoduje, że preprocesora do przetworzenia jeden lub więcej plików określony nagłówek.  
  
     Aby uzyskać więcej informacji, zobacz [/FI (nazwij wymuszone obejmują plik)](/cpp/build/reference/fi-name-forced-include-file).  
  
-   **ForcedUsingFiles**  
  
     Opcjonalne **String []** parametru.  
  
     Powoduje, że preprocesora przetworzyć jednego lub więcej określonych **#using** plików.  
  
     Aby uzyskać więcej informacji, zobacz [/FU (nazwij wymuszone #using)](/cpp/build/reference/fu-name-forced-hash-using-file).  
  
-   **FunctionLevelLinking**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, umożliwia kompilatorowi pakowanie indywidualnych funkcji w formę spakowanych funkcji (Comdat).  
  
     Aby uzyskać więcej informacji, zobacz [/Gy (Włącz funkcję łączenia na poziomie)](/cpp/build/reference/gy-enable-function-level-linking).  
  
-   **GenerateXMLDocumentationFiles**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, powoduje, że kompilator, aby przetworzyć dokumentacji komentarzy w kodu pliki źródłowe i aby utworzyć plik .xdc dla każdego źródła kodu plik, który ma komentarzy do dokumentacji.  
  
     Aby uzyskać więcej informacji, zobacz [/doc (przetwarzanie komentarzy dokumentacji) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Zobacz też **XMLDocumentationFileName** parametru w tej tabeli.  
  
-   **IgnoreStandardIncludePath**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, zabezpiecza kompilator przed wyszukiwaniem dołączonych plików w katalogach określonych w zmiennych środowiskowych PATH lub INCLUDE.  
  
     Aby uzyskać więcej informacji, zobacz [/X (Ignoruj standardowe ścieżki dołączanych plików)](/cpp/build/reference/x-ignore-standard-include-paths).  
  
-   **InlineFunctionExpansion**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa poziom rozwijania funkcji śródwierszowych dla kompilacji.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **Domyślna** - *\<Brak >*  
  
    -   **Wyłączone** - **/Ob0**  
  
    -   **OnlyExplicitInline** - **/Ob1**  
  
    -   **AnySuitable** -   **/ob2**  
  
     Aby uzyskać więcej informacji, zobacz [/Ob (rozszerzenie funkcji wbudowanej)](/cpp/build/reference/ob-inline-function-expansion).  
  
-   **Intrinsicfunctions —**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, zastępuje niektórych funkcji wywołania z wewnętrznych lub w przeciwnym razie szybsze specjalne formy funkcji pomagających w aplikacji.  
  
     Aby uzyskać więcej informacji, zobacz [/Oi (Generuj funkcje wewnętrzne)](/cpp/build/reference/oi-generate-intrinsic-functions).  
  
-   **MinimalRebuild**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, umożliwia minimalną ponowną kompilację, która określa, czy pliki źródłowe C++, które zawierają zmienione C++ klasy definicje (przechowywane w plikach nagłówków (.h)) musi być ponownie kompilowane.  
  
     Aby uzyskać więcej informacji, zobacz [/GM ponowną (Włącz minimalnego odbudować)](/cpp/build/reference/gm-enable-minimal-rebuild).  
  
-   **MultiProcessorCompilation**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, użycie wielu procesorów do skompilowania. Ten parametr tworzy proces dla każdego procesora skuteczne na tym komputerze.  
  
     Aby uzyskać więcej informacji, zobacz [/MP (kompilacja z wieloma procesami)](/cpp/build/reference/mp-build-with-multiple-processes). Zobacz też **ProcessorNumber** parametru w tej tabeli.  
  
-   **ObjectFileName**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa nazwę pliku obiektu (.obj) lub katalog do użycia zamiast domyślnej.  
  
     Aby uzyskać więcej informacji, zobacz [/Fo (nazwa pliku obiektu)](/cpp/build/reference/fo-object-file-name).  
  
-   **ObjectFiles**  
  
     Opcjonalne **String []** parametru.  
  
     Lista plików obiektów.  
  
-   **OmitDefaultLibName**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, pomija domyślną nazwę biblioteki wykonawcze języka C z pliku obiektu (.obj). Domyślnie kompilator umieszcza nazwę biblioteki w pliku obj. przekierować konsolidator odpowiedniej biblioteki.  
  
     Aby uzyskać więcej informacji, zobacz [/Zl (Pomiń domyślną nazwę biblioteki)](/cpp/build/reference/zl-omit-default-library-name).  
  
-   **OmitFramePointers**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, pomija tworzenie wskaźników ramek na stosie wywołań.  
  
     Aby uzyskać więcej informacji, zobacz [/Oy (pominięcie wskaźnika ramki)](/cpp/build/reference/oy-frame-pointer-omission).  
  
-   **OpenMPSupport**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, powoduje, że kompilator przetworzyć klauzule OpenMP i dyrektywy.  
  
     Aby uzyskać więcej informacji, zobacz [/OpenMP (Włącz obsługę OpenMP 2.0)](/cpp/build/reference/openmp-enable-openmp-2-0-support).  
  
-   **Optymalizacja**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa różne optymalizacje kodu szybkość i rozmiaru.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **Wyłączone** - **/Od**  
  
    -   **MinSpace** -   **/O1**  
  
    -   **MaxSpeed** -   **/O2**  
  
    -   **Pełna** - **OX**  
  
     Aby uzyskać więcej informacji, zobacz [/O opcje (Optymalizuj kod)](/cpp/build/reference/o-options-optimize-code).  
  
-   **PrecompiledHeader**  
  
     Opcjonalne **ciąg** parametru.  
  
     Utwórz lub przy użyciu pliku prekompilowanego nagłówka (.pch) podczas kompilacji.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **NotUsing** - *\<Brak >*  
  
    -   **Utwórz** - **/Yc**  
  
    -   **Użyj** - **/Yu**  
  
     Aby uzyskać więcej informacji, zobacz [/Yc (Utwórz prekompilowany plik nagłówka)](/cpp/build/reference/yc-create-precompiled-header-file) i [/Yu (Korzystaj Prekompilowanego pliku nagłówka)](/cpp/build/reference/yu-use-precompiled-header-file). Zobacz też **PrecompiledHeaderFile** i **PrecompiledHeaderOutputFile** parametry w tej tabeli.  
  
-   **PrecompiledHeaderFile**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa nazwę pliku prekompilowanego nagłówka, do utworzenia lub używania.  
  
     Aby uzyskać więcej informacji, zobacz [/Yc (Utwórz prekompilowany plik nagłówka)](/cpp/build/reference/yc-create-precompiled-header-file) i [/Yu (Korzystaj Prekompilowanego pliku nagłówka)](/cpp/build/reference/yu-use-precompiled-header-file).  
  
-   **PrecompiledHeaderOutputFile**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa nazwę ścieżki dla prekompilowanego nagłówka, zamiast domyślna nazwa ścieżki.  
  
     Aby uzyskać więcej informacji, zobacz [/Fp (nazwa. Plik pch)](/cpp/build/reference/fp-name-dot-pch-file).  
  
-   **PreprocessKeepComments**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, zachowuje komentarze podczas przetwarzania wstępnego.  
  
     Aby uzyskać więcej informacji, zobacz [/C (Zachowaj komentarze podczas przetwarzania wstępnego)](/cpp/build/reference/c-preserve-comments-during-preprocessing).  
  
-   **PreprocessorDefinitions**  
  
     Opcjonalne `String[]` parametru.  
  
     Określa symbol przetwarzania wstępnego dla pliku źródłowego.  
  
     Aby uzyskać więcej informacji, zobacz [/D (definicje preprocesora)](/cpp/build/reference/d-preprocessor-definitions).  
  
-   **PreprocessOutput**  
  
     Opcjonalne `ITaskItem[]` parametru.  
  
     Określa tablicę elementów dane wyjściowe preprocesora, które mogą być używane i emitowane przez zadania.  
  
-   **PreprocessOutputPath**  
  
     Opcjonalne `String` parametru.  
  
     Określa nazwę pliku wyjściowego, do którego **PreprocessToFile** parametr zapisuje wstępnie przetworzone produkty wyjściowe.  
  
     Aby uzyskać więcej informacji, zobacz [/Fi (Przetwarzaj wstępnie wyjściowego pliku nazwa)](/cpp/build/reference/fi-preprocess-output-file-name).  
  
-   **PreprocessSuppressLineNumbers**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, przetwarza wstępnie pliki źródłowe C i C++ i kopiuje pliki wstępnie przetworzonych na urządzeniu standardowe dane wyjściowe.  
  
     Aby uzyskać więcej informacji, zobacz [/EP (wstępnie Przetwórz do stdout bez dyrektyw #line)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).  
  
-   **PreprocessToFile**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, przetwarza wstępnie pliki źródłowe C i C++ i zapisuje wstępnie przetworzone produkty wyjściowe do pliku.  
  
     Aby uzyskać więcej informacji, zobacz [/P (Przetwarzaj wstępnie do pliku)](/cpp/build/reference/p-preprocess-to-a-file).  
  
-   **ProcessorNumber**  
  
     Opcjonalne `Integer` parametru.  
  
     Określa maksymalną liczbę procesorów używanych w wieloprocesorowych kompilacji. Tego parametru należy użyć w połączeniu z **MultiProcessorCompilation** parametru.  
  
-   **ProgramDataBaseFileName**  
  
     Opcjonalne `String` parametru.  
  
     Określa nazwę pliku dla pliku programu (PDB) bazy danych.  
  
     Aby uzyskać więcej informacji, zobacz [/Fd (nazwa pliku bazy danych programu)](/cpp/build/reference/fd-program-database-file-name).  
  
-   **RuntimeLibrary**  
  
     Opcjonalne `String` parametru.  
  
     Wskazuje, czy moduł wielowątkowe jest biblioteki DLL i wybiera wersji detalicznych lub debugowanych biblioteki czasu wykonywania.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **Wielowątkowe** -   **/MT**  
  
    -   **MultiThreadedDebug** - **/MTd**  
  
    -   **MultiThreadedDLL** - **/ / MD**  
  
    -   **MultiThreadedDebugDLL** -   **/mdd**  
  
     Aby uzyskać więcej informacji, zobacz [/ / MD, / MT, /LD (Użyj biblioteki wykonawczej)](/cpp/build/reference/md-mt-ld-use-run-time-library).  
  
-   **RuntimeTypeInfo**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, dodaje kod do sprawdzania typów obiektów C++ w czasie wykonywania (informacje typu run-time).  
  
     Aby uzyskać więcej informacji, zobacz [/GR (Włącz Run-Time informacji o typie)](/cpp/build/reference/gr-enable-run-time-type-information).  
  
-   **ShowIncludes**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, powoduje, że kompilator output listy plików dołączanych.  
  
     Aby uzyskać więcej informacji, zobacz [/showincludes (Wymień pliki dołączane)](/cpp/build/reference/showincludes-list-include-files).  
  
-   **SmallerTypeCheck**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, zgłasza błąd wykonania, jeśli wartość jest przypisany do na mniejszy typ danych i powoduje utratę danych.  
  
     Aby uzyskać więcej informacji, zobacz **/RTCc** opcji [/RTC (błąd czasu wykonywania sprawdza)](/cpp/build/reference/rtc-run-time-error-checks).  
  
-   **Źródeł**  
  
     Wymagane `ITaskItem[]` parametru.  
  
     Określa listę plików źródłowych, rozdzielając je spacjami.  
  
-   **StringPooling**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, włącza kompilator, aby utworzyć jedną kopię identycznych ciągów w obrazie programu.  
  
     Aby uzyskać więcej informacji, zobacz [/GF (eliminowanie ciągów zduplikowanych)](/cpp/build/reference/gf-eliminate-duplicate-strings).  
  
-   **StructMemberAlignment**  
  
     Opcjonalne `String` parametru.  
  
     Określa wyrównanie bajtów dla wszystkich elementów członkowskich w strukturze.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **Domyślna** - **/Zp1**  
  
    -   **1 bajt** - **/Zp1**  
  
    -   **2Bytes** - **/Zp2**  
  
    -   **4Bytes** - **/Zp4**  
  
    -   **8Bytes** - **/Zp8**  
  
    -   **16Bytes** - **/Zp16**  
  
     Aby uzyskać więcej informacji, zobacz [/Zp (wyrównanie członka struktury)](/cpp/build/reference/zp-struct-member-alignment).  
  
-   **SuppressStartupBanner**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, uniemożliwia wyświetlanie wiadomości copyright i wersji, podczas uruchamiania zadania.  
  
     Aby uzyskać więcej informacji, zobacz [/nologo (Pomiń transparent początkowy) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).  
  
-   **Katalog TrackerLogDirectory**  
  
     Opcjonalne `String` parametru.  
  
     Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.  
  
     Aby uzyskać więcej informacji, zobacz **TLogReadFiles** i **TLogWriteFiles** parametry w tej tabeli.  
  
-   **TreatSpecificWarningsAsErrors**  
  
     Opcjonalne **String []** parametru.  
  
     Traktuje określona lista ostrzeżeń kompilatora jako błędy.  
  
     Aby uzyskać więcej informacji, zobacz **/we** `n` opcji [/w, /W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, / Wall, /wd, / możemy /wo, /Wv, wx (poziom ostrzegawczy)](/cpp/build/reference/compiler-option-warning-level).  
  
-   **TreatWarningAsError**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, traktuje wszystkie ostrzeżenia kompilatora jako błędy.  
  
     Aby uzyskać więcej informacji, zobacz **wx** opcji [/w, /W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, / Wall, /wd, / możemy /wo, /Wv, wx (poziom ostrzegawczy)](/cpp/build/reference/compiler-option-warning-level).  
  
-   **TreatWChar_tAsBuiltInType**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, Traktuj `wchar_t` typu jako typu natywnego.  
  
     Aby uzyskać więcej informacji, zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).  
  
-   **UndefineAllPreprocessorDefinitions**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, anulowanie definicji symboli specyficzne dla firmy Microsoft, które definiuje kompilatora.  
  
     Aby uzyskać więcej informacji, zobacz **/u** opcji [/U, /u (Usuń definicje symboli)](/cpp/build/reference/u-u-undefine-symbols).  
  
-   **UndefinePreprocessorDefinitions**  
  
     Opcjonalne `String[]` parametru.  
  
     Określa listę jednego lub więcej definicji symboli preprocesora do Usuń.  
  
     Aby uzyskać więcej informacji, zobacz **/U** opcji [/U, /u (Usuń definicje symboli)](/cpp/build/reference/u-u-undefine-symbols).  
  
-   **UseFullPaths**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, wyświetla Pełna ścieżka plików kodu źródłowego przekazane do kompilatora w diagnostyce.  
  
     Aby uzyskać więcej informacji, zobacz [/FC (pełna ścieżka z pliku kodu źródłowego w diagnostyce)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).  
  
-   **UseUnicodeForAssemblerListing**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, powoduje, że plik wyjściowy będzie utworzony w formacie UTF-8.  
  
     Aby uzyskać więcej informacji, zobacz **/FAu** opcji [/FA, /Fa (wyświetlanie listy plików)](/cpp/build/reference/fa-fa-listing-file).  
  
-   **WarningLevel**  
  
     Opcjonalne `String` parametru.  
  
     Określa najwyższy poziom ostrzeżenia, która ma zostać wygenerowane przez kompilator.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    -   **TurnOffAllWarnings** - **/W0**  
  
    -   **Level1** - **/W1**  
  
    -   **Level2** - **/W2**  
  
    -   **Level3** - **/W3**  
  
    -   **Level4** -   **/W4**  
  
    -   **EnableAllWarnings** -   **/ścian**  
  
     Aby uzyskać więcej informacji, zobacz **/W**  *n*  opcji [/w, /W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, / Wall, /wd, / możemy /wo, /Wv, wx (poziom ostrzegawczy)](/cpp/build/reference/compiler-option-warning-level).  
  
-   **WholeProgramOptimization**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, umożliwia optymalizacja całego programu.  
  
     Aby uzyskać więcej informacji, zobacz [/GL (optymalizacja całego programu)](/cpp/build/reference/gl-whole-program-optimization).  
  
-   **XMLDocumentationFileName**  
  
     Opcjonalne `String` parametru.  
  
     Określa nazwę wygenerowanego pliki dokumentacji XML. Ten parametr może być nazwą pliku lub katalogu.  
  
     Aby uzyskać więcej informacji, zobacz `name` argument [/doc (przetwarzanie komentarzy dokumentacji) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Zobacz też **GenerateXMLDocumentationFiles** parametru w tej tabeli.  
  
-   **MinimalRebuildFromTracking**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, śledzonych wzrostowe jest wykonywane; Jeśli `false`, kompilowania jest wykonywana.  
  
-   **TLogReadFiles**  
  
     Opcjonalne `ITaskItem[]` parametru.  
  
     Określa tablicę elementów, które reprezentują *odczytu pliku śledzenia dzienniki*.  
  
     Dziennik śledzenia odczytu pliku (.tlog) zawiera nazwy plików wejściowych, które są odczytywane przez zadanie i jest używana przez system kompilacji projektu do obsługi kompilacji przyrostowej. Aby uzyskać więcej informacji, zobacz **katalog TrackerLogDirectory** i **TrackFileAccess** parametry w tej tabeli.  
  
-   **TLogWriteFiles**  
  
     Opcjonalne `ITaskItem[]` parametru.  
  
     Określa tablicę elementów, które reprezentują *zapisu pliku śledzenia dzienniki*.  
  
     Dziennik śledzenia zapisu pliku (.tlog) zawiera nazwy pliki wyjściowe są zapisywane przez zadanie, które jest używane przez system kompilacji projektu do obsługi kompilacji przyrostowej. Aby uzyskać więcej informacji, zobacz **katalog TrackerLogDirectory** i **TrackFileAccess** parametry w tej tabeli.  
  
-   **TrackFileAccess**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, śledzi wzorce dostępu do pliku.  
  
     Aby uzyskać więcej informacji, zobacz **TLogReadFiles** i **TLogWriteFiles** parametry w tej tabeli.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)