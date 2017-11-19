---
title: Kontekst projektu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 368f6ecb67bc8b01df975da6e68e95b553a0e31d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="project-context"></a>Kontekst projektu
Gdy użytkownik dodaje lub współpracuje z projektów i elementów projektu, IDE korzysta pojęcie kontekst projektu, aby określić, jak różne operacje powinny być wykonywane.  
  
 Zazwyczaj pliki są standardowe projektu obiekty utworzone przez użytkownika jawnie wybierając **nowy projekt** polecenia lub udostępnianych przez wybranie **Otwórz projekt** na  **Plik** menu. W takich przypadkach plików są tworzone i otwarty w kontekście projektu i typ projektu Określa kontekst dla edycji dokumentu.  
  
 Niektóre projekty zapewniają bardzo zaawansowane kontekstu. Na przykład projekt zarządza programowego, zakres projektu przestrzeni nazw lub zakresie projektu połączenia bazy danych dla powiązania danych. Użytkownik może często otwierać plików lub połączenia z bazą danych bezpośrednio za pomocą obiektu konkretnego projektu, na przykład element projektu wyświetlana w Eksploratorze rozwiązań.  
  
 W pozostałych godzinach kontekst projektu elementu nie został jawnie określony. Na przykład kontekst elementu nie jest dostępna, gdy użytkownik otwiera plik, wybierając **Otwórz istniejący plik** na **pliku** menu, gdy debuger działa na plik, lub po kliknięciu przez użytkownika **Znajdź w plikach** w **Znajdź i Zamień** okno dialogowe. Do obsługi tych sytuacji wywołania IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> do zarządzania procesem odnajdywania najlepsze projektu, aby otworzyć dokument.  
  
## <a name="see-also"></a>Zobacz też  
 [Priorytet projektu](../../extensibility/internals/project-priority.md)   
 [Dodawanie projekt oraz szablony elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)