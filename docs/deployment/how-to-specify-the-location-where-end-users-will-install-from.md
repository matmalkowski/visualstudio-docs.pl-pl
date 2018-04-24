---
title: 'Porady: Określanie lokalizacji, gdzie użytkownicy końcowi będą przeprowadzać z | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0152cf6b03f2e089ee8633ef4abae9043e41bc24
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Porady: określanie lokalizacji, z której użytkownicy końcowi będą przeprowadzać instalacje
Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, lokalizacji, gdzie użytkownicy do pobrania i zainstalowania aplikacji nie jest zawsze lokalizacji, w którym początkowo publikowania aplikacji. Na przykład w niektórych organizacjach deweloper może publikowania aplikacji na serwerze tymczasowym, a następnie administrator przeniosłaby aplikacji na serwerze sieci Web.  
  
 W takim przypadku można użyć `Installation URL` właściwości w celu określenia serwera sieci Web, gdzie użytkownicy można pobrać aplikacji. Jest to konieczne, dzięki czemu manifest aplikacji miejsce wyszukać aktualizacje.  
  
 `Installation URL` Można ustawić właściwości **publikowania** strony **projektanta projektu**.  
  
 **Uwaga** `Installation URL` właściwości można również ustawić za pomocą **PublishWizard**. Aby uzyskać więcej informacji, zobacz [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Aby określić adres URL instalacji  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  W polu adresu URL instalacji, wprowadź lokalizację instalacji przy użyciu w pełni kwalifikowany adres URL, w formacie http://www.microsoft.com/ApplicationName, lub ścieżkę UNC w formacie \\\Server\ApplicationName.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Określ, gdzie programu Visual Studio kopiuje pliki](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)