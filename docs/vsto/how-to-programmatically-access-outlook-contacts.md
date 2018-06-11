---
title: 'Porady: programowane dostęp do kontaktów programu Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6ee09e0d0a51675bc00b19aedd0508276cb0cb09
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255944"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Porady: programowane dostęp do kontaktów programu Outlook
  W tym przykładzie znajduje wszystkie kontakty, których nazwiska zawierają określonego ciągu wyszukiwania.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compile-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Kontakty, których nazwiska zawierają ciąg znaków "**Na"** (na przykład Tzipi Butnaru) w **kontaktów** folderu.  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z elementami kontaktów](../vsto/working-with-contact-items.md)   
 [Porady: programowane Dodawanie wpisu do kontaktów programu Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Porady: programowane wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Porady: programowane wyszukiwanie adresu e-mail w kontaktach](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Porady: programowane usuwanie kontaktów programu Outlook](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  