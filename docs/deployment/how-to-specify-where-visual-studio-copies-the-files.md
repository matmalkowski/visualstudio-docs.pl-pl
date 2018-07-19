---
title: 'Porady: Określanie lokalizacji kopiowania plików w programie Visual Studio | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b2a4d642bc551127f34fe7a64ec01665b7ace70
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078631"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Porady: Określanie lokalizacji kopiowania plików w programie Visual Studio
Podczas publikowania aplikacji przy użyciu technologii ClickOnce, `Publish Location` właściwość określa lokalizację, gdzie umieścić pliki aplikacji i manifest. Może to być ścieżka pliku lub ścieżkę do serwera FTP.  
  
 Można określić `Publish Location` właściwość **Publikuj** strony **projektanta projektu**, lub za pomocą Kreatora publikacji. Aby uzyskać więcej informacji, zobacz [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Po zainstalowaniu więcej niż jedna wersja aplikacji przy użyciu technologii ClickOnce, instalacja przemieszcza inne wersje aplikacji do folderu o nazwie archiwum, w lokalizacji publikowania, który określisz. Archiwizowanie starszych w ten sposób utrzymuje katalogu instalacyjnyego folderów z wcześniejszych wersji.  
  
### <a name="to-specify-a-publishing-location"></a>Aby określić lokalizację publikowania  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **Publikuj** kartę.  
  
3.  W **lokalizacji publikowania** wprowadź lokalizację publikowania za pomocą jednego z następujących formatów:  
  
    -   Aby opublikować udziału lub dysku ścieżki pliku, wprowadź ścieżkę przy użyciu ścieżki UNC (*\\\Server\ApplicationName*) lub ścieżkę do pliku (*C:\Deploy\ApplicationName*).  
  
    -   Aby opublikować na serwerze FTP, wprowadź ścieżkę w formacie *ftp://ftp.microsoft.com/\<ApplicationName >*.  
  
     Należy pamiętać, że tekst musi znajdować się w **lokalizację publikowania** polu w kolejności do przeglądania (**...** ) przycisku do pracy.  
  
## <a name="see-also"></a>Zobacz także  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)