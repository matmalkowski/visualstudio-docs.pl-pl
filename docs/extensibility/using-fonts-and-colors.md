---
title: Używanie czcionek i kolorów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4415d00e5a1233bfdf14dbc86a3a7ed2f7b8e770
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="using-fonts-and-colors"></a>Używanie czcionek i kolorów
[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Zapewnia obsługę czcionki i kolory do wyświetlania tekstu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie kolorów i czcionek](../extensibility/font-and-color-overview.md)  
 W tym artykule omówiono ustawienia czcionek i kolorów tekstu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE). Również pojęcia związane z kategorii i Wyświetl elementy, a w tym artykule opisano, jak pakiety VSPackage i Edytor core używają atrybutów tekstu.  
  
 [Pobieranie czcionek i kolorów informacje dotyczące tekstu kolorowania](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Zawiera wskazówki dotyczące wprowadzania tekstu kolorowania w VSPackages zarządzające **kategorii** innych niż **Edytor tekstu**.  
  
 [Dostęp do przechowywanej czcionek i kolorów](../extensibility/accessing-stored-font-and-color-settings.md)  
 Wyjaśniono, jak bieżący czcionek i kolorów ustawienia mogą być przechowywane, pobrać i stosowane.  
  
 [Implementowanie niestandardowych kategorii i wyświetlania elementów](../extensibility/implementing-custom-categories-and-display-items.md)  
 Opisano podstawowe kroki, za pomocą których można tworzyć i używać własnej z okna **wyświetlania elementów** i **kategorii** do obsługi wyświetlania tekstu.  
  
 Ta metoda wymaga pakiet VSPackage do zaimplementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfejsu i interfejsy powiązane.  
  
 [Porady: dostęp do wbudowanych czcionek i schemat kolorów](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 W tym artykule omówiono sposób zdefiniować i zarejestrować kategorię za pomocą wbudowanych czcionek i kolorów i inicjowania stosowania kolorów i czcionek dostarczane przez system.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Udostępnia wystąpienie `IVsFontAndColorDefaults` lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfejsu odpowiadającego danego elementu na liście **Pokaż ustawienia dla** na liście **czcionki i kolory** strony **Opcje** okno dialogowe.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Włącza pakiet VSPackage do obsługi IDE **czcionki i kolory** strony, definiując domyślnej czcionki i kolory w oknie lub składnik interfejsu użytkownika.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Udostępnia mechanizm, za pomocą którego pakiet VSPackage, który zapewnia obsługę czcionek i kolorów można określić grupę wyświetlanego elementu - nadtypem kategorię, która reprezentuje sumę dwóch lub więcej kategorii.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Włącza pakiet VSPackage można pobrać danych czcionek i kolorów lub zapisać go w rejestrze.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Powiadamia VSPackages używanym czcionek i kolorów informacji na temat zmian w ustawieniach czcionek i kolorów.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Udostępnia narzędzia do pracy z danymi wejściowymi i wyjściowymi, który jest używany przez metody [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **czcionek i kolorów** mechanizmu.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Określa buforowanie ustawienia czcionek i kolorów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)  
 W tym artykule omówiono, jak VSPackages języka usługi służy do dostosowywania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edytora.  
  
 [Kolorowania składni w edytorach niestandardowych](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries jak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Edytor korzysta z usług języka Aby zaimplementować kolorowanie składni.  
  
 [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Wyjaśniono, jak używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usługi w celu utworzenia elementów interfejsu użytkownika, zgodne z resztą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].