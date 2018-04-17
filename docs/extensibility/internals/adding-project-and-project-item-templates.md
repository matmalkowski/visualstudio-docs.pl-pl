---
title: Dodawanie projektu i szablony elementów projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 94d521d288b470db56736668f11d47dab71d2533
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="adding-project-and-project-item-templates"></a>Dodawanie projekt oraz szablony elementów projektu
Podczas tworzenia własnych typów projektu do dodawania nowych projektów i elementów projektu przy użyciu standardu musi zapewnić obsługę [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane rozwoju (IDE) środowiska okien dialogowych. W poniższych tematach opisano różne techniki dodawanie projektów i elementów projektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kontekst projektu](../../extensibility/internals/project-context.md)  
 W tym artykule wyjaśniono, że projekt zawiera większość informacje kontekstowe o to, co wynika w środowisku.  
  
 [Priorytet projektu](../../extensibility/internals/project-priority.md)  
 Wyjaśniono, że element projektu jest zwykle członkiem jeden projekt, aby uniknąć niejednoznaczności, o którym projektu jest używany do otwierania elementu.  
  
 [Projekt Różne pliki](../../extensibility/internals/miscellaneous-files-project.md)  
 Zawiera informacje o dwa rodzaje edytory, które mogą służyć do otwierania plików w projekcie i roli się, że projekt jest odtwarzany w określeniu, edytor, którego chce używać po otwarciu elementu projektu.  
  
 [Rejestrowanie szablonów projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)  
 Wyjaśnienie działań po [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekt zostanie utworzony.  
  
 [Dodawanie elementów do okien dialogowych Dodawanie nowego elementu](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Opisano proces dodawania elementów do **Dodaj nowy element** okno dialogowe.  
  
 [Dodawanie katalogów do okna dialogowego Nowy projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Przykład rejestrowania nowy katalog, który zawiera szablony niestandardowe, udostępniane przez pakiet VSPackage.  
  
 [Dodawanie katalogów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Przykład rejestrowania nowy zestaw katalogów dla **Dodaj nowy element** okno dialogowe.  
  
 [Polecenia definiowane w środowisku IDE do rozszerzania systemów projektu](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Wyświetla listę różnych typów elementów polecenia używane do rozszerzania systemów projektów.  
  
 [Identyfikatory CATID obiektów, które są zwykle używane do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Wyświetla listę CATIDs dla obiektów, które służą do rozszerzania [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektu systemów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instrukcje: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)  
 Instrukcje krok po kroku do otwarcia elementu leżą powiązany z określonego edytora dla projektu.  
  
 [Instrukcje: otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)  
 Instrukcje krok po kroku do otwierania Edytora standardowego.  
  
 [Podtypy projektów](../../extensibility/internals/project-subtypes.md)  
 Zawiera łącza do tematy dotyczące pojęć podtypu projektu. Projekt podtypów rozszerzyć istniejących [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektów.  
  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 Zawiera łącza do dodatkowych tematów, które oferują informacji dotyczących sposobu projektowania nowych typów projektów.