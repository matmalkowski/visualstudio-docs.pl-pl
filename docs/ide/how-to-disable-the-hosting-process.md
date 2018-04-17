---
title: 'Porady: wyłączanie procesu hostingu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b5dc19a094e4e5aac8fe1777b3794f100e3f1cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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