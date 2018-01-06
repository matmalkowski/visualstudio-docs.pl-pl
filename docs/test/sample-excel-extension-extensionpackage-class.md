---
title: "Przykładowe rozszerzenie programu Excel: Klasa ExtensionPackage | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: "9"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: e216205ef2e7dfb22524ca3fb83a40958d31fd6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
