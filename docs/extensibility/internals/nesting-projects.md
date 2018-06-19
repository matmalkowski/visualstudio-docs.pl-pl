---
title: Projekty zagnieżdżenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35d0f4f8906acc08733894d1c24b6d8c2199e1f7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131163"
---
# <a name="nesting-projects"></a>Projekty zagnieżdżenia
Deweloperów w przedsiębiorstwach aplikacji korzystających z pakietu VS można grupowania podobnych typów projektów w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] za pomocą *projektu zagnieżdżenia*. Na przykład projektu szablonu używa zagnieżdżonych projekty do grupy projektów do kategorii. Projekty fasad biznesowe, projekty sieci Web interfejsu użytkownika i tak dalej są pogrupowane w jednej kategorii.  
  
 W tym scenariuszu nie ma żadnego limitu liczby projekty, do których dewelopera można zagnieździć w każdym projekcie nadrzędnej, mimo że deweloper może zapewnić programowo limity. Ten rodzaj grupowania można również cyklicznych, w takim przypadku projektów tego samego typu co projektu podrzędnego mogą być zagnieżdżane w obszarze dziecka stają się podprojektu elementu podrzędnego, czyli podprojektu elementu nadrzędnego.  
  
 Zagnieżdżanie projektu nie jest wewnętrzna część [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Trzeba napisać kod, aby włączyć zagnieżdżenia i subproject zagnieżdżenia w obrębie projektów podrzędnych. Projekt nadrzędny jest pakiet VSPackage specjalnych lub typu projektu, utworzona i zarejestrowana z własny identyfikator GUID, który zawiera kod, który jest wymagany do zaimplementowania projektu zagnieżdżenia.  
  
 Przykład zagnieżdżonych projekty można znaleźć w przykładowych projektach Example.Nested C#.  
  
## <a name="nested-projects-example"></a>Przykład zagnieżdżonych projektów  
 ![Zagnieżdżone rozwiązania projekty](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Przykład zagnieżdżonych projektów  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: wdrożeniu zagnieżdżonych projektów](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Zagadnienia dotyczące zwalniania i przeładunku zagnieżdżonych projektów](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Obsługa kreatora dla projektów zagnieżdżonych](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Rejestrowanie szablony projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementowanie obsługi dla projektów zagnieżdżonego polecenia](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Filtrowanie okno dialogowe AddItem dla projektów zagnieżdżonych](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parametry kontekstu](../../extensibility/internals/context-parameters.md)   
 [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)