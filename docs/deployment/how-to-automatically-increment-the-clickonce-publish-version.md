---
title: 'Porady: automatycznie wersji publikacji ClickOnce przyrostu | Dokumentacja firmy Microsoft'
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
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 2e1399795400d52543b92cb13635a8485b160f22
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Porady: automatyczne zwiększenie wersji publikacji ClickOnce
Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, zmiana `Publish Version` aplikacji, które mają zostać opublikowane jako aktualizacja powoduje, że właściwość. Domyślnie program Visual Studio spowoduje automatyczne zwiększenie `Revision` liczba `Publish Version` zawsze będziesz publikować aplikację.  
  
 To zachowanie można wyłączyć na **publikowania** strony **projektanta projektu**.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Aby wyłączyć automatyczne zwiększenie wersji publikowania  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  W **publikowania wersji** sekcji, wyczyść **automatycznie zwiększ numer poprawki przy każdej wersji** pole wyboru.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: zestaw ClickOnce wersji publikacji](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)