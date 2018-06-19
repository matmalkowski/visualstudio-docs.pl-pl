---
title: Zablokuj posiadacz Zarządzanie dokumentami | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65f5a38f5d4da0986b7f95c9287a94e657efa9c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130547"
---
# <a name="document-lock-holder-management"></a>Zarządzanie właściciela blokady dokumentu
Tabela systemem dokumentu (Normalizacją) obsługuje liczbę otwarte dokumenty i wszystkie blokady edycji, które mają. Blokady edycji można umieścić na dokument w Normalizacją, gdy programowo jest edytowany w tle bez użytkownika wyświetlany w oknie dokumentu otwartego dokumentu. Ta funkcja jest często używane przez projektantów, które modyfikują wiele plików za pomocą graficznego interfejsu użytkownika.  
  
## <a name="document-lock-holder-scenarios"></a>Scenariusze właściciela blokady dokumentu  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>Plik "" ma zależność w pliku "b"  
 Rozważmy sytuację, w którym wdrożenia standardowego edytora "A" dla typu pliku "a", a każdy plik typu "" zawiera odwołanie do (lub zależność od) pliku typu "b". Standardowy edytor "B" nie istnieje dla plików typu "b". Po otwarciu edytora "A" pliku "" it pobiera odwołanie do odpowiedniego pliku "b". Plik "b" nie jest wyświetlana, ale można go zmodyfikować edytora "A". Edytor "A" pobiera odwołanie do danych dokumentu z pliku "b" z <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metody, a także utrzymuje blokadę edycji w pliku "b". Po ukończeniu edytora "A" Modyfikowanie plików "b", można zmniejszyć blokady edycji liczba w pliku "b" przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> metody. Ten krok można pominąć, jeśli były nazywane <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metody z parametrem `dwRDTLockType` ustawioną <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>Plik "b" jest otwarty przez inny edytor  
 W przypadku, gdy plik "b" jest już otwarty przez Edytor "B", gdy Edytor "A" spróbuje go otworzyć, istnieją dwa oddzielne scenariusze obsługi:  
  
-   Jeśli plik "b" jest otwarty w edytorze zgodne, musi mieć edytora "A" Zarejestruj blokady edycji dokumentów na pliku "b" przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metody. Po zakończeniu modyfikowania pliku "b" edytora "A" wyrejestrować go edytować, przy użyciu blokady <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> metody.  
  
-   Jeśli plik "b" jest otwarty w sposób niezgodny, albo można pozostawić próba otwarcia pliku "b" przez Edytor błędów "", lub pozwolić widoku skojarzone z edytora "A" częściowo otworzyć i wyświetlić odpowiedni komunikat o błędzie. Komunikat o błędzie należy poinstruować użytkowników, można zamknąć pliku "b" w niezgodnym edytorze, a następnie ponownie otwórz plik "a" przy użyciu edytora "A". Można też wdrożyć [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> monitowanie użytkownika można zamknąć pliku "b", który jest otwarty w niezgodnym edytorze. Jeśli użytkownik zamyka plik "b", otwieranie pliku "" w edytorze "A" kontynuuje działanie.  
  
## <a name="additional-document-edit-lock-considerations"></a>Zagadnienia dotyczące blokowania edycji dodatkowego dokumentu  
 Jeśli Edytor "A" jest tylko edytorze, który ma dokumentu Edytuj blokady w pliku "b", niż w przypadku, jeśli edytor "B" przechowuje także dokumentu Edytuj blokadę pliku "b" get inaczej. W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **Projektant klas** przykładem wizualnego projektanta, który nie posiada blokady edycji w pliku skojarzonego kodu. Oznacza to, że jeśli użytkownik ma diagramu klas, Otwórz w widoku projektu i jednocześnie Otwieranie pliku skojarzonego kodu i użytkownik modyfikuje plik kodu, ale nie powoduje zapisania zmian, zmiany są również utraci plik diagramu (.cd) klasy. Jeśli **Projektant klas** ma tylko dokument edytować blokadę pliku kodu, użytkownik nie jest proszony o zapisanie zmian podczas zamykania pliku kodu. IDE pyta użytkownika, aby zapisać zmiany, tylko wtedy, gdy użytkownik zamyka **Projektant klas**. Zapisano zmiany są odzwierciedlane w obu plików. Jeśli oba **Projektant klas** i edytora plików kodu posiadanych blokad edycji dokumentu w pliku kodu, a następnie użytkownik jest monitowany o zapisanie podczas zamykania pliku kodu lub w formularzu. W tym momencie zapisane zmiany są uwzględniane w formularzu i pliku kodu. Aby uzyskać więcej informacji na diagramach klas, zobacz [Praca z diagramami klas (Projektant klas)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Należy pamiętać, że jeśli chcesz zablokować edycji dokumentu z systemem innym niż edytora, musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfejsu.  
  
 Wiele razy interfejsu użytkownika projektanta, który modyfikuje pliki kodu programowo zmienia więcej niż jeden plik. W takich przypadkach <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> metoda obsługuje zapisywania jednego lub więcej dokumentów za pomocą klasy **czy chcesz zapisać zmiany w następujących elementach?** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchomionej tabeli dokumentu](../extensibility/internals/running-document-table.md)   
 [Trwałość i uruchamianie tabeli dokumentów](../extensibility/internals/persistence-and-the-running-document-table.md)