---
title: 'Porady: tworzenie zlokalizowanego pakietu programu inicjującego | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6948bd0a9cb3469141ea8c879effa130e7b00e86
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38785241"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Porady: tworzenie zlokalizowanego pakietu programu inicjującego
Po utworzeniu pakietu programu inicjującego, tworząc dwie więcej plików dla poszczególnych ustawień regionalnych, można utworzyć zlokalizowane wersje pakietu programu inicjującego: postanowienia licencyjne dotyczące oprogramowania pliku (na przykład eula.rtf) oraz manifest pakietu (package.xml).  
  
 Domyślnie program Visual Studio 2010 zawiera zlokalizowane pakiety programu inicjującego tylko dla .NET Framework 4, .NET Framework 4 Client Profile, 2.0 środowisko uruchomieniowe F # i F # 4.0 środowiska uruchomieniowego. Zlokalizowane pakiety dla innych programów inicjujących można utworzyć, wykonując trzy kroki.  
  
1.  Utwórz folder o nazwie po nazwie ustawień regionalnych \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\*BootstrapperPackageName*.  
  
2.  Utwórz plik, który zawiera postanowienia licencyjne dotyczące oprogramowania pakietu programu inicjującego i umieścić go w nowym folderze.  
  
3.  Tworzenie manifestu pakietu o nazwie package.xml, zaktualizuj ciągi i kultury i umieścić ten plik w nowym folderze. Jeśli program inicjujący programu Visual Studio zostały już utworzone w języku docelowym, można skopiować pliku package.xml programu Visual Studio i zmodyfikuj go w tym kroku.  
  
> [!NOTE]
>  Jeśli używasz projektów Instalatora do wdrażania aplikacji, można zlokalizować aplikację, zmieniając **lokalizacji** właściwości.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-localized-bootstrapper-package"></a>Aby utworzyć zlokalizowanego pakietu programu inicjującego  
  
1.  Utwórz folder o nazwie po nazwie ustawień regionalnych.  
  
     Na komputerach z 32-bitowych, należy utworzyć folder \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\*BootstrapperPackageName*\ folderu.  
  
     Na komputerach 64-bitowych należy utworzyć folder \Program \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages plików (86)\\*BootstrapperPackageName*\ folderu.  
  
     W poniższej tabeli przedstawiono nazwy folderów, które służy do dopasowania ustawień regionalnych.  
  
    |Regionalne|Nazwa folderu|  
    |------------|-----------------|  
    |Chiński uproszczony|nazwy zh-Hans|  
    |Chiński (tradycyjny)|nazwy zh-Hant|  
    |czeski|CS|  
    |niemiecki|Niemcy|  
    |Angielski|pl|  
    |Hiszpański|ES|  
    |Francuski|FR|  
    |Włoski|go|  
    |koreański|ko|  
    |japoński|ja|  
    |polski|pl|  
    |portugalski (Brazylia)|pt-BR|  
    |Rosyjski|ru|  
    |turecki|TR|  
  
2.  Utwórz plik, który zawiera postanowienia licencyjne dotyczące oprogramowania pakietu programu inicjującego i umieścić go w nowym folderze.  
  
3.  Tworzenie manifestu pakietu o nazwie package.xml i umieścić go w nowym folderze. Aby uzyskać więcej informacji, zobacz [porady: tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md).  
  
4.  Aktualizacja `<Strings>` części pakietu manifestu, tak aby ciągi znajdują się w prawidłowym języku dla ustawień regionalnych.  
  
5.  Zmiana `<String Name="Culture">` wartość jest zgodna z nazwą folderu.  
  
6.  Zapisz plik package.xml.  
  
### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Aby utworzyć pakiet programu inicjującego dla programu .NET Framework 3.5 Service Pack 1 zlokalizowane w języku francuskim  
  
1.  Utwórz folder o nazwie fr. Nazwa folderu musi odpowiadać nazwie ustawień regionalnych.  
  
     Na komputerach z 32-bitowych należy utworzyć folder w folderze SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\ \Program Files\Microsoft.  
  
     Na komputerach 64-bitowych należy utworzyć folder w folderze \Program Files \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\ (86).  
  
2.  W tym folderze, fr, należy umieścić zlokalizowaną wersję postanowienia licencyjne dotyczące oprogramowania.  
  
3.  Skopiuj plik \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml pliki (x86) \Program do folderu fr, a następnie otwórz plik w Projektancie XML.  
  
4.  Aktualizacja `<Strings>` sekcji pakietu manifestu, tak aby były ciągi błędów w języku francuskim.  
  
5.  Zmiana `<String Name="Culture">` wartość fr.  
  
6.  Zapisz plik package.xml.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md)   
 [Wymagania wstępne wdrożenia aplikacji](../deployment/application-deployment-prerequisites.md)   
 [Instrukcje: tworzenie manifestu pakietu](../deployment/how-to-create-a-package-manifest.md)