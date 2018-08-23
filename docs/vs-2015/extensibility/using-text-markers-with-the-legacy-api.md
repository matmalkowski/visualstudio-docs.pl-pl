---
title: Znaczniki tekstu przy użyciu starszej wersji interfejsu API | Dokumentacja firmy Microsoft
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
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b276a678d4b5e97e3ef949bdf1fd74b37070f9d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42627548"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Znaczniki tekstu przy użyciu starszej wersji interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [przy użyciu znaczników tekstu przy użyciu starszej wersji interfejsu API](https://docs.microsoft.com/visualstudio/extensibility/using-text-markers-with-the-legacy-api).  
  
Znacznik tekstu jest ruchomy zakres tekstu w buforze, które mogą mieć wpływ na wyświetlanie i zachowanie region tekstu. Znaczniki zawierają punkty przerwania, zakładek, faliste podkreślenia i regionów tylko do odczytu. Znaczniki tekstu po prostu różnią się od kolorowanie składni. Kolorowanie składni to szybki sposób komunikowania się składni języka, która jest skojarzone z regionem tekstu. Kolorowanie składni ogólnie jest wymagany, gdy Windows odświeża ekran, gdy szybkość jest istotna. Kolorowanie składni zmienia kolor tekstu. Znaczniki tekst można zmienić innych właściwości tekstu. Znaczniki tekstu można "float" i zastosować specjalnego zachowania i kolorowania.  
  
 Ze względu na zmniejszenie wydajności związane ze znacznikami tekst nie należy tworzyć wielu znaczników swoje bufory tekstu. Każdy znacznik jest aktualizowana w każdym razem, gdy użytkownik dokona edycji zawartości buforu.  
  
> [!NOTE]
>  Użytkownicy mogą zmieniać kolor typu znacznika widoczne, ale nie jego kształtu i stylu. Aby uzyskać więcej informacji, zobacz [czcionki i kolory, środowisko, opcje, okno dialogowe](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Porady: Dodawanie znaczników standardowy tekst](../extensibility/how-to-add-standard-text-markers.md)|W tym artykule opisano sposób dodawania tekstu standardowego typu znaczników, dostarczone przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytorze podstawowych funkcji do widoku tekstu.|  
|[Porady: Implementowanie znaczniki błędów](../extensibility/how-to-implement-error-markers.md)|W tym artykule opisano sposób wdrażania wystąpienia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] znacznik, który służy do sygnalizowania błędów przy użyciu czerwone faliste podkreślenia.|  
|[Porady: Tworzenie niestandardowego tekstu znaczników](../extensibility/how-to-create-custom-text-markers.md)|W tym artykule opisano, jak utworzyć i dodać typ znacznika niestandardowego tekstu do widoku tekstu.|  
|[Porady: Korzystanie ze znaczników tekstu](../extensibility/how-to-use-text-markers.md)|Wyjaśnia, jak dodawać znaczniki tekstu.|  
|[W edytorze podstawowych](../extensibility/inside-the-core-editor.md)|Opisuje funkcje edytora podstawowe i szczegółowe informacje na temat sposobu dostosowywania podstawowy edytor.|  
|[Funkcje edytora](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|W tym artykule opisano funkcje dostępne w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytorze podstawowych funkcji.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Udostępnia mechanizm jednolitego uzyskiwania informacji na temat typu znacznika określonym tekstem, czy wstępnie zdefiniowane przez Edytor lub zarejestrowany przez funkcję pakietu VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Zapewnia dostęp do, a następnie dopasowuje pozycję znacznika tekstu w buforze tekstu przy użyciu dwuwymiarowe współrzędne.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Udostępnia metody dla zarządzania znaczników tekstu.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Umożliwia wywołania zwrotne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE i inne procesy, które są używane do dostosowywania znacznika tekstu.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Rozszerza funkcjonalność, która jest dostępna za pośrednictwem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu, zapewniając dodatkowe wywołania zwrotne.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Rozszerza funkcjonalność, która jest dostępna za pośrednictwem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu, zapewniając dodatkowe wywołania zwrotne.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Włącza typ znacznika ustalić, czy innych typów znaczników udostępnić ten sam zestaw kolorów.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Udostępnia kontekst dla znaczników tekstu w edytorze podstawowych. Dla każdego typu znacznika tekstu, który znajduje się w edytorze podstawowych, środowisko IDE tworzy oddzielny <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> obiektu.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Program obsługi, który jest udostępniany dla znaczników, którego symbole obsługi przeciągania i upuszczania do edycji. Glif znajduje się ikona, wskazującą położenie znaczników.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Zwraca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> interfejs z usługą, która zawiera tekst znaczniki do innych pakietów VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Zapewnia dostęp do, a następnie dopasowuje pozycję znacznika tekstu w buforze tekstu za pomocą współrzędnych jednowymiarowa. Jeśli jest to możliwe, należy używać tego interfejsu.

