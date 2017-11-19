---
title: "Porady: Określ, gdzie programu Visual Studio kopiuje pliki | Dokumentacja firmy Microsoft"
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
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 0e1bfe41d34c1c507818f7bb255425d31dc2f343
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Porady: określanie lokalizacji kopiowania plików przez program Visual Studio
Podczas publikowania aplikacji przy użyciu technologii ClickOnce, `Publish Location` właściwość określa lokalizację, gdzie umieścić pliki aplikacji i manifest. Może to być ścieżka pliku lub ścieżkę do serwera FTP.  
  
 Można określić `Publish Location` właściwość **publikowania** strony **projektanta projektu**, lub za pomocą Kreatora publikacji. Aby uzyskać więcej informacji, zobacz [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Po zainstalowaniu więcej niż jedną wersję aplikacji przy użyciu technologii ClickOnce instalacji przenosi wcześniejszych wersji aplikacji do folderu o nazwie archiwum w określonej lokalizacji. Archiwizowanie starszych wersji w ten sposób przechowuje katalog instalacyjny wyczyść folderów ze starszej wersji.  
  
### <a name="to-specify-a-publishing-location"></a>Aby określić lokalizację publikowania  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  W **lokalizację publikowania** wprowadź lokalizację publikowania za pomocą jednej z następujących formatów:  
  
    -   Aby opublikować ścieżki dysku lub udziału plików, wprowadź ścieżkę przy użyciu ścieżki UNC (\\\Server\ApplicationName) lub ścieżkę do pliku (C:\Deploy\ApplicationName).  
  
    -   Aby opublikować serwer FTP, wprowadź ścieżkę przy użyciu format ftp://ftp.microsoft.com/ApplicationName.  
  
     Należy pamiętać, że tekst musi znajdować się w **lokalizację publikowania** polu aby Przeglądaj (**...** ) przycisku do pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)