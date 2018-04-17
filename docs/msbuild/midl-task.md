---
title: Midl — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.TypeLibFormat
- vc.task.midl
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), MIDL task
- MIDL task (MSBuild (Visual C++))
ms.assetid: 727efa8c-3336-40b8-8bef-ae6cbd77a422
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 69b46143ed997e4f23600ff3a5d389adc62fa62e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="midl-task"></a>MIDL — Zadanie
Zawijania narzędzie kompilatora Microsoft interfejsu Definition Language (MIDL) midl.exe. Aby uzyskać więcej informacji, zobacz "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **MIDL** zadań. Większość zadań parametrów i kilka zestawów parametrów, odpowiada opcji wiersza polecenia.  
  
-   **AdditionalIncludeDirectories**  
  
     Opcjonalne **String []** parametru.  
  
     Dodaje katalog do listy katalogów, które są wyszukiwane zaimportowane pliki IDL, pliki nagłówkowe dołączone i pliki konfiguracji aplikacji (ACF).  
  
     Aby uzyskać więcej informacji, zobacz **/I** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **AdditionalOptions**  
  
     Opcjonalne **ciąg** parametru.  
  
     Listę opcji wiersza polecenia. Na przykład **"*** / opcja 1 /option2 /option#*". Ten parametr umożliwia określenie opcji wiersza polecenia, które nie są reprezentowane przez inne parametru zadania MIDL.  
  
     Aby uzyskać więcej informacji, zobacz "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **ApplicationConfigurationMode**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, można używać niektórych słowa kluczowe ACF w pliku IDL.  
  
     Aby uzyskać więcej informacji, zobacz **/app_config** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **ClientStubFile**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa nazwę plik szczątkowy klienta dla interfejsu RPC.  
  
     Aby uzyskać więcej informacji, zobacz **/cstub** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web. Zobacz też **ServerStubFile** parametru w tej tabeli.  
  
-   **CPreprocessOptions**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa opcje do przekazania do C/C++ preprocesora. Określ rozdzieloną spacjami listę opcje preprocesora.  
  
     Aby uzyskać więcej informacji, zobacz **/cpp_opt** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **DefaultCharType**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa domyślny typ znakowy kompilatora C użyje do kompilowania wygenerowanego kodu.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    |Wartość|Opcja wiersza polecenia|  
    |-----------|--------------------------|  
    |**Podpisany**|**/CHAR podpisany**|  
    |**Bez znaku**|**/CHAR bez znaku**|  
    |**ASCII**|**/CHAR ascii7**|  
  
     Aby uzyskać więcej informacji, zobacz **/char** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **DllDataFileName**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa nazwę pliku dla wygenerowanej *dlldata* pliku biblioteki DLL serwera proxy.  
  
     Aby uzyskać więcej informacji, zobacz **/dlldata** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **EnableErrorChecks**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa typ błąd podczas sprawdzania, czy wygenerowanych klas zastępczych będzie wykonywać w czasie wykonywania.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    |Wartość|Opcja wiersza polecenia|  
    |-----------|--------------------------|  
    |**Brak**|**/ Error none**|  
    |**EnableCustom**|**/ Error**|  
    |**Wszystkie**|**wszystkie/Error**|  
  
     Aby uzyskać więcej informacji, zobacz **/Error** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **ErrorCheckAllocations**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, sprawdź, czy błędy braku pamięci.  
  
     Aby uzyskać więcej informacji, zobacz **alokacji/Error** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **ErrorCheckBounds**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, sprawdza rozmiar zróżnicowanie zgodność i zróżnicowanie tablice przed Specyfikacja długości transmisji.  
  
     Aby uzyskać więcej informacji, zobacz **/Error bounds_check** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **ErrorCheckEnumRange**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, sprawdza, czy wartości wyliczeniowe są w dopuszczalnym zakresie.  
  
     Aby uzyskać więcej informacji, zobacz **/Error enum** opcję Pomoc wiersza polecenia (**/?**) dla midl.exe.  
  
