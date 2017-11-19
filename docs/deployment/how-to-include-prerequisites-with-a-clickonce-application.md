---
title: "Porady: uwzględnianie wstępnie wymaganych składników za pomocą aplikacji ClickOnce | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 18431ea15b53959234da4b2c6dedb24b8fa2e390
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Porady: uwzględnianie wstępnie wymaganych składników w aplikacji ClickOnce
Przed rozpoczęciem dystrybucji, wstępnie wymaganego oprogramowania z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, należy najpierw pobrać pakietów Instalatora dla tych wymagań wstępnych na komputerze deweloperskim. Podczas publikowania aplikacji i wybierz **Pobierz wstępnie wymagane składniki z tej samej lokalizacji co Moja aplikacja**, wystąpi błąd, jeśli pakietów Instalatora nie ma w **pakiety** folderu.  
  
> [!NOTE]
>  Aby dodać pakiet Instalatora programu .NET Framework, zobacz [.NET Framework — przewodnik wdrażania dla deweloperów](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
##  <a name="Package"></a>Aby dodać pakiet Instalatora przy użyciu plik Package.xml  
  
1.  Otwórz w Eksploratorze plików **pakiety** folderu.  
  
     Domyślnie ścieżka to C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages w 32-bitowym systemie C:\Program Files (x86) \Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages w 64-bitowym systemie.  
  
2.  Otwórz folder wymagania wstępne, które chcesz dodać, a następnie otwórz folder języka dla zainstalowanej wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (na przykład **en** w języku angielskim).  
  
3.  Otwórz w Notatniku **plik Package.xml** pliku.  
  
4.  Zlokalizuj **nazwa** element, który zawiera **http://go.microsoft.com/fwlink**i skopiuj adres URL. Obejmują **LinkID** części.  
  
    > [!NOTE]
    >  Jeśli nie **nazwa** element zawiera **http://go.microsoft.com/fwlink**, otwórz **Product.xml** plików w folderze głównym dla wymagań wstępnych i Znajdź  **fwlink** ciągu.  
  
    > [!IMPORTANT]
    >  Niektóre wstępnie wymagane składniki mają wiele pakietów instalacyjnych (na przykład dla systemów 32-bitowych i 64-bitowych). Jeśli wiele **nazwa** elementy zawierają **fwlink**, pozostałe kroki należy powtórzyć dla każdego z nich.  
  
5.  Wklej adres URL na pasku adresu przeglądarki, a następnie, gdy zostanie wyświetlony monit o uruchomienie lub zapisanie, wybierz **zapisać**.  
  
     W tym kroku plik instalatora jest pobierany na komputer.  
  
6.  Skopiuj plik do folderu głównego dla wstępnie wymaganego składnika.  
  
     Na przykład dla wstępnie wymaganego składnika Instalator Windows 4.5 skopiuj plik do folderu \Packages\WindowsInstaller4_5.  
  
     Teraz można dystrybuować pakiet instalacyjny z aplikacją.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Instalowanie wymagań wstępnych za pomocą aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)