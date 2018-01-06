---
title: "Przegląd modelu automatyzacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 208357343a3e77e29b1dc0a98b6159c5ac3f957e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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