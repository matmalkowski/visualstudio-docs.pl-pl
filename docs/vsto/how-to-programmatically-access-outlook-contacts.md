---
title: "Porady: programowane dostęp do kontaktów programu Outlook | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 4d4d88416507f7e63cd112df350dc93b2e13605f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Porady: Programowane uzyskiwanie dostępu do kontaktów programu Outlook
  W tym przykładzie znajduje wszystkie kontakty, których nazwiska zawierają określonego ciągu wyszukiwania.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Kontakty, których nazwiska zawierają ciąg znaków "**Na"** (na przykład Tzipi Butnaru) w **kontaktów** folderu.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z elementami kontaktów](../vsto/working-with-contact-items.md)   
 [Porady: programowane Dodawanie wpisu do kontaktów programu Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Porady: programowane wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Porady: programowane wyszukiwanie adresu E-Mail w kontaktach](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Instrukcje: Programowe usuwanie kontaktów programu Outlook](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  