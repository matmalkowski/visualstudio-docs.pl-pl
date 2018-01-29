---
title: "Porady: wyłączanie procesu hostingu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b43e285c35601cb0d50536a5f4c499d09ae9bbad
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
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
  
## <a name="see-also"></a>Zobacz także

[Debugowanie i proces hostingu](../debugger/debugging-and-the-hosting-process.md)   
[Proces hostingu (vshost.exe)](../ide/hosting-process-vshost-exe.md)