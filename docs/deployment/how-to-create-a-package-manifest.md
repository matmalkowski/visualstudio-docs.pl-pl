---
title: 'Porady: tworzenie manifestu pakietu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: d36d6c1d4589fa24e4c3e7c53e041d07f359092b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-package-manifest"></a>Porady: tworzenie manifestu pakietu
Aby wdrożyć wymagania wstępne dotyczące aplikacji, można użyć pakietu programu inicjującego. Pakiet programu inicjującego zawiera jeden produkt pliku manifestu ale manifest pakietu dla każdego ustawienia regionalne. Funkcji udostępnionych w różnych wersjach zlokalizowanych powinien przejść do manifestu produkt.  
  
 Aby uzyskać więcej informacji na temat manifestów pakietu, zobacz [porady: tworzenie manifestu produkt](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Tworzenie manifestu pakietu  
  
#### <a name="to-create-the-package-manifest"></a>Aby utworzyć plik manifestu pakietu  
  
1.  Utwórz katalog dla pakietu programu inicjującego. W tym przykładzie użyto C:\package.  
  
2.  Utwórz podkatalog o nazwie ustawień regionalnych, takich jak en dla języka angielskiego.  
  
3.  W programie Visual Studio, Utwórz plik XML o nazwie `package.xml`i zapisz go w folderze C:\package\en.  
  
4.  Dodaj XML, aby wyświetlić listę nazwę pakietu programu inicjującego, culture dla manifest tego pakietu zlokalizowane i umowy licencyjnej opcjonalne. Następujący kod XML używa zmiennych `DisplayName` i `Culture`, które zostały określone w elemencie nowsze.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Dodaj XML, aby wyświetlić listę wszystkich plików, które znajdują się w katalogu ustawień regionalnych. Następujący kod XML używany jest plik o nazwie eula.txt, która jest stosowana do **en** ustawień regionalnych.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Dodaj XML do definiowania Lokalizowalny ciągów dla pakietu programu inicjującego. Następujący kod XML dodaje ciągów błędów dla ustawień regionalnych pl.  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7.  Skopiuj C:\package folder do katalogu zawierającego program inicjujący Instalatora programu Visual Studio. Dla programu Visual Studio 2010 to jest katalog SDKs\Windows\v7.0A\Bootstrapper\Packages \Program Files\Microsoft.  
  
## <a name="example"></a>Przykład  
 Manifest pakietu zawiera informacje specyficzne dla ustawień regionalnych, takie jak komunikaty o błędach, postanowienia licencyjne dotyczące oprogramowania i pakietów językowych.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Produkt i pakiet — dokumentacja schematu](../deployment/product-and-package-schema-reference.md)