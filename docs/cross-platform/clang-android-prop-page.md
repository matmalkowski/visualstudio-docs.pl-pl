---
title: Clang właściwości projektu (Android C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 663140ea-a568-472b-a79a-dfea8818e06a
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.VCClangCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCClangCompilerTool.DebugInformationFormat
- VC.Project.VCClangCompilerTool.ObjectFile
- VC.Project.VCClangCompilerTool.WarningLevel
- VC.Project.VCClangCompilerTool.WarnAsError
- VC.Project.VCClangCompilerTool.Verbose
- VC.Project.VCClangCompilerTool.Optimization
- VC.Project.VCClangCompilerTool.StrictAliasing
- VC.Project.VCClangCompilerTool.OmitFramePointers
- VC.Project.VCClangCompilerTool.ExceptionHandling
- VC.Project.VCClangCompilerTool.EnableFunctionLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.FloatABI
- VC.Project.VCClangCompilerTool.BufferSecurityCheck
- VC.Project.VCClangCompilerTool.PIC
- VC.Project.VCClangCompilerTool.UseShortEnums
- VC.Project.VCClangCompilerTool.RuntimeTypeInfo
- VC.Project.VCClangCompilerTool.CLanguageStandard
- VC.Project.VCClangCompilerTool.CppLanguageStandard
- VC.Project.VCClangCompilerTool.PreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefineAllPreprocessorDefinitions
- VC.Project.VCClangCompilerTool.ShowIncludes
- VC.Project.VCClangCompilerTool.PrecompiledHeader
- VC.Project.VCClangCompilerTool.PrecompiledHeaderFile
- VC.Project.VCClangCompilerTool.PrecompiledHeaderOutputFileDirectory
- VC.Project.VCClangCompilerTool.PrecompiledHeaderCompileAs
- VC.Project.VCClangCompilerTool.CompileAs
- VC.Project.VCClangCompilerTool.ForcedIncludeFiles
- VC.Project.VCClangCompilerTool.MultiProcessorCompilation
- vc.project.AdditionalOptionsPage
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 8a1fd92a41f145e097615bea4434ea80fd592416
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="clang-project-properties-android-c"></a>Clang właściwości projektu (Android C++)

Właściwość | Opis | Opcje
--- | ---| ---
Dodatkowe katalogi dołączenia | Określa jeden lub więcej katalogów do dodania do ścieżki dołączenia; Oddziel przy użyciu średnikami, jeśli istnieje więcej niż jedna. (-I[path]).
Format informacji debugowania | Określa typ informacji dotyczących debugowania generowanych przez kompilator. | **Brak** — tworzy żadnych informacji debugowania, więc kompilacji może przebiegać szybciej.<br>**Pełne informacje debugowania (DWARF2)** -informacje dotyczące debugowania DWARF2 generowania.<br>**Informacje o numerze wiersza** -tylko informacje o Generowanie numeru wiersza.<br>
Nazwa pliku obiektu | Określa nazwę do przesłaniania domyślnej nazwy pliku obiektu; może być nazwą pliku lub katalogu. (/ Fo[name]).
Poziom ostrzeżeń | Wybierz, jak ściśle kompilator o błędach kodu.  Inne flagi należy dodać bezpośrednio do dodatkowe opcje. (/ w, / weverything). | **Włącz Wyłącz wszystkie ostrzeżenia** — wyłącza wszystkie ostrzeżenia kompilatora.<br>**EnableAllWarnings** -włącza wszystkie ostrzeżenia, w tym te domyślnie wyłączone.<br>
Traktuj ostrzeżenia jako błędy | Traktuje wszystkie ostrzeżenia kompilatora jako błędy. Dla nowego projektu jego najlepszym rozwiązaniem może być użycie elementu /WX we wszystkich kompilacjach; rozwiązanie wszystkich ostrzeżeń zapewni najmniejszej defektów możliwe kodu twarde do znalezienia.
Włącz tryb informacji pełnej | Pokaż polecenia do uruchomienia i użyj pełnych danych wyjściowych.
Optymalizacja | Określa poziom optymalizacji dla aplikacji. | **Niestandardowe** -optymalizacji niestandardowe.<br>**Wyłączone** -wyłączenie optymalizacji.<br>**Minimalizuj rozmiar** -Optymalizuj dla rozmiaru.<br>**Maksymalizuj szybkość** -Optymalizacja szybkości.<br>**Pełna optymalizacja** -optymalizacje kosztowne.<br>
Ścisłego aliasów | Przykładowa najbardziej rygorystyczne reguły aliasowania.  Obiekt danego typu zostanie nigdy nie zakłada się, że znajdują się na tym samym adresem co obiekt innego typu.
Pominięcie wskaźnika ramki | Pomija tworzenie wskaźników ramek na stosie wywołań.
Włącz wyjątki C++ | Określa model obsługi wyjątków, aby używane przez kompilator. | **Nie** -wyłączenie obsługi wyjątków.<br>**Tak** — Włączanie obsługi wyjątków.<br>**Unwind tabel** — generuje wszelkie wymagane dane statyczne, ale nie ma wpływu na wygenerowany kod.<br>
Włącz konsolidacje poziomu funkcji | Umożliwia kompilatorowi pakowanie indywidualnych funkcji w formę spakowanych funkcji (Comdat). Wymagane do edycji i kontynuować pracę.     (ffunction Section).
Włączanie łączenia na poziomie danych | Umożliwia optymalizacjom konsolidatora usuwanie nieużywanych danych przez emitowanie każdego elementu danych w osobnej sekcji.
Włącz zaawansowane SIMD(Neon) | Włącza generowanie kodu dla NEON sprzęt zmiennoprzecinkowy. Dotyczy tylko architektury arm.
ABI liczb zmiennoprzecinkowych | Opcja umożliwiająca wybranie zmiennoprzecinkowego interfejsu ABI. | **Elastyczne** — "Soft" umożliwia kompilatorowi Generowanie danych wyjściowych zawierających wywołania bibliotek dotyczące operacji zmiennoprzecinkowych.<br>**SoftFP** — "SoftFP" umożliwia generowanie kodu przy użyciu instrukcji zmiennoprzecinkowych sprzętu, ale nadal używa konwencji wywoływania zmiennoprzecinkowych.<br>**Twarde** -alows "Twardym" Generowanie liczb zmiennoprzecinkowych instrukcje i używa FPU konwencji wywoływania specyficznych.<br>
Kontrola zabezpieczeń | Kontrola zabezpieczeń pomaga wykryć przepełnienie stosu buforu, typowy atak na zabezpieczenia programu. (fstack-protector). | **Wyłącz sprawdzanie zabezpieczeń** -wyłączyć sprawdzanie zabezpieczeń.<br>**Włącz kontrolę zabezpieczeń** -Włącz kontrolę zabezpieczeń. (fstack-protector)<br>
Kod niezależny | Generowanie pozycji niezależne kodu (PIC) do użycia w bibliotece udostępnionej.
Użyj krótkich wyliczenia | Typ wyliczenia używa tylko liczby bajtów wymaganej przez wejściowy zestaw możliwych wartości.
Włącz informacje typu Run-Time | Dodaje kod do sprawdzania typów obiektów C++ w czasie wykonywania (informacje o typie środowiska uruchomieniowego).     (frtti, fno-rtti)
Standard języka C | Określa standard języka C. | **Default**<br>**C89** -C89 Standard języka.<br>**C99** -C99 Standard języka.<br>**C11** -C11 Standard języka.<br>**C99 (GNU dialekt)** — Standard języka C99 (GNU dialekt).<br>**C11 (GNU dialekt)** — Standard języka C11 (GNU dialekt).<br>
Standard języka C++ | Określa standard języka C++. | **Default**<br>**C ++ 03** — Standard 03 języka C ++.<br>**C ++ 11** -C ++ 11 języka Standard.<br>**C ++ 14** -C ++ 14 języka Standard.<br>**03 c ++ (GNU dialekt)** C ++ - 03 Standard języka (GNU dialekt).<br>**C ++ 11 (GNU dialekt)** - C ++ 11 Standard języka (GNU dialekt).<br>**C ++ 14 (GNU dialekt)** - C ++ 14 Standard języka (GNU dialekt).<br>
Definicje preprocesora | Definiuje symbole przetwarzania wstępnego dla pliku źródłowego. (-D)
Usuń definicje preprocesora | Określa, że co najmniej jeden anulowanie definicji preprocesora.  (-U [macro])
Usuń definicje wszystkich Preprocesorów | Usuń definicje wszystkich zdefiniowanych wcześniej wartości preprocesora.  (-undef)
Pokaż obejmuje | Generuje listę załączonych plików z danych wyjściowych kompilatora.  (-H)
Prekompilowanego nagłówka | Utworzenie/użycie Prekompilowanego nagłówka: umożliwia tworzenie i używanie prekompilowanych nagłówków podczas kompilacji. | **Użyj** -Użyj Prekompilowanego nagłówka.<br>**Nie używa prekompilowanych nagłówków** — nie używa Prekompilowanego nagłówka.<br>
Prekompilowany plik nagłówka | Określa nazwę pliku nagłówka dla prekompilowanego pliku nagłówka. Ten plik zostanie też dodany do elementu "Wymuszone pliki dyrektywy Include" podczas kompilacji
Katalog pliku wyjściowego prekompilowanego nagłówka | Określa katalog wygenerowanego prekompilowanego nagłówka. Ten katalog zostanie też dodany do elementu "Dodatkowe katalogi dołączenia" podczas kompilacji
Kompiluj prekompilowany nagłówek jako | Wybierz język kompilacji dla prekompilowanego pliku nagłówkowego (- x c-header, - x c ++ - nagłówka). | **Skompiluj jako kod języka C** -skompiluj jako kod języka C.<br>**Skompiluj jako kod języka C++** -skompiluj jako kod języka C++.<br>
Skompiluj jako | Wybierz opcję języka kompilowania dla plików .c i .cpp.  "Default" wykryje na podstawie rozszerzenia c lub CPP rozszerzenie. (-x c, - x c ++) | **Domyślna** — domyślna.<br>**Skompiluj jako kod języka C** -skompiluj jako kod języka C.<br>**Skompiluj jako kod języka C++** -skompiluj jako kod języka C++.<br>
Wymuszone pliki dołączane | co najmniej jeden wymuszony Dołącz pliki.     (-include [nazwa])
Kompilacja wielu procesorów | Kompilacja wielu procesorów.
Dodatkowe opcje | Dodatkowe opcje.
