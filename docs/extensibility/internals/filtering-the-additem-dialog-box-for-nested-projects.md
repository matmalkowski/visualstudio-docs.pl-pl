---
title: "Filtrowanie okno dialogowe AddItem dla projektów zagnieżdżonych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e1f5fc7695df028330d0e53faebefc178f499da1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Filtrowanie okno dialogowe AddItem dla projektów zagnieżdżonych
Po wyświetleniu **AddItem** okno dialogowe dla projektu zagnieżdżonego projektu nadrzędnego można kontrolować, jakie elementy są wyświetlane w oknie dialogowym.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Interfejs umożliwia filtrowanie węzły, które będą znajdować się w **AddItem** okno dialogowe. Gdy wyświetla projektu podrzędnego **AddItem** okno dialogowe, można zaimplementować nadrzędnego `IVsFilterAddProjectItemDlg` interfejsu i filtrowania elementów, które w przeciwnym razie będzie wyświetlana w projekcie dziecka.  
  
 Gdy projekty są pogrupowane według funkcji w obszarze nadrzędnego określonych projektów, można zaimplementować `IVsFilterAddProjectItemDlg` użytkownik wybrał **Dodaj element projektu** menu skrótów w projektu zagnieżdżonego. Implementowanie `IvsFilterAddProjectItemDlg displays` projektu tylko elementy lub pliki specyficzne dla tej grupy. Elementy projektu dla innych grup są odfiltrowywane z okna dialogowego, nawet jeśli są one przechowywane w tym samym katalogu.  
  
 Gdy użytkownik uruchomi **AddItem** okno dialogowe elementem podrzędnym implementacji projektu nadrzędnego `IVsFilterAddProjectItemDlg` wywoływany jest interfejs.  
  
 `IVsFilterAddProjectItemDlg` Interfejsu można też wdrożyć filtrowanie według kategorii. Aby uzyskać więcej informacji, zobacz [Dodawanie elementów do dodawania nowego elementu okien dialogowych](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) i [rejestrowanie Project and Item Templates](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Dodawanie elementów do Dodaj nowy element okien dialogowych](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Rejestrowanie szablony projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)