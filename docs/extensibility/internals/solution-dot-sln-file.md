---
title: "Rozwiązania (. Plik sln) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b7be9b3bf7783980cfbbe1abfc44fe1748dd20a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="solution-sln-file"></a>Rozwiązania (. Plik sln)
Rozwiązanie to struktura służący do organizowania projekty w programie Visual Studio. Rozwiązania przechowuje informacje o stanie dla projektów w .sln (tekstowych, udostępnionych) i pliki .suo (opcje rozwiązania binarnego, specyficzne dla użytkownika). Aby uzyskać więcej informacji o .suo — pliki Zobacz [opcji użytkownika rozwiązania (. Pliku suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Jeśli VSPackage został załadowany w wyniku, do którego odwołuje się plik .sln, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> do odczytu w pliku sln.  
  
 Plik .sln zawiera informacji tekstowych środowiska używa do znalezienia i załadować parametrów nazwa wartość dla istniejących danych i VSPackages odwołuje się projekt. Po otwarciu rozwiązania środowiska przełączanie po kolei `preSolution`, `Project`, i `postSolution` informacje w pliku SLN załadować rozwiązania, projekty w ramach rozwiązania, a wszelkie informacje utrwalonego dołączony do rozwiązania.  
  
 Pliku każdego projektu zawiera dodatkowe informacje, przeczytaj przez środowisko do wypełniania hierarchii z elementami tego projektu. Trwałość danych hierarchii jest kontrolowany przez projekt; dane nie są zwykle przechowywane w pliku SLN, mimo że można celowo zapisać informacji o projekcie do pliku SLN, jeśli chcesz to zrobić. Aby uzyskać więcej informacji dotyczących trwałości, zobacz [trwałości projektu](../../extensibility/internals/project-persistence.md) i [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Zawartość pliku rozwiązania  
 Plik .sln składa się z kilku sekcji, jak pokazano w poniższym kodzie.  
  
```  
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
EndProject  
Global  
  GlobalSection(SolutionNotes) = postSolution  
  EndGlobalSection  
  GlobalSection(SolutionConfiguration) = preSolution  
       ConfigName.0 = Debug  
       ConfigName.1 = Release  
  EndGlobalSection  
  GlobalSection(ProjectDependencies) = postSolution  
  EndGlobalSection  
  GlobalSection(ProjectConfiguration) = postSolution  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86  
  EndGlobalSection  
  GlobalSection(ExtensibilityGlobals) = postSolution  
  EndGlobalSection  
  GlobalSection(ExtensibilityAddIns) = postSolution  
  EndGlobalSection  
EndGlobal  
```  
  
 Aby załadować rozwiązania, środowisko wykonuje następująca sekwencja zadań.  
  
1.  Środowiska odczytuje globalne sekcję plik .sln i przetwarza wszystkie sekcje oznaczone `preSolution`. W takim przypadku jest jednej z tych instrukcji:  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution  
         ConfigName.0 = Debug  
         ConfigName.1 = Release  
    ```  
  
     Jeśli środowisko odczytuje `GlobalSection('name')` tagu mapowania nazwy pakiet VSPackage za pomocą rejestru. Nazwa klucza powinna istnieć w kluczu rejestru [HKLM\\< katalog główny rejestru identyfikator aplikacji\>\SolutionPersistence\AggregateGUIDs]. Klucze ze słownika wartość domyślna to identyfikator GUID pakietu (REG_SZ) o pakiet VSPackage, która zarejestrowała wpisów.  
  
2.  Środowisko ładuje pakiet VSPackage, wywołania `QueryInterface` na pakiet VSPackage dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfejsu i wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> metody z danymi w sekcji, pakiet VSPackage mogą przechowywać dane. Środowisko ten proces jest powtarzany dla każdego `preSolution` sekcji.  
  
3.  Środowisko iterację w blokach nietrwałości projektu. W takim przypadku jest jeden projekt.  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
    "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
    EndProject  
    ```  
  
     Ta instrukcja zawiera unikatowy identyfikator GUID projektu i identyfikator GUID typu projektu. Te informacje jest używane przez środowisko można znaleźć w pliku projektu lub pliki należące do rozwiązania, a pakiet VSPackage wymagane dla każdego projektu. Identyfikator GUID jest przekazywana do projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> można załadować określonego pakiet VSPackage związanych z projektem, następnie projektu jest ładowany przez pakiet VSPackage. W takim przypadku pakiet VSPackage, który jest ładowany dla tego projektu jest Visual Basic.  
  
     Każdy projekt może się powtarzać, identyfikator wystąpienia unikatowego projektu, dzięki czemu mogą uzyskiwać odpowiednio do potrzeb innych projektów w rozwiązaniu. Najlepiej Jeśli rozwiązanie i projekty są pod kontrolą kodu źródłowego, ścieżka do projektu powinna być określona względem ścieżki do rozwiązania. Po załadowaniu rozwiązania pliki projektu nie może znajdować się na komputerze użytkownika. Dzięki użyciu plik projektu przechowywane na serwerze względem pliku rozwiązania, jest stosunkowo proste pliku projektu, należy znaleźć i skopiować do komputera użytkownika. Go, a następnie kopiuje i ładuje pozostałe pliki potrzebne do projektu.  
  
4.  Na podstawie informacji zawartych w sekcji projektu w pliku SLN, środowisko ładuje każdego pliku projektu. Samym projekcie następnie jest odpowiedzialny za wypełnianie hierarchii projektu i ładuje wszystkie projekty zagnieżdżonych.  
  
5.  Po przetworzeniu wszystkich sekcji w pliku SLN, rozwiązanie jest wyświetlana w Eksploratorze rozwiązań i jest gotowy do modyfikowania przez użytkownika.  
  
 Jeśli wszystkie pakiet VSPackage, który implementuje projektu w rozwiązaniu nie udało się załadować, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> wywołania metody, co innych projektów w rozwiązaniu jest miał możliwość zignorować zmiany mogą mieć wprowadzone podczas ładowania. Jeśli wystąpią błędy analizy, jak najwięcej informacji jest zachowywana przy użyciu plików rozwiązania i środowiska Wyświetla okno dialogowe z ostrzeżeniem, że rozwiązanie jest uszkodzony.  
  
 Po zapisaniu lub zamknięty, rozwiązanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> metoda jest wywoływana i przekazane do tej hierarchii, jeśli wprowadzono zmiany do rozwiązania, które muszą być wprowadzane do pliku sln. Wartość null, przekazany do `QuerySaveSolutionProps` w <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, wskazuje, że informacje jest jest trwały dla rozwiązania. Jeśli wartość nie jest zerowa, utrwalonego informacje są przeznaczone dla konkretnego projektu, określany przez wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejsu.  
  
 Jeśli ma informacji do zapisania, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfejsu jest wywoływana za pomocą wskaźnika do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> metody. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> Metoda następnie jest wywoływana przez środowisko w celu pobrania pary nazwa wartość z `IPropertyBag` interfejsu i zapisze informacje pliku sln.  
  
 `SaveSolutionProps`i `WriteSolutionProps` obiekty są nazywane rekursywnie przez środowisko można pobrać informacji o zapisane z `IPropertyBag` interfejsu, aż wszystkie zmiany wprowadzono w pliku sln. W ten sposób można upewnić się, że dane zostaną utrwalone z rozwiązania i dostępne następnym otwarciu rozwiązania.  
  
 Aby sprawdzić, czy ma ona żadnych czynności, aby zapisać plik .sln wyliczeniu co załadowany pakiet VSPackage. Jest tylko w czasie ładowania, którego wysyłane są zapytania kluczy rejestru. Środowisko zna wszystkie pakiety załadowany ponieważ znajdują się w pamięci w czasie, który zapisano rozwiązania.  
  
 Tylko plik .sln zawiera wpisy w `preSolution` i `postSolution` sekcje. Plik .suo są podobne sekcji, ponieważ te informacje można prawidłowo załadować potrzebuje rozwiązania. Plik .suo zawiera opcje specyficzne dla użytkownika, takie jak informacje prywatne, które nie mają być udostępnione lub umieszczone pod kontrolą kodu źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Opcje użytkownika rozwiązania (. Pliku suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Rozwiązania](../../extensibility/internals/solutions.md)