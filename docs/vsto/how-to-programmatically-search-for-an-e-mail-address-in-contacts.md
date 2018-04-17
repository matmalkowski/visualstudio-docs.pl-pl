---
title: 'Porady: programowane wyszukiwanie adresu E-Mail w kontaktach | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 16b79f5f14f1e0d8c5c82a00f5f2ccf2412b991b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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
  
  