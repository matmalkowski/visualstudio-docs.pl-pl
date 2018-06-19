---
title: 'Porady: ustawienie uprawnień niestandardowych dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0980b2ddb2dd6a8db86078cb600f2486bb63f325
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31560443"
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
    >  Można użyć `ToXml` ustawiona metoda uprawnienia, aby wygenerować kod XML dla manifest aplikacji. Na przykład, aby wygenerować plik XML dla <xref:System.Security.Permissions.EnvironmentPermission> zestaw uprawnień, wywołania <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)