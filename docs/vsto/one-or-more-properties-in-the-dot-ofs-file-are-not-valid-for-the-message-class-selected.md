---
title: Jedna właściwość lub więcej w pliku .ofs jest nieprawidłowa dla klasy wybranego komunikatu
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
ms.openlocfilehash: cfae8533337bbe18c89dbb670fb58a0c89c6c54c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692502"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Jedna właściwość lub więcej w pliku .ofs jest nieprawidłowa dla klasy wybranego komunikatu
  Ten błąd pojawia się po zaimportowaniu regionów formularzy zaprojektowanych w programie Outlook, ale co najmniej jedno pole na region formularza nie są zgodne z klas wiadomości, które wybiera się na ostatniej stronie **nowego regionu formularza** kreatora.  

Na przykład możesz wybrać pozycję **zadań (IPM. Zadanie)** na ostatniej stronie **nowego regionu formularza** kreatora. Jeśli ma regionu formularza **adres firmy** pola, otrzymasz ten błąd, ponieważ zadanie nie ma adres firmy. W związku z tym **adres firmy** pola nie jest zgodny z `IPM.Task` klasą wiadomości.  
  
 Możesz wybrać pozycję **zadań (IPM. Zadanie)** na ostatniej stronie **nowego regionu formularza** kreatora. Jeśli ma regionu formularza **adres firmy** pola, otrzymasz ten błąd, ponieważ zadanie nie ma adres firmy. W związku z tym **adres firmy** pola nie jest zgodny z `IPM.Task` klasą wiadomości.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Na ostatniej stronie **nowego regionu formularza** kreatora wybierz klasy wiadomości, która jest zgodna z pola regionu formularza.  
  
-   W narzędziu Projektant dla formularzy w programie Outlook usuń pola, które nie są zgodne z klas wiadomości. Usuń pola, które mają być wybierz na ostatniej stronie **nowego regionu formularza** kreatora.  
  
## <a name="see-also"></a>Zobacz także  
 [Wskazówki: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  