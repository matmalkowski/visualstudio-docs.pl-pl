---
title: Używanie czcionek i kolorów | Dokumentacja firmy Microsoft
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
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6db4f030a3367a5fd2fb449b3515643fe6cd6033
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42632769"
---
# <a name="using-fonts-and-colors"></a>Używanie czcionek i kolorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [przy użyciu czcionki i kolory](https://docs.microsoft.com/visualstudio/extensibility/using-fonts-and-colors).  
  
[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Zapewnia obsługę wyświetlania tekstu przy użyciu czcionek i kolorów.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie kolorów i czcionek](../extensibility/font-and-color-overview.md)  
 W tym artykule omówiono ustawienia czcionek i kolorów tekstu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE). Ponadto wprowadza pojęcia kategorii i wyświetlenie elementów i w tym artykule opisano, jak pakietów VSPackage i podstawowy edytor za pomocą atrybutów tekstu.  
  
 [Wprowadzenie czcionkę i kolor informacje dotyczące kolorowania tekstu](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Zawiera wskazówki dotyczące implementowania Kolorowanie tekstu w pakietach VSPackage, zarządzać **kategorie** innych niż **edytora tekstów**.  
  
 [Uzyskiwanie dostępu do przechowywanych czcionkę i kolor ustawienia](../extensibility/accessing-stored-font-and-color-settings.md)  
 Wyjaśnia, jak bieżący czcionek i kolorów ustawień mogą być przechowywane pobierane i stosowane.  
  
 [Implementowanie niestandardowych kategorii i wyświetlenie elementów](../extensibility/implementing-custom-categories-and-display-items.md)  
 W tym artykule opisano podstawowe kroki, według których okna można tworzyć i używać własnego programu **wyświetlania elementów** i **kategorie** do obsługi wyświetlania tekstu.  
  
 Takie podejście wymaga pakietu VSPackage do zaimplementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfejsu i interfejsy powiązane.  
  
 [Porady: dostęp do wbudowanych czcionek i schemat kolorów](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 W tym artykule omówiono, jak zdefiniować i zarejestrować kategorii przy użyciu wbudowanych czcionek i kolorów i zainicjować użycie dostarczane przez system czcionek i kolorów.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Udostępnia wystąpienia `IVsFontAndColorDefaults` lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> interfejs, który odnosi się do określonego elementu na liście **Pokaż ustawienia dla** listy w **czcionki i kolory** strony **Opcje** okno dialogowe.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Włącza VSPackage do obsługi środowiska IDE **czcionki i kolory** strony, definiując domyślny czcionki i kolory w oknie lub składnik interfejsu użytkownika.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Udostępnia mechanizm, za pomocą którego pakietu VSPackage, który zapewnia obsługę czcionek i kolorów można określić grupę wyświetlanego elementu — bardzo kategorię, która reprezentuje sumę dwóch lub więcej kategorii.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Umożliwia VSPackage można pobrać danych czcionek i kolorów lub zapisać go w rejestrze.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Powiadamia pakietów VSPackage przy użyciu czcionek i kolorów informacje o zmianach wprowadzonych w ustawieniach czcionek i kolorów.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Udostępnia narzędzia do pracy z danych wejściowych i wyjściowych, który jest używany przez metody [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **czcionek i kolorów** mechanizm.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Kontroluje, buforowanie ustawienia czcionek i kolorów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)  
 W tym artykule omówiono, jak pakietów VSPackage języka usługi służy do dostosowywania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytora.  
  
 [Kolorowania składni w edytorach niestandardowych](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries sposób, w jaki [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Edytor używa usług językowych do zaimplementowania kolorowanie składni.  
  
 [Rozszerzanie innych części programu Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Opis sposobu użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usługi, aby tworzyć elementy interfejsu użytkownika, które pasują reszty [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

