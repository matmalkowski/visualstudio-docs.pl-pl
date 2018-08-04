---
title: 'Porady: używanie wbudowanych elementów z możliwością kolorowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 658b024a57912bf96a7988363f2bf363e9cb1f0a
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512619"
---
# <a name="how-to-use-built-in-colorable-items"></a>Porady: używanie wbudowanych elementów z możliwością kolorowania
Przed użyciem wbudowanych elementów z możliwością kolorowania użytkownik musi najpierw zasygnalizowania do zintegrowanego środowiska programistycznego (IDE) są one udostępniane własne niestandardowe elementy z możliwością kolorowania, w tym przypadku byłaby <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> obiektów. Możesz to zrobić, ustawiając wpis rejestru dla usługi w języka.  
  
## <a name="to-use-built-in-colorable-items"></a>Aby użyć wbudowanych elementów z możliwością kolorowania  
  
1.  W obszarze **HKEY_LOCAL_MACHINE\VisualStudio\\usług \Languages\Language < X.Y >\\< nazwa języka\>**, gdzie \<X.Y > wersja [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i \<Nazwa języka > jest nazwą Twojego języka, Utwórz wartości wpisu rejestru DWORD o nazwie **RequestStockColors**.  
  
2.  Ustaw **RequestStockColors** wartości wpisu rejestru w celu *1*.  
  
     Po utworzeniu wpisu rejestru colorizer Twojej firmy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metoda może używać członkowie <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> wyliczeniu, aby wypełnić tablicę atrybutów koloru do użycia przez edytor.  
  
    > [!NOTE]
    >  Nie należy ustawiać ten wpis rejestru, jeśli udostępniasz niestandardowe elementy z możliwością kolorowania. Aby uzyskać więcej informacji, zobacz [niestandardowe elementy z możliwością kolorowania](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Kolorowanie składni w edytorach niestandardowych](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementowanie kolorowania składni](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Niestandardowe elementy z możliwością kolorowania](../../extensibility/internals/custom-colorable-items.md)   
 [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service2.md)