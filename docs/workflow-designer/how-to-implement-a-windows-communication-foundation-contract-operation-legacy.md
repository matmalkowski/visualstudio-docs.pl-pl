---
title: 'Porady: Implementowanie systemu Windows Communication Foundation kontrakt operacji (starsze) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 02d6a544b660a110c618bdcb7d3b778fd82ceaaa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Porady: Implementowanie systemu Windows Communication Foundation kontrakt operacji (starsze)
W tym temacie opisano sposób wykonania [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] kontraktu operacji za pomocą starszego [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] którego element docelowy [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Po przeciąganie **ReceiveActivity** działania z przybornika do powierzchni projektu przepływu pracy, albo utworzysz nową [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] kontraktu lub zaimportować istniejący kontrakt i wykonania operacji. Wybierz lub Utwórz umowy i jego operacji za pomocą [wybierz okno dialogowe operacji (starsze)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
### <a name="to-implement-a-wcf-contract-operation"></a>Aby zaimplementować operację kontraktu usługi WCF  
  
1.  Kliknij dwukrotnie **ReceiveActivity** działania w projektancie, lub kliknij przycisk wielokropka obok **właściwości ServiceOperationInfo** właściwości w **właściwości** okienka.  
  
2.  Wykonaj jedną z następujących czynności:  
  
    -   Kliknij przycisk **dodać umowy** w prawym górnym rogu okna dialogowego. Spowoduje to utworzenie nowego [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] kontrakt i operacja dla Ciebie.  
  
         —lub—  
  
    -   Kliknij przycisk **importu** w prawym górnym rogu okna dialogowego. [Wyszukaj i wybierz typ .NET dialogowe (starsze)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) otwiera. Zestaw lub projekt, który zawiera kontrakt, który chcesz wyszukać. Wybierz umowę, a następnie kliknij przycisk **OK**.  
  
     Po utworzeniu lub zaimportować kontrakt, można dodać nowych operacji umowę utworzonych lub importowany. Aby dodać nową operację, wybierz umowę, a następnie kliknij przycisk **operacji dodawania** w prawym górnym rogu okna dialogowego. Po zakończeniu operacji dodawania, przejdź do kroku 3.  
  
3.  Wybierz operację, którą chcesz skojarzyć z **ReceiveActivity** działania. Definicja operacji można manipulować, zmieniając nazwę, parametry, właściwości i ustawienia uprawnień wykonać operację.  
  
     Aby zmienić nazwę, wprowadź nową nazwę w **nazwy operacji** pola tekstowego.  
  
     Kliknij przycisk **parametry** kartę, aby uzyskać dostępu do parametrów operacji. Możesz zmienić nazwę, typ lub kierunek parametru, a także dodać lub usunąć parametry z operacji.  
  
     Kliknij przycisk **właściwości** kartę, aby uzyskać dostęp do funkcji programu exchange operacji ochrony poziomu i obsługiwane komunikatu operacji.  
  
     Kliknij przycisk **uprawnienia** kartę, aby określić, które grupy są dozwolone do wykonania operacji.  
  
4.  Kliknij przycisk **OK** i **ReceiveActivity** działania będzie wyświetlana nazwa operacji operacji, która implementuje.  
  
5.  Umieść działań przepływu pracy będą używać do wykonania tej operacji w ramach **ReceiveActivity** działania.  
  
## <a name="see-also"></a>Zobacz też  
 [Wybierz operację, okno dialogowe (starsze)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Porady: wywoływanie operacja kontraktu usługi WCF (starsze)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Działania przepływu pracy w starszej wersji](../workflow-designer/legacy-workflow-activities.md)