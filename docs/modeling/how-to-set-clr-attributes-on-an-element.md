---
title: "Porady: Ustawianie atrybutów CLR dla elementu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1eedf41931c7f9476691e507ab0afcd9e2a4c4ee
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
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