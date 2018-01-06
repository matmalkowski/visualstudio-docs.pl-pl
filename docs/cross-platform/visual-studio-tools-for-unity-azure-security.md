---
title: "Visual Studio Tools for Unity Azure wskazówki zabezpieczeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: F4FD6E1C-EA64-4613-BDDE-6E4E5CCF983E
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 1ffb0c57329a8453208978cee69daa771d8ee0e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="update-unity-mono-security-certificate-store"></a>Magazyn certyfikatów zabezpieczeń Unity Mono aktualizacji

Mono Unity firmy jest dostarczany z magazynu certyfikatów pusty i w związku z tym nie ufa dowolnej lokacji. Więcej na temat [Mono zabezpieczeń — często zadawane pytania](http://www.mono-project.com/docs/faq/security/).

W celu połączenia z platformą Azure bez ignorowanie TLS / SSL, Unity Mono magazynu certyfikatów musi być aktualizowane.

## <a name="using-mozroots-to-install-certificates"></a>Instalowanie certyfikatów za pomocą mozroots

Narzędzie mozroots jest dołączone do Mono. Go pobiera i instaluje firmy Mozilla listy certyfikatów głównych.

1. Otwórz wiersz polecenia terminala.

2. Przejdź w terminalu, aby **C:\Program Files\Unity\Editor\Data\MonoBleedingEdge\bin >** katalogu. Lokalizacja może się różnić w zależności od tego, gdzie Unity jest zainstalowany na komputerze lokalnym.

3. Wpisz następujące polecenie i naciśnij **Enter** uruchamiania:

  `mono ..\lib\mono\4.5\mozroots.exe --sync --import`

4. Należy pobrać następujące wyniki (chociaż numer lub dodać certyfikaty mogą różnić się):

  ```
  Downloading from 'https://hg.mozilla.org/releases/mozilla-release/raw-file/default/security/nss/lib/ckfw/builtins/certdata.txt'...
  Importing certificates into user store...
  1 new root certificates were added to your trust store.
  Import process completed.
  ```

5. Teraz powinno być możliwe do uruchomienia przykładowy projekt bez otrzymania TLS powiązane błędy.

## <a name="next-step"></a>Następny krok

* [Testowanie połączenia klienta](visual-studio-tools-for-unity-azure-connection.md)
