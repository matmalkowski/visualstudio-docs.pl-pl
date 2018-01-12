---
title: "Porady: programowane wysyłanie wiadomości E-Mail | Dokumentacja firmy Microsoft"
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
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f8681fecf8dc2d4c3a26aeaeb372faeb57e54094
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-send-e-mail"></a>Porady: programowane wysyłanie wiadomości E-Mail  
  W tym przykładzie wysyła wiadomość e-mail do kontaktów, które mają nazwy domeny **example.com** w ich adresów e-mail.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Kontakty, które mają nazwy domeny **example.com** w ich adresów e-mail.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Nie usuwaj kod filtru, która szuka nazwy domeny **example.com**. Rozwiązanie będzie wysyłać wiadomości e-mail do wszystkich kontaktów, po usunięciu filtru.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z elementami poczty](../vsto/working-with-mail-items.md)   
 [Porady: programowane Tworzenie elementu poczty E-Mail](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Porady: programowane dostęp do kontaktów programu Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Instrukcje: Programowe wykonywanie akcji po otrzymaniu wiadomości e-mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  