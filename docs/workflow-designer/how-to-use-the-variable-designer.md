---
title: "Porady: Użyj projektanta zmiennych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: c9bf63222f16e29044a9a07078096b765421fbb3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-variable-designer"></a>Porady: Użyj projektanta zmiennych
Projektanta zmiennych służy do tworzenia zmiennych do użycia w instrukcjach warunkowe i scenariusze powiązania danych. Projektant jest dostępne po kliknięciu **zmienne** przycisk w lewym dolnym rogu obszaru projektowania. Projektant zawiera listę zmiennych, które znajdują się w formie tabelarycznej i można sortować według poszczególnych nagłówków kolumn, z wyjątkiem **domyślne** kolumny. Każdej zmiennej zawiera nazwę, typ zmiennej, zakresu i wartość domyślną (jeśli istnieje). Nazwa i domyślne wartości są pola edycji, a typie i zakresie są listach rozwijanych. Zakres jest działania, które zostały wybrane podczas projektanta zmiennych. Jeśli nie można utworzyć zmiennej w zakresie zaznaczenia, zakres jest domyślnie do najbliższej działania nadrzędnego zaznaczenia umożliwiający zmiennych mogą być tworzone w swoim zakresie. [! OBEJMUJĄ[crabout](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).  
  
 Kolejność sortowania nie została zastosowana, dopóki użytkownik jawnie używa sortowania formantów, zamyka i ponownie otwiera projektanta zmiennych lub tworzy innej zmiennej.  
  
### <a name="to-create-a-new-variable"></a>Aby utworzyć nową zmienną  
  
1.  Otwórz rozwiązanie przepływu pracy lub działania w [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2.  W obszarze roboczym Projekt wybierz działanie w przepływie pracy.  
  
3.  Otwórz projektanta zmiennych, klikając przycisk **zmienne** przycisk w lewym dolnym rogu obszaru projektowania. Zostanie wyświetlona projektanta zmiennych.  
  
4.  Kliknij pusty wiersz z etykietą **tworzenia zmiennej**. Spowoduje to dodanie nowego wiersza z nową zmienną przy użyciu następujących wartości domyślnych: variablex dla **nazwa** gdzie x jest liczbą całkowitą o początkowej wartości 1, który jest automatycznie zwiększany można utworzyć unikatowych nazw zmiennych,  **Ciąg** dla **typ zmiennej**, i **sekwencji** dla **zakres**. Wartość nie jest dodawany do **domyślne**. Te wartości można zmienić w dowolnym momencie podczas tworzenia projektu przepływu pracy.  
  
    > [!NOTE]
    >  Aby usunąć zmienną, wybierz zmienną, klikając go, a następnie naciśnij klawisz **usunąć** klucza.  
  
## <a name="see-also"></a>Zobacz też  
 [Za pomocą projektanta przepływów pracy](../workflow-designer/using-the-workflow-designer.md)   
 [Argumenty i zmienne](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)   
 [Instrukcje: Używanie projektanta argumentów](../workflow-designer/how-to-use-the-argument-designer.md)