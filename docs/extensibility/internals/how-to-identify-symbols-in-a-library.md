---
title: 'Porady: Identyfikowanie symbole w bibliotece | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 60365f3722ae4e2c1f8b52dacc3df03840fb3304
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-identify-symbols-in-a-library"></a>Porady: Identyfikowanie symbole w bibliotece
Przeglądanie symbol narzędzia wyświetlanie widoków hierarchiczna symboli. Symbole reprezentują przestrzeni nazw, obiektów, klas, elementy członkowskie klasy i inne elementy języka.  
  
 Każdy symbol w hierarchii można zidentyfikować przez nawigacji informacje przekazywane przez bibliotekę symboli do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Menedżera obiektów za pomocą następujących interfejsów:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.,  
  
 Lokalizacja symbolu w hierarchii odróżnia symbolu. Umożliwia przeglądanie symbol narzędzia można przejść do określony symbol. Unikatowa, w pełni kwalifikowaną ścieżkę do symbolu Określa lokalizację. Każdy element w ścieżce jest węzłem. Ścieżka rozpoczyna się od węzła najwyższego poziomu i kończy określony symbol. Jeśli metoda M1 jest elementem członkowskim klasy C1 C1, a w przestrzeni nazw N1 pełną ścieżkę metody M1 jest N1. C1. M1. Ta ścieżka zawiera trzy węzły: N1, C1 i M1.  
  
 Informacje o nawigacji umożliwia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Menedżera obiektów lokalizowanie, wybierz i Zachowaj wybrane symbole w hierarchii. Umożliwia przechodzenie z jednego przeglądania narzędzia do innego. Podczas używania **przeglądarki obiektów** do przeglądania symbole w [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektu, można kliknij prawym przyciskiem myszy metodę i rozpocząć **przeglądarce wywołań** narzędzia do wyświetlenia na wykresie wywołania metody.  
  
 Dwie formy opisują lokalizację symbolu. Forma kanoniczna opiera się na pełną ścieżkę symbolu. Reprezentuje unikatowy pozycji symbolu w hierarchii. Nie jest zależny od narzędzia przeglądanie symbolu. Aby uzyskać informacje forma kanoniczna [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obiekt Menedżera wywołań <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> — metoda. Prezentacja formularz określa lokalizację symbolu w określonym narzędziu przeglądanie symbolu. Położenie symbolu jest położeniu innych symboli w hierarchicy. Dany symbol może mieć kilka ścieżek prezentacji, ale tylko jednej ścieżki kanonicznej. Na przykład, jeśli klasa C1 jest dziedziczona z klasy C2, obie klasy znajdują się w przestrzeni nazw N1 **przeglądarki obiektów** wyświetla następujące hierarchiczne drzewo:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 Canonical ścieżka klasy C2, w tym przykładzie jest N1 + C2. Ścieżka prezentacji C2 zawiera węzły "Podstaw i interfejsy" i C1: N1 + C1 + "Interfejsów i podstaw" + C2.  
  
 Uzyskanie informacji formularza prezentacji, wywołań Menedżera obiektów <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> metody.  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>Identyfikowanie Symbol w hierarchii  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>Uzyskanie kanonicznej i prezentacji formularzy informacji  
  
1.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> metody.  
  
     Menedżer obiektu wywołuje tę metodę w celu uzyskania listy węzłów zawartych w ścieżce canonical symbolu.  
  
    ```vb  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```csharp  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> metody.  
  
     Menedżer obiektu wywołuje tę metodę w celu uzyskania listy węzłów zawartych w ścieżce prezentacji symbolu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa narzędzia do przeglądania Symbol](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Porady: rejestrowanie biblioteki z Menedżera obiektów](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Instrukcje: uwidacznianie listy symboli udostępnianych przez bibliotekę dla menedżera obiektów](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)