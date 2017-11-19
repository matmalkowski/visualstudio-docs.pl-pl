---
title: "Rozszerzanie zakodowanych testów interfejsu użytkownika i nagrywanie akcji obsługujących program Microsoft Excel | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b0f72a4-70ca-4e55-b236-2ea1034fd8a7
caps.latest.revision: "30"
ms.author: douge
manager: douge
ms.openlocfilehash: fa2ffd383d2180b672347043dd02459473e3a608
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel"></a>Rozszerzanie zakodowanych testów interfejsu użytkownika i nagrywanie akcji obsługujących program Microsoft Excel
Testowanie framework kodowane testy interfejsu użytkownika i nagrywania akcji nie obsługuje co przykładowy interfejs użytkownika. Nie obsługuje określonego interfejsu użytkownika, który ma zostać przetestowana. Na przykład nie można bezpośrednio utworzyć kodowanego testu interfejsu użytkownika lub akcji rejestrowania dla [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] arkusza kalkulacyjnego. Można jednak utworzyć własne rozszerzenie kodowanych struktury testowej interfejsu użytkownika, która będzie obsługiwać określonego interfejsu użytkownika korzystając z rozszerzalności platformy kodowanego testu interfejsu użytkownika. Poniższy temat zawiera przykładowy sposób rozszerzyć framework do obsługi tworzenia kodowane testy interfejsu użytkownika i nagrywania akcji dla [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)]. Aby uzyskać więcej informacji na temat platformy, które są obsługiwane, zobacz [obsługiwane konfiguracje oraz platformy kodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).  
  
 **Wymagania**  
  
-   Visual Studio Enterprise  
  
 W tej sekcji przedstawiono rozszerzenia kodowanego testu interfejsu użytkownika, można rejestrować i odtwarzanie testów arkusze programu Excel. Każda część rozszerzenia opisanej w tej sekcji i komentarze w kodzie dla deweloperów, którzy chcą tworzyć tylko takie rozszerzenie.  
  
 ![Architektura testu interfejsu użytkownika](../test/media/ui_testarch.png "UI_TestArch")  
Przegląd architektury  
  
## <a name="download-the-sample"></a>Pobieranie próbki  
 Próbka składa się z czterech projektów w `CodedUIExtensibilitySample.sln` rozwiązania:  
  
-   CodedUIextensibilitySample  
  
-   ExcelCodedUIAddInHelper  
  
-   ExcelUICommunicationHelper  
  
-   SampleTestProject  
  
 Pobierz z tej próbki [wpis w blogu](http://go.microsoft.com/fwlink/?LinkID=185592).  
  
> [!NOTE]
>  Próbki jest przeznaczony do użytku z programem Microsoft Excel 2010. Próbki mogą działać z innych wersji programu Microsoft Excel, ale nie jest obecnie obsługiwany.  
  
## <a name="details-about-the-sample"></a>Szczegółowe informacje o próbki  
 Poniższe sekcje zawierają informacje o próbki i jego struktury.  
  
### <a name="microsoft-excel-add-in-excelcodeduiaddinhelper"></a>Dodatek programu Microsoft Excel: ExcelCodedUIAddinHelper  
 Ten projekt zawiera dodatek działa w procesie programu Excel. Zobacz [próbki Dodaj programu Excel dla kodowanych testów UI](../test/sample-excel-add-in-for-coded-ui-testing.md) dla krótkie omówienie projektu dodatku.  
  
 Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie swój pierwszy VSTO Add-in for Excel](http://msdn.microsoft.com/Library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f).  
  
### <a name="excel-ui-communication-exceluicommunicationhelper"></a>Komunikacja interfejsu użytkownika programu Excel: ExcelUIcommunicationHelper  
 Ten projekt zawiera `IExcelUICommunication` interfejsu i klasy informacje, które są używane do przekazywania danych między Framework testowanie kodowanego interfejsu użytkownika i Excel. Aby uzyskać więcej informacji, zobacz [interfejs komunikatora programu Excel](../test/sample-excel-communicator-interface.md).  
  
### <a name="coded-ui-test-extension-codeduiexentsibilitysample"></a>Rozszerzenie kodowanych testów UI: CodedUIExentsibilitySample  
 Ten projekt zawiera klas niestandardowych, które są używane w testach arkuszu programu Excel. Kod dla każdego z tych klas jest dość oczywiste. Jednak udostępniamy krótki opis każdego klasy niestandardowej. Aby uzyskać więcej informacji, zobacz [rozszerzenia kodowanego testu interfejsu użytkownika próbki dla programu Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
### <a name="deploying-your-add-in-and-extension"></a>Wdrażanie z dodatku i rozszerzenia  
 Po utworzeniu wszystkich projektów i obiektów, uruchom dostarczonych `CopyDrop.bat` pliku jako administrator. Kopiuje tego pliku `ExcelCodedUIAddinHelper` plików DLL i PDB:  
  
 "`%CommonProgramFiles(x86)%\Microsoft Shared\VSTT\<version number>\UITestExtensionPackages\*.*`", gdzie numer wersji może być 11.0, 12,0 itp zależnie od wersji programu Visual Studio.  
  
 `ExcelUICommunicationHelper` DLL i pliku PDB, pliki są kopiowane do `"%ProgramFiles(x86)%\Microsoft Visual Studio <version number>\Common7\IDE\PrivateAssemblies"`.  
  
 Może być konieczne dostosowanie ścieżek dokładna kopia, ale instalacja dodatkowych nie jest wymagana. Na komputerze 64-bitowym, użyj wiersza polecenia programu Visual Studio Enterprise 32-bitowej do uruchomienia `CopyDrop.bat` pliku.  
  
### <a name="testing-excel-with-the-sampletestproject"></a>Testowanie Excel za pomocą SampleTestProject  
 Można uruchomić testu w projekcie testowym podany, używanym w określonej wersji programu Excel może nie mieć, lub utworzenie projektu testowego i zarejestruj własnego testu. Aby uzyskać więcej informacji, zobacz [tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)   
 [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
