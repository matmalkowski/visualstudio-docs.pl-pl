---
title: Struktura pakietu VSIX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d811c1539dde655657331b7ca3511bbd4e80063f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="anatomy-of-a-vsix-package"></a>Struktura pakietu VSIX
Pakiet VSIX jest plik .vsix, który zawiera jeden lub więcej rozszerzeń programu Visual Studio, razem z metadanymi, używanych do klasyfikowania i zainstalowania rozszerzeń programu Visual Studio. Metadane są zawarte w manifeście VSIX i pliku XML [Content_Types]. Pakiet VSIX może również zawierać jeden lub więcej plików Extension.vsixlangpack, aby umieścić tekst Instalatora zlokalizowanych i może zawierać dodatkowe pakiety VSIX, aby zainstalować zależności.  
  
 Format pakietu VSIX jest zgodna ze standardu otwarte konwencje pakietów (OPC). Pakiet zawiera pliki binarne i pliki pomocnicze, wraz z pliku XML [Content_Types] i .vsix pliku manifestu. Jeden pakiet VSIX może zawierać wielu projektów lub nawet kilka pakietów, które mają własne manifestów dane wyjściowe.  
  
> [!NOTE]
>  Nazwy plików zawarte w pliku VSIX pakietów nie może zawierać spacji ani znaków, które są zastrzeżone w identyfikatory URI (Uniform Resource), zdefiniowane w obszarze [ \[specyfikacja RFC 2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>VSIX Manifest  
 VSIX manifest zawiera informacje o rozszerzenia do zainstalowania i schematu VSX w następujący sposób. Aby uzyskać więcej informacji, zobacz [odwołania 1.0 schematu rozszerzenia VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Dla manifest VSIX przykład [PackageManifest elementu (Element główny, schemat VSX)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 VSIX manifest musi mieć nazwę `extension.vsixmanifest` po nie zostało uwzględnione w pliku .vsix.  
  
## <a name="the-content"></a>Zawartość  
 Pakiet VSIX może zawierać szablony, elementy przybornika, VSPackages lub dowolny inny rodzaj rozszerzenia, która jest obsługiwana przez program Visual Studio.  
  
## <a name="language-packs"></a>Pakiety językowe  
 Pakiet VSIX może zawierać jeden raz lub więcej plików Extension.vsixlangpack zapewnienie zlokalizowanego tekstu podczas instalacji. Aby uzyskać więcej informacji, zobacz [lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Zależności i odwołań  
 Pakiet VSIX może zawierać inne pakiety VSIX jako odwołania. Każdy z tych innych pakietów musi zawierać manifeście VSIX.  
  
 Jeśli użytkownik próbuje zainstalować rozszerzenie, które ma zależności, Instalator sprawdza, czy wymagane zestawy są zainstalowane na komputerze użytkownika. Jeśli nie ma wymaganych zestawów, **rozszerzenia i aktualizacje** Wyświetla listę brakujących zestawów.  
  
 Jeśli manifestu rozszerzenia zawiera co najmniej jedną [odwołania](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) elementów **rozszerzenia i aktualizacje** porównuje manifest każde odwołanie do rozszerzenia, które są zainstalowane w systemie, a następnie instaluje Odwołanie do rozszerzenia, jeśli nie jest już zainstalowany. Jeśli jest zainstalowana starsza wersja dołączonego przez odwołanie rozszerzenia, nowsza wersja zastępuje go.  
  
 Jeśli projekt w rozwiązaniu do wielu projektów zawiera odwołanie do innego projektu w tym samym rozwiązaniu, pakiet VSIX zawiera zależności projektu. To zachowanie można przesłonić, klikając odwołania dla wewnętrznego projektu, a następnie w **właściwości** okna Ustawianie **dane wyjściowe grupy uwzględnione w pliku VSIX** właściwości `BuiltProjectOutputGroup`.  
  
 Aby dołączać satelitarne bibliotek DLL, z którym związane są odwołania zestawów w pakiecie VSIX, Dodaj `SatelliteDllsProjectOutputGroup` do **dane wyjściowe grupy uwzględnione w pliku VSIX** właściwości.  
  
## <a name="installation-location"></a>Lokalizacja instalacji  
 Podczas instalacji **rozszerzenia i aktualizacje** szuka zawartości pakietu VSIX w folderze % LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.  
  
 Domyślnie instalacja dotyczy tylko bieżącego użytkownika, ponieważ % LocalAppData % to katalog specyficzne dla użytkownika. Jednak jeśli ustawisz [AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b) element manifestu do `True`, rozszerzenie zostanie zainstalowane w obszarze... \\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions i będzie dostępna dla wszystkich użytkowników komputera.  
  
## <a name="contenttypesxml"></a>XML [Content_Types]  
 Plik XML [Content_Types] określa typów plików w pliku .vsix rozwinięte. Ten plik jest używany podczas instalacji pakietu programu Visual Studio, ale nie można zainstalować w samym pliku. Aby uzyskać więcej informacji dotyczących tego pliku, zobacz [struktury XML [Content_types] pliku](the-structure-of-the-content-types-dot-xml-file.md).  
  
 Plik XML [Content_Types] jest wymagany przez otwarty pakowania konwencje pakietów (OPC) standardowa. Aby uzyskać więcej informacji na temat OPC zobacz [OPC: A nowe standardowe dla pakietów danych](http://go.microsoft.com/fwlink/?LinkID=148207) w witrynie MSDN.