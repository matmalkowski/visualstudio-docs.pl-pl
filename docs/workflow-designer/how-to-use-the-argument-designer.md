---
title: "Porady: Użyj projektanta argumentów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: "16"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: aa1cdd0dd563a5f87d4e32f779985afd63319032
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-argument-designer"></a>Porady: Użyj projektanta argumentów
W porównaniu z poprzednimi wersjami [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], projektanta argumentów ułatwia umożliwiają przepływ do i z działania danych. Projektant jest dostępne po kliknięciu **argumenty** przycisk w lewym dolnym rogu obszaru projektowania. Projektant zawiera listę argumentów, które znajdują się w formie tabelarycznej i można sortować według poszczególnych nagłówków kolumn, z wyjątkiem **wartość domyślna** kolumny. Każdy argument zawiera nazwa, kierunek w/out/w out/właściwości, typ i domyślne wyrażenie wartości (jeśli istnieją). Nazwa i wartość domyślną, wyrażenia są pola edycji, a typie i kierunku są listach rozwijanych. [! OBEJMUJĄ[crabout](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).  
  
### <a name="to-create-a-new-argument"></a>Aby utworzyć nowy argument  
  
1.  Otwórz rozwiązanie przepływu pracy lub działania w [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
2.  Otwórz projektanta argumentów, klikając przycisk **argumenty** przycisk w lewym dolnym rogu obszaru projektowania. Zostanie wyświetlona projektanta argumentów.  
  
3.  Kliknij pusty wiersz z etykietą **utworzyć Argument**. Spowoduje to dodanie nowego wiersza z argumentem nowe przy użyciu następujących wartości domyślnych: argumentx dla **nazwa** gdzie x jest liczbą całkowitą o początkowej wartości 1, który jest automatycznie zwiększany można utworzyć nazwy argumentu unikatowy **w**  dla **kierunek**, i **ciąg** dla **typ argumentu**. Wartość nie jest dodawany do **wartość domyślna**. Te wartości można zmienić w dowolnym momencie podczas tworzenia projektu przepływu pracy.  
  
    > [!NOTE]
    >  Aby usunąć argumentu, zaznacz argument, klikając go, a następnie naciśnij klawisz **usunąć** klucza.  
  
## <a name="see-also"></a>Zobacz też  
 [Za pomocą projektanta przepływów pracy](../workflow-designer/using-the-workflow-designer.md)   
 [Zmienne i argumenty](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)