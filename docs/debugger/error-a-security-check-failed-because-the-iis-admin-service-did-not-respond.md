---
title: 'Błąd: Sprawdzanie zabezpieczeń nie powiodło się, ponieważ usługa administratora usług IIS nie odpowiada. | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3b0b3412c450976cb15211813de32ab6e78eaa9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471115"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Błąd: Sprawdzanie zabezpieczeń nie powiodło się ponieważ usługa administratora nie odpowiada
Ten błąd występuje, gdy administrator usług IIS nie odpowiada. Zwykle oznacza to, że jest problem z instalacją usług IIS. Po pierwsze sprawdzenie, czy usługa jest uruchomiona za pomocą **usług** narzędzia z **narzędzia administracyjne**.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Ponownie zainstaluj usługi IIS, za pomocą **Dodaj lub usuń programy** Panelu sterowania.  
  
-   —lub—  
  
-   Usuwanie usług IIS z komputera, za pomocą apletu Dodaj lub usuń programy w Panelu sterowania. Jeśli usunięto usług IIS i nadal występują problemy, sprawdź w rejestrze i upewnij się, że ten klucz już istnieje:  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     —lub—  
  
-   Wyłącz usługę administratora usług IIS przy użyciu narzędzia administracyjne w Panelu sterowania. Spowoduje to wyłączenie usług IIS na tym komputerze.  
  
     Po wykonaniu któregokolwiek te trzy kroki, uruchom ponownie komputer.  
  
     Aby uzyskać dodatkowe informacje Zobacz dokumentację usług IIS.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji sieci Web: Błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)