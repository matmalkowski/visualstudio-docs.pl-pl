---
title: "Przykładowy interfejs komunikatora programu Excel | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: "11"
ms.author: douge
manager: douge
ms.openlocfilehash: 653d6430f18b2ca5cdbd2e1307f0c8386cebea91
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="sample-excel-communicator-interface"></a>Interfejs komunikatora programu Excel
Przykład `IExcelUICommunication` interfejs jest używany w `ExcelUICommunicator` obiektu w `ExcelAddIn` projektu.  
  
## <a name="iexceluicommunication-interface"></a>Interfejs IExcelUICommunication  
 Ten interfejs definiuje punkty komunikacji między `CodedUIExtension`, która działa w procesie kodowanego testu interfejsu użytkownika i `ExcelCodedUIAddIn`, które są uruchamiane [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] procesu.  
  
 `ExcelCodedUIAddinHelper` Zestaw ma `ExcelUICommunicator` klasy, która jest pochodną interfejsu i używa modelu obiektów programu Excel do przetwarzania metody.  
  
 W przypadku niektórych metod uzyskać wymaganych informacji z programu Excel, a następnie utworzyć i zwracać jedną informacji obiekty, takie jak `CellInformation` obiektu.  
  
 Inne metody użyć obiektu podane informacje, znaleźć odpowiedniego formantu w programie Excel i wykonania procesu w formancie. Na przykład `ScrollIntoView` — metoda Przewija arkusz, dzięki czemu wyznaczonych komórki jest widoczny.  
  
## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>CodedUIExtensibilitySample i ExcelCodedUIAddinHelper komunikacji  
 `ExcelCodedUIAddinHelper` Zestaw działa w procesie programu Excel i ma `UICommunicator` klasa implementująca `IExcelUITestCommunication` interfejsu i pobiera lub ustawia wymagane informacje bezpośrednio w Interfejsie użytkownika programu Excel.  
  
 `CodedUIExtensibilitySample` Zestawu działa w procesie programu Visual Studio kodowanego testu interfejsu użytkownika. Ten zestaw zawiera `Communicator` klasy, która otwiera kanał funkcji zdalnych .NET, a także `Instance` właściwość, która używa `IExcelUICommunication` interfejsu do użycia `UICommunicator` obiektu w `ExcelCodedUIAddinHelper` zestawu do przekazywania żądań i informacji obiekty, takie jak `CellInformation` obiektu i z powrotem między dwoma zestawami.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie zakodowanych testów interfejsu użytkownika i nagrywanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Przykładowy dodatek Excel dla kodowanych testów UI](../test/sample-excel-add-in-for-coded-ui-testing.md)   
 [Przykładowe rozszerzenie kodowanych testów UI dla programu Excel](../test/sample-coded-ui-test-extension-for-excel.md)
