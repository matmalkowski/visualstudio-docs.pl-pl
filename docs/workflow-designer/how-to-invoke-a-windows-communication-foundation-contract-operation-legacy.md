---
title: 'Projektanta przepływów pracy — porady: wywoływanie Windows Communication Foundation kontraktu operacji (starsze)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b39d2132b29ec1f8fbfd8339bdb8f81e6f752a0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Porady: wywoływanie Windows Communication Foundation kontraktu operacji (starsze)

W tym temacie opisano, jak do wywołania operacji kontraktu usługi Windows Communication Foundation (WCF), za pomocą projektanta przepływów pracy programu starszej wersji systemu Windows, którego element docelowy .NET Framework w wersji 3.5 lub WinFX.

Gdy zostanie przeciągnięty **SendActivity** działania z przybornika na powierzchnię projektu przepływu pracy zaimportować istniejący kontrakt. Określić, która operacja jest wywoływana od tego **SendActivity** działania. Wybierz kontrakt i jego operacji za pomocą [wybierz okno dialogowe operacji (starsze)](../workflow-designer/choose-operation-dialog-box-legacy.md).

Ponadto jeśli plik konfiguracji korzystają z usługą, należy określić <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> Identyfikuje konfiguracji punktu końcowego działanie send będzie używana do łączenia usługi przepływu pracy.

## <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Aby wywołać operację kontraktu usługi WCF z działania SendActivity

1.  Kliknij dwukrotnie **SendActivity** działania w projektancie, lub kliknij przycisk wielokropka obok **właściwości ServiceOperationInfo** właściwości w **właściwości** okienka.

2.  Gdy **wybierz operacji** zostanie otwarte okno dialogowe, kliknij przycisk **importu** w prawym górnym rogu okna dialogowego.

     [Wyszukaj i wybierz typ .NET dialogowe (starsze)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) otwiera.

3.  Zestaw lub projekt, który zawiera kontrakt, który chcesz wyszukać.

4.  Wybierz umowę, a następnie kliknij przycisk **OK**.

5.  W obszarze **dostępne operacje**, wybierz operację, aby wywołać, a następnie kliknij przycisk **OK**.

## <a name="to-specify-a-channel-token"></a>Aby określić tokenu kanału

1.  Wybierz <xref:System.Workflow.Activities.SendActivity> działania w projektancie.

2.  W **właściwości** okienka, określ nazwę <xref:System.Workflow.Activities.ChannelToken>. Ta nazwa jest unikatowo identyfikuje tokenu kanału.

3.  Rozwiń węzeł tokenu kanału i określ nazwę punktu końcowego klienta będą używać w <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> pola. Konfiguracja punktu końcowego o tej samej nazwie w pliku konfiguracji jest używany do konfigurowania kanału.

4.  Tworzenie konfiguracji punktu końcowego w pliku konfiguracji, jeśli już istnieje. Aby uzyskać więcej informacji o konfigurowaniu klienta, zobacz [Przegląd klienta programu WCF](/dotnet/framework/wcf/wcf-client-overview).

## <a name="see-also"></a>Zobacz także

- [Wybieranie operacji, okno dialogowe (starsza wersja)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [Porady: Implementowanie operacja kontraktu usługi WCF (starsze)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)
- [Działania przepływu pracy w starszej wersji](../workflow-designer/legacy-workflow-activities.md)