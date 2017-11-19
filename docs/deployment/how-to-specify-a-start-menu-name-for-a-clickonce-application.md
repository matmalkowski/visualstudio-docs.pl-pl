---
title: "Porady: Określanie nazwy Menu Start dla aplikacji ClickOnce | Dokumentacja firmy Microsoft"
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
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: b27cf6d67cef1098a54277d4857b75d3fba0ff65
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Porady: określanie nazwy menu Start dla aplikacji ClickOnce
Gdy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalacji aplikacji do użytku w trybie online i offline, wpis zostanie dodany do **Start** menu i **Dodaj lub usuń programy** listy. Domyślnie wyświetlana nazwa jest taka sama jak nazwa zestawu aplikacji, ale można zmienić nazwę wyświetlaną, ustawiając **nazwa produktu** w **opcji publikowania** okno dialogowe.  
  
 **Nazwa produktu** będą wyświetlane na stronie publish.htm; dla zainstalowanej aplikacji w trybie offline, będzie on nazwę wpisu w **Start** menu, a także być nazwę, która zawiera w **Dodawanie lub usuwanie Programy**.  
  
 **Nazwa wydawcy** będą wyświetlane na stronie publish.htm powyżej **nazwa produktu**, oraz zainstalowanych aplikacji w trybie offline, konieczne będzie również nazwę folderu, który zawiera ikonę aplikacji w **Start**  menu.  
  
 Można ustawić **nazwa produktu** i **nazwę wydawcy** właściwości w **opcji publikowania** okno dialogowe, dostępnych na **publikowania** strony z **Projektant projektu**.  
  
### <a name="to-specify-a-start-menu-name"></a>Aby określić nazwy menu Start  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  Kliknij przycisk **opcje** przycisk, aby otworzyć **opcji publikowania** okno dialogowe.  
  
4.  Kliknij przycisk **opis**.  
  
5.  W **opcji publikowania** okna dialogowego wprowadź nazwę wyświetlaną w **nazwa produktu**.  
  
6.  Opcjonalnie można wprowadzić nazwę wydawcy w **nazwę wydawcy**.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)