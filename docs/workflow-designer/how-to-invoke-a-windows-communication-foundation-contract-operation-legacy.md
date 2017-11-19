---
title: "Porady: wywoływanie Windows Communication Foundation kontraktu operacji (starsze) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 51b20275f63b47d607679e04ff061cf77b0d9f90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Porady: wywoływanie Windows Communication Foundation kontraktu operacji (starsze)
W tym temacie opisano sposób wywołania [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] kontraktu operacji za pomocą starszego [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] którego element docelowy [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Po przeciąganie **SendActivity** działania z przybornika do powierzchni projektu przepływu pracy, musisz zaimportować istniejący kontrakt i określić, która operacja zostanie wywołany niż **SendActivity** działanie. Wybierz umowy i jego operacji za pomocą [wybierz okno dialogowe operacji (starsze)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Również, korzystając z pliku konfiguracji z usługą, należy określić <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> Identyfikuje konfiguracji punktu końcowego działanie send będzie używana do łączenia usługi przepływu pracy.  
  
### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Aby wywołać operację kontraktu usługi WCF z działania SendActivity  
  
1.  Kliknij dwukrotnie **SendActivity** działania w projektancie, lub kliknij przycisk wielokropka obok **właściwości ServiceOperationInfo** właściwości w **właściwości** okienka.  
  
2.  Gdy **wybierz operacji** zostanie otwarte okno dialogowe, kliknij przycisk **importu** w prawym górnym rogu okna dialogowego.  
  
     [Wyszukaj i wybierz typ .NET dialogowe (starsze)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) otwiera.  
  
3.  Zestaw lub projekt, który zawiera kontrakt, który chcesz wyszukać.  
  
4.  Wybierz umowę, a następnie kliknij przycisk **OK**.  
  
5.  W obszarze **dostępne operacje**, wybierz operację, aby wywołać, a następnie kliknij przycisk **OK**.  
  
### <a name="to-specify-a-channel-token"></a>Aby określić tokenu kanału  
  
1.  Wybierz <xref:System.Workflow.Activities.SendActivity> działania w projektancie.  
  
2.  W **właściwości** okienka, określ nazwę <xref:System.Workflow.Activities.ChannelToken>. Ta nazwa jest unikatowo identyfikuje tokenu kanału.  
  
3.  Rozwiń węzeł tokenu kanału i określ nazwę punktu końcowego klienta będą używać w <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> pola. Konfiguracja punktu końcowego o tej samej nazwie w pliku konfiguracji będzie służyć do konfigurowania kanału.  
  
4.  Tworzenie konfiguracji punktu końcowego w pliku konfiguracji, jeśli już istnieje. Aby uzyskać więcej informacji o konfigurowaniu klienta, zobacz [Przegląd klienta programu WCF](/dotnet/framework/wcf/wcf-client-overview).  
  
## <a name="see-also"></a>Zobacz też  
 [Wybierz operację, okno dialogowe (starsze)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Porady: Implementowanie operacja kontraktu usługi WCF (starsze)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Działania przepływu pracy w starszej wersji](../workflow-designer/legacy-workflow-activities.md)