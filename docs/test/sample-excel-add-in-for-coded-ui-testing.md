---
title: "Przykładowy dodatek Excel dla kodowanych testów UI | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 0842ecffff4624e4b3cd7c88fa9231ff71c364e6
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>Przykładowy dodatek Excel dla kodowanych testów UI
Ten przykład dodatku dla [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] jest zaprojektowana specjalnie do obsługi arkuszy kodowanych testów interfejsu użytkownika programu Excel, które są rejestrowane i uruchomić w Visual Studio Enterprise. Dodatek jest tworzony za pomocą narzędzi Visual Studio Tools dla pakietu Office.

 Aby uzyskać więcej informacji na temat tworzenia dodatek programu Excel, zobacz [wskazówki: tworzenie swój pierwszy VSTO Add-in for Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) lub Wyszukaj MSDN dla "Dodaj programu Excel".

 Mimo że dodatek programu Excel nie jest podstawowym podmiotu w niniejszej dokumentacji rozszerzenia kodowanego testu interfejsu użytkownika dla programu Excel, pomocne może być kilka komentarze.

 Ważne części tego dodatku:

-   `ThisAddIn`  Klasa — zarządza kanału .NET Remoting między `ExcelUICommunicator` i [rozszerzenia kodowanego testu interfejsu użytkownika próbki dla programu Excel](../test/sample-coded-ui-test-extension-for-excel.md).

-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx`  -Certyfikatu zabezpieczeń do testowania dodatku.

-   `ExcelUICommunicator`  Klasa — ta klasa implementuje `IExcelUICommunication` interfejsu.

## <a name="thisaddin-class"></a>Thisaddin — klasa
 Większość tej klasy faktycznie jest generowany przez Visual Studio Tools dla pakietu Office w `ThisAddIn.Designer.cs` pliku po utworzeniu projektu dodatek programu Excel.

 Elementy członkowskie, które należy zaimplementować są obsługi zdarzeń: `ThisAddIn_Startup()` i `ThisAddIn_Shutdown()`. Ich celem jest zainicjować lub zamknąć kanał funkcji zdalnych .NET, który jest używany przez `ExcelUICommunicator`.

## <a name="excelcodeduiaddinhelpertemporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey.pfx
 Ten plik zawiera certyfikat zabezpieczeń tymczasowego, który jest generowany przez Visual Studio Tools dla pakietu Office i zapewnia dodatku zestawu uprawnień do działania w procesie programu Excel do testowania dodatków i rozszerzeń. Należy usunąć ten certyfikat i albo utwórz nową w **podpisywanie** kartę projektu **właściwości** okna, lub Dołącz własnego testowania certyfikatu.

## <a name="exceluicommunicator-class"></a>Klasa ExcelUICommunicator
 Ta klasa implementuje `IExcelUITestCommunication` interfejsu i pobiera żądane informacje interfejsu użytkownika z modelu obiektów programu Excel. Aby uzyskać więcej informacji, zobacz [interfejs komunikatora programu Excel](../test/sample-excel-communicator-interface.md).

## <a name="see-also"></a>Zobacz także

- [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
- [Przewodnik: Tworzenie pierwszego dodatku VSTO dla programu Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)
- [Pakietu Office i programu SharePoint](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio)
