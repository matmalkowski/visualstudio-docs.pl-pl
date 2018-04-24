---
title: 'Porady: Określanie alternatywnej lokalizacji aktualizacji wdrażania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14c6778d5cad698e6eea541b94df6f8eb793746c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Porady: określanie alternatywnej lokalizacji aktualizacji wdrażania
Można zainstalować programu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji początkowo z dysku CD lub udziału plików, ale aplikacja musi sprawdzić okresowej aktualizacji w sieci Web. Alternatywnej lokalizacji aktualizacji można określić w manifeście wdrażania, aby aplikację można aktualizować się z sieci Web po początkowej instalacji.  
  
> [!NOTE]
>  Twoje aplikacja musi być skonfigurowana do zainstalowania lokalnie, aby użyć tej funkcji. Aby uzyskać więcej informacji, zobacz [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Ponadto po zainstalowaniu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji z sieci, ustawianie lokalizacji alternatywnej przyczyny [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] do użycia dla początkowej instalacji i wszystkie kolejne aktualizacje tej lokalizacji. Po zainstalowaniu aplikacji lokalnie (na przykład z dysku CD) początkowej instalacji odbywa się przy użyciu oryginalnego nośnika, a wszystkie kolejne aktualizacje użyje lokalizacji alternatywnej.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Określanie alternatywnej lokalizacji aktualizacji przy użyciu MageUI.exe (narzędzie oparte na formularzach systemu Windows)  
  
1.  Otwórz wiersz polecenia .NET Framework i wpisz:  
  
     **mageui.exe**  
  
2.  Na **pliku** menu, wybierz **Otwórz** otworzyć manifest wdrażania aplikacji.  
  
3.  Wybierz **opcje wdrażania** kartę.  
  
4.  W polu tekstowym o nazwie **uruchamianie lokalizacji**, wprowadź adres URL do katalogu, który będzie zawierał manifest wdrażania aktualizacji aplikacji.  
  
5.  Zapisz manifest wdrażania.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Określanie alternatywnej lokalizacji aktualizacji przy użyciu Mage.exe  
  
1.  Otwórz wiersz polecenia .NET Framework.  
  
2.  Ustaw lokalizację aktualizacji przy użyciu następującego polecenia. W tym przykładzie **HelloWorld.exe.application** to ścieżka do Twojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji, która ma zawsze rozszerzenie .application, i **http://adatum.com/Update/Path** jest adres URL tego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] będzie sprawdzać dostępność aktualizacji aplikacji.  
  
     **Obraz — aktualizacja HelloWorld.exe.application - ProviderUrl http://adatum.com/Update/Path**  
  
3.  Zapisz plik.  
  
    > [!NOTE]
    >  Teraz należy ponownie podpisać plik z Mage.exe. Aby uzyskać więcej informacji, zobacz [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Jeśli zainstalować aplikację z nośnika w trybie offline, takich jak dysk CD, a komputer jest w trybie online, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] najpierw sprawdza ją na adres URL określony przez `<deploymentProvider>` tag w manifeście wdrażania, aby ustalić, czy lokalizacja aktualizacji zawiera nowszą wersję aplikacja. Jeśli tak, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instaluje aplikację bezpośrednio z niego, a nie w katalogu instalacyjnym początkowej i środowisko uruchomieniowe języka wspólnego (CLR) określa zaufania aplikacji poziomu przy użyciu `<deploymentProvider>`. Jeśli komputer jest w trybie offline lub `<deploymentProvider>` jest nieosiągalny, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zaufania oparta na punkcie instalacji przyznaje instalacji z dysku CD, a środowisko CLR; w przypadku instalacji z dysku CD, oznacza to, aplikacja odbiera pełnego zaufania. Wszystkie kolejne aktualizacje będzie dziedziczyć tego poziomu zaufania.  
  
 Wszystkie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, które używają `<deploymentProvider>` powinny jawnie deklarować uprawnienia muszą w manifeście aplikacji, aby aplikacja nie otrzyma różne poziomy zaufania na różnych komputerach.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)