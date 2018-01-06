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
ms.workload: multiple
ms.openlocfilehash: 7617b7aafac6c7345a94d0e792bc312c7e212e56
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
 [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
