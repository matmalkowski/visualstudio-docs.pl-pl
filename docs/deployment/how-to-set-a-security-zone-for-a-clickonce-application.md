---
title: "Porady: ustawienie strefy zabezpieczeń dla aplikacji ClickOnce | Dokumentacja firmy Microsoft"
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
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
caps.latest.revision: "18"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 2bba62850791f637e93d6c82ff2186ffc5f09652
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Porady: ustawienie strefy zabezpieczeń dla aplikacji ClickOnce
Podczas ustawiania uprawnień zabezpieczeń dla aplikacji ClickOnce kod dostępu, należy uruchomić podstawowy zestaw uprawnień na **zabezpieczeń** strony **projektanta projektu**.  
  
 W większości przypadków można także **Internet** strefy, który zawiera ograniczony zestaw uprawnień, lub **lokalny Intranet** strefy, który zawiera większy zestaw uprawnień. Jeśli aplikacja wymaga uprawnień niestandardowych, możesz to zrobić, wybierając **niestandardowych** strefy zabezpieczeń. Aby uzyskać więcej informacji o ustawianiu uprawnień niestandardowych, zobacz [porady: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
### <a name="to-set-a-security-zone"></a>Aby ustawić strefy zabezpieczeń  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.  
  
2.  Kliknij przycisk **zabezpieczeń** kartę.  
  
3.  Wybierz **włączenia ustawień zabezpieczeń technologii ClickOnce** pole wyboru.  
  
4.  Wybierz **jest częściowo zaufanych aplikacji** przycisk opcji.  
  
     Formanty w **uprawnień zabezpieczeń ClickOnce** sekcji są włączone.  
  
5.  W **strefy aplikacja zostanie zainstalowana z** listy rozwijanej wybierz strefę zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)