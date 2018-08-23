---
title: Kontekst projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 280864c69e75d37c73095320787d74e61a93ab38
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678149"
---
# <a name="project-context"></a>Kontekst projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [kontekstem projektu](https://docs.microsoft.com/visualstudio/extensibility/internals/project-context).  
  
Gdy użytkownik dodaje lub współpracuje z projektów i elementów projektu, IDE używa pojęcie kontekstem projektu, aby określić, jak różne operacje, które powinny być wykonywane.  
  
 Zazwyczaj pliki są standardowy projekt obiektów tworzonych użytkownik jawnie, wybierając **nowy projekt** polecenia lub udostępnia, wybierając **Otwórz projekt** polecenie  **Plik** menu. W takich przypadkach pliki są tworzone i otwierane w ramach projektu, a typ projektu Określa kontekst dla edytowania dokumentu.  
  
 Niektóre projekty zawierają bardzo szeroki kontekst. Na przykład projekt zarządza o zasięgu projektu, programowe przestrzeni nazw lub zakresie projektu połączenia bazy danych dla powiązania danych. Użytkownik może często otwierać pliki lub połączenia z bazą danych bezpośrednio przy użyciu obiektu określonego projektu, takich jak element projektu wyświetlane w Eksploratorze rozwiązań.  
  
 W pozostałym czasie kontekstem projektu elementu nie jest jawnie określona. Na przykład kontekst elementu nie jest dostępne po użytkownik otwiera plik, wybierając **Otwórz istniejący plik** polecenie **pliku** menu, gdy debuger działa z pliku lub po kliknięciu przez użytkownika **Znajdź w plikach** polecenia w pliku **Znajdź i Zamień** okno dialogowe. Do obsługi tych sytuacji wywołania IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> do zarządzania procesem odnajdywania najlepsze projekt, aby otworzyć dokument.  
  
## <a name="see-also"></a>Zobacz też  
 [Priorytet projektu](../../extensibility/internals/project-priority.md)   
 [Dodawanie projektu i szablonów elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)

