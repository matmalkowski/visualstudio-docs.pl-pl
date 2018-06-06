---
title: Strona publikowania, Projektant projektu (Office development w Visual Studio)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d63044dbe191a2143b4800b57ee5344bf030107d
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692847"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Strona publikowania, Projektant projektu (Office development w Visual Studio)
  **Publikowania** strony **projektanta projektu** służy do konfigurowania właściwości wdrożenia.  
  
 Dostępu do tej strony, wybierz projekt **Eksploratora rozwiązań**, a następnie na **projektu** menu, wybierz *Projectname* **właściwości** . Jeśli **publikowania** nie zostanie wyświetlona strona, wybierz **publikowania** kartę.  
  
> [!NOTE]  
>  Można też ustawić lokalizację publikowania w **Kreator publikowania**. Aby uzyskać więcej informacji, zobacz [porady: publikowanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).  
  
## <a name="uielement-list"></a>Lista elementów interfejsu użytkownika  
 **Lokalizację folderu publikowania (witryny sieci web, serwera ftp lub ścieżka pliku)**  
 Wymagana.  
  
 Lokalizacja folderu publikowania jest katalogu, do którego Visual Studio kopiuje pliki rozwiązania, takie jak manifesty zestawów i innych plików z kompilacji. Musi mieć dostęp do zapisu do tego katalogu.  
  
 Obejmują one komputera lokalnego, udziałem pliku UNC lub witryny sieci web HTTP/HTTPS. Ścieżka może być kontem lokalnym (*c:\foldername\publishfolder*) względnych (*publikowania\\*), lub w pełni kwalifikowaną lokalizacji (*\\\servername\foldername* lub http://*servername/nazwa folderu*).  
  
 Domyślnie jest lokalizację publikowania *http://localhost/projectname/* Jeśli usługi IIS są zainstalowane, lub *publikowania\\*  katalogu, jeśli nie masz zainstalowane usługi IIS.  
  
 **Adres URL folderu instalacji**  
 Opcjonalna.  
  
 Adres URL folderu instalacji jest katalogu, z którego użytkownik końcowy zainstaluje dostosowań. Istnieje również ścieżki, który rozwiązanie będzie używany do sprawdzania aktualizacji. Ścieżka może być taka sama jak lokalizacja folderu publikowania, ale nie jest wymagane.  
  
 Obejmują one komputera lokalnego, udziałem pliku UNC lub witryny sieci web HTTP/HTTPS. Ścieżka może być kontem lokalnym (*c:\foldername\publishfolder*) względnych (*publikowania\\*), lub w pełni kwalifikowaną lokalizacji (*\\\servername\foldername* lub http://*servername/nazwa folderu*). Wszystkie lokalizacje HTTP/HTTPS, należy utworzyć znakami US-ASCII. Znaki Unicode nie są obsługiwane.  
  
 Jeśli ścieżka instalacji jest ustawiona, pliki dostosowania muszą być w tej lokalizacji, użytkownicy mogą zainstalować dostosowań. Lokalizacja powinna być ustawiona tylko wtedy, gdy znasz lokalizacji końcowej wdrożenia.  
  
 Jeśli pliki instalacyjne znajdują się w lokalizacji względnej wobec dokumentu lub program instalacyjny, takich jak z opcją dysku CD, pozostaw to pole puste.  
  
 Tę wartość można przypisać później przez administratora. Aby uzyskać więcej informacji, zobacz [porady: Zmienianie ścieżki instalacji rozwiązania do pakietu Office](http://msdn.microsoft.com/en-us/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 **Wymagania wstępne**  
 Wymagania wstępne można dołączone do programu instalacyjnego lub pobrany na żądanie podczas instalacji.  
  
-   **Pobierz wstępnie wymagane składniki z witryny dostawcy składników**: Użyj tej opcji, aby pobrać te wymagania wstępne firmy Microsoft.  
  
-   **Pobierz wstępnie wymagane składniki z tej samej lokalizacji co Moja aplikacja**: Użyj tej opcji do wymagań wstępnych w Instalatorem pakietu. W tym pliki wymagań wstępnych programu instalacyjnego spowoduje zwiększenie rozmiaru rozwiązania.  
  
-   **Pobierz wstępnie wymagane składniki z następującej lokalizacji**: Użyj tej opcji do udostępnienia wymagania wstępne dla użytkowników końcowych oddzielnie jako inny program instalacyjny na stronie sieci web lub udziału sieciowego.  
  
 **Aktualizacje**  
 Interwał aktualizacji określa, jak często rozwiązania sprawdza dostępność aktualizacji. Wartość domyślna to do sprawdzenia co siedem dni.  
  
 Sprawdzanie dostępności aktualizacji za każdym razem, gdy dostosowania na poziomie dokumentu lub VSTO dodatek jest załadowany zachowa aktualizacji, ale mających wpływ na wydajność uruchamiania.  
  
 Jeśli wdrażasz przy użyciu dysku CD lub dysk wymienny, ustaw tę wartość na **nigdy nie sprawdzaj aktualizacji**.  
  
 **Opcje (opis)**  
 Można skonfigurować opcje publikowania dla następujących właściwości:  
  
-   Języka publikacji: ustawienia regionalne rozwiązania pakietu Office.  
  
-   Nazwa wydawcy: Nazwa firmy lub deweloperem, ponieważ jest wyświetlana w **Dodaj lub usuń programy** lub **programy i funkcje**.  
  
-   Nazwa produktu: Nazwa rozwiązania pakietu Office, w jakiej jest wyświetlana w **Dodaj lub usuń programy** lub **programy i funkcje**.  
  
-   Adres URL pomocy technicznej: lokalizacja dla użytkowników końcowych do kontaktowania się z działem pomocy technicznej dla rozwiązań pakietu Office.  
  
 **Opcje (ustawienia pakietu Office)**  
 Można skonfigurować opcje publikowania dla następujących właściwości:  
  
-   Nazwa rozwiązania: Nazwa rozwiązania pakietu Office, w jakiej jest wyświetlana w aplikacji pakietu Office.  
  
-   Opis: opis rozwiązania pakietu Office, w jakiej jest wyświetlany w aplikacji pakietu Office.  
  
-   Zachowanie obciążenia w dodatku VSTO.  
  
    -   Obciążenia podczas uruchamiania: Określa, czy dodatku VSTO ładuje podczas uruchamiania aplikacji pakietu Office.  
  
    -   Obciążenia na żądanie: Określa, że dodatku VSTO ładuje, kiedy aplikacja wymaga, np. gdy użytkownik kliknie element interfejsu użytkownika, który korzysta z funkcji w dodatku VSTO.  
  
 **Języka publikacji**  
 Ta opcja określa język postanowienia licencyjne dotyczące oprogramowania firmy Microsoft i zawiera listę wymagań wstępnych, pakiety językowe. Nie ma ona wpływu na język dostosowań. Język w programie instalacyjnym jest określana przez zainstalowane języki programu Visual Studio.  
  
 Aby uzyskać więcej informacji na temat zmiany **języka publikacji**, zobacz [porady: Zmienianie języka publikacji dla aplikacji ClickOnce](/visualstudio/deployment/how-to-change-the-publish-language-for-a-clickonce-application).  
  
 **Opublikuj wersję**  
 Ustawia numer wersji do dostosowania. Po zmianie numeru wersji aplikacji jest publikowany jako aktualizacja. Nowy folder jest tworzony dla każdej wersji podczas procesu kompilacji, aby zapobiec zastąpieniu poprzednio opublikowanej wersji. Każda część wersji publikowania (**głównych**, **pomocnicza**, **kompilacji**, **poprawki**) może zawierać maksymalnie pięciu cyfr.  
  
 **Automatycznie zwiększ numer poprawki przy każdej wersji**  
 Opcjonalna. W przypadku wybrania (ustawienie domyślne), **poprawki** część numeru wersji jest zwiększany o jeden dostosowań zostanie opublikowana. Powoduje to, że dostosowania, które mają zostać opublikowane jako aktualizacja.  
  
 **Publikuj teraz**  
 Publikowanie aplikacji przy użyciu bieżących ustawień. Odpowiednikiem **Zakończ** przycisk **Kreator publikowania**.  
  
## <a name="see-also"></a>Zobacz także  
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Wdrażanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Wymagania wstępne rozwiązania pakietu Office dla wdrożenia](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e)  
  
  