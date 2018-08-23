---
title: 'Porady: wyłączanie aktywacji adresu URL aplikacji ClickOnce za pomocą projektanta | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 6cc5571dffba9daa3ac1f5f78e354487cbc654fe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678347"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Porady: wyłączanie aktywacji adresu URL aplikacji ClickOnce za pomocą Projektanta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: wyłączanie adresu URL aktywacji dla aplikacji ClickOnce za pomocą projektanta](https://docs.microsoft.com/visualstudio/deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer).  
  
Zazwyczaj [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji rozpocznie się automatycznie natychmiast, po zakończeniu instalacji z serwera sieci Web. Ze względów bezpieczeństwa może zdecydować wyłączyć to zachowanie i poinformuj użytkowników, aby uruchomić aplikację z **Start** menu zamiast tego. Poniższa procedura opisuje sposób wyłączanie aktywacji adresu URL.  
  
 Ta technika może zostać użyta tylko w przypadku [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji zainstalowanych na komputerze użytkownika z serwera sieci Web. Nie można używać dla aplikacji tylko w trybie online, które można uruchomić tylko przy użyciu swojego adresu URL. Aby uzyskać więcej informacji na temat różnic między tylko w trybie online i zainstalowanych aplikacji, zobacz [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Ta procedura wykorzystuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. To zadanie można również wykonać przy użyciu [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Aby uzyskać więcej informacji, zobacz [porady: wyłączanie aktywacji adresu URL dla aplikacji ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Aby wyłączanie aktywacji adresu URL aplikacji  
  
1.  Kliknij prawym przyciskiem myszy nazwę projektu w **Eksploratora rozwiązań**i kliknij przycisk **właściwości**.  
  
2.  Na **właściwości** kliknij **Publikuj** kartę.  
  
3.  Kliknij przycisk **opcje**.  
  
4.  Kliknij przycisk **manifesty**.  
  
5.  Zaznacz pole wyboru przy opcji **Block aktywowania aplikacji za pomocą adresu URL**.  
  
6.  Wdrażanie aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)



