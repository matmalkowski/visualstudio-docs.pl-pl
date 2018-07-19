---
title: 'Porady: Określanie lokalizacji, w której użytkownicy końcowi będą przeprowadzać instalacje | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 6b0731a5e218b6fcd6a13ac00fe19daad86f6b3d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078088"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Porady: Określanie lokalizacji, w której użytkownicy końcowi będą przeprowadzać instalacje
Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, lokalizację, do którego użytkownicy używają do pobrania i zainstalowania aplikacji nie jest koniecznie lokalizacji, w którym początkowo opublikować aplikację. Na przykład w niektórych organizacjach deweloper może publikować aplikacje na serwerze tymczasowym, a następnie administrator może przenieść aplikację na serwerze sieci Web.  
  
 W takim przypadku można użyć `Installation URL` właściwości w celu określenia serwera sieci Web, gdzie użytkownicy pobierać aplikację. Jest to konieczne, tak aby wie, gdzie szukać aktualizacji manifestu aplikacji.  
  
 `Installation URL` Właściwość można ustawić na **Publikuj** strony **projektanta projektu**.  
  
 **Uwaga** `Installation URL` właściwości można również ustawić za pomocą **PublishWizard**. Aby uzyskać więcej informacji, zobacz [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Aby określić adres URL instalacji  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **Publikuj** kartę.  
  
3.  W polu adres URL instalacji wprowadź lokalizację instalacji przy użyciu w pełni kwalifikowany adres URL w formacie *http://www.microsoft.com/ApplicationName*, lub ścieżkę UNC w formacie  *\\\Server\ApplicationName*.  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: Określanie lokalizacji kopiowania plików w programie Visual Studio](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)