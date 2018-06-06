---
title: Debugowanie za pomocą przeglądarki sklepu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5424fc8e3bdf80f5a6f19086f4e73360af95dad7
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748413"
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

 ![](../modeling/media/storeviewer2.png) Podgląd magazynu

 Podgląd magazynu ma trzy okienka: okienka po lewej stronie, prawym górnym rogu i prawym dolnym rogu. W lewym okienku będzie typów w widoku drzewa `DomainDataDirectory` elementu członkowskiego magazynu. Rozwiń węzeł partycję, kliknij element elementu właściwości są wyświetlane w prawym górnym rogu okienka. Jeśli element jest połączony z innymi elementami, dodatkowe elementy są widoczne w okienku prawym dolnym rogu. Jeśli zostanie dwukrotnie kliknięty element w prawym dolnym rogu okienka, element zostanie wyróżniona w okienku po lewej stronie.

## <a name="see-also"></a>Zobacz też

- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)