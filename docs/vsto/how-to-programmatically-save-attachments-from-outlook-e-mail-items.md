---
title: "Porady: programowane zapisywanie załączników z elementów poczty E-Mail programu Outlook | Dokumentacja firmy Microsoft"
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
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f87b05b45fafab3ad28a6da6a98391b8d121be7e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-save-attachments-from-outlook-e-mail-items"></a>Porady: Programowane zapisywanie załączników z elementów poczty e-mail programu Outlook
  Po odebraniu wiadomości e-mail w skrzynce odbiorczej, w tym przykładzie zapisuje załączniki wiadomości e-mail do określonego folderu.  
  
> [!IMPORTANT]  
>  W tym przykładzie działa tylko wtedy, gdy dodać folder o nazwie **TestFileSave** w głównym katalogu C.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z elementami poczty](../vsto/working-with-mail-items.md)   
 [Porady: programowane pobieranie folderu na podstawie nazwy](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Porady: programowane wykonywanie akcji po odebraniu wiadomości E-Mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)   
 [Instrukcje: Programowe wyszukiwanie w określonym folderze](../vsto/how-to-programmatically-search-within-a-specific-folder.md)  
  
  