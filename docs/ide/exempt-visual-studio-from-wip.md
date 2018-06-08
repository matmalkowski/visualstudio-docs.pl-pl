---
title: Wykluczone z ochrony informacji systemu Windows
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1a1b38e6e30a816382da72ef8280868fa68dfb10
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845895"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>Konfigurowanie programu Visual Studio jako aplikacja wykluczona pracy w toku

[Rozwiązanie Windows Information Protection](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) (pracy w toku) pomaga chronić dane przedsiębiorstwa przed wyciekiem do aplikacji, takich jak poczty e-mail, media społecznościowe i chmura publiczna, które są poza kontrolą przedsiębiorstwa. Pracy w toku pomaga chronić przed wyciekiem danych przypadkowemu z urządzeń należących do przedsiębiorstwa oraz urządzeń osobistych, bez konieczności wprowadzania zmian w Twoim środowisku lub innych aplikacji.

*Z obsługą* aby zapobiec przechodząc do lokalizacji sieciowych niechronione danych przedsiębiorstwa i uniknąć szyfrowania danych osobowych powinny aplikacji do pracy w toku. Program Visual Studio nie jest usprawnionych aplikacji, więc nie działa w środowiskach z obsługą pracy w toku, chyba że go wyłączyć. Wykonaj kroki opisane w tym artykule, aby włączyć program Visual Studio do funkcji na komputerze z włączonym pracy w toku.

## <a name="configure-vs-as-a-wip-exempt-app"></a>Konfigurowanie programu VS jako aplikację wykluczona pracy w toku

Można zwolnić Visual Studio z ograniczeń pracy w toku, ale nadal zezwolić na używanie danych przedsiębiorstwa. Aplikacje wykluczona pracy w toku mogą łączyć się przy użyciu adresu IP lub nazwy hosta zasobów chmury przedsiębiorstwa. Nie jest zastosowano szyfrowania, a aplikacja może uzyskiwać dostęp do lokalnych plików.

Aby wyłączyć program Visual Studio z pracy w toku, wykonaj [kroki, aby zwolnić aplikacji komputerowej](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy).

## <a name="create-a-wip-exempt-applocker-policy-file"></a>Utwórz plik zasad funkcji AppLocker wykluczona pracy w toku

Ponieważ program Visual Studio zawiera wiele plików binarnych, [Tworzenie pliku zasad funkcji AppLocker wykluczona pracy w toku](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard). Funkcja AppLocker umożliwia automatyczne generowanie reguł dla wszystkich plików w folderze.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>Dodaj AppCompat do zasad zasobów chmury przedsiębiorstwa

Aby określić, gdzie programu Visual Studio mają dostęp do danych przedsiębiorstwa w sieci, wykonaj następujące [kroki, aby zdefiniować, gdzie chronionych aplikacji można znaleźć i wysyłać dane przedsiębiorstwa](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data). Aby zatrzymać systemu Windows blokuje połączenia do chmury zasobów za pomocą adresu IP, upewnij się dodać /\*AppCompat\*/ ciąg do ustawienia.

## <a name="see-also"></a>Zobacz także

- [Zachowanie aplikacji z pracy w toku](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)