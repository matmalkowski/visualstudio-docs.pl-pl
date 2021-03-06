---
title: 'Błąd: Usługi zdalnego debugera Visual Studio na komputerze docelowym nie można połączyć z powrotem do tego komputera | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3cfd2db1e4bf5b87d12eb5d5ffcf94d06e142516
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471755"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Błąd: Usługa zdalnego debugera Visual Studio na komputerze docelowym nie może połączyć się ponownie z tym komputerem
Ten błąd oznacza, że usługa zdalnego debugera Visual Studio jest uruchomiona na koncie użytkownika, który nie może uwierzytelnić, gdy próbuje połączyć się z komputerem, który jest debugowany z.  
  
 W poniższej tabeli przedstawiono co konta można uzyskać dostępu do komputera:  
  
|||||  
|-|-|-|-|  
||Konto System lokalny|Konto domeny|Konta lokalne, które mają taką samą nazwę użytkownika i hasło na obu komputerach|  
|Oba komputery w tej samej domenie|Tak|Tak|Tak|  
|Oba komputery w domenach, które mają zaufanie dwukierunkowe|Nie|Nie|Tak|  
|Jeden lub oba komputery w grupie roboczej|Nie|Nie|Tak|  
|Komputery w różnych domenach|Nie|Nie|Tak|  
  
 Ponadto:  
  
-   Konto uruchamiania usługi zdalnego debugera Visual Studio w obszarze powinien być administratorem na komputerze zdalnym, dzięki czemu można debugować żaden proces.  
  
-   Konto ma również przyznane `Log on as a service` uprawnień na komputerze zdalnym, który używa **zasady zabezpieczeń lokalnych** narzędzie administracyjne.  
  
-   Jeśli korzystasz z lokalnego konta dostępu do komputera, należy uruchomić usługi zdalnego debugera Visual Studio przy użyciu lokalnego konta.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że usługa zdalnego debugera Visual Studio jest prawidłowo skonfigurowany na komputerze zdalnym. Aby uzyskać więcej informacji, zobacz [zdalnego debugowania](../debugger/remote-debugging.md).  
  
2.  Uruchom usługę zdalnego debugera na koncie dostęp do komputera hosta debugera, jak pokazano w poprzedniej tabeli.  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>Aby dodać uprawnienia "Zaloguj jako usługa"  
  
1.  Na **Start** menu, wybierz **Panelu sterowania**.  
  
2.  W Panelu sterowania, wybierz **Klasyczny**, jeśli to konieczne.  
  
3.  Kliknij dwukrotnie **narzędzia administracyjne**.  
  
4.  W oknie Narzędzia administracyjne kliknij dwukrotnie **zasady zabezpieczeń lokalnych**.  
  
5.  W **ustawienia zabezpieczeń lokalnych** okna, rozwiń węzeł **zasady lokalne** folderu.  
  
6.  Kliknij przycisk **Przypisywanie praw użytkownika**.  
  
7.  W **zasad** kolumny, kliknij dwukrotnie **Zaloguj jako usługa** Aby wyświetlić bieżące przypisania zasad grupy lokalne, w **Zaloguj jako usługa** okno dialogowe.  
  
8.  Do dodawania nowych użytkowników, kliknij przycisk **Dodaj użytkownika lub grupę** przycisku.  
  
9. Po zakończeniu dodawania użytkowników kliknij **OK**.  
  
### <a name="to-work-around-this-error"></a>Aby obejść ten błąd  
  
-   Uruchom Monitor debugera zdalnego jako aplikacji zamiast usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdalne debugowanie błędów i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)