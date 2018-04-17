---
title: Przykładowy interfejs komunikatora programu Excel | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 85d369ad7ddb468da86f3b19c070be4e125f941a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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

## <a name="see-also"></a>Zobacz także

- [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
- [Przykładowy dodatek dla programu Excel na potrzeby kodowanych testów interfejsu użytkownika](../test/sample-excel-add-in-for-coded-ui-testing.md)
- [Przykładowe rozszerzenie kodowanych testów interfejsu użytkownika dla programu Excel](../test/sample-coded-ui-test-extension-for-excel.md)
