---
title: Zarządzane pakietów VSPackage | Dokumentacja firmy Microsoft
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
- VSPackages, managed
- managed VSPackages
ms.assetid: a4f17068-c563-45a8-bbbf-4203ea99e9d2
caps.latest.revision: 34
manager: douge
ms.openlocfilehash: f221cf99234a2e3128e29636368e5fa78169425d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681570"
---
# <a name="managed-vspackages"></a>Zarządzane pakietów VSPackage
W poniższych tematach opisano sposób tworzenia pakietu VSPackage. Pakietu VSPackage jest to moduł oprogramowania, który rozszerza [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE), zapewniając elementy interfejsu użytkownika, usługi, projekty, edytorów i projektantów. Aby uzyskać więcej informacji, zobacz [pakietów VSPackage](../extensibility/internals/vspackages.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Korzystanie z zestawów międzyoperacyjnych programu Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md)  
 Zawiera opis funkcji i lokalizację [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zestawy międzyoperacyjne i przestrzenie nazw zapewniają.  
  
 [Informacje o HRESULT w kodzie zarządzanym](../misc/hresult-information-in-managed-code.md)  
 W tym artykule omówiono sposób tłumaczy wartość HRESULT informacji do zgłoszenia wyjątku i `int` zwracają wartości w kodzie zarządzanym.  
  
 [Parametr zestawu międzyoperacyjnego programu Visual Studio Marshalingu](../misc/visual-studio-interop-assembly-parameter-marshaling.md)  
 W tym artykule omówiono zagadnienia dotyczące współdziałania między [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zestawy międzyoperacyjne i interfejsów COM.  
  
 [Pakietów VSPackage i środowiska pakietu zarządzanego](../misc/vspackages-and-the-managed-package-framework.md)  
 W tym artykule opisano i przedstawiono pakietu zarządzanego framework (MPF) klasy w przestrzeni nazw i pliki DLL i pokazuje, jak używać ich do tworzenia pakietu VSPackage.  
  
 [Zasoby w pakietach VSPackage](../extensibility/internals/resources-in-vspackages.md)  
 W tym artykule opisano korzystanie z zasobów zarządzanych i niezarządzanych w zarządzanych pakietów VSPackage.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Narzędzia VSSDK](../extensibility/internals/vssdk-utilities.md)  
 Przedstawia kolekcję Tematy zaawansowane i elementy wewnętrzne pakietu VSPackage.