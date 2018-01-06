---
title: "Przy użyciu znaczników tekstu przy użyciu interfejsu API starszych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 98c889bc1bc128a941f726348781a633799475de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-text-markers-with-the-legacy-api"></a>Przy użyciu znaczników tekstu przy użyciu interfejsu API starsza wersja
Znacznik tekst jest przestawne zakres tekstu w buforze, który może mieć wpływ na wyświetlanie i zachowanie obszaru tekstu. Znaczniki zawierają punkty przerwania, zakładki faliste podkreślenie i regionów tylko do odczytu. Znacznikach tekstu zasadniczo różnią się od kolorowanie składni. Kolorowanie składni jest szybkim sposobem przekazywania składni języka, który jest skojarzony z obszaru tekstu. Kolorowanie składni zazwyczaj jest wymagany, gdy Windows odświeża ekranu, gdy szybkość jest istotna. Kolorowanie składni zmienia kolor tekstu. Inne właściwości tekstu, można zmienić znacznikach tekstu. Znaczniki tekst można "float" i zastosować specjalnego zachowania i kolorowania.  
  
 Ze względu na wydajność obciążenia związanego z znacznikach tekstu, nie należy tworzyć wiele znaczników dla buforów z tekstu. Każdy znacznik jest za każdym razem, że użytkownik edytuje zawartości buforu aktualizowane.  
  
> [!NOTE]
>  Użytkownicy mogą zmieniać kolor typ znacznika widoczne, ale nie jego kształtu i styl. Aby uzyskać więcej informacji, zobacz [czcionki i kolory, środowisko, opcje — Okno dialogowe](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Porady: Dodawanie znaczników tekstu standardowego](../extensibility/how-to-add-standard-text-markers.md)|Opisuje sposób dodawania udostępniane przez typ znacznika tekstu standardowego [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Edytor core do widoku tekstu.|  
|[Porady: Implementowanie znaczników błąd](../extensibility/how-to-implement-error-markers.md)|Opisuje sposób wdrożenia wystąpienie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] znacznik służy do wskazywania błędów przy użyciu czerwone faliste podkreślenie.|  
|[Porady: Tworzenie niestandardowego tekstu znaczników](../extensibility/how-to-create-custom-text-markers.md)|Opisuje sposób tworzenia i Dodaj tekst niestandardowy typ znacznika do widoku tekstu.|  
|[Porady: Użyj znacznikach tekstu](../extensibility/how-to-use-text-markers.md)|Wyjaśniono, jak dodać znacznikach tekstu.|  
|[W edytorze Core](../extensibility/inside-the-core-editor.md)|Zawiera opis funkcji edytora rdzeni i szczegółowe informacje na temat sposobu dostosowywania edytora core.|  
|[Funkcje edycji](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Zawiera opis funkcji dostępnych w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] core edytora.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Udostępnia mechanizm uniform uzyskiwania informacji na temat typu określonego tekstu znacznika, czy wstępnie zdefiniowane przez Edytor lub zarejestrowany przez pakiet VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Zapewnia dostęp do i dopasowuje pozycję znacznika tekstu w buforze tekstu przy użyciu dwuwymiarowe współrzędne.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Udostępnia metody do zarządzania znacznikach tekstu.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Udostępnia wywołania zwrotne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE i inne procesy, które są używane do dostosowywania znacznika tekstu.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Rozszerza funkcje, które są dostępne za pośrednictwem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu, zapewniając dodatkowe wywołań zwrotnych.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Rozszerza funkcje, które są dostępne za pośrednictwem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu, zapewniając dodatkowe wywołań zwrotnych.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Umożliwia typu znacznik w celu ustalenia, czy innych typów znaczników udostępniać ten sam zestaw kolorów.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Udostępnia kontekst dla znaczników tekstu w edytorze core. Dla każdego typu znacznika tekstu w edytorze core IDE tworzy oddzielne <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> obiektu.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Program obsługi, który jest dostępne znaczniki, których symboli obsługuje edycję przeciągania i upuszczania. Symbol jest ikonę, która wskazuje położenie znacznika.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Zwraca <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> interfejsu z usługą, która zapewnia tekstu znacznikami inne pakiety VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Zapewnia dostęp do i dopasowuje pozycję znacznika tekstu w buforze tekstu przy użyciu współrzędnych jednowymiarowa. Jeśli to możliwe, należy używać tego interfejsu.