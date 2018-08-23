---
title: Pakietów VSPackage i środowiska pakietu zarządzanego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed package framework
- VSPackages, managed package framework
- managed VSPackages, managed package framework
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
manager: douge
ms.openlocfilehash: 41eb5cc816616ca2d99b68eb73fedbd527778274
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42632056"
---
# <a name="vspackages-and-the-managed-package-framework"></a>Pakietów VSPackage i środowiska pakietu zarządzanego
Tworząc pakietu VSPackage przy użyciu pakietu zarządzanych klas framework (MPF) zamiast przy użyciu klas międzyoperacyjnego modelu COM, można zmniejszyć czas opracowywania.  
  
 Istnieją dwa sposoby tworzenia zarządzanego pakietu VSPackage:  
  
-   Użyj [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablon projektu pakietu  
  
     Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie Menu polecenia za pomocą szablonu pakietu Visual Studio](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
-   Twórz swoje pakietu VSPackage bez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablon projektu pakietu  
  
     Można na przykład skopiuj przykład pakietu VSPackage i zmieniać identyfikatory GUID i nazw. Przykłady można znaleźć w sekcji VSX [galerii kodów](http://code.msdn.microsoft.com/vsx/).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zarządzane klasy Framework pakietu](../misc/managed-package-framework-classes.md)  
 W tym artykule opisano i przedstawiono MPF klasy w przestrzeni nazw i pliki DLL.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wskazówki: Tworzenie polecenia Menu za pomocą szablonu pakietu programu Visual Studio](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 Wyjaśnia sposób tworzenia zarządzanego pakietu VSPackage.  
  
 [Zarządzane pakietów VSPackage](../misc/managed-vspackages.md)  
 Wprowadza aspektów pakietów VSPackage, które są stosowane do kodu zarządzanego.