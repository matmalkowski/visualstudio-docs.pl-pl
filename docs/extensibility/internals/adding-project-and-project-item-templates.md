---
title: "Dodawanie projektu i szablony elementów projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0201d2f282365a028b6251324b07276c995621ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="adding-project-and-project-item-templates"></a>Dodawanie projekt oraz szablony elementów projektu
Podczas tworzenia własnych typów projektu do dodawania nowych projektów i elementów projektu przy użyciu standardu musi zapewnić obsługę [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane rozwoju (IDE) środowiska okien dialogowych. W poniższych tematach opisano różne techniki dodawanie projektów i elementów projektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kontekst projektu](../../extensibility/internals/project-context.md)  
 W tym artykule wyjaśniono, że projekt zawiera większość informacje kontekstowe o to, co wynika w środowisku.  
  
 [Priorytet projektu](../../extensibility/internals/project-priority.md)  
 Wyjaśniono, że element projektu jest zwykle członkiem jeden projekt, aby uniknąć niejednoznaczności, o którym projektu jest używany do otwierania elementu.  
  
 [Projekt różne pliki](../../extensibility/internals/miscellaneous-files-project.md)  
 Zawiera informacje o dwa rodzaje edytory, które mogą służyć do otwierania plików w projekcie i roli się, że projekt jest odtwarzany w określeniu, edytor, którego chce używać po otwarciu elementu projektu.  
  
 [Rejestrowanie szablony projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)  
 Wyjaśnienie działań po [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekt zostanie utworzony.  
  
 [Dodawanie elementów do Dodaj nowy element okien dialogowych](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Opisano proces dodawania elementów do **Dodaj nowy element** okno dialogowe.  
  
 [Dodawanie katalogów do okna dialogowego Nowy projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Przykład rejestrowania nowy katalog, który zawiera szablony niestandardowe, udostępniane przez pakiet VSPackage.  
  
 [Dodawanie katalogów do dodania okno dialogowe Nowy element](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Przykład rejestrowania nowy zestaw katalogów dla **Dodaj nowy element** okno dialogowe.  
  
 [Definicja IDE poleceń do rozszerzania systemów projektów](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Wyświetla listę różnych typów elementów polecenia używane do rozszerzania systemów projektów.  
  
 [CATIDs dla obiektów, które są zazwyczaj używane do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Wyświetla listę CATIDs dla obiektów, które służą do rozszerzania [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektu systemów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Porady: Otwórz edytory specyficznego dla projektu](../../extensibility/how-to-open-project-specific-editors.md)  
 Instrukcje krok po kroku do otwarcia elementu leżą powiązany z określonego edytora dla projektu.  
  
 [Porady: otwieranie standardowe edytory](../../extensibility/how-to-open-standard-editors.md)  
 Instrukcje krok po kroku do otwierania Edytora standardowego.  
  
 [Podtypów projektu](../../extensibility/internals/project-subtypes.md)  
 Zawiera łącza do tematy dotyczące pojęć podtypu projektu. Projekt podtypów rozszerzyć istniejących [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektów.  
  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 Zawiera łącza do dodatkowych tematów, które oferują informacji dotyczących sposobu projektowania nowych typów projektów.