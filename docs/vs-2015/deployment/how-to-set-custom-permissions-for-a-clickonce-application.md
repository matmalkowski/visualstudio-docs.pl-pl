---
title: 'Porady: ustawienie uprawnień niestandardowych dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
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
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 6cf4b1c91650bf505daececfdf46ba42cfee68fb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678259"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Porady: ustawienie uprawnień niestandardowych dla aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: Ustaw uprawnienia niestandardowe dla aplikacji ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-set-custom-permissions-for-a-clickonce-application).  
  
Możesz wdrożyć [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji, która używa domyślnych uprawnień dla stref Internet lub lokalny Intranet. Alternatywnie można utworzyć strefę niestandardową dla określonych uprawnień wymaganych przez aplikację. Można to zrobić poprzez dostosowanie uprawnień zabezpieczeń w **zabezpieczeń** strony **projektanta projektu**.  
  
### <a name="to-customize-a-permission"></a>Aby dostosować uprawnienia  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **zabezpieczeń** kartę.  
  
3.  Wybierz **włączenia ustawień zabezpieczeń technologii ClickOnce** pole wyboru.  
  
4.  Wybierz **to częściowo zaufanych aplikacji** przycisku opcji.  
  
     Formanty w **uprawnienia zabezpieczeń aplikacji ClickOnce** sekcji są włączone.  
  
5.  Z **strefy, aplikacja zostanie zainstalowana z** listy rozwijanej kliknij **(niestandardowy)**.  
  
6.  Kliknij przycisk **Edytuj uprawnienia XML**.  
  
     Plik app.manifest zostanie otwarty w edytorze XML.  
  
7.  Przed `</applicationRequestMinimum>` elementu Dodawanie kodu XML uprawnienia, których wymaga aplikacja.  
  
    > [!NOTE]
    >  Możesz użyć `ToXml` ustawiona metoda uprawnienia, można wygenerować kodu XML manifestu aplikacji. Na przykład, aby wygenerować plik XML dla <xref:System.Security.Permissions.EnvironmentPermission> zestaw uprawnień, wywołanie <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> metody. Aby uzyskać więcej informacji na temat struktury uprawnienie ustawić XML, zobacz [NIB: instrukcje: importowanie uprawnienie ustawione przy użyciu pliku XML](http://msdn.microsoft.com/en-us/dea16b54-c108-408a-ac36-cdc05f746236).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)



