---
title: "Przegląd okna właściwości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1f766fe903df4f7a7ea36fb4ec1654b889457f65
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="properties-window-overview"></a>Omówienie okno właściwości
**Właściwości** okna jest używana do wyświetlania właściwości dla obiekt wybrany w dwa główne typy dostępnych w systemie windows [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE). Te dwa typy systemu windows są:  
  
-   Okna narzędzi, takich jak Eksplorator rozwiązań, Widok klas i obiektów przeglądarki  
  
-   Okna dokumentów zawierających takie edytory i projektantom jako projektant formularzy, edytora XML i edytora HTML  
  
## <a name="using-the-properties-window"></a>W oknie właściwości  
 **Właściwości** okno wyświetla właściwości jednego lub wielu wybrane elementy. Jeśli zaznaczono wiele elementów, zostanie wyświetlony przecięcie wszystkie właściwości dla wszystkich wybranych obiektów.  
  
 Zdarzenia związane z obiektu wybranego w oknie projektowania formularza lub edytora HTML przy użyciu metadanych modelu COM + są wyświetlane w **właściwości** okna. Na przykład można wybrać przycisk i wyświetlić jej skojarzonego zdarzenia, takie jak `OnClick` zdarzenie może odnosić się do tego przycisku.  
  
 Zdarzenia wyświetlane w **właściwości** okna są używane przede wszystkim z obiektami, które są powiązane z kodu. Jeśli edytujesz formacie, który nie ma nic wspólnego z kodu nie będą mieć żadnych zdarzeń. Zdarzenia są wyświetlane tylko w **właściwości** okna, jeśli jest powiązaniem między systemami kodu i niektóre zdarzenia związane z określonymi obiektami. Przykładem tego może być kodzie wybrany obiekt, który wykonuje po uaktywnieniu tego obiektu.  
  
 W poniższej tabeli wymieniono głównej interfejsy używane przez **właściwości** okna.  
  
|Nazwa interfejsu|Opis|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Zawiera listę kategorii do **właściwości** okna i mapy każdej właściwości do kategorii.|  
|[Interfejs IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)|Udostępnia metody i właściwości do programowania narzędzia i inne aplikacje obsługujące automatyzację obiektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Zawiera przyciski wielokropek (...) o nazwie *konstruktorów* który okna modalnego okna dialogowego implementowane przez sam obiekt. Używany, gdy wartość nie jest łatwo typu przez użytkownika w polu tekstowym. Na przykład mogą być wykorzystane do otwarcia próbnika kolorów, który określa wartości RGB.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Zapewnia dostęp do obiektów używane do aktualizowania informacji wyświetlanych w **właściwości** okna. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>jest implementowany przez VSPackages dla każdego okna zawierającego wybieranych obiektów powiązanych właściwości do wyświetlenia.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Zawiera informacje o typie obiektu, takiego jak metody interfejsu i pola struktury.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Umożliwia VSPackages, aby otrzymywać powiadomienia o zdarzeniach zaznaczenia oraz do pobierania informacji na temat bieżącej hierarchii projektu, element, wartość elementu i kontekst interfejsu użytkownika poleceń.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Udostępnia środowisko z dostępem do wielokrotny.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Używane w celu dostarczania zlokalizowanych nazw na niektóre właściwości wyświetlane w **właściwości** okna.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Powiadamia zarejestrowanych VSPackages zmian do bieżącego zaznaczenia, wartość elementu lub kontekst poleceń interfejsu użytkownika.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Powiadamia środowiska zmiany w bieżącym zaznaczeniu i zapewnia dostęp do informacji elementu i hierarchii odnoszących się do nowego zaznaczenia.|  
  
 Aby uzyskać więcej informacji o `IDispatch`, zobacz bibliotece MSDN.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)   
 [Pola i interfejsy okna właściwości](../../extensibility/internals/properties-window-fields-and-interfaces.md)