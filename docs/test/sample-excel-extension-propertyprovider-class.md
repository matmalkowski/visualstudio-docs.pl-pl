---
title: "Przykładowe rozszerzenie programu Excel: Klasa PropertyProvider | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: "9"
ms.author: douge
manager: douge
ms.openlocfilehash: 28cc3774c48eabc240f2f51b9b40f23faba74377
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>   
 [Rozszerzanie zakodowanych testów interfejsu użytkownika i nagrywanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
