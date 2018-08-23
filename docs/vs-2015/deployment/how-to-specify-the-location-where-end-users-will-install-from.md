---
title: 'Porady: Określanie lokalizacji, w której użytkownicy końcowi będą przeprowadzać instalacje | Dokumentacja firmy Microsoft'
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
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 68f50fe847d1432292491cd2970c7897eb1388da
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42695458"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Porady: określanie lokalizacji, z której użytkownicy końcowi będą przeprowadzać instalacje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: Określ lokalizację gdzie użytkownicy końcowi będą zainstalować z](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-the-location-where-end-users-will-install-from).  
  
Podczas publikowania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji, lokalizację, do którego użytkownicy używają do pobrania i zainstalowania aplikacji nie jest koniecznie lokalizacji, w którym początkowo opublikować aplikację. Na przykład w niektórych organizacjach deweloper może publikować aplikacje na serwerze tymczasowym, a następnie administrator może przenieść aplikację na serwerze sieci Web.  
  
 W takim przypadku można użyć `Installation URL` właściwości w celu określenia serwera sieci Web, gdzie użytkownicy pobierać aplikację. Jest to konieczne, tak aby wie, gdzie szukać aktualizacji manifestu aplikacji.  
  
 `Installation URL` Właściwość można ustawić na **Publikuj** strony **projektanta projektu**.  
  
 **Uwaga** `Installation URL` właściwości można również ustawić za pomocą **PublishWizard**. Aby uzyskać więcej informacji, zobacz [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Aby określić adres URL instalacji  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **Publikuj** kartę.  
  
3.  W polu adres URL instalacji wprowadź lokalizację instalacji przy użyciu w pełni kwalifikowany adres URL w formacie http://www.microsoft.com/ApplicationName, lub ścieżkę UNC w formacie \\\Server\ApplicationName.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Określanie lokalizacji kopiowania plików w programie Visual Studio](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



