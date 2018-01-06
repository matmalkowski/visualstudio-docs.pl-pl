---
title: "Obsługa kreatora dla projektów zagnieżdżonych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 757968aabfc256cda37a103d48c8d12f1fc16fa5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wizard-support-for-nested-projects"></a>Obsługa kreatora dla projektów zagnieżdżonych
Dwa kreatory, które można wdrożyć projektu nadrzędnego dla projektów zagnieżdżonych uruchamia IDE: **nowy projekt** kreatora i **Dodaj element** kreatora.  
  
 Jeśli użytkownik uruchamia **nowy projekt** kreatora, wybierając **Dodawanie projektu** i klikając **nowy projekt** menu Plik lub wybierając **Dodaj** i klikając prawym przyciskiem myszy **nowy projekt** w Eksploratorze rozwiązań, uruchamia IDE **AddProject** polecenia i realizacji projektu nadrzędnego **AddProject**polecenie to zwraca plik szablonu projektu lub pliku kreatora (.vsz), który ma zestaw parametrów kontekstu.  
  
 Podobnie, projektu nadrzędnego implementacja **AddItem** kreatorów zwraca plik .vsz, który ma inny zestaw parametrów kontekstu.  
  
 Aby uzyskać więcej informacji o kreatorach, zobacz [kreatora (. Pliku Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [parametrów kontekstu](../../extensibility/internals/context-parameters.md) i [rejestrowanie szablony projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)