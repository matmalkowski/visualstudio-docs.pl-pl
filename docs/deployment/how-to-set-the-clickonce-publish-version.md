---
title: 'Porady: wersji publikacji ClickOnce zestawu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96bb991efed7d5a353fc7b73bcb647190438ff84
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
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