---
title: "Obowiązków administratora | Visual Studio Marketplace"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Learn about responsibilities of subscriptions administrators.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 92dcfe8b975596fc2f137630f6acfead6b935508
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="administrator-overview"></a>Omówienie administratora
## <a name="roles--responsibilities"></a>Role i obowiązki
W zamian za obniżonej cenie na swoich produktów i usług organizacja wyraża zgodę na określonych obowiązków i ograniczenia dotyczące subskrypcji programu Visual Studio. Administrator programu Visual Studio ma cztery obowiązki klucza:
1.  **Zrozumieć korzyści i ograniczenia subskrypcji programu Visual Studio.** Poprawnie opis korzyści programu można włączyć można zmniejszyć koszty sprzętu przy użyciu usługi w chmurze i zmniejszyć koszty oprogramowania z licencjami na użytkownika w środowiskach produkcji wstępnej. 
2.  **Przypisz subskrypcji programu Visual Studio do określonych, o nazwie osób, a następnie zachęcić użycia.** Dany kontrakt wymaga przypisania do osób, określone, o nazwie subskrypcji programu Visual Studio. Dostosuj się z przypisaną osób zapewniające dostęp i w pełni korzystać z zalet zawarte w ich subskrypcja programu Visual Studio.
3.  **Dokładnie spisu w środowisku przedprodukcyjnym.** Jest to konieczne w celu zapewnienia, że wszyscy użytkownicy, którzy prowadzą interakcję z oprogramowania z licencją programu Visual Studio są odpowiednio licencjonowane własnych subskrypcji programu Visual Studio. 
4.  **Śledzenie zmian w przypisaniu użytkownika i nabyć dodatkowe licencje zgodnie z harmonogramem.** Umowy Microsoft wolumin Licencjonowania zapewniają elastyczność w sposób używania i przypisać subskrypcji programu Visual Studio. W zamian powinny śledzić zmiany użycia oprogramowania i przypisania użytkowników oraz proces zamówień dodatkowe licencje zgodnie z harmonogramem opisane w umowie.

## <a name="benefits-and-limitations"></a>Korzyści i ograniczenia
Subskrypcje w Visual Studio umożliwia członkom zespołu, aby zainstalować i używać oprogramowania do projektowanie, tworzenie, testowanie i ocena rozwoju i Wykaż, innego oprogramowania. Oprogramowania Visual Studio subskrypcji nie jest licencjonowany do środowiska produkcyjnego. 

