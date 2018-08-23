---
title: Wybór i aktualność w środowisku IDE | Dokumentacja firmy Microsoft
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
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 87796930b8b1f76e7601bfd2dbffdddcf8d32da6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676705"
---
# <a name="selection-and-currency-in-the-ide"></a>Wybór i aktualność w środowisku IDE
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wybór i aktualność w środowisku IDE](https://docs.microsoft.com/visualstudio/extensibility/internals/selection-and-currency-in-the-ide).  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Zintegrowanego środowiska programistycznego (IDE) przechowuje informacje o użytkownikach aktualnie wybrane obiekty za pomocą wyboru *kontekstu*. Za pomocą kontekst zaznaczenia pakietów VSPackage mogą brać udział w walucie śledzenia na dwa sposoby:  
  
-   Poprzez propagowanie waluty informacji na temat pakietów VSPackage środowiska IDE.  
  
-   Monitorując wybory aktualnie aktywnych użytkowników w środowisku IDE.  
  
## <a name="selection-context"></a>Kontekst zaznaczenia  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE globalnie śledzi informacje o walucie IDE w obiekcie kontekstu własnego wyboru globalnego. W poniższej tabeli przedstawiono elementów, które tworzą kontekst zaznaczenia.  
  
|Element|Opis|  
|-------------|-----------------|  
|Bieżącej hierarchii|Zazwyczaj bieżącego projektu; wartość NULL z bieżącej hierarchii wskazuje bieżącego rozwiązania jako całości.|  
|Identyfikator bieżącego elementu|Wybrany element w bieżącej hierarchii; w przypadku wielokrotny w oknie projektu może istnieć wiele bieżących elementów.|  
|bieżący `SelectionContainer`|Zawiera co najmniej jeden obiekt, dla których w oknie właściwości należy wyświetlić właściwości.|  
  
 Ponadto środowisko obsługuje dwie listy globalne:  
  
-   Lista aktywnych identyfikatory poleceń interfejsu użytkownika  
  
-   Lista typów obecnie aktywnym elementem.  
  
### <a name="window-types-and-selection"></a>Typy okien i wybór  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE organizuje systemu windows na dwa ogólne typy:  
  
-   Typ hierarchii systemu windows  
  
-   Okna ramowe, takich jak narzędzia i okna dokumentu  
  
 IDE śledzi waluty inaczej dla każdego z tych typów okna.  
  
 Najbardziej typowe typ projektu jest ono Eksploratorze rozwiązań, który kontroluje IDE. Okno typu projektu śledzi hierarchii globalnej i ItemID kontekst zaznaczenia globalnych i okna zależy od wybranych przez użytkownika, aby określić bieżącą hierarchią. Dla typów projektów systemu windows, środowisko udostępnia globalną usługę <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>za pośrednictwem których pakietów VSPackage można monitorować bieżące wartości dla elementów, Otwórz. Właściwość przeglądania w środowisku jest wymuszany przez tę usługę globalnego.  
  
 Okien ramowych z drugiej strony, umożliwia element DocObject wewnątrz okna ramki wypychania wartość SelectionContext (Trójka hierarchii/ItemID/SelectionContainer). . Okna ramowe korzystania z usługi <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> do tego celu. Element DocObject można wypchnąć tylko wartości w kontenerze zaznaczenia, pozostawiając wartości lokalne dla hierarchii i identyfikator elementu bez zmian, podobnie jak w typowej dokumentów podrzędnego MDI.  
  
### <a name="events-and-currency"></a>Zdarzenia i waluty  
 Mogą wystąpić dwa typy zdarzeń, które mają wpływ na środowisko pojęcie waluty:  
  
-   Zdarzenia, które są przenoszone na poziomie globalnym i Zmień kontekst zaznaczenia ramki okna. Przykłady tego typu zdarzeń okno podrzędne MDI, są otwarte okna narzędzi globalnego otwierana lub okna narzędzi typu projektu otwieranego.  
  
-   Zdarzenia, które zmieniają elementy śledzone w kontekście wybór ramki okna. Przykłady obejmują zmianę w obiekt DocObject lub zmianę w oknie typu projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wybór obiektów kontekstu](../../extensibility/internals/selection-context-objects.md)   
 [Opinia dla użytkownika](../../extensibility/internals/feedback-to-the-user.md)

