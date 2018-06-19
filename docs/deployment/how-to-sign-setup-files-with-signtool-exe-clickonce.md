---
title: 'Porady: podpisywanie plików konfiguracji przy SignTool.exe (ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc4dc7b2f96b1d36e91e8114458a7a8e9f3231f3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31566124"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Porady: podpisywanie plików konfiguracji przy użyciu narzędzia SignTool.exe (ClickOnce)
SignTool.exe służący do podpisywania program instalacyjny (setup.exe). Ten proces zapewnia, że zmodyfikowany pliki nie są zainstalowane na komputerach użytkowników końcowych.  
  
 Domyślnie ClickOnce podpisała manifestów i podpisem program instalacyjny. Jednak jeśli chcesz zmienić parametry Instalatora później, należy się zalogować Instalatora później. Zmiana parametrów po podpisaniu Instalatora sygnatury uległa uszkodzeniu.  
  
 Poniższa procedura generuje manifestów bez znaku i bez znaku program instalacyjny. Następnie w wygenerować podpisanych manifestów ClickOnce podpisywania jest włączona w programie Visual Studio. Pozostało program instalacyjny bez znaku, aby zarejestrować plik wykonywalny z własnych certyfikatów klienta.  
  
### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>Aby wygenerować niepodpisane program instalacyjny i zarejestrować później  
  
1.  Na komputerze dewelopera, należy zainstalować certyfikat, które mają znak manifesty z.  
  
2.  Wybierz projekt **Eksploratora rozwiązań**.  
  
3.  Na **projektu** menu, kliknij przycisk *ProjectName* **właściwości**.  
  
4.  W **podpisywanie** wyczyść **podpisania manifestów ClickOnce**.  
  
5.  W **publikowania** kliknij przycisk **wymagania wstępne**.  
  
6.  Sprawdź, czy wszystkie wymagania wstępne są zaznaczone, a następnie kliknij **OK**.  
  
7.  W **publikowania** strony, sprawdź ustawienia publikowania, a następnie kliknij przycisk **opublikować teraz**.  
  
     Rozwiązanie publikuje manifest aplikacji bez znaku, manifest wdrażania bez znaku, specyficzne dla wersji plików i bez znaku program instalacyjny do publikowania lokalizacji folderu.  
  
8.  W **publikowania** kliknij przycisk **wymagania wstępne**.  
  
9. W **wymagania wstępne** okno dialogowe, usuń zaznaczenie **Utwórz Instalatora, aby zainstalować wstępnie wymagane składniki**.  
  
10. W **publikowania** strony, sprawdź ustawienia publikowania, a następnie kliknij przycisk **opublikować teraz**.  
  
     Rozwiązanie publikuje manifestu podpisaną aplikację, manifest rozmieszczenia podpisane i specyficzne dla wersji plików do publikowania lokalizacji folderu. Niepodpisane program instalacyjny nie jest zastępowana przez proces publikowania.  
  
11. W lokacji klienta otwórz wiersz polecenia.  
  
12. Przejdź do katalogu, w którym znajduje się plik .exe.  
  
13. Utwórz plik .exe przy użyciu następującego polecenia:  
  
    ```  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     Na przykład do podpisania Instalatora, użyj jednej z następujących poleceń:  
  
    ```  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md)