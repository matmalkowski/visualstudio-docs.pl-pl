---
title: 'Porady: ustawienie strefy zabezpieczeń dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
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
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 697632e70c8b72fa0b540c3b1652d5a110a4b085
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42689419"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Porady: ustawienie strefy zabezpieczeń dla aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: ustawienie strefy zabezpieczeń dla aplikacji ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-set-a-security-zone-for-a-clickonce-application).  
  
Podczas ustawiania dostępu kodu uprawnień zabezpieczeń dla aplikacji ClickOnce, należy uruchomić podstawowy zestaw uprawnień na **zabezpieczeń** strony **projektanta projektu**.  
  
 W większości przypadków można także **Internet** strefy, który zawiera ograniczony zestaw uprawnień lub **lokalny Intranet** strefy, który zawiera większy zestaw uprawnień. Jeśli aplikacja wymaga uprawnień niestandardowych, możesz to zrobić, wybierając **niestandardowe** strefy zabezpieczeń. Aby uzyskać więcej informacji na temat ustawiania uprawnień niestandardowych, zobacz [porady: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
### <a name="to-set-a-security-zone"></a>Aby ustawienie strefy zabezpieczeń  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.  
  
2.  Kliknij przycisk **zabezpieczeń** kartę.  
  
3.  Wybierz **włączenia ustawień zabezpieczeń technologii ClickOnce** pole wyboru.  
  
4.  Wybierz **to częściowo zaufanych aplikacji** przycisku opcji.  
  
     Formanty w **uprawnienia zabezpieczeń aplikacji ClickOnce** sekcji są włączone.  
  
5.  W **strefy, aplikacja zostanie zainstalowana z** listy rozwijanej wybierz strefę zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)



