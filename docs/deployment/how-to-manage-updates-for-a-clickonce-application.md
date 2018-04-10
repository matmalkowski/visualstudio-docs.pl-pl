---
title: 'Porady: Zarządzanie aktualizacji dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: f239f13a7dcefe0ce6f2bf8c12c641e97a48ce26
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Porady: zarządzanie aktualizacji dla aplikacji ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje można sprawdzić aktualizacje automatyczne lub programowo. Deweloperzy masz dużą elastyczność określania, kiedy i jak aktualizacji są sprawdzane, czy aktualizacje są obowiązkowe i gdy aplikacja ma sprawdzać dostępność aktualizacji.  
  
 Można skonfigurować aplikację do sprawdzania aktualizacji automatycznie przed uruchomieniem aplikacji lub w ustalonych odstępach czasu, po uruchomieniu aplikacji. Ponadto można określić minimalnej wymaganej wersji; oznacza to, że aktualizacja jest zainstalowana, jeśli jego wersja jest starsza niż wymagana wersja.  
  
 Można skonfigurować aplikację do sprawdzania aktualizacji programowo oparte na zdarzeniach takich jak żądanie użytkownika. Procedury "Aby wyszukać aktualizacje programowo" w tym temacie przedstawiono sposób czy pisania kodu, który używa <xref:System.Deployment.Application.ApplicationDeployment> klasy, aby wyszukać aktualizacje na podstawie zdarzenia.  
  
 Można także wdrożyć aplikację z jednej lokalizacji i zaktualizować go z innej. Zapoznaj się z procedurą "Aby określić lokalizację inną aktualizację."  
  
 Aby uzyskać więcej informacji, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Zachowanie aktualizacji jest zarządzana w **aktualizacji aplikacji** okno dialogowe, dostępne z **publikowania** strony **projektanta projektu.**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>Aby sprawdzić dostępność aktualizacji przed uruchomieniem aplikacji  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  Kliknij przycisk **aktualizacje** przycisk, aby otworzyć **aktualizacji aplikacji** okno dialogowe.  
  
4.  W **aktualizacji aplikacji** okna dialogowego upewnij się, że **aplikacja ma sprawdzać dostępność aktualizacji** pole wyboru jest zaznaczone.  
  
5.  W **wybierz, gdy aplikacja ma sprawdzać dostępność aktualizacji** zaznacz **przed uruchomieniem aplikacji**. Dzięki temu, że użytkownicy połączeni z siecią zawsze uruchomić aplikację z najnowszymi aktualizacjami.  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Aby sprawdzić dostępność aktualizacji w tle, po uruchomieniu aplikacji  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  Kliknij przycisk **aktualizacje** przycisk, aby otworzyć **aktualizacji aplikacji** okno dialogowe.  
  
4.  W **aktualizacji aplikacji** okna dialogowego upewnij się, że pole wyboru **aplikacja ma sprawdzać dostępność aktualizacji** jest zaznaczone.  
  
5.  W **wybierz, gdy aplikacja ma sprawdzać dostępność aktualizacji sekcji**, wybierz pozycję **po uruchomieniu aplikacji**. Aplikacja zostanie uruchomiona szybciej w ten sposób, a następnie go będzie Wyszukaj aktualizacje w tle, Powiadom użytkownika, gdy dostępna jest aktualizacja. Po zainstalowaniu aktualizacji nie zostały wprowadzone do czasu ponownego uruchomienia aplikacji.  
  
6.  W **Określ, jak często aplikacja ma sprawdzać dostępność aktualizacji** wybierz opcję **Sprawdź za każdym razem, gdy aplikacja zostanie uruchomiona** (ustawienie domyślne) lub **Sprawdź każdy** i wprowadź interwał numerów i czasu.  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Aby określić minimalną wersję wymaganą dla aplikacji  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  Kliknij przycisk **aktualizacje** przycisk, aby otworzyć **aktualizacji aplikacji** okno dialogowe.  
  
4.  W **aktualizacji aplikacji** okna dialogowego upewnij się, że **aplikacja ma sprawdzać dostępność aktualizacji** pole wyboru jest zaznaczone.  
  
5.  Wybierz **określ minimalną wersję wymaganą dla tej aplikacji** pole wyboru, a następnie wprowadź **głównych**, **pomocnicza**, **kompilacji**i  **Poprawki** numery dla aplikacji.  
  
### <a name="to-specify-a-different-update-location"></a>Aby określić lokalizację inną aktualizację  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  Kliknij przycisk **aktualizacje** przycisk, aby otworzyć **aktualizacji aplikacji** okno dialogowe.  
  
4.  W **aktualizacji aplikacji** okna dialogowego upewnij się, że **aplikacja ma sprawdzać dostępność aktualizacji** pole wyboru jest zaznaczone.  
  
5.  W **zaktualizować lokalizację** wprowadź lokalizację aktualizacji z w pełni kwalifikowany adres URL w formacie http://Hostname/ApplicationName, lub ścieżkę UNC w formacie \\\Server\ApplicationName, lub kliknij przycisk **Przeglądaj** przycisk Przeglądaj w poszukiwaniu lokalizacji aktualizacji.  
  
### <a name="to-check-for-updates-programmatically"></a>Aby wyszukać aktualizacje programowo  
  
1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **publikowania** kartę.  
  
3.  Kliknij przycisk **aktualizacje** przycisk, aby otworzyć **aktualizacji aplikacji** okno dialogowe.  
  
4.  W **aktualizacji aplikacji** okna dialogowego upewnij się, że **aplikacja ma sprawdzać dostępność aktualizacji** pole wyboru jest wyczyszczone. (Opcjonalnie można zaznacz to pole wyboru w celu wyszukania aktualizacji programowo, a także umożliwić środowiska uruchomieniowego ClickOnce sprawdzał dostępność aktualizacji.)  
  
5.  W **zaktualizować lokalizację** wprowadź lokalizację aktualizacji z w pełni kwalifikowany adres URL w formacie http://Hostname/ApplicationName, lub ścieżkę UNC w formacie \\\Server\ApplicationName, lub kliknij przycisk **Przeglądaj** przycisk Przeglądaj w poszukiwaniu lokalizacji aktualizacji. Lokalizacja aktualizacji jest, gdzie aplikacja będzie szukać zaktualizowana wersja tego samego.  
  
6.  Utwórz przycisk, element menu lub innego elementu interfejsu użytkownika na formularzu systemu Windows, która będzie wybierać użytkowników, aby wyszukać aktualizacje. Z obsługi zdarzeń dla tego elementu należy wywołać metodę Sprawdź i zainstaluj aktualizacje. Przykładowy kod Visual Basic i Visual C# można znaleźć metody w [porady: Sprawdź, czy aplikacja aktualizacje programowo przy użyciu wdrażania interfejsu API ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).  
  
7.  Tworzenie aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [Okno dialogowe aktualizacje aplikacji](http://msdn.microsoft.com/en-us/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Instrukcje: sprawdzanie aktualizacji aplikacji w sposób programowy za pomocą wdrażania interfejsu API technologii ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)