---
title: 'Porady: określanie strony publikowania dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: a368f3294056df75ca1a780d89079688cdb1ead9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Porady: określanie strony publikowania dla aplikacji ClickOnce
Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji domyślnej strony sieci Web (publish.htm) zostaną wygenerowane i opublikowane wraz z aplikacji. Ta strona zawiera nazwę aplikacji, łącze do zainstalowania aplikacji i/lub wymagań wstępnych i link do tematu Pomocy zawierająca opis [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. **Opublikuj stronę** właściwości projektu można określić nazwę strony sieci Web dla Twojego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.  
  
 Po stronie publikacji został określony, przy następnym możesz opublikować go zostaną skopiowane do lokalizacji publikacji; nie zostaną zastąpione w przypadku publikowania ponownie. Jeśli chcesz dostosować wygląd strony, możesz to zrobić bez obaw o utratę danych. Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie strony sieci Web technologii ClickOnce domyślne](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 **Opublikuj stronę** właściwości można ustawić w **opcji publikowania** okno dialogowe, dostępne z **publikowania** okienku **projektanta projektu**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Aby określić niestandardowe strony sieci Web dla aplikacji ClickOnce  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.  
  
2.  Wybierz **publikowania** okienka.  
  
3.  Kliknij przycisk **opcje** przycisk, aby otworzyć **opcji publikowania** okno dialogowe.  
  
4.  Kliknij przycisk **wdrożenia**.  
  
5.  W **opcji publikowania** okna dialogowego upewnij się, że **opublikować stronę sieci web Otwórz wdrożenia po** jest zaznaczone pole wyboru (ona powinny zostać wybrana domyślnie).  
  
6.  W **stronę sieci web wdrożenia:** , wprowadź nazwę dla strony sieci Web, a następnie kliknij **OK**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Aby zapobiec uruchamianiu zawsze, gdy opublikujesz strony publikowania  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.  
  
2.  Wybierz **publikowania** okienka.  
  
3.  Kliknij przycisk **opcje** przycisk, aby otworzyć **opcji publikowania** okno dialogowe.  
  
4.  Kliknij przycisk **wdrożenia**.  
  
5.  W **opcji publikowania** okno dialogowe, usuń zaznaczenie **opublikować stronę sieci web Otwórz wdrożenia po** pole wyboru.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Porady: dostosowywanie ClickOnce domyślnej strony sieci Web](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)