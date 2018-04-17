---
title: Co najmniej jednej właściwości w pliku .ofs nie są prawidłowe dla klasy wybranego komunikatu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7ac9f5ab05ba6ed858946b5f665d850eea51c230
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Jedna właściwość lub więcej w pliku .ofs jest nieprawidłowa dla klasy wybranego komunikatu
  Ten błąd pojawia się po zaimportowaniu regionów formularzy zaprojektowanych w programie Outlook, ale co najmniej jedno pole na region formularza nie są zgodne z klas wiadomości, które wybiera się na ostatniej stronie **nowego regionu formularza** kreatora.  
  
 Na przykład możesz wybrać pozycję **zadań (IPM. Zadanie)** na ostatniej stronie **nowego regionu formularza** kreatora. Jeśli regionu formularza zawiera **adres firmy** pola, zostanie wyświetlony ten błąd, ponieważ zadanie nie ma adres firmy. W związku z tym **adres firmy** pola nie jest zgodny z IPM. Klasy wiadomości zadań.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Na ostatniej stronie **nowego regionu formularza** kreatora wybierz klasy wiadomości, która jest zgodna z pola regionu formularza.  
  
-   W narzędziu Projektant dla formularzy w programie Outlook, usuń pola, które nie są zgodne z klas wiadomości, które mają być wybierz na ostatniej stronie **nowego regionu formularza** kreatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  