---
title: "Porady: włączenie funkcji AutoStart dla instalacji z dysku CD | Dokumentacja firmy Microsoft"
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
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: e3656c3d32dcba946cf66d7fba56a68b3de467f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Porady: włączenie funkcji AutoStart dla instalacji z dysku CD
W przypadku wdrażania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji za pomocą nośników wymiennych, takich jak stacje CD-ROM lub DVD-ROM, można włączyć `AutoStart` , aby [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja jest uruchamiana automatycznie, gdy znajduje się nośnik.  
  
 `AutoStart`można włączyć dla **publikowania** strony **projektanta projektu**.  
  
### <a name="to-enable-autostart"></a>Aby włączyć automatyczne uruchamianie  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  Kliknij przycisk **opcje** przycisku.  
  
     **Opcji publikowania** zostanie wyświetlone okno dialogowe.  
  
4.  Kliknij przycisk **wdrożenia**.  
  
5.  Wybierz **instalacji na dysku CD automatycznie Rozpocznij instalację po włożeniu dysku CD** pole wyboru.  
  
     Plik Autorun.inf zostaną skopiowane do lokalizacji publikacji po opublikowaniu aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)