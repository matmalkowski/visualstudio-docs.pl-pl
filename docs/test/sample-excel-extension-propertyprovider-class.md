---
title: "Przykładowe rozszerzenie programu Excel: Klasa PropertyProvider | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c8917661d4df4034cfb97a94c7a515659c558da5
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Przykładowe rozszerzenie programu Excel: klasa PropertyProvider
Wewnętrzna klasa rozszerza <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> klasy i udostępnia usługi właściwości dla [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] elementy zapisywanie i odtwarzanie testów interfejsu użytkownika.

## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel — metoda
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> Metoda zwraca liczbę wskazującą poziomu obsługi, które może zaoferować Dostawca właściwości, dla podanego formantu. Im wyższa wartość zwrócona więcej właściwości dostawcy może obsługiwać formantu. W tym przypadku metoda sprawdza wartość <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> właściwość podanego formantu. Jeśli wartość to "Excel" i <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> wskazuje jest `CellElement`, metoda zwraca największą wartość; w przeciwnym razie zwraca wartość zero, co oznacza, że nie jest obsługiwana.

## <a name="getpropertynames-method"></a>GetPropertyNames — metoda
 Zwraca słownik nazw właściwości i deskryptorów właściwości dla obsługiwanych właściwości formantu komórki w programie Excel.

## <a name="getpropertydescriptor-method"></a>GetPropertyDescriptor — metoda
 Ta metoda jest wywoływana przez platformę testowania można pobrać deskryptora właściwości wstępnie zdefiniowane dla danej nazwy właściwości podana.

## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>GetPropertyValue i SetPropertyValue metody
 `GetPropertyValue` Używa metody `Communicator` klasy tego rozszerzenia, aby zwrócić wartość właściwości z programu Excel. `SetPropertyValue` Używa metody <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> klasy i `Communicator` składnika można ustawić wartości właściwości. Te metody są wywoływane przez platformę, testowych.

## <a name="code-generation-customization-methods"></a>Metod dostosowywania generowania kodu
 Te metody nie zaimplementowano dla tego rozszerzenia. W związku z tym albo zwracają `null` lub zgłaszać <xref:System.NotImplementedException>.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>
- [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
