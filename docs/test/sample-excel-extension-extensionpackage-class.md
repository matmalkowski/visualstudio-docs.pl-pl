---
title: 'Przykładowe rozszerzenie programu Excel: klasa ExtensionPackage'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 43234161979df9190daddeec168e7a40a14db498
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
