---
title: 'Porady: Instalowanie wymagań wstępnych przy użyciu aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 31319b0d04ff68649996ca374e3961d8fa67c833
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42690720"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Porady: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: instalowanie wstępnie wymaganych składników w aplikacji ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application).  
  
Wszystkie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje wymagają poprawną wersję programu .NET Framework jest zainstalowanie na komputerze przed zadania mogą być uruchamiane; wiele aplikacji ma również inne wymagania wstępne. Podczas publikowania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji, można wybrać zestaw wstępnie wymagane składniki do umieszczenia w pakiecie wraz z aplikacji. W trakcie instalacji będą sprawdzane dla poszczególnych wymagań wstępnych określić, jeśli już istnieje; Jeśli nie zostanie zainstalowany przed zainstalowaniem [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji.  
  
 Zamiast pakowanie i publikowania wymagań wstępnych, można również określić lokalizację pobierania dla składników. Na przykład, zamiast w tym wstępnie wymaganych składników w każdej publikowanej aplikacji, można na przykład udział scentralizowanego pliku lub lokalizacji w sieci Web, który zawiera pliki instalacyjne, wszystkie Twoje wymagania wstępne — w czasie instalacji składników zostaną pobrane i instalowane z tej lokalizacji.  
  
> [!IMPORTANT]
>  Należy dodać pakietów wymagań wstępnych Instalatora na komputerze dewelopera, przed opublikowaniem pierwszej [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji. Aby uzyskać więcej informacji, zobacz [jak: obejmują wstępnie wymaganych składników w aplikacji ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).  
  
 Wymagania wstępne są zarządzane w **wymagania wstępne** okno dialogowe, dostępna z **Publikuj** okienku **projektanta projektu**.  
  
> [!NOTE]
>  Oprócz listy wstępnie zdefiniowanych wymagań wstępnych można dodać własne składniki do listy. Aby uzyskać więcej informacji, zobacz [tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md).  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Aby określić wymagania wstępne dotyczące instalacji za pomocą aplikacji ClickOnce  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.  
  
2.  Wybierz **Publikuj** okienka.  
  
3.  Kliknij przycisk **wymagania wstępne** przycisk, aby otworzyć **wymagania wstępne** okno dialogowe.  
  
4.  W **wymagania wstępne** okna dialogowego pole, upewnij się, że **Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki** pole wyboru jest zaznaczone.  
  
5.  W **wymagania wstępne** listy, należy sprawdzić te składniki, które chcesz zainstalować, a następnie kliknij przycisk **OK**.  
  
     Wybrane składniki zostaną spakowane i opublikowanych wraz z aplikacji.  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Aby określić lokalizację pobierania różnych wstępnie wymaganych składników  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.  
  
2.  Wybierz **Publikuj** okienka.  
  
3.  Kliknij przycisk **wymagania wstępne** przycisk, aby otworzyć **wymagania wstępne** okno dialogowe.  
  
4.  W **wymagania wstępne** okna dialogowego pole, upewnij się, że **Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki** pole wyboru jest zaznaczone.  
  
5.  W **Określ lokalizację instalacji wstępnie wymaganych składników** zaznacz **Pobierz wstępnie wymagane składniki z następującej lokalizacji**.  
  
6.  Wybierz lokalizację z listy rozwijanej lub wprowadź adres URL, ścieżkę pliku lub lokalizację FTP, a następnie kliknij **OK.**  
  
    > [!NOTE]
    >  Upewnij się, że instalatory dla określone składniki istnieje w określonej lokalizacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



