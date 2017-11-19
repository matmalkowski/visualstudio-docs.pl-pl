---
title: "Porady: używanie wbudowanych elementów Colorable | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 519b842f99ff3e4460626b82aafd24a02f9e720d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-built-in-colorable-items"></a>Porady: używanie wbudowanych elementów Colorable
Przed użyciem wbudowanych elementów colorable, użytkownik musi najpierw sygnału zintegrowane środowisko programistyczne (IDE) nie udostępniasz własne niestandardowe colorable elementów, które w tym przypadku <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> obiektów. W tym celu ustawienia wpisu rejestru dla usługi języka.  
  
### <a name="to-use-built-in-colorable-items"></a>Aby użyć wbudowanych elementów colorable  
  
1.  W obszarze HKEY_LOCAL_MACHINE\VisualStudio\\*X.Y*usług \Languages\Language\\*nazwy języka*, gdzie *X.Y* to wersja [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i *nazwy języka* to nazwa Twojego języka, Utwórz wartości wpisu rejestru DWORD o nazwie `RequestStockColors`.  
  
2.  Ustaw `RequestStockColors` wartości wpisu rejestru do 1.  
  
     Po utworzeniu wpisu rejestru, colorizer Twojej firmy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metoda może używać elementów członkowskich <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> wyliczeniu, aby wypełnić tablicę atrybutów koloru do użytku przez edytor.  
  
    > [!NOTE]
    >  Nie należy ustawiać ten wpis rejestru, jeśli udostępniasz niestandardowe elementy colorable. Aby uzyskać więcej informacji, zobacz [Colorable elementy niestandardowe](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kolorowania w edytorach niestandardowych](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Kolorowania w starsza wersja usługi języka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementowanie kolorowanie składni](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Niestandardowe elementy Colorable](../../extensibility/internals/custom-colorable-items.md)   
 [Zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service2.md)