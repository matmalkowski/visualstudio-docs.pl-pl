---
title: "Porady: programowane wyznaczanie bieżącego elementu programu Outlook | Dokumentacja firmy Microsoft"
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
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: de17e299e98a46a82547bc38dfecd17a9f5aea58
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Porady: Programowane wyznaczanie bieżącego elementu programu Outlook
  W tym przykładzie użyto Explorer.SelectionChange zdarzeń, aby wyświetlić nazwę w bieżącym folderze i niektóre informacje na temat wybranego elementu. Następnie kod wyświetla wybrany element.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Termin, skontaktuj się z pomocą i elementów poczty e-mail w programie Microsoft Office Outlook.  
  
## <a name="see-also"></a>Zobacz też  
 [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)   
 [Porady: programowane pobieranie folderu na podstawie nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Instrukcje: Programowe wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  