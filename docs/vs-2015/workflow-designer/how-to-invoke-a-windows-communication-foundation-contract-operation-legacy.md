---
title: 'Porady: wywoływanie Windows Communication Foundation operacji kontraktu usługi WCF (starsza wersja) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 70f96176cb40fd531ddb41f58126ea310091d3fe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678419"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Porady: wywoływanie Windows Communication Foundation operacji kontraktu usługi WCF (starsza wersja)
W tym temacie opisano, jak wywołać [!INCLUDE[indigo1](../includes/indigo1-md.md)] kontrakt operacji za pomocą starszego [!INCLUDE[wfd1](../includes/wfd1-md.md)] przeznaczonego [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Po przeciągnięciu **SendActivity** działania z przybornika do powierzchni projektu przepływu pracy, musisz zaimportować istniejący kontrakt i określić, która operacja zostanie wywołany przy jego użyciu **SendActivity** działanie. Zaznacz kontrakt usługi i jego operacji za pośrednictwem [wybierz operację okno dialogowe (starsza wersja)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Ponadto korzystania z plików konfiguracji przy użyciu usługi należy określić <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> Identyfikuje konfiguracji punktu końcowego działania wysyłania będzie używana do łączenia usługi przepływu pracy.  
  
### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Do wywołania operacji kontraktu usługi WCF z działania SendActivity  
  
1.  Kliknij dwukrotnie **SendActivity** działania w Projektancie lub kliknij wielokropek obok pozycji **właściwości ServiceOperationInfo** właściwość **właściwości** okienka.  
  
2.  Gdy **wybierz operację** zostanie otwarte okno dialogowe, kliknij przycisk **importu** w prawym górnym rogu okna dialogowego.  
  
     [Wyszukaj i wybierz .NET typu, okno dialogowe (starsza wersja)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) zostanie otwarty.  
  
3.  Wyszukaj zestaw lub projekt, który zawiera kontrakt, który chcesz.  
  
4.  Wybierz umowę, a następnie kliknij przycisk **OK**.  
  
5.  W obszarze **dostępne operacje**, wybrać operację, aby wywołać, a następnie kliknij przycisk **OK**.  
  
### <a name="to-specify-a-channel-token"></a>Aby określić token kanału  
  
1.  Wybierz <xref:System.Workflow.Activities.SendActivity> działania w projektancie.  
  
2.  W **właściwości** okienko, określ nazwę <xref:System.Workflow.Activities.ChannelToken>. Ta nazwa jest jednoznacznie identyfikuje tokenu kanału.  
  
3.  Rozwiń węzeł tokenu kanału i określ nazwę dla punktu końcowego klienta, które zamierzasz używać w <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> pola. Konfiguracja punktu końcowego o takiej samej nazwie w pliku konfiguracji będzie służyć do konfigurowania kanału.  
  
4.  Tworzenie konfiguracji punktu końcowego w pliku konfiguracji, jeśli go jeszcze nie istnieje. Aby uzyskać więcej informacji na temat konfigurowania klienta, zobacz [Przegląd klienta programu WCF](http://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).  
  
## <a name="see-also"></a>Zobacz też  
 [Wybierz operację, okno dialogowe (starsza wersja)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Porady: Implementowanie operacji kontraktu usługi WCF (starsza wersja)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Działania przepływu pracy w starszej wersji](../workflow-designer/legacy-workflow-activities.md)