---
title: "Pobieranie czcionek i kolorów informacje dotyczące tekstu kolorowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e3b31ad2ec080070dec3c68b304f400d204d47a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Pobieranie czcionek i kolorów informacje dotyczące tekstu kolorowania
Proces, który renderuje lub wyświetla tekst kolorowane w elementy interfejsu użytkownika zależy od typu projektu, jego technologii i deweloperów preferencji. **Czcionki i kolory** ustawienia są przechowywane strony właściwości.  
  
 Większości wdrożeń, zawierające tekst pokolorowane muszą `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` i skojarzone interfejsy, dla ustawienia wyświetlania prezentacji, pobieranie i przechowywanie tekstu.  
  
> [!NOTE]
>  W przypadku dostosowywania edytora core (który obsługuje **EditorCategory tekst**), zaleca się używać technologii kolorowanie usługi języka. Aby uzyskać więcej informacji, zobacz [Omówienie kolorów i czcionek](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Pobieranie domyślnej czcionki i informacji o kolorze  
 Wszystkie **czcionki i kolory** powinny być określone ustawienia okna Wyświetlanie tekstu w **wyświetlania elementów** jednego **kategorii**. Aby uzyskać więcej informacji, zobacz [czcionki i kolory, środowisko, opcje — Okno dialogowe](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Aby kolorowanie, pakiet VSPackage musi uzyskać bieżące **czcionki i kolory** ustawienia. Pakiet VSPackage można to zrobić w następujący sposób, w zależności od jego potrzeb:  
  
-   Użyj mechanizmu stanu trwałego czcionek i kolorów można pobrać przechowywane lub bieżącego stanu. Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do przechowywanych czcionkę i ustawienia koloru](../extensibility/accessing-stored-font-and-color-settings.md).  
  
-   Użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfejsu dostarcza dane czcionek i kolorów można pobrać wystąpienia usługi <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, jeśli pakiet VSPackage nie jest również dostawcy czcionek i kolorów.  
  
-   Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> interfejsu.  
  
 Aby upewnić się, że wyniki uzyskane za pomocą sondowania znajdują się w górę do chwili, może być przydatne do użycia <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfejs do określenia, czy aktualizacja jest wymagana przed wywołaniem metody pobierania <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu.  
  
 Po uzyskaniu informacji czcionek i kolorów, przeanalizować tekstu, które mają być wyświetlane, aby zidentyfikować elementy wymagające kolorowania i wyświetl tekst w oknie przy użyciu odpowiednich czcionek i kolorów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Używanie czcionek i tekstu](/dotnet/framework/winforms/advanced/using-fonts-and-text)   
 [Praca z kolorem](/cpp/windows/working-with-color-image-editor-for-icons)   
 [GDI (graficzny interfejs urządzenia)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)