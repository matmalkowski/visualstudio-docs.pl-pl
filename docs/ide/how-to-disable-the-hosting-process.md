---
title: "Porady: wyłączanie procesu hostingu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 94d40fe18ff4cca228fb39ab16bcfaa6ac42a172
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-disable-the-hosting-process"></a>Porady: wyłączanie procesu hostingu
Może mieć wpływ wywołania do niektórych interfejsów API, gdy proces hostingu jest włączone. W takich sytuacjach należy wyłączanie procesu hostingu do zwracać poprawnych wyników.  
  
### <a name="to-disable-the-hosting-process"></a>Aby wyłączyć procesu hostingu  
  
1.  Otwórz projekt wykonywalny w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Ta opcja nie jest projektów, które generuje pliki wykonywalne (na przykład klasa biblioteki lub usługi projektów).  
  
2.  Na **projektu** menu, kliknij przycisk **właściwości**.  
  
3.  Kliknij przycisk **debugowania** kartę.  
  
4.  Wyczyść **włączyć procesu hostingu Visual Studio** pole wyboru.  
  
 Po wyłączeniu procesu hostingu kilka funkcji debugowania są niedostępne lub zmniejszyć wydajność. Aby uzyskać więcej informacji, zobacz [debugowanie i proces hostingu](../debugger/debugging-and-the-hosting-process.md).  
  
 Ogólnie rzecz biorąc, gdy proces hostingu jest wyłączone:  
  
-   Czas potrzebny na rozpocząć debugowanie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zwiększa aplikacji.  
  
-   Szacowanie wyrażeń w czasie projektowania jest niedostępny.  
  
-   Debugowanie w częściowej relacji zaufania jest niedostępny.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie i proces hostingu](../debugger/debugging-and-the-hosting-process.md)   
 [Proces hostingu (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Tworzy podczas tworzenia aplikacji](http://msdn.microsoft.com/en-us/c9497d62-3b7b-4449-88e8-cf27acc9efe6)