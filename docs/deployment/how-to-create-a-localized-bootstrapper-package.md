---
title: "Porady: tworzenie zlokalizowanego pakietu programu inicjującego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
caps.latest.revision: "15"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: f19ec03dda8666eea39b50af40a44ab2c68694ce
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Porady: tworzenie zlokalizowanego pakietu programu inicjującego
Po utworzeniu pakietu programu inicjującego zlokalizowane wersje pakietu programu inicjującego można utworzyć przez utworzenie dwóch większej liczby plików dla poszczególnych ustawień regionalnych: postanowień licencyjnych dotyczących oprogramowania, plik (na przykład eula.rtf) oraz manifest pakietu (plik package.xml).  
  
 Domyślnie program Visual Studio 2010 obejmuje zlokalizowanych pakietów programu inicjującego tylko dla programu .NET Framework 4, .NET Framework 4 Client Profile, F # Runtime 2.0 i 4.0 środowiska uruchomieniowego języka F #. Zlokalizowane pakiety można tworzyć dla innych bootstrappers, wykonując trzy kroki.  
  
1.  Utwórz folder o nazwie po nazwie ustawień regionalnych w \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\*BootstrapperPackageName*.  
  
2.  Utwórz plik zawierający postanowienia licencyjne dotyczące oprogramowania dla pakietu programu inicjującego i umieszcza je w nowym folderze.  
  
3.  Tworzenie manifestu pakietu o nazwie plik package.xml, ciągi i kultury aktualizacji i umieścić plik w nowym folderze. Jeśli utworzono już programu inicjującego programu Visual Studio w języku docelowym, można skopiować pliku plik package.xml programu Visual Studio, a następnie zmodyfikować go w tym kroku.  
  
> [!NOTE]
>  Jeśli używasz instalacji projektu do wdrażania aplikacji, zmieniając można lokalizować aplikacji **lokalizacja** właściwości.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-localized-bootstrapper-package"></a>Aby utworzyć zlokalizowanego pakietu programu inicjującego  
  
1.  Utwórz folder o nazwie po nazwie ustawień regionalnych.  
  
     Na komputerach z 32-bitowych, należy utworzyć folder w \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\*BootstrapperPackageName*\ folderu.  
  
     Na komputerach 64-bitowych, należy utworzyć folder \Program \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages plików (86)\\*BootstrapperPackageName*\ folderu.  
  
     W poniższej tabeli przedstawiono nazwy folderów, które służy do dopasowania ustawień regionalnych.  
  
    |Regionalne|Nazwa folderu|  
    |------------|-----------------|  
    |Chiński uproszczony|zh-Hans|  
    |Chiński (tradycyjny)|zh-Hant|  
    |czeski|CS|  
    |niemiecki|Niemcy|  
    |angielski|EN|  
    |Hiszpański|ES|  
    |Francuski|FR|  
    |Włoski|go|  
    |koreański|Ko|  
    |japoński|Japonia|  
    |polski|pl|  
    |portugalski (Brazylia)|pt-BR|  
    |Rosyjski|RU|  
    |turecki|TR|  
  
2.  Utwórz plik zawierający postanowienia licencyjne dotyczące oprogramowania dla pakietu programu inicjującego i umieszcza je w nowym folderze.  
  
3.  Tworzenie manifestu pakietu o nazwie plik package.xml i umieszcza je w nowym folderze. Aby uzyskać więcej informacji, zobacz [porady: tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md).  
  
4.  Aktualizacja `<Strings>` sekcji pakietu dla manifest, aby w języku ustawień regionalnych dla ciągów.  
  
5.  Zmień `<String Name="Culture">` wartość jest zgodna z nazwą folderu.  
  
6.  Zapisz plik plik package.xml.  
  
### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Aby utworzyć pakiet programu inicjującego dla programu .NET Framework 3.5 Service Pack 1 zlokalizowane w języku francuskim  
  
1.  Utwórz folder o nazwie fr. Nazwa folderu musi odpowiadać nazwie ustawień regionalnych.  
  
     Na komputerach z 32-bitowych należy utworzyć folder w folderze SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\ \Program Files\Microsoft.  
  
     Na komputerach 64-bitowych należy utworzyć folder w folderze \Program Files \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\ (86).  
  
2.  Umieść zlokalizowanej wersji postanowień licencyjnych w folderze fr.  
  
3.  Skopiuj plik \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml pliki (x86) \Program do folderu fr, a następnie otwórz plik w Projektancie XML.  
  
4.  Aktualizacja `<Strings>` sekcji pakietu manifestu, tak aby były ciągi błędu w języku francuskim.  
  
5.  Zmień `<String Name="Culture">` wartość fr.  
  
6.  Zapisz plik plik package.xml.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md)   
 [Wymagania wstępne dotyczące wdrażania aplikacji](../deployment/application-deployment-prerequisites.md)   
 [Porady: tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md)