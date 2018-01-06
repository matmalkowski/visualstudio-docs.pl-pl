---
title: 'Porady: programowane wyszukiwanie adresu E-Mail w kontaktach | Dokumentacja firmy Microsoft'
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
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
ms.assetid: e973a407-8b94-45c7-acdf-fe330115fb33
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 57c0cac0dd2b22b38284caec0a2bfb40d6e5b101
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-search-for-an-e-mail-address-in-contacts"></a>Porady: Programowane wyszukiwanie adresu e-mail w kontaktach
  W tym przykładzie wyszukuje folderu kontaktów, kontaktów, które mają nazwy domeny **example.com** w ich adresów e-mail.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Kontakty, które mają nazwy domeny **example.com** w ich adresów e-mail (na przykład `somebody@example.com`), i mają imiona i nazwiska.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z elementami kontaktów](../vsto/working-with-contact-items.md)   
 [Porady: programowane wysyłanie wiadomości E-Mail](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [Porady: programowane dostęp do kontaktów programu Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Instrukcje: Programowe dodawanie wpisu do kontaktów programu Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  