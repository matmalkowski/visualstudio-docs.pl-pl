---
title: 'Porady: włączenie ustawień zabezpieczeń technologii ClickOnce | Dokumentacja firmy Microsoft'
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
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 65cba913afdee2379e5f702dda460cea2a33598f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42631811"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Porady: włączenie ustawień zabezpieczeń technologii ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: włączanie ustawień zabezpieczeń technologii ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-enable-clickonce-security-settings).  
  
Zabezpieczenia dostępu kodu dla aplikacji ClickOnce musi być włączony, aby można było opublikować aplikację. Odbywa się to automatycznie podczas publikowania aplikacji za pomocą Kreatora publikacji.  
  
 W niektórych przypadkach włączenie zabezpieczeń dostępu kodu może wpłynąć na wydajność podczas kompilowania lub debugowania aplikacji; w takich przypadkach mogą chcieć tymczasowo wyłączyć ustawienia zabezpieczeń.  
  
 Ustawień zabezpieczeń technologii ClickOnce można włączać lub wyłączać na **zabezpieczeń** strony **projektanta projektu**.  
  
### <a name="to-enable-clickonce-security-settings"></a>Aby włączyć ustawień zabezpieczeń technologii ClickOnce  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **zabezpieczeń** kartę.  
  
3.  Wybierz **włączenia ustawień zabezpieczeń technologii ClickOnce** pole wyboru.  
  
     Możesz teraz dostosować ustawienia zabezpieczeń dla aplikacji na stronie zabezpieczenia.  
  
    > [!NOTE]
    >  To pole wyboru jest wybierana z każdym opublikowaniu aplikacji za pomocą **Publikuj** kreatora.  
  
### <a name="to-disable-clickonce-security-settings"></a>Aby wyłączyć ustawień zabezpieczeń technologii ClickOnce  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **zabezpieczeń** kartę.  
  
3.  Wyczyść **włączenia ustawień zabezpieczeń technologii ClickOnce** pole wyboru.  
  
     Twoja aplikacja będzie uruchamiana za pomocą ustawień zabezpieczeń w trybie pełnego zaufania; wszystkie ustawienia na **zabezpieczeń** strony zostaną zignorowane.  
  
    > [!NOTE]
    >  Każdorazowo, gdy aplikacja została opublikowana przy użyciu Kreatora publikowania tego pola wyboru zostanie wybrany; należy usunąć je ponownie po każdej publikacji pomyślnie.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)



