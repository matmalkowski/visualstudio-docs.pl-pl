---
title: "Porady: Określanie ClickOnce w trybie Offline lub Online instalowania tryb | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: "8"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: b1c0f8615513639081351bdf77ea9ec63fc8309b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Porady: określanie trybu offline lub online instalowania za pomocą technologii ClickOnce
`Install Mode` Dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji określa, czy aplikacja będzie dostępna w trybie offline lub online. Po wybraniu **aplikacja jest dostępna online tylko**, użytkownik musi mieć dostęp do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publikowania lokalizacji (strony sieci Web lub udział plików), aby uruchomić aplikację. Po wybraniu **aplikacja jest dostępna w trybie offline oraz**, aplikacja dodaje wpisy do **Start** menu i **Dodaj lub usuń programy** okno dialogowe; użytkownika jest można uruchomić aplikację, gdy nie są połączone.  
  
 `Install Mode` Można ustawić **publikowania** strony **projektanta projektu**.  
  
 **Uwaga** `Install Mode` można również ustawić za pomocą Kreatora publikacji. Aby uzyskać więcej informacji, zobacz [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Aby udostępnić aplikacji ClickOnce online tylko  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  W **tryb instalacji i ustawienia** obszaru, kliknij przycisk **aplikacja jest dostępna online tylko** przycisk opcji.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Aby udostępnić aplikacji ClickOnce, online lub offline  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  W **tryb instalacji i ustawienia** obszaru, kliknij przycisk **aplikacja jest dostępna w trybie offline oraz** przycisk opcji.  
  
     Po zainstalowaniu aplikacji dodaje wpisy do **Start** menu i **Dodaj lub usuń programy** w Panelu sterowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)