-   **ErrorCheckRefPointers**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, sprawdź, czy wskaźniki nie odwołanie o wartości null są przekazywane do klas zastępczych klienta.  
  
     Aby uzyskać więcej informacji, zobacz **/Error ref** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **ErrorCheckStubData**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, generuje skrótowa, która przechwytuje unmarshaling wyjątki po stronie serwera i propaguje je do klienta.  
  
     Aby uzyskać więcej informacji, zobacz **/Error stub_data** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **GenerateClientFiles**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa, czy kompilator generuje pliki źródłowe C po stronie klienta dla interfejsu RPC.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    |Wartość|Opcja wiersza polecenia|  
    |-----------|--------------------------|  
    |**Brak**|**/Client none**|  
    |**Stub**|**/Client stub**|  
  
     Aby uzyskać więcej informacji, zobacz **/client** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **GenerateServerFiles**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa, czy kompilator generuje pliki źródłowe C po stronie serwera dla interfejsu RPC.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    |Wartość|Opcja wiersza polecenia|  
    |-----------|--------------------------|  
    |**Brak**|**/ Server none**|  
    |**Stub**|**stub/Server**|  
  
     Aby uzyskać więcej informacji, zobacz **/Server** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **GenerateStublessProxies**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, generuje w pełni interpretowane klas zastępczych wraz z pośredników bez namiastek dla interfejsów obiektów.  
  
     Aby uzyskać więcej informacji, zobacz **/oicf** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **GenerateTypeLibrary**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, nie jest generowany plik biblioteki (.tlb) typu.  
  
     Aby uzyskać więcej informacji, zobacz **notlb** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **HeaderFileName**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa nazwę wygenerowanego pliku nagłówka.  
  
     Aby uzyskać więcej informacji, zobacz **/h** lub **/header** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **IgnoreStandardIncludePath**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, midl — zadanie wyszukuje tylko katalogi określone przy użyciu **AdditionalIncludeDirectories** przełącznika i ignoruje w bieżącym katalogu i katalogi określone przez zmienną środowiskową INCLUDE.  
  
     Aby uzyskać więcej informacji, zobacz **/no_def_idir** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **InterfaceIdentifierFileName**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa nazwę *pliku identyfikatora interfejsu* dla interfejsu COM. Przesłania domyślną nazwę uzyskany przez dodanie nazwy pliku IDL "_i.c".  
  
     Aby uzyskać więcej informacji, zobacz **/iid** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **Identyfikator ustawień regionalnych**  
  
     Opcjonalne **int** parametru.  
  
     Określa *identyfikator ustawień regionalnych* , umożliwia użycie znaków międzynarodowych plików wejściowych, nazw plików i ścieżek katalogów. Określ identyfikator ustawień regionalnych dziesiętną.  
  
     Aby uzyskać więcej informacji, zobacz **/LCID** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web. Zobacz też "Ustawień regionalnych identyfikatory przypisane przez Microsoft" w witrynie MSDN.  
  
-   **MkTypLibCompatible**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, wymaga format pliku wejściowego, aby był zgodny z mktyplib.exe w wersji 2.03.  
  
     Aby uzyskać więcej informacji, zobacz **/mktyplib203** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web. Zobacz też "ODL pliku składni" w witrynie MSDN.  
  
-   **OutputDirectory**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa domyślny katalog, w którym midl — zadanie zapisuje pliki wyjściowe.  
  
     Aby uzyskać więcej informacji, zobacz **/out** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **PreprocessorDefinitions**  
  
     Opcjonalne **String []** parametru.  
  
     Określa co najmniej jeden *definiuje*; oznacza to, nazwę i wartość opcjonalna do przekazania do preprocesora C jako Jeśli przez `#define` dyrektywy. Formularz każdego Definiuj jest, *nazwa [= value]*.  
  
     Aby uzyskać więcej informacji, zobacz **/D** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web. Zobacz też **UndefinePreprocessorDefinitions** parametru w tej tabeli.  
  
-   **ProxyFileName**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa nazwę pliku proxy interfejsu dla interfejsu COM.  
  
     Aby uzyskać więcej informacji, zobacz **/proxy** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **RedirectOutputAndErrors**  
  
     Opcjonalne **ciąg** parametru.  
  
     Przekierowuje dane wyjściowe, takie jak komunikaty o błędach i ostrzeżenia, standardowe dane wyjściowe do określonego pliku.  
  
     Aby uzyskać więcej informacji, zobacz **/o** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **ServerStubFile**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa nazwę plik szczątkowy serwera dla interfejsu RPC.  
  
     Aby uzyskać więcej informacji, zobacz **/sstub** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web. Zobacz też **ClientStubFile** parametru w tej tabeli.  
  
