---
title: "Porady: Instalowanie wymagań wstępnych za pomocą aplikacji ClickOnce | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
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
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 83458b627949cda5f918ec06a5f84bd9697ba6d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Porady: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce
Wszystkie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje wymagają, że poprawna wersja programu .NET Framework jest zainstalowany na komputerze, zanim zostaną one uruchomione; wiele aplikacji ma również inne wymagania wstępne. Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, możesz wybrać zestaw wstępnie wymagane składniki do umieszczone razem z aplikacji. Podczas instalacji zostanie wykonane sprawdzenie dla poszczególnych wymagań wstępnych określić, jeśli już istnieje; Jeśli nie zostanie zainstalowany przed zainstalowaniem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.  
  
 Zamiast tworzenia pakietu i publikowania wymagań wstępnych, można również określić lokalizację pobierania dla składników. Na przykład zamiast w tym wstępnie wymaganych składników w każdej aplikacji, która publikowania, można na przykład udział scentralizowanego pliku lub lokalizacji w sieci Web, który zawiera pliki instalacyjne wszystkie Twoje wymagania wstępne — w czasie instalacji składniki zostaną pobrane i zainstalowane z tej lokalizacji.  
  
> [!IMPORTANT]
>  Należy dodać pakietów wymagań wstępnych Instalatora na komputerze deweloperskim, przed opublikowaniem pierwszego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Aby uzyskać więcej informacji, zobacz [porady: obejmują wstępnie wymaganych składników w aplikacji ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).  
  
 Wymagania wstępne są zarządzane w **wymagania wstępne** okno dialogowe, dostępne z **publikowania** okienku **projektanta projektu**.  
  
> [!NOTE]
>  Oprócz wstępnie określoną listę warunków wstępnych można dodać własne składniki do listy. Aby uzyskać więcej informacji, zobacz [tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md).  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Aby określić wymagania wstępne dotyczące instalacji za pomocą aplikacji ClickOnce  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.  
  
2.  Wybierz **publikowania** okienka.  
  
3.  Kliknij przycisk **wymagania wstępne** przycisk, aby otworzyć **wymagania wstępne** okno dialogowe.  
  
4.  W **wymagania wstępne** okna dialogowego upewnij się, że **Utwórz Instalatora, aby zainstalować wstępnie wymagane składniki** pole wyboru jest zaznaczone.  
  
5.  W **wymagania wstępne** listy, składników, które chcesz zainstalować, a następnie kliknij przycisk Sprawdź **OK**.  
  
     Wybrane składniki zostaną umieszczone i opublikowani razem aplikacji.  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Aby określić lokalizację pobierania różne wymagania wstępne  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.  
  
2.  Wybierz **publikowania** okienka.  
  
3.  Kliknij przycisk **wymagania wstępne** przycisk, aby otworzyć **wymagania wstępne** okno dialogowe.  
  
4.  W **wymagania wstępne** okna dialogowego upewnij się, że **Utwórz Instalatora, aby zainstalować wstępnie wymagane składniki** pole wyboru jest zaznaczone.  
  
5.  W **Określ lokalizację instalacji wymagań wstępnych** zaznacz **Pobierz wstępnie wymagane składniki z następującej lokalizacji**.  
  
6.  Wybierz lokalizację z listy rozwijanej lub wprowadź adres URL, ścieżka do pliku lub lokalizacji FTP, a następnie kliknij przycisk **OK.**  
  
    > [!NOTE]
    >  Należy się upewnić, że instalatorów określone składniki istnieje w określonej lokalizacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)