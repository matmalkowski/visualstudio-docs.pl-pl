---
title: Przykładowy dodatek programu Excel dla kodowanych testów UI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- coded UI tests, Excel Add-in sample
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 18
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0f0b4211b51940564041fab5777d6594168e1329
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679271"
---
# <a name="sample-excel-add-in-for-coded-ui-testing"></a>Przykładowy dodatek Excel dla kodowanych testów UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [przykładowy dodatek Excel dla kodowanych testów interfejsu użytkownika](https://docs.microsoft.com/visualstudio/test/sample-excel-add-in-for-coded-ui-testing).  
  
Ten przykład dodatku [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] jest zaprojektowany specjalnie w celu obsługi arkuszy kodowanych testów interfejsu użytkownika programu Excel, które są rejestrowane i uruchamiać w programie Visual Studio Enterprise. Dodatek jest tworzony przy użyciu programu Visual Studio Tools dla pakietu Office.  
  
 Aby uzyskać więcej informacji o tym, jak utworzyć dodatek programu Excel, zobacz [wskazówki: tworzenie Twojej pierwszej dodatku narzędzi VSTO dla programu Excel](http://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) lub przeszukiwania witryny MSDN dla "dodatek programu Excel".  
  
 Mimo że dodatek programu Excel nie jest podstawowym przedmiotem niniejszy rozszerzenie kodowanych testów interfejsu użytkownika dla programu Excel, pomocne może być kilka komentarzy.  
  
 Ważne elementy tego dodatku:  
  
-   `ThisAddIn`  Klasy — zarządza kanał wywołaniem funkcji zdalnych .NET między `ExcelUICommunicator` i [rozszerzenie kodowanych testów interfejsu użytkownika przykładowe dla programu Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx`  -Certyfikatu zabezpieczeń do testowania dodatku.  
  
-   `ExcelUICommunicator`  Klasa — ta klasa implementuje `IExcelUICommunication` interfejsu.  
  
## <a name="thisaddin-class"></a>Thisaddin — klasa  
 Większość tej klasie faktycznie jest generowany przez Visual Studio Tools dla pakietu Office w `ThisAddIn.Designer.cs` pliku podczas tworzenia projektu dodatku programu Excel.  
  
 Elementy członkowskie, które należy zaimplementować są procedury obsługi zdarzeń: `ThisAddIn_Startup()` i `ThisAddIn_Shutdown()`. Ich celem jest zainicjowanie lub zamknij kanał wywołaniem funkcji zdalnych .NET, który jest używany przez `ExcelUICommunicator`.  
  
## <a name="excelcodeduiaddinhelpertemporarykeypfx"></a>ExcelCodedUIAddinHelper_TemporaryKey.pfx  
 Ten plik zawiera tymczasowe certyfikatem, który został wygenerowany przez Visual Studio Tools dla pakietu Office i zapewnia dodatku zestawu uprawnień do działania w procesie programu Excel do testowania dodatków i rozszerzeń. Należy usunąć ten certyfikat i Utwórz nowe konto w **podpisywanie** projektu na karcie **właściwości** oknie lub dołączyć własnego testowania certyfikatu.  
  
## <a name="exceluicommunicator-class"></a>Klasa ExcelUICommunicator  
 Ta klasa implementuje `IExcelUITestCommunication` interfejsu, a następnie pobiera wymagane informacje o interfejsie użytkownika z modelu obiektów programu Excel. Aby uzyskać więcej informacji, zobacz [interfejs komunikatora programu Excel przykładowe](../test/sample-excel-communicator-interface.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Wskazówki: Tworzenie Twojego pierwszego dodatku narzędzi VSTO dla programu Excel](http://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)   
 [Pakiet Office i programu SharePoint](http://msdn.microsoft.com/library/2ddec047-263a-4901-a54c-a15fc8472329)



