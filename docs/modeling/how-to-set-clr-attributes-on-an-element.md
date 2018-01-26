---
title: "Porady: Ustawianie atrybutów CLR dla elementu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.EditAttributesDialog
helpviewer_keywords: Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8e73b12b1ca3fa3760bf1b074eb42370130534b6
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Porady: ustawienie atrybutów CLR w elemencie
Atrybuty niestandardowe są specjalne atrybuty, które mogą być dodawane do elementów domeny, kształtów, łączniki i diagramy. Można dodać dowolny atrybut, który dziedziczy z `System.Attribute` klasy.  
  
### <a name="to-add-a-custom-attribute"></a>Aby dodać atrybutu niestandardowego  
  
1.  W **DSL Explorer**, wybierz element, do którego chcesz dodać atrybutu niestandardowego.  
  
2.  W **właściwości** okna, obok **atrybuty niestandardowe** właściwości, kliknij przycisk Przeglądaj (**...** ) ikona.  
  
     **Edycja atrybutów** zostanie otwarte okno dialogowe.  
  
3.  W **nazwa** kolumny, kliknij przycisk  **\<Dodaj atrybut >** i wpisz nazwę atrybut. Naciśnij klawisz ENTER.  
  
4.  Wiersz w obszarze Nazwa atrybutu zawiera nawiasy. W tym wierszu typu parametru atrybutu (na przykład `string`), a następnie naciśnij klawisz ENTER.  
  
5.  W **właściwość Name** kolumny, wpisz odpowiednią nazwę, na przykład `MyString`.  
  
6.  Kliknij przycisk **OK**.  
  
     **Atrybuty niestandardowe** właściwości są obecnie wyświetlane atrybutu w następującym formacie:  
  
     `[`*AttributeName* `(` *ParameterName* `=` *typu*`)]`  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)