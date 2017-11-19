---
title: "Uruchomiona tabeli dokumentów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf66dce40cda2d72757c3a2fe141ed023b286d78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="running-document-table"></a>Uruchomionej tabeli dokumentu
IDE przechowuje listę wszystkich aktualnie otwarte dokumenty w wewnętrznej struktury o nazwie uruchomionej tabeli dokumentów (Normalizacją). Ta lista zawiera wszystkie otwarte dokumenty w pamięci, niezależnie od tego, czy te dokumenty są obecnie edytowany. Dokument jest dowolny element, który jest trwały, w tym pliki w projekcie, lub głównego pliku projektu (na przykład plik .vcxproj).  
  
## <a name="elements-of-the-running-document-table"></a>Elementy pracy tabeli dokumentu  
 Uruchomionej tabeli dokumentu zawiera następujące wpisy.  
  
|Element|Opis|  
|-------------|-----------------|  
|Krótka nazwa dokumentu|Ciąg unikatowo identyfikujący obiekt danych dokumentu. Będzie to ścieżka bezwzględna do pliku dla systemu projektu, który zarządza plikami (na przykład C:\MyProject\MyFile). Ten ciąg jest również używane do projektów zapisanych w magazynach innych niż systemy plików, takich jak procedur przechowywanych w bazie danych. W takim przypadku system projektu można magazynowa unikatowy ciąg, który może rozpoznawać i prawdopodobnie analizy w celu ustalenia sposobu przechowywania dokumentu.|  
|Właściciel hierarchii|Obiekt hierarchii, który jest właścicielem dokumentu, reprezentowany przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejsu.|  
|Identyfikator elementu|Identyfikator elementu konkretny element w hierarchii. Ta wartość jest unikatowa wśród wszystkich dokumentów w hierarchii, która jest właścicielem tego dokumentu, ale wartość ta nie musi być unikatowe w obrębie różnych hierarchii.|  
|Obiekt danych dokumentu|Co najmniej, to`IUnknown`<br /><br /> obiekt. IDE nie wymaga żadnych konkretnego interfejsu poza `IUnknown` interfejs dla obiekt danych dokumentu Edytor niestandardowy. Niemniej jednak w przypadku standardowego edytora implementacja edytor <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfejsu jest wymagana do obsługi połączeń trwałości plik z projektu. Aby uzyskać więcej informacji, zobacz [zapisywania standardowego dokumentu](../../extensibility/internals/saving-a-standard-document.md).|  
|Flagi|Gdy wpisy są dodawane do Normalizacją można określić flagi określające, czy dokument zostanie zapisany, czy zastosowano blokady odczytu lub edycji i tak dalej. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> wyliczenia.|  
|Edytuj liczbę blokad|Liczba blokad edycji. Zablokuj edycji oznacza, że niektóre Edytor ma dokument otwarty do edycji. Liczba blokad edycji przejścia do zera, użytkownik jest monitowany można zapisać dokumentu, jeśli został on zmodyfikowany. Na przykład zawsze po otwarciu dokumentu w edytorze przy użyciu **nowe okno** poleceń edycji blokady jest dodawany do tego dokumentu w Normalizacją. Aby blokady edycji należy ustawić dokumentu musi mieć hierarchii lub elementu identyfikatora.|  
|Liczba blokady odczytu|Liczba blokady odczytu. Blokada odczytu wskazuje, że odczytu dokumentu za pomocą mechanizmu, takich jak kreatora. Blokada odczytu przechowuje dokumentu w Normalizacją wskazujące, że nie można edytować dokumentu. Można ustawić blokady odczytu, nawet jeśli dokument nie ma hierarchii lub elementu identyfikatora. Ta funkcja umożliwia otwieranie dokumentu w pamięci i wprowadź go Normalizacją bez dokumentu właścicielem żadnych hierarchii. Ta funkcja jest rzadko używana.|  
|Symbol zastępczy blokady|Wystąpienie <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfejsu. Właściciel blokady jest implementowany przez funkcje, takie jak kreatorów otwierających i edycji dokumentów poza edytorem. Właściciela blokady umożliwia tę funkcję, aby dodać blokady edycji do dokumentu, aby zapobiec dokument zostanie zamknięty, gdy nadal jest ono edytowane. Zwykle, Edytuj blokad tylko są dodawane przez okna dokumentów (to znaczy edytory).|  
  
 Każdy wpis w Normalizacją ma unikatowy hierarchii lub skojarzone z nim, identyfikator elementu, który zazwyczaj odpowiada jednemu węzłowi w projekcie. Wszystkie dokumenty dostępne do edycji są zazwyczaj należącymi do przez hierarchię. Wpisy w Normalizacją kontroli projektu, lub — dokładniej — które hierarchii jest bieżącym właścicielem obiektu danych dokumentu edytowany. Korzystając z informacji w Normalizacją, IDE uniemożliwia dokument jest otwarty przez więcej niż jednego projektu w czasie.  
  
 Hierarchii również kontroluje trwałości danych i informacje są używane w Normalizacją zaktualizować **zapisać** i **Zapisz jako** okien dialogowych. Po modyfikacji dokumentu użytkowników, a następnie wybierz pozycję **zakończenia** polecenie **pliku** menu IDE wyświetli monit o **Zapisz zmiany** okno dialogowe, aby wyświetlić wszystkie projekty i elementy projektu, które aktualnie są modyfikowane. Dzięki temu użytkownicy mogą wybrać dokumentów, aby zapisać. Na liście dokumentów, aby zapisać (czyli tych dokumentów, których zmian) są generowane na podstawie Normalizacją. Wszystkie elementy, które powinny być widoczne w **Zapisz zmiany** okno dialogowe podczas zamykania aplikacji powinny być rekordów w Normalizacją. Normalizacją koordynuje dokumenty, które są zapisywane i czy użytkownik jest wyświetlany monit o zapisanie operację przy użyciu wartości określonej we wpisie flagi dla każdego dokumentu. Aby uzyskać więcej informacji o flagach Normalizacją, zobacz <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> wyliczenia.  
  
