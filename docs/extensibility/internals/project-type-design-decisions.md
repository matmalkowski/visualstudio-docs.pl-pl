---
title: Decyzje projektowe typ projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c28c6f29454feed94407d6e37c3432247b9a4a26
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131500"
---
# <a name="project-type-design-decisions"></a>Decyzje projektowe typ projektu
Przed utworzeniem nowego typu projektu, należy kilka decyzji projektowych dotyczących danego typu projektu. Należy zdecydować, jakie typy elementów, który będzie zawarty w projektach, jak pliki projektu zostaną utrwalone i jakie modelu zobowiązań będzie używać.  
  
## <a name="project-items"></a>Elementy projektu  
 Projekt użyje plików lub abstrakcyjny obiektów? Jeśli używasz plików ich będzie oparte na odwołania lub oparte na katalog plików? Czy plików lub obiektów abstrakcyjnych przerywaj lokalnego lub zdalnego?  
  
 Elementy w projekcie może być plików lub w Internecie mogą być bardziej abstrakcyjny obiekty, takie jak obiekty w repozytorium lub dane połączenia bazy danych. Jeśli pliki znajdują się elementy, projekt może być odwołania na lub katalogu projektu.  
  
 W projektach opartych na odwołanie elementów może występować więcej niż jednym projekcie. Jednak rzeczywisty plik, który reprezentuje element znajduje się w tylko jeden katalog. W projektach opartych na katalogu wszystkie elementy projektu istnieje w strukturze katalogów.  
  
 Elementy lokalne są przechowywane na tym samym komputerze, na którym aplikacja jest zainstalowana. Zdalne elementy mogą być przechowywane na oddzielnym serwerze w sieci lokalnej lub w innym miejscu w Internecie.  
  
## <a name="project-file-persistence"></a>Trwałość pliku projektu  
 Będą dane przechowywane w typowe systemy plików prostych lub magazynem strukturalnym? Zostanie otwarty plików przy użyciu standardowego edytora lub edytora określonego projektu?  
  
 Aby zachować swoje dane, większość aplikacji zapisać swoje dane w pliku, a następnie przeczytaj go ponownie, gdy użytkownik musi przejrzeć lub zmienić informacje.  
  
 Magazynem strukturalnym, nazywany również pliki złożone, zazwyczaj jest używany, gdy niektóre obiekty składnik modelu COM. trzeba utrwalonego dane przechowywane w jednym pliku. Z magazynem strukturalnym kilka innych składników oprogramowania można udostępniać pliku jednego dysku.  
  
 Istnieje kilka opcji aspektem trwałości dla elementów w projekcie. Można wykonać jeden z następujących opcji:  
  
-   Zapisz plik pojedynczo, gdy zostanie zmieniona.  
  
-   Przechwyć wiele transakcji w jednej **zapisać** operacji.  
  
-   Zapisywanie plików lokalnie, a następnie opublikować na serwerze lub użyć innej metody do zapisywania elementów projektu, gdy element reprezentuje połączenie danych z obiektu zdalnego.  
  
 Aby uzyskać więcej informacji o trwałości, zobacz [trwałości projektu](../../extensibility/internals/project-persistence.md) i [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Model zobowiązań projektu  
 Zostanie otwarty danych utrwalonych obiektów w trybie bezpośredniego lub transakcyjne?  
  
 Po otwarciu obiektów danych w trybie bezpośredniego, zmiany wprowadzone w danych są włączone, natychmiast, lub gdy użytkownik zapisuje ręcznie pliku.  
  
 Otwarcie obiektów danych przy użyciu trybu transakcyjne zmiany są zapisywane w tymczasowej lokalizacji w pamięci i nie są przekazywane, dopóki użytkownik ręcznie wybierze opcję Zapisz plik. W tym czasie wszystkie zmiany muszą występować razem lub nie zostaną wprowadzone nie zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Trwałość projektu](../../extensibility/internals/project-persistence.md)   
 [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)   
 [Projekt modelu podstawowe składniki](../../extensibility/internals/project-model-core-components.md)   
 [Tworzenie typów projektów](../../extensibility/internals/creating-project-types.md)