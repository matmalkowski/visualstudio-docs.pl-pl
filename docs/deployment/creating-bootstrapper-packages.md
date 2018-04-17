---
title: Tworzenie pakietów programu inicjującego | Dokumentacja firmy Microsoft
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
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 569b3834685b119ebb8a539d1c2fa79e9bb51161
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="creating-bootstrapper-packages"></a>Tworzenie pakietów programu inicjującego
Program instalacyjny jest ogólny Instalatora, które mogą być skonfigurowane do wykrywania i zainstaluj pakiet redystrybucyjny składniki, takie jak pliki Instalatora Windows (msi) i programy wykonywalne. Instalator jest nazywana programu inicjującego. Jest on zaprogramowane za pomocą zestawu Manifesty XML, określających metadanych do zarządzania instalacją składnika.  
  
 Program inicjujący najpierw wykrywa, czy wszelkie wymagania wstępne są już zainstalowane. Jeśli wymagania wstępne nie są zainstalowane, najpierw inicjujący zawiera umowy licencyjne. Drugie po użytkownik końcowy akceptuje umów licencyjnych, instalacja rozpocznie się wymagań wstępnych. W przeciwnym razie jeśli wszystkie wymagania wstępne zostaną wykryte, inicjujący tylko uruchamiania Instalatora aplikacji.  
  
