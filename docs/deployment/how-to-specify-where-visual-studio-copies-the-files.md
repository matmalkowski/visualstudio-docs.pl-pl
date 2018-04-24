---
title: 'Porady: Określ, gdzie programu Visual Studio kopiuje pliki | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 2b4e626253d9d07a9f263304d02739bdb3f4b012
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
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
 [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)