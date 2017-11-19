---
title: "Porady: wyłączanie aktywacji adresu URL aplikacji ClickOnce | Dokumentacja firmy Microsoft"
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
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 1142a047dc1e3ad74b75cf2d82432e1d2f16c1a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Porady: wyłączanie aktywacji adresu URL aplikacji ClickOnce
Zazwyczaj [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji będą automatycznie uruchamiane natychmiast po zainstalowaniu przez serwer sieci Web. Ze względów bezpieczeństwa może zdecydować wyłączyć to zachowanie i poinformuj użytkowników, aby uruchomić aplikację z **Start** menu zamiast tego. W poniższej procedurze opisano sposób wyłączanie aktywacji adresu URL.  
  
 Ta technika może służyć tylko do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje zainstalowane na komputerze z serwerem sieci Web. Nie można używać dla aplikacji tylko w trybie online, które mogą być przeprowadzane tylko przy użyciu swojego adresu URL. Aby uzyskać więcej informacji na różnicy między tylko w trybie online i zainstalowanych aplikacji, zobacz [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Ta procedura wykorzystuje [! OBEJMUJĄ[winsdklong](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Można również wykonywać tej procedury przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Aby wyłączyć aktywacji adresu URL aplikacji  
  
1.  Otwórz manifeście wdrażania w MageUI.exe. Jeśli użytkownik jeszcze nie utworzono jedną, postępuj zgodnie z instrukcjami [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Wybierz **opcje wdrażania** kartę.  
  
3.  Wyczyść **automatycznego uruchamiania aplikacji po zainstalowaniu** pole wyboru.  
  
4.  Zapisz i podpisać manifest.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)