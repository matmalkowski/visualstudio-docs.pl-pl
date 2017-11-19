---
title: 'Porady: wersji publikacji ClickOnce zestawu | Dokumentacja firmy Microsoft'
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
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: be66edb3880e8ef91f8fd95d7f11fe465322451f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Porady: ustawienie wersji publikacji technologii ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` Właściwość określa, czy w przypadku publikowania aplikacji będzie traktowany jako aktualizacji. Każda wersja czasu jest zwiększany, aplikacja zostanie opublikowana jako aktualizacja.  
  
 `Publish Version` Można ustawić właściwości **publikowania** strony **projektanta projektu**.  
  
> [!NOTE]
>  Ma opcji projektu, który automatycznie powoduje zwiększenie `Publish Version` właściwość zawsze aplikacja jest opublikowana; ta opcja jest domyślnie włączona. Aby uzyskać więcej informacji, zobacz [porady: automatyczne zwiększenie wersji publikowania ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Aby zmienić wersję publikowania  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  W **publikowania wersji** pola, zwiększyć **głównych**, **pomocnicza**, **kompilacji**, lub **poprawki** wersji cyfry.  
  
    > [!NOTE]
    >  Nigdy nie należy zmniejszyć numeru wersji; to może spowodować nieprzewidywalne aktualizacji zachowanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Porady: automatycznie wersji publikacji ClickOnce inkrementacji](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)