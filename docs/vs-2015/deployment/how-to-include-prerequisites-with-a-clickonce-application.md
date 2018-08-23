---
title: 'Porady: uwzględnianie wstępnie wymaganych składników w aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: bd50b69bc46b1f00f797fd120351dd47f3bb8b03
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42628692"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Porady: uwzględnianie wstępnie wymaganych składników w aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: obejmują wstępnie wymaganych składników w aplikacji ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-include-prerequisites-with-a-clickonce-application).  
  
Aby można było dystrybuować wstępnie wymagane oprogramowanie za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji, musisz najpierw pobrać pakiety instalacyjne tych wstępnie wymaganych składników na komputerze dewelopera. Po opublikowaniu aplikacji i wybraniu **Pobierz wstępnie wymagane składniki z tej samej lokalizacji co aplikację**, wystąpi błąd, jeśli pakiety instalacyjne nie są w **pakietów** folderu.  
  
> [!NOTE]
>  Aby dodać pakiet instalacyjny dla programu .NET Framework, zobacz [.NET Framework — przewodnik wdrażania dla deweloperów](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
##  <a name="Package"></a> Aby dodać pakiet instalacyjny przy użyciu pliku Package.xml  
  
1.  W Eksploratorze plików otwórz **pakietów** folderu.  
  
     Domyślna ścieżka jest 14.0\SDK\Bootstrapper\Packages C:\Program Files\Microsoft Visual Studio w systemie 32-bitowe i C:\Program Files (x86) \Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages w systemie 64-bitowych.  
  
2.  Otwórz folder wstępnie wymaganego składnika, który chcesz dodać, a następnie otwórz folder języka dla zainstalowanej wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (na przykład **en** w języku angielskim).  
  
3.  Otwórz w Notatniku **Package.xml** pliku.  
  
4.  Znajdź **nazwa** element, który zawiera **http://go.microsoft.com/fwlink**, a następnie skopiuj adres URL. Obejmują **LinkID** części.  
  
    > [!NOTE]
    >  Jeśli nie **nazwa** element zawiera **http://go.microsoft.com/fwlink**, otwórz **Product.xml** pliku w folderze głównym wstępnie wymaganego składnika i zlokalizuj **fwlink** ciągu.  
  
    > [!IMPORTANT]
    >  Niektóre wstępnie wymagane składniki mają wiele pakietów instalacyjnych (na przykład dla systemów 32-bitowych i 64-bitowych). Jeśli wiele **nazwa** elementy zawierają **fwlink**, pozostałe kroki należy powtórzyć dla każdego z nich.  
  
5.  Wklej adres URL w pasku adresu przeglądarki, a następnie, gdy zostanie wyświetlony monit o uruchomienie lub zapisanie, wybierz **Zapisz**.  
  
     W tym kroku plik instalatora jest pobierany na komputer.  
  
6.  Skopiuj plik do folderu głównego dla wstępnie wymaganego składnika.  
  
     Na przykład dla wstępnie wymaganego składnika Instalator Windows 4.5 skopiuj plik do folderu \Packages\WindowsInstaller4_5.  
  
     Teraz można dystrybuować pakiet instalacyjny z aplikacją.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)



