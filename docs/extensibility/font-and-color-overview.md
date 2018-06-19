---
title: Omówienie kolorów i czcionek | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8185d5c931ccf0b3b15fba10405cf050eb7c6241
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130235"
---
# <a name="font-and-color-overview"></a>Omówienie kolorów i czcionek
W tym temacie omówiono ustawienia czcionek i kolorów tekstu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE). Również wprowadza pojęcia związane z kategorii i Wyświetl elementy, a także opisano, jak pakiety VSPackage i Edytor core używają atrybutów tekstu.  
  
## <a name="the-fonts-and-colors-property-page"></a>Czcionki i kolory strony właściwości  
 Możesz zarządzać atrybutów tekstu wyświetlanego w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE) za pośrednictwem **czcionki i kolory** strony właściwości. Aby znaleźć **czcionki i kolory** na stronie właściwości **narzędzia** menu, kliknij przycisk **opcje**. Rozwiń węzeł **środowiska**, a następnie kliknij przycisk **czcionki i kolory**.  
  
## <a name="categories-and-display-items"></a>Kategorie i wyświetlania elementów  
 Czcionki i kolory są podzielone na **kategorii** i **wyświetlania elementów**.  
  
-   A **kategorii** jest logiczną lub funkcjonalności kontener dla wielu **wyświetlania elementów**.  
  
     Lista **kategorii** w **Pokaż ustawienia dla** w polu listy rozwijanej **czcionki i kolory** strony właściwości.  
  
-   A **wyświetlanego elementu** jest jednostką dobrze zdefiniowany tekstu, takie jak komentarz, ciągu lub strukturą kontrolki, która ma kolorowane podczas wyświetlania.  
  
 Każdy **wyświetlanego elementu** jednoznacznie jest zdefiniowany w **kategorii** go zawiera. W rezultacie więcej niż jeden **kategorii** może mieć **wyświetlanego elementu** o takiej samej nazwie.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>Pakiet VSPackage kontrolę nad czcionki i kolory  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Umożliwia VSPackages do:  
  
-   Zdefiniuj czcionek i kolorów **kategorii**.  
  
-   Określ czcionki i kolory używane do prezentowania **wyświetlania elementów**.  
  
-   Interakcje z **czcionki i kolory** strony właściwości.  
  
-   Łączny wielu **kategorii** w grupach.  
  
-   Utrwalania zmian w domyślnych ustawieniach.  
  
 Istnieją dwa sposoby interakcji z opcjami czcionek i kolorów w [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].  
  
-   Jednym ze sposobów jest określany jako *kolorowanie składni*. Jest on używany przez pakiet VSPackage, który dostosowuje istniejące [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edytora w celu wdrożenia usługi języka i utworzyć źródło edytora.  
  
     Tylko jeden **kategorii** obsługuje ten mechanizm, to znaczy, **Edytor tekstu**.  
  
-   Więcej ogólnych zamiast obsługuje wszystkich innych **kategorii** i składniki interfejsu użytkownika innych niż Edytor źródła podczas wyświetlania tekstu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Ustawienia podstawowe Edytor tekstu  
 Ustawienia czcionek i kolorów podstawowych edytora obiektu usługi języka są regulowane przez **EditorCategory tekst** w **Pokaż ustawienia dla** w polu listy rozwijanej **czcionki i kolory** stronę właściwości.  
  
 Podczas pracy z edytory, należy używać specjalnych czcionki i mechanizmu kontroli kolor udostępniający usługi języka kontroli i rozszerzać **Edytor tekstu** ustawienia. Mechanizm jest określany jako *kolorowanie składni* i zawiera:  
  
-   Uproszczona metoda zarządzania czcionki i kolory wyświetlania elementów.  
  
     Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
-   Mechanizm kolorowania dobrze zdefiniowany i zoptymalizowane.  
  
     Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
-   Możliwość zarówno używanie wbudowanych wyświetlania elementów z **EditorCategory tekst** i rozszerzyć je.  
  
     Aby uzyskać więcej informacji, zobacz [porady: użycie wbudowanych elementów Colorable](../extensibility/internals/how-to-use-built-in-colorable-items.md) i [Colorable elementy niestandardowe](../extensibility/internals/custom-colorable-items.md).  
  
-   Automatyczne trwałości bieżącego stanu zarówno wbudowanych i niestandardowych wyświetlania elementów z **Edytor tekstu** kategorii.  
  
 Aby uzyskać więcej informacji na temat składni, zobacz kolorowaniu [kolorowania składni w starsza wersja usługi języka](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy starszej wersji w edytorze](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Kolorowanie składni w starszej wersji usługi językowej](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)