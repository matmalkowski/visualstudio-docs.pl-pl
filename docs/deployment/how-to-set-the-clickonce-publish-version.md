---
title: 'Porady: wersji publikacji ClickOnce zestawu | Dokumentacja firmy Microsoft'
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
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: a0f96a3837a2c3a05a8fac20a9b6e5d4448f9c7e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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
 [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)