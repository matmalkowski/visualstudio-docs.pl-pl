---
title: 'Projektant przepływu pracy — porady: Implementowanie systemu Windows Communication Foundation kontrakt operacji (starsze)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b069d8ca8c1adb72e2869eb59644e8abeff14ae
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Porady: Implementowanie systemu Windows Communication Foundation kontrakt operacji (starsze)

W tym temacie opisano, jak do zaimplementowania operacja kontraktu usługi Windows Communication Foundation (WCF), za pomocą projektanta przepływów pracy programu starszej wersji systemu Windows, którego element docelowy .NET Framework w wersji 3.5 lub WinFX.

Po przeciąganie **ReceiveActivity** działania z przybornika do powierzchni projektu przepływu pracy, albo utworzysz nową [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] kontraktu lub zaimportować istniejący kontrakt i wykonania operacji. Wybierz lub Utwórz umowy i jego operacji za pomocą [wybierz okno dialogowe operacji (starsze)](../workflow-designer/choose-operation-dialog-box-legacy.md).

## <a name="to-implement-a-wcf-contract-operation"></a>Aby zaimplementować operację kontraktu usługi WCF

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

## <a name="see-also"></a>Zobacz także

- [Wybieranie operacji, okno dialogowe (starsza wersja)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [Porady: wywoływanie operacja kontraktu usługi WCF (starsze)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)
- [Działania przepływu pracy w starszej wersji](../workflow-designer/legacy-workflow-activities.md)