-   **Źródło**  
  
     Wymagane `ITaskItem[]` parametru.  
  
     Określa listę plików źródłowych, rozdzielając je spacjami.  
  
-   **StructMemberAlignment**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa wyrównanie (*poziom pakowania*) struktur w systemie docelowym.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    |Wartość|Opcja wiersza polecenia|  
    |-----------|--------------------------|  
    |**NotSet**|*\<Brak >*|  
    |**1**|**/Zp1**|  
    |**2**|**/Zp2**|  
    |**4**|**/Zp4**|  
    |**8**|**/Zp8**|  
  
     Aby uzyskać więcej informacji, zobacz **/Zp** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web. **/Zp** opcja jest równoważna wartości **/dodatkiem Service pack** opcja i starszej **/ align** opcji.  
  
-   **SuppressCompilerWarnings**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, pomija komunikaty ostrzegawcze z midl — zadanie.  
  
     Aby uzyskać więcej informacji, zobacz **/no_warn** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **SuppressStartupBanner**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, uniemożliwia wyświetlanie wiadomości copyright i wersji, podczas uruchamiania zadania.  
  
     Aby uzyskać więcej informacji, zobacz **/nologo** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **TargetEnvironment**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa środowisko, w którym jest uruchomiona aplikacja.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    |Wartość|Opcja wiersza polecenia|  
    |-----------|--------------------------|  
    |**NotSet**|*\<Brak >*|  
    |**Win32**|**/ ENV win32**|  
    |**Itanium**|**/ ENV ia64**|  
    |**X64**|**/ ENV x64**|  
  
     Aby uzyskać więcej informacji, zobacz **/ENV** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **Katalog TrackerLogDirectory**  
  
     Opcjonalne `String` parametru.  
  
     Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.  
  
-   **TypeLibFormat**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa format pliku biblioteki typów.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    |Wartość|Opcja wiersza polecenia|  
    |-----------|--------------------------|  
    |**NewFormat**|**/newtlb**|  
    |**OldFormat**|**/oldtlb**|  
  
     Aby uzyskać więcej informacji, zobacz **/newtlb** i **/oldtlb** opcje w "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **TypeLibraryName**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa nazwę pliku biblioteki typów.  
  
     Aby uzyskać więcej informacji, zobacz **/TLB** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **UndefinePreprocessorDefinitions**  
  
     Opcjonalne **String []** parametru.  
  
     Usuwa wszelkie poprzednie definicji nazwy przekazując nazwy preprocesora C jako Jeśli przez `#undefine` dyrektywy. Określ co najmniej jeden uprzednio zdefiniowanej nazwy.  
  
     Aby uzyskać więcej informacji, zobacz **/U** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web. Zobacz też **PreprocessorDefinitions** parametru w tej tabeli.  
  
-   **ValidateAllParameters**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, generuje dodatkowe informacje sprawdzanie błędów, który służy do sprawdzania integralności w czasie wykonywania. Jeśli `false`, sprawdzanie błędów informacje nie są generowane.  
  
     Aby uzyskać więcej informacji, zobacz **/ robust** i **/no_robust** opcje w "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
-   **WarnAsError**  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, traktuje wszystkie ostrzeżenia jako błędy.  
  
     Jeśli **WarningLevel** MIDL zadań parametr nie zostanie określony, ostrzeżenia na poziomie domyślnym, poziom 1, są traktowane jako błędy.  
  
     Aby uzyskać więcej informacji, zobacz **wx** opcje w "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web. Zobacz też **WarningLevel** parametru w tej tabeli.  
  
-   **WarningLevel**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa ważność (*poziom ostrzeżeń*) ostrzeżeń do wysyłania. Bez ostrzeżenia jest emitowany do wartości 0. W przeciwnym razie jest emitowany ostrzeżenie, jeśli jego poziom ostrzeżeń jest wartość liczbowa mniejsza niż określona wartość.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
    |Wartość|Opcja wiersza polecenia|  
    |-----------|--------------------------|  
    |**0**|**/W0**|  
    |**1**|**/W1**|  
    |**2**|**/W2**|  
    |**3**|**/W3**|  
    |**4**|**/W4**|  
  
     Aby uzyskać więcej informacji, zobacz **/W** opcji "Odwołania do wiersza polecenia MIDL" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web. Zobacz też **WarnAsError** parametru w tej tabeli.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)