## <a name="edit-locks-and-read-locks"></a>Edytuj blokad i blokady odczytu  
 Edytuj blokad i blokady odczytu znajdują się w Normalizacją. Zwiększa okno dokumentu i zmniejsza zablokować edycji. W związku z tym gdy użytkownik otwiera nowe okno dokumentu, Edytuj liczbę blokad zwiększa o jeden. Gdy liczbę blokad edycji do zera, hierarchii jest informowany trwałe i zapisać dane dla skojarzonego dokumentu. Hierarchii można następnie zachować dane w dowolny sposób, w tym utrwalanie jako plik lub element w repozytorium. Można użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> metody w <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfejsu dodaje blokady do edycji i odczytu blokady i <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> metodę, aby usunąć te blokad.  
  
 Zwykle gdy okno dokumentu edytora zostanie uruchomiony, ramki okna automatycznie dodaje blokady edycji dokumentu Normalizacją. Niemniej jednak w przypadku utworzenia widoku niestandardowego dokumentu nie wykorzystujące okno dokumentu standardowe (to znaczy nie implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfejsu), należy ustawić własne blokady edycji, a następnie. Na przykład w kreatorze, dokument jest edytowany nie jest otwarty w edytorze. Aby blokad dokumentu do otwierania przez kreatorów i podobne jednostki, należy zaimplementować te jednostki <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfejsu. Aby zarejestrować Twoje blokadę dokumentu, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> — metoda i przekazać w Twojej <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementacji. Dzięki temu dodaje użytkownika blokadę dokumentu do Normalizacją. Inny scenariusz wdrażania właściciela blokady dokumentu jest, jeśli można otworzyć dokumentu za pomocą okna narzędzia specjalne. W tym wystąpieniu jest niemożliwe ma zamknąć dokument okna narzędzia. Jednak rejestrując jako właściciela blokady dokumentu Normalizacją IDE można wywołać implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> metody monitowanie koniec dokumentu.  
  
## <a name="other-uses-of-the-running-document-table"></a>Innych celów uruchomiona tabeli dokumentu  
 Inne jednostki w środowisku IDE Użyj Normalizacją, aby uzyskać informacje o dokumentach. Na przykład menedżera kontroli źródła używa Normalizacją mówić systemu, aby ponownie załadować dokumentu w edytorze, po jego pobiera najnowsza wersja pliku. Aby to zrobić, menedżera kontroli źródła wyszukuje pliki w Normalizacją, aby zobaczyć, czy dowolna z nich jest otwarty. Jeśli są one, a następnie menedżera kontroli źródła najpierw sprawdza, czy hierarchia implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metody. Jeśli projekt nie zawiera implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metody, a następnie źródło kontrolować manager sprawdza implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> metody bezpośrednio obiektu danych dokumentu.  
  
 IDE używa również Normalizacją do resurface (Przesuń na wierzch) otwartego dokumentu, jeśli użytkownik zażąda tego dokumentu. Aby uzyskać więcej informacji, zobacz [wyświetlanie plików za pomocą polecenia Otwórz plik](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Aby ustalić, czy plik jest otwarty w Normalizacją, wykonaj jedną z następujących czynności.  
  
-   Zapytanie o moniker dokumentu (to znaczy ścieżki pełnego dokumentu) sprawdzić, czy element jest otwarty.  
  
-   Identyfikator hierarchii lub element umożliwia poproś system projektu dla ścieżki pełnego dokumentu, a następnie wyszukaj element Normalizacją.  
  
## <a name="see-also"></a>Zobacz też  
 [Użycie RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)   
 [Trwałość i uruchomiona tabeli dokumentu](../../extensibility/internals/persistence-and-the-running-document-table.md)