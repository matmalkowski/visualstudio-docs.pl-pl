---
title: Szablon zasad i w oknie właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 759864533aa5bd3455a4e01c6642817107abb1a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130045"
---
# <a name="template-policy-and-the-properties-window"></a>Szablon zasad i w oknie właściwości
Gdy projekt znajduje się wewnątrz szablonu projektu w przedsiębiorstwie, ten szablon projektu przedsiębiorstwa mogą wymusić zasady. Szablon zasad staje się ograniczający systemu, w którym można ustawić wartości domyślne dla właściwości, Ukryj właściwości, Dodaj właściwości i tak dalej.  
  
 Kontrola wyświetlania informacji w przy użyciu szablonu zasad **właściwości** okna różni się od wykonania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> obsługuje właściwości obiektów na poziomie składnika, podczas gdy szablonu zasad można ograniczyć właściwości obiektów na poziomie rozwiązania lub projektu. Innymi słowy  
  
-   Implementacja metod na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> ustalenie, co jest wyświetlane w **właściwości** okna dla określonych obiektów  
  
-   Użyj szablonu zasad na poziomie rozwiązania i projektu Aby ustalić, co jest wyświetlane w **właściwości** w oknie wcześniej określonych obiektów  
  
 Przy użyciu szablonu zasad można selektywnie ograniczyć określonej właściwości w **właściwości** wybrano okna, jeśli element projektu o określonym typie **Eksploratora rozwiązań** korzystne może okazać się wszystkie elementy członkowskie zespół deweloperów pracy nad projektem. Na przykład za pomocą szablonu zasad, należy skonfigurować wszystkie parametry połączenia informacje w bazie danych dla deweloperów i utworzyć parametry połączenia tylko do odczytu. W ten sposób można zapewnić prosty sposób, aby mieć pewność, że każdy Deweloper używa poprawną ścieżkę dla dostępu do danych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)