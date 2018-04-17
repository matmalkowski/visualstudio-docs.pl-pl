---
title: 'Porady: Otwórz edytory dla otwartych dokumentów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 621ed4436160b6f491abb34d8194c75595d9a54c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-open-editors-for-open-documents"></a>Porady: Otwórz edytory dla otwarte dokumenty
Przed projekt zostanie otwarte okno dokumentu, projekt najpierw należy określić czy plik jest już otwarte okno dokumentu dla innego edytora. Plik można otworzyć w edytorze specyficznego dla projektu, lub jeden z standardowe edytory zarejestrowany w usłudze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="opening-a-project-specific-editor"></a>Otwieranie Edytora specyficznego dla projektu  
 Poniższa procedura umożliwia Otwórz Edytor specyficznego dla projektu dla pliku, który jest już otwarty.  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Aby otworzyć Edytor specyficznego dla projektu, dla której plik otwarty  
  
1.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metody.  
  
     To wywołanie zwraca wskaźników do hierarchii, element hierarchii i ramki okna dokumentu, w razie potrzeby.  
  
2.  Jeśli dokument jest otwarty, projekt musi sprawdzić, czy istnieje tylko obiekt danych dokumentu Jeśli obiekt widoku dokument jest również obecny.  
  
    -   Jeśli istnieje obiekt widoku dokumentu, a ten widok jest przeznaczony dla innej hierarchii lub element hierarchii, projekt używa wskaźnik do ramki okna widoku do resurface istniejące okno.  
  
    -   Jeśli istnieje obiekt widoku dokumentu, a ten widok jest przeznaczony dla elementu hierarchii i tej samej hierarchii, projektu można otworzyć drugiego widoku Jeśli można dołączyć do podstawowego obiektu danych dokumentu. W przeciwnym razie projekt powinien używać wskaźnika do widoku okienka do resurface istniejące okno.  
  
    -   Jeśli tylko obiekt danych dokumentu istnieje, projektu należy określić, czy obiektu danych dokumentu można używać jej w widoku. Jeśli obiekt danych dokumentu jest zgodny, pełną kroki omówione w [otwierania Edytora określonego projektu](../extensibility/how-to-open-project-specific-editors.md).  
  
     Jeśli obiekt danych dokumentu nie jest zgodny, błąd powinien zostać wyświetlony do użytkownika, który wskazuje, że plik jest aktualnie w użyciu. Ten błąd powinien być wyświetlany tylko w wypadku przejściowych np. Jeśli plik jest kompilowany w tym samym czasie użytkownik próbuje otworzyć plik za pomocą edytora innych niż [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] core edytora tekstu. Edytor tekstu core można udostępniać obiekt danych dokumentu przez kompilator.  
  
3.  Jeśli dokument nie jest otwarty, ponieważ nie istnieje obiekt danych dokumentu lub obiekt widoku dokumentu, wykonaj kroki [otwierania Edytora określonego projektu](../extensibility/how-to-open-project-specific-editors.md).  
  
## <a name="opening-a-standard-editor"></a>Otwieranie Edytora Standard  
 Użyj poniższej procedury można otworzyć standardowego edytora dla pliku, który jest już Otwórz.  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>Aby otworzyć standardowego edytora dla otwartego pliku  
  
1.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
     Ta metoda sprawdza najpierw, czy dokument nie jest już otwarty przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>. Jeśli dokument jest już otwarty, jest resurfaced okna edytora.  
  
2.  Jeśli dokument nie jest otwarty, wykonaj kroki [porady: otwieranie standardowe edytory](../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md)   
 [Porady: Otwórz edytory specyficznego dla projektu](../extensibility/how-to-open-project-specific-editors.md)   
 [Instrukcje: otwieranie standardowych edytorów](../extensibility/how-to-open-standard-editors.md)