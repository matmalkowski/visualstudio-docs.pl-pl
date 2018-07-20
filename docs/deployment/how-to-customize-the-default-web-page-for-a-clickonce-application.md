---
title: 'Porady: Dostosowywanie domyślnej strony sieci Web dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d64e6432c1bfe696bf3b116aa35b5f4a5c597507
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153140"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Porady: Dostosowywanie domyślnej strony sieci Web dla aplikacji ClickOnce
Podczas publikowania aplikacji ClickOnce w sieci Web, strony sieci Web jest automatycznie generowany i opublikowanych wraz z aplikacji. Domyślna strona zawiera nazwę aplikacji i linki do zainstalowania aplikacji, instalowanie wstępnie wymaganego oprogramowania lub dostępu do pomocy w witrynie MSDN.  
  
> [!NOTE]
>  Rzeczywiste łącza, widocznych na stronie zależy od komputera, na którym wyświetlania strony i wymagania wstępne są włącznie.  
  
 Nazwa domyślnej strony sieci Web jest *Publish.htm*; możesz zmienić nazwę w **projektanta projektu**. Aby uzyskać więcej informacji, zobacz [porady: określanie strony publikowania dla aplikacji ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 *Publish.htm* strony sieci Web jest publikowany, tylko wtedy, gdy Wykryto nowszą wersję.  
  
> [!NOTE]
>  Zmiany wprowadzone do usługi **publikowania** nie wpłynie na ustawienia *Publish.htm* strony z jednym wyjątkiem: Jeśli dodasz lub usuniesz wymagania wstępne po początkowym opublikowaniu, będzie listę wymagań wstępnych już nie być dokładna. Należy edytować tekst łącza wymagań wstępnych odzwierciedlić zmiany.  
  
### <a name="to-customize-the-publish-web-page"></a>Aby dostosować strony sieci Web publikowania  
  
1.  Publikowanie aplikacji ClickOnce do lokalizacji w sieci Web. Aby uzyskać więcej informacji, zobacz [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2.  Na serwerze sieci Web otwórz *Publish.htm* pliku w Visual Web Designer lub innego edytora HTML.  
  
3.  Dostosowywanie strony zgodnie z potrzebami i zapisz go.  
  
4.  Opcjonalna. Aby zapobiec zastąpieniu strony sieci Web publikowanie niestandardowych programu Visual Studio, usuń zaznaczenie pola wyboru **automatycznie Generuj stronę sieci Web wdrożenia po każdej publikowania** w **opcji publikowania** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz także  
 [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Porady: Instalowanie wymagań wstępnych przy użyciu aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Porady: określanie strony publikowania dla aplikacji ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)