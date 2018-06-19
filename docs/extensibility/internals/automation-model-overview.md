---
title: Przegląd modelu automatyzacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a9369bb6074bb294223051ba7dfa158648fe0cad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134750"
---
# <a name="automation-model-overview"></a>Przegląd modelu automatyzacji
Model automatyzacji zawiera zestaw obiektów, które można zapisywać i — w programie Visual Studio rozszerzenia. Dodatek jest aplikacja, która może manipulować środowiska Visual Studio i automatyzowania typowych zadań. Rozszerzenia programu Visual Studio można utworzyć niestandardowe składniki programu Visual Studio lub dodać działanie standardowe składniki, takie jak edytor tekstów.  
  
## <a name="objects-in-the-automation-model"></a>Obiekty w modelu automatyzacji  
 Model automatyzacji składa się z grupy kontrolować najważniejszych aspektów wspólnego środowiska. Poniżej przedstawiono diagram, który zawiera rozbudowany zestaw obiektów, które tworzą model automatyzacji.  
  
 ![Wykres obiektu automatyzacji programu Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Obiekty automatyzacji usługi Visual Studio  
  
 Aby uzyskać więcej informacji, zobacz [rozszerzanie środowiska Visual Studio](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 Środowisko udostępnia model dla różnych obszarów funkcjonalnych. Na przykład jest model kodu dla różnych elementów, które mogą być w kodzie. Brak modelu dokumentu dla różnych elementów dokumentu. Jednego obszaru, w obszarze projektu jest szczególne znaczenie pakiet VSPackage dostawców. Prawdopodobnie będzie Twoje nowe typy projektu przyczynienie się do modelu automatyzacji w znacznie taki sam sposób jak [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] przyczyniają się do modelu automatyzacji. Czy proces jest opisane w temacie [dostarczanie automatyzacji do VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Miejsca, w którym możesz rozważyć Rozszerzanie modelu automatyzacji środowiska:  
  
-   Projekt  
  
-   dokument  
  
-   Kod  
  
-   Kompilacja  
  
 Aby uzyskać więcej informacji o automatyzacji, zobacz [automatyzacji i rozszerzeń dla programu Visual Studio](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Ten dokument i dokumenty zawiera łącza do, ułatwiającym podejmowanie decyzji dotyczących sposobu powinien zawierać automatyzacji dla VSPackage.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Tworzenie dodatku](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)