|                                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Oparta na użytkowniku licencjonowania                     | Platformy MSDN i na wszystkich poziomach subskrypcji programu Visual Studio są licencjonowane na poszczególnych użytkowników. Każdego członka zespołu Programowanie będzie współpracować (instalowanie, konfigurowanie lub dostępu do) z oprogramowania z tych produktów i usług wymaga subskrypcję programu Visual Studio.                                                                                                                                                                                                                                                                                                                                  |
| Nieograniczone instalacji                  | Każdy użytkownik mający licencję może zainstalować i korzystać z oprogramowania na dowolnej liczbie urządzeń na projektowanie, tworzenie, testowanie i ocenić i prezentacja oprogramowania. Wyjątek stanowi Microsoft Office, która jest licencjonowana dla jednego pulpitu. Visual Studio licencjonowanego oprogramowania można instalować i używane w pracy, home, szkoły i na urządzeniach w biurze klienta lub na dedykowanym sprzęcie hostowana przez inną firmę.                                                                                                                                                                                                                                  |
| Nie jest przeznaczona dla środowisk produkcyjnych | Oprogramowania subskrypcji Visual Studio nie ma licencji w środowiskach produkcyjnych, łącznie z dowolnym środowisku używane przez użytkowników końcowych przez ponad testów akceptacyjnych lub opinie na temat nawiązywania połączenia z bazą danych produkcyjnych, środowisko obsługi odzyskiwania po awarii lub Produkcja kopii zapasowej lub używanego w środowisku produkcyjnym w okresach szczytowego aktywności. Wyjątki od tej reguły obejmują korzyści niektórych poziomów subskrypcji, opisane w temacie [programu Visual Studio licencjonowania oficjalny dokument](http://aka.ms/vslicensing).                                                                                            |
| Ponowne przypisanie licencji                     | Gdy użytkownik opuści zespołu i nie wymaga już licencji, może zmienić przypisanie licencji, po upływie 90 dni. Po przypisaniu licencji nie można zamienić żadnych kluczy produktów, które zostały już użyte. Jest to funkcji innej niż istniał już w wolumin licencjonowania Service Center (VLSC). Wszystkie korzyści, które były używane dla oryginalnego użytkownika, takich jak szkolenia Pluralsight zostaną zresetowane.                                                                                                                                                                                                                                                 |
| Wyjątek dla użytkowników końcowych                  | Po zakończeniu tworzenia projektu oprogramowania użytkownicy końcowi zwykle Przegląd aplikacji i określenie, czy spełnia kryteria niezbędne w wersji. Ten proces jest nazywany testy Akceptacyjne akceptacji użytkownika. Członkowie zespołu, takie jak sponsor biznesowych lub Menedżer produktu może działać jako serwer proxy dla użytkowników końcowych. Użytkownicy końcowi, którzy nie mają subskrypcji programu Visual Studio może uzyskiwać dostęp do oprogramowania dla UAT Jeśli korzystanie z oprogramowania, w przeciwnym razie spełnia wszystkie Visual Studio umowy licencyjnej. Jest rzadko ktoś projektowanie, tworzenie lub testowania oprogramowania którego podstawową rolą również umożliwi zakwalifikowanie jako "użytkownik końcowy". |

## <a name="inventory-of-pre-production-environment"></a>Spis w środowisku przedprodukcyjnym
Visual Studio subskrypcje uprościć zarządzanie zasobami zliczanie użytkowników, a nie urządzeń.

Administratorzy usługi Visual Studio należy przypisać subskrypcji programu Visual Studio **osoby określone, nazwany**. Konwencje nazewnictwa, takich jak Dev1, Dev2 lub Dev3 są **niedozwolone**.

Poniżej przedstawiono kilka sposobów, aby uprościć spisu z argumentami środowiska produkcji wstępnej:
- Przejrzyj przypisaniami użytkownika. Firma Microsoft udostępnia witryny sieci Web o nazwie [portalu administracyjnego usługi Visual Studio](https://manage.visualstudio.com/) ułatwiające śledzenie przypisania subskrypcji programu Visual Studio.
- Użyj lokalnie lub w chmurze usługi Active Directory do listy użytkowników. Zarządzanie dostępem użytkowników za pomocą usługi Active Directory może być mógł rozpoznawać programowanie i testowanie użytkowników według ich członkostwa w katalogu.
- Narzędzia zautomatyzowanych systemów spisu. Ponadto może być konieczne użycie narzędzia stanu zapasów oprogramowania pomagające w zarządzaniu zasobami oprogramowania rozróżnienia produkcji wstępnej środowisk produkcyjnych z nich. Wielu klientów z programu Microsoft System Center utworzyć konwencje nazewnictwa w celu automatyzacji to część procesu spisu.
- Uzyskaj pomoc dotyczącą ręcznego uzgadniania. Zarejestrować działu, aby ułatwić uzgadnianie projektowania i testowania użytkownikami przy użyciu środowiska projektowania i testowania. 

## <a name="large-teams-and-external-contractors"></a>Duże zespoły i wykonawców zewnętrznych
Administratorzy subskrypcji w usłudze Visual Studio jest odpowiedzialny za zapewnienie, że każdy użytkownik, który współdziała z oprogramowania z licencją programu Visual Studio jest odpowiednio licencjonowane własnych subskrypcji programu Visual Studio.
### <a name="internal-teams"></a>Zespoły wewnętrzne
Zwykle organizacje nowoczesnych oprogramowania zawierają uczestników z kilku grup. Zidentyfikuj kontakty z każdej grupy, który pomoże Ci śledzić użytkownika spisu i zmiany. Każda organizacja jest inny, ale listę typowych zespołów zajmujących się programowanie może obejmować:
- Zespoły inżynieryjne oprogramowania. 
- Zespoły firmy, tym właścicieli produktu i analitycy biznesowi.
- Zespoły zarządzania projektu. 
- Jakość zespołów, w tym personelu jednostki i testerów ręcznych.
- Operacje IT, w tym zarządzających infrastrukturą produkcji wstępnej i laboratorium.

### <a name="external-contractors-and-partners"></a>Zewnętrznych kontrahentów i partnerów
Zewnętrznych wykonawców może zwrócić licencji nawiązanie połączenia ze środowiskiem licencję programu Visual Studio. Certyfikowanymi partnerami firmy Microsoft może się pojawić kilka bezpłatnej subskrypcji programu Visual Studio do użytku wewnętrznego. Jednak te subskrypcje nie obejmują działania generowania przychodów, takie jak tworzenie niestandardowego oprogramowania dla klienta. Poproś partnerami, aby wysłać certyfikowanych litery, który objaśnia licencji, które zapewniają one i konieczne jest uzyskania z nich.

## <a name="track-user-assignment-and-process-orders"></a>Śledzenie zamówień proces i przypisanie użytkownika
Administratorzy subskrypcji w usłudze Visual Studio powinny śledzić użycie programu Visual Studio i przetworzyć zamówienia dla dowolnego wzrost użycia zgodnie z harmonogramem opisane w ich umowy licencjonowania zbiorowego lub Microsoft Products i umowy o świadczenie usług. Nowy portal administracyjnej subskrypcji w usłudze Visual Studio wprowadził to proste z przydatne śledzenia, przedstawiający dostępnych i używanych licencji.
### <a name="high-water-mark-of-usage"></a>Znacznik limitu górnego użycia
**Zobowiązanie firmy kupować subskrypcje Visual Studio obowiązuje natychmiast po:**
- Licencja jest przypisana do użytkownika.
- Użytkownik korzysta z oprogramowania Visual Studio.

Na zakończenie zakupu zobowiązania jest określany przez **górny limit użycia**. Znaku wodnego jest punktem wysokiej codzienne przypisania użytkownika lub użytkowników korzysta z oprogramowania Visual Studio, zależności jest wyższa.
1.  Administratorzy subskrypcji w usłudze Visual Studio może zwiększyć górny limit użycia, przypisując subskrypcje w Visual Studio do osób.
2.  Jeśli upłynie 90 dni od czasu przypisania oryginalnego Administratorzy subskrypcji w usłudze Visual Studio może ponownie przypisać subskrypcje z jednego abonenta. Aby uniknąć sztucznie wysokiej znaku wodnego, zawsze tym wcześniejszego usunięcia istniejącej subskrypcji, a następnie dodanie nowego.
3.  Administratorzy subskrypcji w usłudze Visual Studio może ulec zmianie poziomu przypisanej subskrypcji przez osoby, stanowiący spadek jednego przypisania i zwiększenia w innym. Gdy obniżyć subskrybenta przypisany poziom subskrypcji poszczególne natychmiast zaprzestać używania i odinstalować wszystko, co jest tylko w wyższego poziomu subskrypcji. 

### <a name="open-license-and-open-value"></a>Otwórz licencji i Open Value
Może przypisywanie subskrypcji przy użyciu innego programu licencjonowania zbiorowego firmy Microsoft, takich jak Microsoft Open License lub Open Value. Jeśli tak, należy przetworzyć zamówienia dla innych użytkowników w miesiącu, w którym użytkownicy (lub wykonawców zewnętrznych pracowników) rozpocząć interakcji z oprogramowania z licencją programu Visual Studio.
### <a name="enterprise-agreements"></a>Umowa Enterprise
Microsoft umowy Enterprise (EA), MPSA i wybierz umowy oraz zapewniają elastyczność w sposób używania i licencji oprogramowania Visual Studio w czasie. Administratorzy usługi Visual Studio należy roczne True nakaz można wyświetlić ich licencji na oprogramowanie do górnego limitu użycia ustalone w okresie umowy.