## <a name="creating-custom-packages"></a>Tworzenie niestandardowych pakietów  
 Manifesty można wygenerować za pomocą edytora XML w Visual Studio. Aby uzyskać więcej informacji, zobacz [porady: tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md) i [porady: tworzenie manifestu produkt](../deployment/how-to-create-a-product-manifest.md). Aby zapoznać się z przykładem tworzenia pakietu programu inicjującego, zobacz [wskazówki: Tworzenie niestandardowego programu inicjującego wyświetlającego monitu prywatności](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
 Aby utworzyć pakiet programu inicjującego, należy podać pakietu redystrybucyjnego w formie pliku EXE lub MSI file.to Generator manifestu programu inicjującego. Następnie Generator manifestu programu inicjującego tworzy następujące pliki:  
  
-   Manifest produktu product.xml, który zawiera wszystkie metadane niezależny od języka dla pakietu. Zawiera wspólne dla wszystkie zlokalizowane wersje składnik redystrybucyjny metadanych.  
  
-   Manifest pakietu plik package.xml zawierającego metadane specyficzne dla języka; zwykle zawiera zlokalizowane komunikaty. Składnik musi mieć co najmniej jeden manifest pakietu dla każdego zlokalizowanej wersji tego składnika.  
  
 Po utworzeniu te pliki poddane folder o nazwie niestandardowego programu inicjującego pliku manifestu produktu. Plik manifestu pakietu przechodzi w folderze o nazwie dla ustawień regionalnych. Na przykład jeśli plik manifestu pakietu jest przeznaczony dla angielskiej wersji językowej redystrybucji, należy umieścić plik do folderu o nazwie en. Powtórz ten proces dla każdego ustawienia regionalne, takie jak Japonia w języku japońskim i de na język niemiecki. Końcowe niestandardowy pakiet programu inicjującego może mieć następującą strukturę folderów.  
  
 `CustomBootstrapperPackage`  
  
 `product.xml`  
  
 `CustomBootstrapper.msi`  
  
 `de`  
  
 `eula.rtf`  
  
 `package.xml`  
  
 `en`  
  
 `eula.rtf`  
  
 `package.xml`  
  
 `ja`  
  
 `eula.rtf`  
  
 `package.xml`  
  
 Na koniec skopiuj pliki redystrybucyjne do lokalizacji folderu programu inicjującego. Aby uzyskać więcej informacji, zobacz [porady: tworzenie zlokalizowanego pakietu programu inicjującego](../deployment/how-to-create-a-localized-bootstrapper-package.md).  
  
```  
\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 lub  
  
```  
\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 Można również określić lokalizację folderu programu inicjującego z **ścieżki** wartość w następującym kluczu rejestru:  
  
```  
HKLM\Software\Microsoft\GenericBootstrapper\11.0  
```  
  
 W systemach 64-bitowych należy użyć następującego klucza rejestru:  
  
```  
HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0  
```  
  
 Każdy składnik redystrybucyjny pojawia się we własnym podfolderze w katalogu pakietów. Produkt pliki manifestu i pakietu redystrybucyjnego są wprowadzane do tego podfolderu. Zlokalizowane wersje manifestów składnika i pakietu są umieszczane w podfoldery o nazwach według nazwy kultury.  
  
 Gdy te pliki zostaną skopiowane do folderu programu inicjującego pakietu programu inicjującego automatycznie zostanie wyświetlony w oknie dialogowym wymagania wstępne programu Visual Studio. Nie ma Twojego niestandardowy pakiet programu inicjującego, zamknij i ponownie otworzyć okno dialogowe wymagania wstępne. Aby uzyskać więcej informacji, zobacz [wstępnie wymagane składniki — okno dialogowe](../ide/reference/prerequisites-dialog-box.md).  
  
 W poniższej tabeli przedstawiono właściwości, które są wypełniane automatycznie przez program inicjujący.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|ApplicationName|Nazwa aplikacji.|  
|Element ProcessorArchitecture|Procesor i usługi bits na word platformy docelowej przez plik wykonywalny. Następujące wartości:<br /><br /> -Intel<br />-IA64<br />— AMD64|  
|[Version9x](https://msdn.microsoft.com/en-us/library/aa372490\(v=vs.140\).aspx)|Numer wersji systemów operacyjnych Microsoft Windows 95, Windows 98 lub Windows ME. Składnia wersji jest Major.Minor.ServicePack.|  
|[VersionNT](https://msdn.microsoft.com/en-us/library/aa372495\(v=vs.140\).xaspx)|Numer wersji systemów operacyjnych Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 lub Windows 7. Składnia wersji jest Major.Minor.ServicePack.|  
|[VersionMSI](https://msdn.microsoft.com/en-us/library/aa372493\(v=vs.140\).aspx)|Wersja zestawu Instalatora Windows (msi.dll) uruchom podczas instalacji.|  
|[AdminUser](https://msdn.microsoft.com/en-us/library/aa367545\(v=vs.140\).aspx)|Ta właściwość jest ustawiona, jeśli użytkownik ma uprawnienia administratora. Wartości to PRAWDA lub FAŁSZ.|  
|Tryb instalacji|Tryb instalacji wskazuje, gdzie składnik musi zostać zainstalowany z. Następujące wartości:<br /><br /> -HomeSite — wstępnie wymagane składniki są instalowane z witryny sieci Web dostawcy.<br />-SpecificSite — wstępnie wymagane składniki są instalowane z wybranej lokalizacji.<br />-SameSite — wstępnie wymagane składniki są instalowane z tej samej lokalizacji co aplikacja.|  
  
## <a name="separating-redistributables-from-application-installations"></a>Oddzielanie pakietów redystrybucyjnych z instalacje aplikacji  
 Aby zapobiec plików pakietu redystrybucyjnego wdrażany w projektach Instalatora. Aby to zrobić, należy utworzyć listę pakietu redystrybucyjnego w folderze redistlist — w katalogu .NET Framework:  
  
 `%ProgramFiles%\Microsoft.NET\RedistList`  
  
 Pakiet redystrybucyjny listy jest plik XML, który należy nazwę w następującym formacie: *nazwa firmy*. *Nazwa składnika*. RedistList.xml. Tak na przykład, jeśli składnik jest wywoływana przez xyz Datawidgets, użycie Acme.DataWidgets.RedistList.xml. Przykładem listy do dystrybucji zawartości, może wyglądać następująco:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Instalowanie wymagań wstępnych za pomocą aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Wstępnie wymagane składniki — okno dialogowe](../ide/reference/prerequisites-dialog-box.md)   
 [Produkt i pakiet — odwołanie do schematu](../deployment/product-and-package-schema-reference.md)   
 [Użyj programu Visual Studio 2005 programu inicjującego wystartuj instalacji](http://go.microsoft.com/fwlink/?LinkId=107537)