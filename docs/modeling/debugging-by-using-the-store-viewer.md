---
title: "Debugowanie przy użyciu podglądu magazynu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: "17"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 6fde5dfc012b43d71f6d8db2519607724eeeadc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="debugging-by-using-the-store-viewer"></a>Debugowanie za pomocą przeglądarki sklepu
Z podglądem przechowywania możesz zbadać stan *przechowywania* używane przez [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Podgląd przechowywania Wyświetla listę wszystkich elementów modelu domeny znajdujących się w określonym magazynie, wraz z właściwości elementu i łącza między elementami.  
  
## <a name="opening-store-viewer"></a>Otwieranie magazynu podglądu  
 Jeśli jesteś w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eksperymentalne kompilacji, Zatrzymaj kodu w punkcie przerwania, w którym wystąpienia magazynu zawiera informacje o modelu. Następnie otwórz Podgląd magazynu, wpisując następujące polecenie w **Immediate** okno:  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
>  Należy zastąpić `mystore` o nazwie wystąpienia magazynu. Ponadto przestrzeni nazw można dodać do kodu, należy wpisać polecenia do wyświetlania podglądu magazynu bez w pełni kwalifikowaną przestrzeni nazw:  
>   
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
>  `...`  
>   
>  `StoreViewer.Show(mystore);`  
  
 `Show` Metoda ma kilka przeciążeń. Wystąpienie sklepu lub partycję można określić jako parametr.  
  
 Alternatywnie, można umieścić wiersza kodu, który wyświetla podgląd magazynu dowolne miejsce w kodzie gdzie parametr, który jest przekazywany do `Show` metoda znajduje się w zakresie. Ta akcja wyświetla przechowywania podglądu podczas wiersz kodu jako migawka zawartość magazynu.  
  
### <a name="using-store-viewer"></a>Przy użyciu przeglądarki plików magazynu  
 Po otwarciu podglądu magazynu niemodalne okno dialogowe formularzy systemu Windows pojawi się, jak przedstawiono na poniższej ilustracji.  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
Podgląd magazynu  
  
 Podgląd magazynu ma trzy okienka: okienka po lewej stronie, prawym górnym rogu i prawym dolnym rogu. W lewym okienku będzie typów w widoku drzewa `DomainDataDirectory` elementu członkowskiego magazynu. Rozwiń węzeł partycję, kliknij element elementu właściwości są wyświetlane w prawym górnym rogu okienka. Jeśli element jest połączony z innymi elementami, dodatkowe elementy są widoczne w okienku prawym dolnym rogu. Jeśli zostanie dwukrotnie kliknięty element w prawym dolnym rogu okienka, element zostanie wyróżniona w okienku po lewej stronie.  
  
## <a name="see-also"></a>Zobacz też  
 [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)