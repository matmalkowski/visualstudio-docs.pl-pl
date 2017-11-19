---
title: "Neutralny język zasobów do lokalizacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 89e6e1f0814165781f92049537b4ae8748246b48
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="neutral-resources-languages-for-localization"></a>Neutralny język zasobów do lokalizacji
<xref:System.Resources.NeutralResourcesLanguageAttribute> Klasy określa kulturę zasobów zawarte w zestawie głównym. Ten atrybut służy jako zwiększenie wydajności, dzięki czemu <xref:System.Resources.ResourceManager> obiektu nie wyszukuje zasoby, które znajdują się w zestawie głównym.  
  
 Poniższy kod przedstawia sposób ustawić język neutralne zasoby. Kod można umieścić w skrypcie kompilacji lub plik AssemblyInfo.vb lub AssemblyInfo.cs.  
  
```vb  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```csharp  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Resources.ResourceManager>   
 [Wprowadzenie do aplikacji międzynarodowych oparte na programie .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Hierarchiczna organizacja zasobów do lokalizacji](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [Lokalizowanie aplikacji](../ide/localizing-applications.md)   
 [Globalizacja i lokalizacja aplikacji](../ide/globalizing-and-localizing-applications.md)