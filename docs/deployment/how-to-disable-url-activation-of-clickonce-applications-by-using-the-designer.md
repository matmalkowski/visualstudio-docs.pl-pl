---
title: 'Porady: wyłączanie aktywacji adresu URL aplikacji ClickOnce za pomocą projektanta | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 366c4362ca3c3b6140380ab64000a01fe8e1aa6b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Porady: wyłączanie aktywacji adresu URL aplikacji ClickOnce za pomocą Projektanta
Zazwyczaj [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji rozpocznie się automatycznie natychmiast po zainstalowaniu przez serwer sieci Web. Ze względów bezpieczeństwa może zdecydować wyłączyć to zachowanie i poinformuj użytkowników, aby uruchomić aplikację z **Start** menu zamiast tego. W poniższej procedurze opisano sposób wyłączanie aktywacji adresu URL.  
  
 Ta technika może służyć tylko do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje zainstalowane na komputerze z serwerem sieci Web. Nie można używać dla aplikacji tylko w trybie online, które można uruchomić tylko przy użyciu swojego adresu URL. Aby uzyskać więcej informacji na temat różnic między tylko w trybie online i są zainstalowane aplikacje, zobacz [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Ta procedura wykorzystuje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Można również wykonać to zadanie za pomocą [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Aby uzyskać więcej informacji, zobacz [porady: wyłączanie aktywacji adresu URL z aplikacji ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Aby wyłączyć aktywacji adresu URL aplikacji  
  
1.  Kliknij prawym przyciskiem myszy nazwę projektu w **Eksploratora rozwiązań**i kliknij przycisk **właściwości**.  
  
2.  Na **właściwości** kliknij przycisk **publikowania** kartę.  
  
3.  Kliknij przycisk **opcje**.  
  
4.  Kliknij przycisk **manifesty**.  
  
5.  Zaznacz pole wyboru **blokowania aplikacji z aktywowane za pomocą adresu URL**.  
  
6.  Wdrażanie aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)