---
title: "Przykładowe rozszerzenie programu Excel: Klasa ExtensionPackage | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 3603746325be5feff231d5e2538282f7bf6d6893
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Przykładowe rozszerzenie programu Excel: klasa ExtensionPackage
Ta klasa rozszerza <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> klasy i zapewnia punkt wejścia dla kodowanego testu interfejsu użytkownika, który jest testowany [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] arkusza.  
  
## <a name="assembly-attribute"></a>Atrybut zestawu  
 Plik zaczyna się od atrybutu zestawu, który identyfikuje zestaw jako rozszerzenie testu interfejsu użytkownika.  
  
```  
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
    "ExcelExtensionPackage",  
    typeof(  
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]  
```  
  
 Ten atrybut deklaruje nazwę klasy podstawowej, nazwa klasy pakietu i klasy w pełni kwalifikowaną nazwę klasy pakietu rozszerzenia niestandardowego.  
  
## <a name="simple-properties"></a>Proste właściwości  
 Ta klasa ma właściwości, które dostarczają wartości, które są używane przez platformę testowanie kodowanego interfejsu użytkownika do identyfikujące i opisujące rozszerzenia i zestawu. Zobacz komentarze w kodzie Aby uzyskać więcej informacji.  
  
## <a name="getservice-method"></a>Funkcja GetService — metoda  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> Metoda jest jeden punkt wejścia używane przez platformę testowanie kodowanego interfejsu użytkownika do uzyskania dostępu do Menedżera technologii, Dostawca właściwości i filtr akcji określonej przez klasę podstawową dla każdego obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
