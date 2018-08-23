---
title: Tworzenie pakietu Instalatora Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a9b56ea9120e3cbee18d8018420a94748dc52eec
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42633877"
---
# <a name="authoring-a-windows-installer-package"></a>Tworzenie pakietu Instalatora Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Tworzenie pakietu Instalatora Windows](https://docs.microsoft.com/visualstudio/extensibility/internals/authoring-a-windows-installer-package).  
  
Danych zależy od modelu Instalatora Windows. Zamiast pisania procedurach skryptu, aby skopiować pliki i Zapisz wpisy rejestru, na przykład, możesz tworzyć wierszy i kolumn w tabelach bazy danych, które zawierają dane plików i rejestru.  
  
## <a name="database-entries"></a>Wpisy w bazie danych  
 Do zainstalowania pakietu VSPackage, to pakiet Instalatora Windows musi zawierać wpisy w bazie danych można wykonywać następujące zadania:  
  
-   Wyszukaj systemu, aby zlokalizować wersje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Twojego pakietu VSPackage obsługuje (przy użyciu tabel Instalatora Windows, które zawierają AppSearch powoduje niepoprawne obcięcie CompLocator, RegLocator, DrLocator i podpis).  
  
-   Anuluj instalację, jeśli nie obsługiwaną wersję [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest zainstalowany lub jeśli wymagania systemu innego pakietu VSPackage nie jest spełniony (przy użyciu tabeli LaunchCondition).  
  
-   Instalowanie pakietu VSPackage i pliki zależne (przy użyciu katalogu, składników i tabele plików).  
  
-   Dodaj odpowiednie informacje dotyczące pakietu VSPackage (przy użyciu tabeli w rejestrze).  
  
-   Integrowanie pakietu VSPackage w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] przez wywołanie metody **/Setup devenv.exe** (przy użyciu tabeli Akcja niestandardowa).  
  
 Aby uzyskać więcej informacji, zobacz [Instalatora Windows](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Konfigurowanie narzędzia  
 Szeroką gamą narzędzi innych firm Instalatora zapewniają środowisko projektowe dla pakietów Instalatora Windows. Dwa bezpłatne narzędzia są następujące:  
  
-   InstallShield Limited Edition  
  
     Ograniczona wersja programu InstallShield można uzyskać za pomocą programu Visual Studio **nowy projekt** okna dialogowego. Rozwiń **inne typy projektów** , a następnie wybierz **instalacja i wdrożenie**. Wybierz szablon InstallShield.  
  
-   Zestaw narzędzi XML Instalatora Windows  
  
     Zestaw narzędzi kompilacji pakietów Instalatora Windows przy użyciu plików źródłowych XML. Zestaw narzędzi to projekt typu open source firmy Microsoft. Możesz pobrać kod źródłowy i pliki wykonywalne z [ http://sourceforge.net/projects/wix ](http://sourceforge.net/projects/wix).  
  
 Komercyjne produktów, które integrują [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] przy użyciu [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], zobacz [ http://visualstudiogallery.com ](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Zobacz też  
 [Instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

