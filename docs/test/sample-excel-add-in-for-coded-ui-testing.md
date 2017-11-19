---
title: "Przykładowy dodatek Excel dla kodowanych testów UI | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: coded UI tests, Excel Add-in sample
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: "16"
ms.author: douge
manager: douge
ms.openlocfilehash: 7fd461a6fea45676dcb443c8cf69c064af675793
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>Przykładowy dodatek Excel dla kodowanych testów UI
Ten przykład dodatku dla [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] jest zaprojektowana specjalnie do obsługi arkuszy kodowanych testów interfejsu użytkownika programu Excel, które są rejestrowane i uruchomić w Visual Studio Enterprise. Dodatek jest tworzony za pomocą narzędzi Visual Studio Tools dla pakietu Office.  
  
 Aby uzyskać więcej informacji na temat tworzenia dodatek programu Excel, zobacz [wskazówki: tworzenie swój pierwszy VSTO Add-in for Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) lub Wyszukaj MSDN dla "Dodaj programu Excel".  
  
 Mimo że dodatek programu Excel nie jest podstawowym podmiotu w niniejszej dokumentacji rozszerzenia kodowanego testu interfejsu użytkownika dla programu Excel, pomocne może być kilka komentarze.  
  
 Ważne części tego dodatku:  
  
-   `ThisAddIn`Klasa — zarządza kanału .NET Remoting między `ExcelUICommunicator` i [rozszerzenia kodowanego testu interfejsu użytkownika próbki dla programu Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx`-Certyfikatu zabezpieczeń do testowania dodatku.  
  
-   `ExcelUICommunicator`Klasa — ta klasa implementuje `IExcelUICommunication` interfejsu.  
  
## <a name="thisaddin-class"></a>Thisaddin — klasa  
 Większość tej klasy faktycznie jest generowany przez Visual Studio Tools dla pakietu Office w `ThisAddIn.Designer.cs` pliku po utworzeniu projektu dodatek programu Excel.  
  
 Elementy członkowskie, które należy zaimplementować są obsługi zdarzeń: `ThisAddIn_Startup()` i `ThisAddIn_Shutdown()`. Ich celem jest zainicjować lub zamknąć kanał funkcji zdalnych .NET, który jest używany przez `ExcelUICommunicator`.  
  
## <a name="excelcodeduiaddinhelpertemporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey.pfx  
 Ten plik zawiera certyfikat zabezpieczeń tymczasowego, który jest generowany przez Visual Studio Tools dla pakietu Office i zapewnia dodatku zestawu uprawnień do działania w procesie programu Excel do testowania dodatków i rozszerzeń. Należy usunąć ten certyfikat i albo utwórz nową w **podpisywanie** kartę projektu **właściwości** okna, lub Dołącz własnego testowania certyfikatu.  
  
## <a name="exceluicommunicator-class"></a>Klasa ExcelUICommunicator  
 Ta klasa implementuje `IExcelUITestCommunication` interfejsu i pobiera żądane informacje interfejsu użytkownika z modelu obiektów programu Excel. Aby uzyskać więcej informacji, zobacz [interfejs komunikatora programu Excel](../test/sample-excel-communicator-interface.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie zakodowanych testów interfejsu użytkownika i nagrywanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Wskazówki: Tworzenie Twojego pierwszego dodatku narzędzi VSTO dla programu Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)   
 [Pakietu Office i programu SharePoint](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio)
