---
title: "VBA i rozwiązania pakietu Office w Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
ms.assetid: 31756c2f-8829-4011-ad77-134cb3728344
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1b83d4d9064132be9a8b007dd46c9c360f5fed1e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>VBA i rozwiązania pakietu Office w Visual Studio
  Microsoft Visual Basic for Applications (VBA) korzysta z kodu niezarządzanego, który jest ściśle zintegrowany z aplikacjami pakietu Office. Projekty Microsoft Office utworzone za pomocą programu Visual Studio umożliwiają korzystać z programu .NET Framework i narzędzi projektowania Visual Studio.  
  
 Informacje o typach rozwiązań pakietu Office można tworzyć przy użyciu programu Visual Studio, zobacz [rozwój rozwiązań Office ― omówienie &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="comparison"></a>Porównanie  
 Poniższa tabela zawiera podstawowe porównanie rozwiązań VBA i rozwiązania pakietu Office w Visual Studio.  
  
|Rozwiązania VBA|Rozwiązania pakietu Office w Visual Studio|  
|-------------------|---------------------------------------|  
|Używa kodu, który jest połączony i utrwalone z określonego dokumentu.|Korzysta z kodu, które były przechowywane osobno od dokumentu (na poziomie dokumentu), lub w zestawie, który jest ładowany przez aplikację (dla dodatków VSTO VSTO).|  
|Współdziała z API VBA i modele obiektów pakietu Office.|Zapewnia dostęp do oba modele obiektów pakietu Office i [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] interfejsów API.|  
|Przeznaczone do rejestrowania makr i środowisko dewelopera uproszczone.|Przeznaczona dla zabezpieczeń, ułatwia utrzymanie kodu i możliwość używania pełnego programu Visual Studio zintegrowane środowisko programistyczne (IDE).|  
|Sprawdza się dobrze w przypadku rozwiązania, które korzystają z bardzo ścisłej integracji z aplikacjami pakietu Office.|Który dobrze rozwiązania, które korzystają z pełną zasobów programu Visual Studio i [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|  
|Ma ograniczenia dla przedsiębiorstw, szczególnie w zakresie zabezpieczeń i wdrażania.|Przeznaczony do użytku w przedsiębiorstwie.|  
  
 Niektóre elementy są nadal prostsze szybko przy użyciu języka VBA. W szczególności można kontynuować korzystanie z języka VBA do:  
  
-   Funkcje niestandardowy.  
  
-   Rejestrowanie makra.  
  
## <a name="combining-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Łączenie VBA rozwiązań i rozwiązań pakietu Office utworzony za pomocą programu Visual Studio  
 Kod VBA można wywołać z rozwiązań pakietu Office utworzony za pomocą programu Visual Studio i możesz także wywołać kodu w rozwiązaniach pakietu Office utworzony za pomocą programu Visual Studio z języka VBA. Określonych technik różni się w zależności od tego, czy rozwiązania do pakietu Office jest dodatku VSTO lub dostosowanie poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) i [łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwój rozwiązań Office ― omówienie &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Łączenie VBA i dostosowywanie na poziomie dokumentu](../vsto/combining-vba-and-document-level-customizations.md)   
 [Architektura Dostosowywanie na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Wprowadzenie &#40; programowanie Office w Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
  
  