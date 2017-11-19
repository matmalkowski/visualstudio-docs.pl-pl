---
title: "Porady: ustawienie uprawnień niestandardowych dla aplikacji ClickOnce | Dokumentacja firmy Microsoft"
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
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 0e99583b9222e71421e548b0cdf1338e81c3c45b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Porady: ustawienie uprawnień niestandardowych dla aplikacji ClickOnce
Można wdrożyć [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, która używa domyślnych uprawnień w strefach Internet lub lokalny Intranet. Alternatywnie można utworzyć strefę niestandardowe uprawnienia, które są wymagane przez aplikację. Można to zrobić przez dostosowanie uprawnień zabezpieczeń w **zabezpieczeń** strony **projektanta projektu**.  
  
### <a name="to-customize-a-permission"></a>Aby dostosować uprawnienia  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **zabezpieczeń** kartę.  
  
3.  Wybierz **włączenia ustawień zabezpieczeń technologii ClickOnce** pole wyboru.  
  
4.  Wybierz **jest częściowo zaufanych aplikacji** przycisk opcji.  
  
     Formanty w **uprawnień zabezpieczeń ClickOnce** sekcji są włączone.  
  
5.  Z **strefy aplikacja zostanie zainstalowana z** listy rozwijanej, kliknij przycisk **(niestandardowy)**.  
  
6.  Kliknij przycisk **Edytuj uprawnienia XML**.  
  
     Pliku app.manifest zostanie otwarty w edytorze XML.  
  
7.  Przed `</applicationRequestMinimum>` element, należy dodać kod XML uprawnienia wymagane przez aplikację.  
  
    > [!NOTE]
    >  Można użyć `ToXml` ustawiona metoda uprawnienia, aby wygenerować kod XML dla manifest aplikacji. Na przykład, aby wygenerować plik XML dla <xref:System.Security.Permissions.EnvironmentPermission> zestaw uprawnień, wywołania <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> metody. Aby uzyskać więcej informacji na temat struktury uprawnienie ustawić XML, zobacz [NIB: porady: Importowanie zestawu uprawnień przy użyciu pliku XML](http://msdn.microsoft.com/en-us/dea16b54-c108-408a-ac36-cdc05f746236).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)