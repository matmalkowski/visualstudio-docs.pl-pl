---
title: 'Porady: Definiowanie wystąpienia metody | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6e6dd6c0d7676c6b3c2071f0fcb07e8073313633
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120284"
---
# <a name="how-to-define-a-method-instance"></a>Porady: Definiowanie wystąpienia metody
  Należy zdefiniować co najmniej jedno wystąpienie metody dla każdej metody w modelu.  
  
 Dodaj wystąpienie metody przy użyciu **szczegóły metody usługi łączności danych biznesowych** okna. Po dodaniu wystąpienia metody Visual Studio dodaje `<MethodInstance>` — element XML w pliku modelu w projekcie. Aby uzyskać więcej informacji na temat atrybutów `<MethodInstance>` elementu, zobacz [wystąpienia metody](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
### <a name="to-define-a-method-instance"></a>Aby określić wystąpienie metody  
  
1.  W **szczegóły metody usługi łączności danych biznesowych** , rozwiń węzeł metody, a następnie rozwiń węzeł **wystąpień** węzła.  
  
2.  W **dodać wystąpienia metody** wybierz **Utwórz wystąpienie wyszukiwania**.  
  
     Nowe wystąpienie metody zostanie wyświetlone poniżej **wystąpień** węzła.  
  
3.  Na pasku menu wybierz **widoku** > **okna właściwości**.  
  
4.  W **właściwości** Ustaw właściwości wystąpienia metody. Aby uzyskać więcej informacji na temat każdej właściwości, zobacz [wystąpienia metody](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
## <a name="see-also"></a>Zobacz także
 [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Porady: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Porady: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Porady: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
