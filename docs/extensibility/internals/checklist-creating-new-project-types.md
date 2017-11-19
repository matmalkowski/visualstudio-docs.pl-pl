---
title: "Lista kontrolna: Tworzenie nowych typów projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 06b6dc2fab4158f36126b6509909dd0db6fd7125
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="checklist-creating-new-project-types"></a>Lista kontrolna: Tworzenie nowych typów projektów
Należy wykonać kilka zadań, aby utworzyć nowy typ projektu. Poniższa lista kontrolna zawiera przewodnik dotyczący tych zadań.  
  
1.  Projektowanie funkcji nowego typu projektu. Aby uzyskać więcej informacji, zobacz [decyzji projektowych typ projektu](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Ustal, które edytory są używane dla kodu i inne elementy projektu. Można użyć rdzeni lub standardowe edytory lub można utworzyć i użycie edytorów specyficznego dla projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych edytory i projektantom](../../extensibility/creating-custom-editors-and-designers.md) i [porady: Otwórz edytory specyficznego dla projektu](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Ustal poziom udział elementów projektu mają w **widoku klasy** i **przeglądarki obiektów**. Aby uzyskać więcej informacji, zobacz [przeglądanie Symbol obsługi narzędzia](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Wyprowadzać nowe klasy oparte na decyzje dotyczące projektu wprowadzone uprzednio dla projektów i elementów projektu.  
  
5.  Pisanie kodu dla następujących składników typ projektu:  
  
    -   Fabryka projektu do zarządzania, tworzenie nowych projektów i otwieranie istniejących projektów. Aby uzyskać więcej informacji, zobacz [tworzenia projektu wystąpień przez za pomocą fabryk projektów przez ustawienie](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Projekt hierarchii i obsługa polecenia. Aby uzyskać więcej informacji, zobacz [nie znajduje się w kompilacji: przy użyciu HierUtil7 projektu klasy do zaimplementowania typ projektu (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346), [elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md), [projektu modelu podstawowe składniki](../../extensibility/internals/project-model-core-components.md)i [MenuCommands Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
    -   Zarządzanie projektami elementy, takie jak dodawanie projektu do **nowy projekt** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Dodawanie projekt oraz szablony elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md) i [rejestrowanie Project and Item Templates](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Stan trwały stan projektu i poszczególne elementy. Aby uzyskać więcej informacji, zobacz [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md). Trwałości informacje o rozwiązaniu, zobacz [rozwiązań](../../extensibility/internals/solutions.md).  
  
    -   Niezależnie od właściwości konfiguracji do wyświetlenia w oknie właściwości. Aby uzyskać więcej informacji, zobacz [rozszerzanie właściwości](../../extensibility/internals/extending-properties.md).  
  
    -   Właściwości konfiguracji projektu, zgodnie z implementacją na stronach właściwości, aby wyświetlić właściwości zależne od konfiguracji. Aby uzyskać więcej informacji, zobacz [zarządzanie opcje konfiguracji](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Wyliczanie danych wyjściowych dla wdrożenia. Aby uzyskać więcej informacji, zobacz [konfiguracji projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Projekt uruchomienia usługi. Aby uzyskać więcej informacji, zobacz [elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md) i [projektu modelu podstawowe składniki](../../extensibility/internals/project-model-core-components.md).  
  
    -   Obiekty i klasy pochodne od `IDispatch`, dostępne dla automatyzacji.  
  
    -   Pliki XML polecenia tabeli (vsct). Aby uzyskać więcej informacji, zobacz [tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Testowanie, debugowania i uruchomić danego typu projektu.  
  
7.  Wyświetlić projekt w **projektu** karcie **Dodaj odwołanie** okno dialogowe przez ustawienie `VARIANT_TRUE` jako wartość `VSHPROPID_ShowProjInSolutionPage`. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Utwórz plik Microsoft Installer (msi) dotyczące instalowania programu VSPackages. Aby uzyskać więcej informacji, zobacz [instalowanie VSPackages z Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [rejestrowania typu projektu](../../extensibility/internals/registering-a-project-type.md), i [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Kiedy należy utworzyć typy projektów](../../extensibility/internals/when-to-create-project-types.md)   
 [Tworzenie typów projektów](../../extensibility/internals/creating-project-types.md)