---
title: 'Porady: programowane wyszukiwanie adresu e-mail w kontaktach'
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
ms.openlocfilehash: e7b9c4c7d02f3cd1564e6733c46cb821eade7f54
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677628"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>Porady: programowane wyszukiwanie adresu e-mail w kontaktach
  W tym przykładzie wyszukuje skontaktuj się z folderu kontaktów, które mają taką nazwę domeny **example.com** w ich adresy e-mail.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Ten przykład wymaga:  
  
-   Kontakty, które mają taką nazwę domeny **example.com** w ich adresy e-mail (na przykład `somebody@example.com`), których imiona i nazwiska.  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z elementami kontaktów](../vsto/working-with-contact-items.md)   
 [Porady: programowane wysyłanie wiadomości e-mail](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [Instrukcje: programowe uzyskiwanie dostępu do kontaktów programu Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Porady: programowane Dodawanie wpisu do kontaktów programu Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  