---
title: Start | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 563120e107b6b6e16c9a1512cc073e0866f61ef1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="start"></a>Uruchamianie
**Start** opcja to opcja VSPerfCmd.exe, która inicjuje profilera do określonej metody profilowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Method`  
 Musi mieć jedną z następujących słów kluczowych:  
  
-   **ŚLEDZENIA** — określa metody instrumentacji.  
  
-   **Przykładowe** — określa metody pobierania próbek.  
  
-   **POKRYCIE** — określa pokrycia kodu.  
  
-   **WSPÓŁBIEŻNOŚĆ** — określa metodę kontencji zasobów.  
  
## <a name="required-options"></a>Wymagane opcje  
 **Dane wyjściowe** opcja musi być określona gdy **Start** jest określona w wierszu polecenia.  
  
 **Dane wyjściowe:** `filename`  
 Określa nazwę pliku wyjściowego.  
  
## <a name="exclusive-options"></a>Wykluczających się opcji  
 Następujące opcje można używać tylko z **Start** opcji wiersza polecenia.  
  
 **CrossSession**&#124;**CS**  
 Umożliwia międzyprocesowa profilowania. Nazwy opcji **CrossSession** i **CS** są obsługiwane.  
  
 **Użytkownik:**[`domain\`]`username`  
 Umożliwia dostęp klienta do monitora z określonego konta.  
  
 **WinCounter:** `Path` [**Automark**:`n`]  
 **WinCounter** Określa licznik wydajności systemu Windows, aby uwzględnić jako znacznik w pliku danych profilowania. **AutoMark** Określa interwał w milisekundach między kolekcjami pliku danych.  
  
## <a name="invalid-options"></a>Nieprawidłowe opcje  
 Nie można używać następujących opcji z **Start** opcji wiersza polecenia.  
  
 **Status**  
 **Stan** dotyczy tych procesów, które są profilowaniu. Wyświetlane są procesów i wątków oraz ich bieżący stan profilu (wł. / wył.). Na przykład, jeśli proces zostanie zatrzymana **stan** nie będzie wskazywać to w raporcie. **Stan** opisano proces albo jest profilowane lub nie.  
  
 **Zamknięcie**[**:**`Timeout`]  
 Wyłącza profilera.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia VSPerfCmd.exe **Start** opcji inicjowania profilera.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)