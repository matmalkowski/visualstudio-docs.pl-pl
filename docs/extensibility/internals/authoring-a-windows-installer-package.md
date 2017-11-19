---
title: Tworzenie pakietu Instalatora Windows | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5f646e2234adf0eb0117f154838b15d7b3aa200e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="authoring-a-windows-installer-package"></a>Tworzenie pakietu Instalatora Windows
Dane dysków modelu Instalatora Windows. Zamiast pisania procedurach skryptu do kopiowania plików i zapisywanie wpisów rejestru, na przykład można tworzyć wierszy i kolumn w tabelach bazy danych, które zawierają dane plików i rejestru.  
  
## <a name="database-entries"></a>Wpisy w bazie danych  
 Aby zainstalować pakiet VSPackage, pakiet Instalatora systemu Windows musi zawierać wpisy w bazie danych można wykonywać następujące zadania:  
  
-   Wyszukaj systemu można znaleźć wersje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage obsługuje (przy użyciu tabel Instalatora Windows, które zawierają AppSearch powoduje niepoprawne obcięcie, CompLocator RegLocator, DrLocator i podpis).  
  
-   Anuluj instalację, jeśli nie obsługiwaną wersję [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest zainstalowany lub jeśli inny pakiet VSPackage wymagania systemowe nie jest spełniony (przy użyciu tabeli LaunchCondition).  
  
-   Zainstaluj pakiet VSPackage i pliki zależne (przy użyciu katalogu, składników i tabel plików).  
  
-   Dodaj odpowiednie informacje o pakiecie VSPackage (przy użyciu tabeli rejestru).  
  
-   Integracja pakiet VSPackage w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przez wywołanie metody **/Setup devenv.exe** (przy użyciu tabeli Akcja niestandardowa).  
  
 Aby uzyskać więcej informacji, zobacz [Instalatora Windows](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Instalator narzędzia  
 Różnych narzędzi innych firm ustawienia zawierają Środowisko deweloperskie do pakietów Instalatora Windows. Dwa bezpłatnych narzędzi są następujące:  
  
-   InstallShield Limited Edition  
  
     Ograniczoną wersję InstallShield można uzyskać za pomocą programu Visual Studio **nowy projekt** okna dialogowego. Rozwiń węzeł **inne typy projektów** , a następnie wybierz **instalacji i wdrażania**. Wybierz szablon InstallShield.  
  
-   Zestaw narzędzi XML Instalatora Windows  
  
     Zestaw narzędzi kompilacji pakietów Instalatora Windows przy użyciu plików źródłowych XML. Zestaw narzędzi to projekt open source firmy Microsoft. Możesz pobrać kodu źródłowego i plików wykonywalnych z [http://sourceforge.net/projects/wix](http://sourceforge.net/projects/wix).  
  
 Komercyjnych produktów, które integrują [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] za pomocą [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], zobacz [http://visualstudiogallery.com](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Zobacz też  
 [Instalowanie VSPackages za pomocą Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)