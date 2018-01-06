---
title: 'Porady: tworzenie manifestu produkt | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 071bfa46df7e11f760bc32cda0a732388835d2d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-product-manifest"></a>Porady: tworzenie manifestu produkt
Aby wdrożyć wymagania wstępne dotyczące aplikacji, można utworzyć pakiet programu inicjującego. Pakiet programu inicjującego zawiera jeden produkt pliku manifestu ale manifest pakietu dla każdego ustawienia regionalne. Manifest pakietu zawiera aspekty specyficzne dla lokalizacji pakietu. W tym ciągów, Umowa licencyjna użytkownika oprogramowania i pakietów językowych.  
  
 Aby uzyskać więcej informacji na temat manifestów produktu, zobacz [porady: tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md).  
  
## <a name="creating-the-product-manifest"></a>Tworzenie manifestu produkt  
  
#### <a name="to-create-the-product-manifest"></a>Aby utworzyć manifestu produkt  
  
1.  Utwórz katalog dla pakietu programu inicjującego. W tym przykładzie użyto C:\package.  
  
2.  W programie Visual Studio Utwórz nowy plik XML o nazwie `product.xml`i zapisz go w folderze C:\package.  
  
3.  Dodaj następujące XML opisujący kod XML przestrzeń nazw i produktu dla pakietu. Zastąp kod produktu unikatowy identyfikator dla pakietu.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  Dodaj XML, aby określić, że pakiet ma zależność. W tym przykładzie użyto zależność w systemie Microsoft Windows Installer 3.1.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  Dodaj XML, aby wyświetlić listę wszystkich plików znajdujących się w pakiet programu inicjującego. W tym przykładzie używane CorePackage.msi nazwę pliku pakietu.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  Skopiuj lub Przenieś plik CorePackage.msi do folderu C:\package.  
  
7.  Dodaj XML do zainstalowania pakietu za pomocą poleceń programu inicjującego. Program inicjujący automatycznie dodaje **/qn** flagi do pliku msi, który zostanie zainstalowany w trybie dyskretnym. Jeśli plik .exe, inicjujący uruchamia plik .exe przy użyciu powłoki. Następujący kod XML zawiera bez argumentów do CorePackage.msi, ale argument wiersza polecenia można umieszczać w atrybucie argumentów.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  Dodaj następujący kod XML, sprawdź, czy jest zainstalowany ten pakiet programu inicjującego. Zastąp kod produktu o identyfikatorze GUID pakietu redystrybucyjnego składnika.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Dodaj XML do zmiany zachowania programu inicjującego zależnie od tego, jeśli jest już zainstalowany składnik inicjujący. Jeśli jest zainstalowany składnik, nie zostanie uruchomiony pakiet programu inicjującego. Następujący kod XML sprawdza, czy aktualny użytkownik ma uprawnienia administratora, ponieważ ten składnik wymaga uprawnień administracyjnych.  
  
    ```  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. Dodaj XML można ustawić kody wyjścia, jeśli Instalacja powiodła się i konieczne jest ponowne uruchomienie. Następujący kod XML przedstawiono zakończy się niepowodzeniem i FailReboot kody, które wskazują, że inicjujący nie będzie kontynuowane, instalowanie pakietów zakończenia.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Dodaj następujący kod XML koniec sekcji poleceń programu inicjującego.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Przenieść C:\package folder do katalogu zawierającego program inicjujący Instalatora programu Visual Studio. Dla programu Visual Studio 2010 to jest katalog SDKs\Windows\v7.0A\Bootstrapper\Packages \Program Files\Microsoft.  
  
## <a name="example"></a>Przykład  
 Manifest produktu zawiera instrukcje dotyczące niestandardowe wstępne wymagania instalacji.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Produkt i pakiet — dokumentacja schematu](../deployment/product-and-package-schema-reference.md)