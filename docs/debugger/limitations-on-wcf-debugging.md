---
title: Ograniczenia debugowania WCF | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72e166d5501849dd84964364a94b2bdf6dc239a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="limitations-on-wcf-debugging"></a>Ograniczenia debugowania WCF
Istnieją trzy sposoby, aby można było rozpocząć debugowanie usługi WCF:  
  
-   Debugowany proces klienta, który wywołuje usługę. Kroki debugera do usługi. Usługa nie musi należeć do tego samego rozwiązania co aplikacja kliencka.  
  
-   Debugowany proces klienta, który wysyła żądanie do usługi. Usługa musi być częścią rozwiązania.  
  
-   Możesz użyć **dołączyć do procesu** do dołączenia do usługi, która jest obecnie uruchomiona. Debugowanie rozpoczyna się wewnątrz usługi.  
  
 W tym temacie opisano ograniczenia w tych scenariuszach.  
  
## <a name="limitations-on-stepping-into-a-service"></a>Ograniczenia dotyczące Wkraczanie do usługi  
 Aby wkraczać do usługi za pośrednictwem aplikacji klienckich, które są debugowania, muszą być spełnione następujące warunki:  
  
-   Klienta należy wywołać usługę za pomocą obiektu synchroniczne klienta.  
  
-   Operacja kontraktu nie może być jednokierunkowe.  
  
-   Jeśli serwer jest asynchroniczne, nie można wyświetlić stosu wywołań pełne podczas wykonywania kodu wewnątrz usługi.  
  
-   Debugowanie musi być włączone w pliku Web.config lub app.config następującym kodem:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     Ten kod zawiera tylko do dodania jeden raz. Można dodać tego kodu przez edycję pliku .config lub dołączanie do usługi przy użyciu **dołączyć do procesu**. Jeśli używasz **dołączyć do procesu** w usłudze, debugowania kodu zostanie automatycznie dodany do pliku .config. Po wykonaniu tej można debugować i krok w usłudze bez konieczności edytowania pliku .config.  
  
## <a name="limitations-on-stepping-out-of-a-service"></a>Wykonywanie krok po kroku, poza usługą ograniczenia  
 Wykonywanie krok po kroku z usługi z powrotem do klienta ma te same ograniczenia opisane dla Wkraczanie do usługi. Ponadto debuger musi być dołączony do klienta. W przypadku debugowania klienta i Wkrocz do usługi, debuger pozostaje dołączone do usługi. Jest to wartość true, czy klient jest uruchomiony przy użyciu **Rozpocznij debugowanie** lub dołączony do klienta przy użyciu **dołączyć do procesu**. Jeśli rozpoczęciu debugowania przez dołączenie do usługi, debuger nie jest jeszcze dołączony do klienta. W takim przypadku, jeśli masz do kroku poza usługi i z powrotem do klienta, musisz najpierw użyć **dołączyć do procesu** ręcznie Dołącz do klienta.  
  
## <a name="limitations-on-automatic-attach-to-a-service"></a>Ograniczenia dotyczące automatyczne dołączanie do usługi  
 Automatyczne dołączanie do usługi ma następujące ograniczenia:  
  
-   Usługa musi być częścią [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania debugowania.  
  
-   Usługa musi być obsługiwana. Może być częścią projekt witryny sieci Web (System plików i HTTP), projekt aplikacji sieci Web (System plików i HTTP) lub projektu biblioteki usługi WCF. Projekty biblioteki usługi WCF można bibliotek usługi lub biblioteki usługi przepływu pracy.  
  
-   Usługi muszą być wywoływane z klienta programu WCF.  
  
-   Debugowanie musi być włączone w pliku Web.config lub app.config następującym kodem:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## <a name="self-hosting"></a>Hostingu samodzielnego  
 A *usługi hosta samodzielnego* to usługa WCF, która nie jest uruchamiane w usługach IIS, Host usługi WCF, lub [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server. Informacje o sposobie debugowanie hostowania samoobsługowego, zobacz [porady: debugowanie WCF Self-Hosted](../debugger/how-to-debug-a-self-hosted-wcf-service.md).  
  
## <a name="self-hosting"></a>Hostingu samodzielnego  
 Aby włączyć debugowanie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 lub 3.5 aplikacji, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 lub 3.5 musi zostać zainstalowany przed [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] jest zainstalowany. Jeśli [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] została zainstalowana przed [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 lub 3.5, wystąpi błąd podczas próby debugowania [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji w wersji 3.0 lub 3.5. Komunikat o błędzie jest, "nie można automatycznie wkroczyć do serwera." Aby rozwiązać ten problem, należy użyć systemu Windows **Panelu sterowania** > **programy i funkcje** naprawić Twojej [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] instalacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie usług WCF](../debugger/debugging-wcf-services.md)   
 [Porady: debugowanie hostowania samoobsługowego WCF](../debugger/how-to-debug-a-self-hosted-wcf-service.md)