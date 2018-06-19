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
ms.openlocfilehash: 743d7f259da4129eda578808d1ce04619104a3f1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31557674"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Porady: dostosowywanie domyślnej strony sieci Web dla aplikacji ClickOnce
Podczas publikowania aplikacji ClickOnce w sieci Web, strony sieci Web jest automatycznie generowany i opublikowani razem aplikacji. Domyślna strona zawiera nazwę aplikacji i łącza do zainstalowania aplikacji, instalowanie wymagań wstępnych lub dostępu do pomocy w witrynie MSDN.  
  
> [!NOTE]
>  Rzeczywiste łącza, które są wyświetlane na stronie zależą od komputera, na którym jest wyświetlana strona i wymagania wstępne są włącznie.  
  
 Nazwa domyślnej strony sieci Web jest Publish.htm; można zmienić nazwę w **projektanta projektu**. Aby uzyskać więcej informacji, zobacz [porady: określanie strony publikowania dla aplikacji ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 Strona sieci Publish.htm Web jest publikowany tylko wtedy, gdy Wykryto nowszą wersję.  
  
> [!NOTE]
>  Zmiany wprowadzone do Twojej **publikowania** ustawienia nie będzie miało wpływ na stronie Publish.htm z jednym wyjątkiem: Jeśli dodać lub usunąć wymagania wstępne po początkowym opublikowaniu, listę wymagań wstępnych nie będą już dokładne. Należy edytować tekst łącza wymagań wstępnych odzwierciedlić zmiany.  
  
### <a name="to-customize-the-publish-web-page"></a>Aby dostosować strony publikowania w sieci Web  
  
1.  Publikowanie aplikacji ClickOnce do lokalizacji w sieci Web. Aby uzyskać więcej informacji, zobacz [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2.  Na serwerze sieci Web otwórz plik Publish.htm w wizualnego projektanta sieci Web lub innego edytora HTML.  
  
3.  Dostosowywanie strony zgodnie z potrzebami i zapisz go.  
  
4.  Opcjonalna. Aby zapobiec zastępowaniu strony sieci Web Publikowanie dostosowanego programu Visual Studio, usuń zaznaczenie pola wyboru **automatycznego generowania strony sieci web wdrożenia po każdej publikowania** w oknie dialogowym Opcje publikowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Porady: Instalowanie wymagań wstępnych za pomocą aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Instrukcje: określanie strony publikowania dla aplikacji ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)