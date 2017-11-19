---
title: "Porady: Tworzenie skojarzenia między typami (Projektant klas) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 69c1a3ddb60008f14dd76aeef224c040c7faace3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-associations-between-types-class-designer"></a>Porady: Tworzenie skojarzenia między typami (Projektant klas)
Linie skojarzenia w Konstruktorze klasy pokazują relacje klas na diagramie. Linia skojarzenia reprezentuje klasę, która jest typem właściwości lub polem innej klasy w projekcie. Linii skojarzeń zwykle używa się do ilustrowania najważniejszych relacji między klasami w projekcie.  
  
 Podczas gdy można wyświetlić wszystkie pola i właściwości jako skojarzenia, więcej sensu ma wyświetlanie tylko ważnych elementów członkowskich jako skojarzeń, w zależności od tego, co zamierzasz podkreślić na diagramie. (Można wyświetlić mniej ważne elementy członkowskie jako zwykłe elementy członkowskie lub je całkowicie ukryć.)  
  
> [!NOTE]
>  Projektant klasy obsługuje tylko jednokierunkowe skojarzenia.  
  
### <a name="to-define-an-association-line-in-the-class-diagram"></a>Aby zdefiniować linię skojarzenia na Diagramie klasy  
  
1.  W przyborniku w Projektancie klas, wybierz **skojarzenia**.  
  
2.  Narysuj linię między dwoma kształtami, które chcesz połączyć przez skojarzenie.  
  
     Nowa właściwość jest tworzona w pierwszej klasie. Ta właściwość służy jako linia skojarzenia, (a nie jako właściwość w ramach przedziału w kształcie) z domyślną nazwą. Jej typ to kształt, na który wskazuje linia skojarzenia.  
  
### <a name="to-change-the-name-of-an-association"></a>Aby zmienić nazwę skojarzenia  
  
-   Na powierzchni diagramu kliknij etykietę linii skojarzenia i ją wyedytuj.  
  
 \-lub -  
  
1.  Kliknij kształt, który zawiera właściwość, która jest wyświetlana jako skojarzenie.  
  
     Kształt uzyskuje fokus, a jego składniki są prezentowane w oknie Szczegóły klasy i w oknie Właściwości.  
  
2.  W oknie Szczegóły klasy lub w oknie Właściwości, wyedytuj pole nazwy dla tej właściwości, a następnie naciśnij klawisz Enter.  
  
     Nazwa jest aktualizowana w **szczegółów klasy** okna w wierszu skojarzenia, w oknie właściwości, a w kodzie.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: zmiana pomiędzy notacją członka i skojarzeniem notacji (Projektant klas)](../ide/how-to-change-between-member-notation-and-association-notation-class-designer.md)