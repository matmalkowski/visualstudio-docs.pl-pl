---
title: 'Porady: Dodawanie parametru do metody | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
ms.assetid: c5b6fd32-bf85-4b2a-a01e-f9199f0fb26e
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f6810d69628c66a011123250b8e0efb8622f0be7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Porady: dodawanie parametru do metody
  Użyj parametru do przekazywania informacji do metody lub do zwracania informacji z metody. Wszystkie metody musi mieć co najmniej jeden parametr. Aby uzyskać więcej informacji na temat projektowania parametru na potrzeby obsługi typu metody, która ma zostać utworzona, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Po dodaniu parametru do metody Visual Studio dodaje `<Parameter>` — element XML w pliku modelu w projekcie. Aby uzyskać więcej informacji na temat atrybutów `<Parameter>` elementu, zobacz [parametru](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### <a name="to-add-a-parameter-to-a-method"></a>Aby dodać parametr do metody  
  
1.  Dodawanie metody do jednostki.  
  
2.  Na pasku menu wybierz **widoku**, **inne okna**, **szczegóły metody usługi łączności danych biznesowych**.  
  
     **Szczegóły metody usługi łączności danych biznesowych** zostanie otwarte okno. Aby uzyskać więcej informacji, zobacz [omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  W **szczegóły metody usługi łączności danych biznesowych** , rozwiń węzeł metody, a następnie rozwiń węzeł **parametry** węzła.  
  
4.  W **dodać parametr** wybierz **tworzenie parametru**.  
  
     Nowy parametr pojawia się poniżej **parametry** węzła.  
  
5.  Na pasku menu wybierz **widoku**, **okna właściwości**.  
  
6.  W **właściwości** ustaw **nazwa** dowolną nazwę, która ma sens dla właściwości. Na przykład, jeśli metoda zwróci klientów, możesz nazwać metody **GetCustomers**.  
  
7.  W **szczegóły metody usługi łączności danych biznesowych** okna, Otwórz na liście dla kierunku parametru, a następnie wybierz **w**, **InOut**, **się**, lub **zwracać**.  
  
     Aby uzyskać więcej informacji na temat kierunku, aby wybrać dla metody typu, który tworzysz, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Zmodyfikuj deskryptor typu parametru. Aby uzyskać więcej informacji, zobacz [porady: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Porady: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Porady: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Porady: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)   
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  