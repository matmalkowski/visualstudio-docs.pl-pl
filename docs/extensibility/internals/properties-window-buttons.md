---
title: Przyciski okna właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 361333fdfceda28ecd78dc54145fded716ee81eb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130706"
---
# <a name="properties-window-buttons"></a>Przyciski okno właściwości
W zależności od języka programowania i typ produktu, domyślnie na pasku narzędzi są wyświetlane przyciski niektórych **właściwości** okna. We wszystkich przypadkach **według kategorii**, **Alphabetized**, **właściwości**, i **strony właściwości** są wyświetlane przyciski. W programie Visual C# i Visual Basic **zdarzenia** przycisk będzie również wyświetlana. W niektórych projektów Visual C++ **VC ++ wiadomości** i **zastępuje VC** są wyświetlane przyciski. Dodatkowe przyciski mogą być wyświetlane dla innych typów projektów. Aby uzyskać więcej informacji na temat przycisków w **właściwości** okna, zobacz [okna właściwości](../../ide/reference/properties-window.md).  
  
## <a name="implementation-of-properties-window-buttons"></a>Implementacja przycisków w oknie właściwości  
 Po kliknięciu **według kategorii** przycisk wywołań Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> interfejsu dla obiektu, który ma fokus, aby posortować według kategorii jego właściwości. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> jest wdrażana w `IDispatch` obiektów, które są prezentowane **właściwości** okna.  
  
 Istnieje 11 kategorii wstępnie zdefiniowanych właściwości, które mają wartości ujemnych. Można zdefiniować niestandardowe kategorie, ale firma Microsoft zaleca, aby przypisać ich wartość dodatnią, aby odróżnić je od wstępnie zdefiniowanych kategorii.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> Metoda zwraca wartość właściwości odpowiednią kategorię dla określonej właściwości. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> Metoda zwraca ciąg zawierający nazwę kategorii. Masz zapewnienie wsparcia dla kategorii niestandardowej wartości, ponieważ wartości kategorii standardowe właściwości wie, Visual Studio.  
  
 Po kliknięciu **Alphabetized** przycisku, właściwości są wyświetlane w porządku alfabetycznym według nazwy. Nazwy są pobierane przez `IDispatch` zgodnie z algorytmem sortowania zlokalizowane.  
  
 Podczas **właściwości** okno jest otwarte, **właściwości** przycisk automatycznie jest wyświetlany jako wybrany. W innych częściach środowiska jest wyświetlany przycisk tego samego i kliknięcie, aby wyświetlić **właściwości** okna.  
  
 **Strony właściwości** przycisk jest niedostępny, jeśli `ISpecifyPropertyPages` nie została zaimplementowana dla wybranego obiektu. Właściwości zależne od konfiguracji wyświetlania, które są zwykle skojarzone z rozwiązań i projektów stron właściwości, ale można można je również skojarzony z elementów projektu (na przykład w programie Visual C++).  
  
> [!NOTE]
>  Nie można dodać przycisków paska narzędzi **właściwości** oknie za pomocą kodu niezarządzanego. Aby dodać przycisku paska narzędzi, należy utworzyć obiekt zarządzany, którego pochodzi z <xref:System.Windows.Forms.Design.PropertyTab>.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)