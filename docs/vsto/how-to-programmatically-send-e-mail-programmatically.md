---
title: 'Porady: programowane wysyłanie wiadomości e-mail'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 32977852ffbc4bb1411ed699cc97bb54035fada4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677590"
---
# <a name="how-to-programmatically-send-email"></a>Porady: programowane wysyłanie wiadomości e-mail  
  W tym przykładzie wysyła wiadomość e-mail do kontaktów, które mają taką nazwę domeny **example.com** adresu e-mail.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Ten przykład wymaga:  
  
-   Kontakty, które mają taką nazwę domeny **example.com** adresu e-mail.  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Nie usuwaj kodu filtr, który wyszukuje nazwy domeny **example.com**. Rozwiązanie będzie wysyłać wiadomości e-mail do wszystkich kontaktów, jeśli usuniesz filtr.  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z elementami poczty](../vsto/working-with-mail-items.md)   
 [Porady: programowane Tworzenie elementu poczty e-mail](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Instrukcje: programowe uzyskiwanie dostępu do kontaktów programu Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Porady: programowane wykonywanie akcji po otrzymaniu wiadomości e-mail](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  