---
title: 'Porady: edytowanie zapytań TableAdapter | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DbSource
- vbdata.Microsoft.VSDesigner.DataSource.DbSource
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- queries [Visual Basic], editing
- TableAdapters, editing queries
- data [Visual Studio], TableAdapters
- editing queries
ms.assetid: aac7b7b4-bd91-4225-95d4-a07643568c43
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 14157d10f105c6f3a1e95442edfe18bfd3aebd6e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677117"
---
# <a name="how-to-edit-tableadapter-queries"></a>Porady: edytowanie zapytań TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytowanie zapytań TableAdapter z [edytowanie TableAdapters](../data-tools/editing-tableadapters.md) w **Projektanta obiektów Dataset**. Należy zmodyfikować zapytania TableAdapter, gdy już nie spełnia wymagań aplikacji. (, Możesz też utworzyć dodatkowych kwerend w metodzie TableAdapter. Aby uzyskać więcej informacji o dodawaniu nowych zapytań, zobacz [porady: tworzenie zapytań TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).)  
  
> [!NOTE]
>  Jeśli [Kreator konfiguracji TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8) otwiera zamiast **Kreatora konfiguracji zapytania TableAdapter**, być może wybrano main TableAdapter `Fill` zapytania, a nie w jednym z Dodatkowe zapytania TableAdapter firmy. Dla głównego informacji na temat edytowania TableAdapter `Fill` zapytania o dane, zobacz [jak: edytowanie TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
 ![TableAdapter z wieloma zapytaniami](../data-tools/media/tableadapter.gif "TableAdapter")  
  
### <a name="to-edit-a-tableadapter-query"></a>Edytowanie zapytań TableAdapter  
  
1.  Otwórz zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [porady: otwieranie zestawu w Projektancie obiektów Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Wybierz zapytanie TableAdapter, które chcesz edytować.  
  
3.  Kliknij prawym przyciskiem myszy zapytanie TableAdapter, a następnie wybierz pozycję **Konfiguruj**.  
  
     **Kreatora konfiguracji zapytania TableAdapter** zostanie otwarta, możesz zmodyfikować zapytanie lub procedura składowana dla tego zapytania.  
  
4.  Wykonaj **Kreatora konfiguracji zapytania TableAdapter** ze zmianami, które chcesz. Aby uzyskać więcej informacji, zobacz [edytowanie TableAdapters](../data-tools/editing-tableadapters.md).  
  
## <a name="see-also"></a>Zobacz też  
 [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [O łączeniu z danymi w programie Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Przygotowanie aplikacji na odbieranie danych](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md)   
 [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edytowanie danych w aplikacji](../data-tools/editing-data-in-your-application.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Zapisywanie danych](../data-tools/saving-data.md)   
 [Wskazówki dotyczące danych](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)